# Functional Requirements
## Core requirements
1. User can upload videos 
2. User can stream videos
## Out of scope
1. User can view information about a video like view count.
2. User can search for a video.
3. User can comment on a video.
4. User can see recommended video.
5. User can make a channel and manage their channel.
6. User can subscribe to channels.
# Nonfunctional Requirements
## Core requirements
1. The system should be highly available.
2. The system should allow for low latency streaming of videos, even in low bandwidth scenarios.
3. The system should support uploading and streaming large videos (10s of GBs).
4. The system should scale to a high number of videos uploaded and watched per day (~1M videos uploaded per day, 100M videos watched per day).
5. The system should support resumable uploads.
## Out of scope
1. The system should protect against bad content in videos.
2. The system should protect against bots or fake accounts uploading or consuming videos.
3. The system should have monitoring / alerting.
