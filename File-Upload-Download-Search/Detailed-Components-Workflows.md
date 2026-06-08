1) File Upload Pipeline (Direct-to-Storage with Multipart)

[ User Action ] ──> Drag & Drop a File
                         │
                         ▼
[ UI Layer ]    ──> Read file properties (Name: "video.mp4", Size: 50MB)
                         │
                         ▼
[ Step 1: Network ] ──> Automatically call POST /api/upload-init (Takes ~50ms)
                         │
                         ▼
[ Step 2: Network ] ──> Receive Presigned URL from backend (Takes ~10ms)
                         │
                         ▼
[ Step 3: Data ]    ──> Instantly fire HTTP PUT to S3 URL (Progress bar starts!)

2) Forward Index: Search for the given keyword in each document word by word.
Inverted Index: The mapping will be like a word and the list of documents in which that word exists. Elastic Search works based on this

3) Secure and Resiliant downloads:
Secure means Authorization is checked. and RBAC is checked

The presigned URL targets to CDN cache or the object storage
The bytes are streamed using standard browser streaming
