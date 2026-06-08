                 +---------------------------+

                     | Object Storage (S3 Event) |
                     +-------------+-------------+

                                   |
                                   v
                     +---------------------------+
                     | Message Queue (Kafka/SNS) |
                     +-------------+-------------+

                                   |
                                   v
                     +---------------------------+
                     |   Asynchronous Workers    |
                     +------+-------------+------+

                            |             |
           (Extract Text)   |             | (Extract Metadata)
                            v             v
             +-----------------+       +-----------------+

             | Apache Tika /   |       |   Elasticsearch |
             | OCR Pipeline    |       |   Inverted Index|
             +--------+--------+       +--------+--------+

                      |                         ^
                      |                         |
                      +-------------------------+
                            (Index Content)
