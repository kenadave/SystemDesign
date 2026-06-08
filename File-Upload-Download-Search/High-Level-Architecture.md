1) API Gateway acts as a reverse proxy, rate limiter, and SSL Termination
2) Metadata Service: Metadata DB acts as a SQL database for storing Metadata
3) Search service: Elastic Search is used
4) Notification service: Used for notifing user for the status of the file upload. It is on WebSocket connection

               +-------------------+

               |    API Gateway    |
               +---------+---------+

                         |
      +------------------+------------------+
      |                  |                  |
+-----v-----+      +-----v-----+      +-----v-----+

| Metadata  |      |   Search  |      | Notification|
|  Service  |      |  Service  |      |  Service  |
+-----+-----+      +-----+-----+      +-----+-----+

      |                  |                  |
+-----v-----+      +-----v-----+      +-----v-----+

| Metadata  |      | Elastic-  |      | Redis     |
|   DB      |      | search    |      | Pub/Sub   |
+-----------+      +-----------+      +-----------+
