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




-======================================================================================



[ Kafka Event ]
        │
        ▼
 1. Fetch File Metadata ──(Fast)──► Send directly to Elasticsearch Index
        │
        ▼
 2. Inspect File Type (PDF? PNG?)
        │
        ├── Is Image/Scanned PDF? ──► Send to OCR Pipeline ──┐
        │                                                     ▼
        └── Is Plain Text/Word?   ──► Send to Apache Tika ───┼─► 3. Raw Text Extracted
                                                                        │
                                                                        ▼
 4. Update Elasticsearch Index ◄────────────────────────────────────────┘
    (Appends raw text to the existing file document)
