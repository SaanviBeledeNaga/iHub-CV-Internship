# iHub-CV-Internship
## Week 1 — Video Frame Extraction

### Task 1 — Extract Frames from Video
- Downloaded a YouTube video using yt-dlp
- Extracted multiple frames using ffmpeg
-  [Source YouTube Video](https://youtu.be/wB-Zr35McIU)

### Task 2 — 1800 Frames & Reconstruction
- Extracted 1800 frames at 30fps from 1 minute of video
- Reconstructed frames back into a 1 minute video using ffmpeg
-  [Reconstructed Video](https://youtu.be/ZdLajfzKDuQ)

### Task 3 — Add Music
- Downloaded royalty-free music from Pixabay
- Clipped to 1 minute using Audacity
- Merged audio with video using ffmpeg
-  [Final Video with Music](https://youtu.be/QnuAquxG7xU)

---

## Week 2 — Object Detection

### Tasks 1, 2, 3
- Created Python virtual environment using venv
- Installed Ultralytics package
- Ran YOLOv8 pretrained object detection model
-  [Object Detection](https://drive.google.com/drive/folders/1dDGEY7tCzNHd2AUi6PjaAUvv60AeSuiP?usp=drive_link)

---

## Week 3 — Segmentation

### Task 1 — Semantic Segmentation
- Ran YOLOv8 segmentation on animal images
- Each object segmented with unique colored pixel mask
- Stitched segmented frames back into video with new music

#### Performance Metrics
| Metric | Value |
|--------|-------|
| Precision | 0.659 |
| Recall | 0.552 |
| mAP@50 | 0.604 |
| mAP@50:95 | 0.395 |

- Metrics (https://drive.google.com/drive/folders/1rRuePcBYR6MrXHFfGCIGKQNKiXmuV0Z4?usp=drive_link)

### Task 2 — Stacked Video (Raw + Detected + Segmented)
- Created 3 videos: Raw, Object Detected, Object Segmented
- Ensured all videos same dimensions (1280x720)
- Stacked all 3 vertically using ffmpeg vstack
- Removed original audio with -an option
-  [Final Stacked Video](https://youtube.com/shorts/mz0_EVOsPK0)

---

## Tools Used
- yt-dlp — YouTube video downloader
- ffmpeg — Video processing
- YOLOv8 (Ultralytics) — Object detection & segmentation
- Python, OpenCV
- Google Colab

## Week 4 — YOLO Dataset Configuration & Labeling

### Task 1 — YOLO Configuration Files Report

Explored the directory/file structures and meta configuration files used in YOLOv8 models.
 [Full Report](https://drive.google.com/drive/folders/1hfDHfFsUdIelrUo-Sn_mskbdrLJRXD6G?usp=drive_link)
 ### Task 2 — Label Studio Setup & Dataset Creation

**Object to detect:**  Planes / Aircraft

**Tools used:**
- Label Studio — for annotating bounding boxes
- yt-dlp — to download aircraft footage
- ffmpeg — to extract frames from video

**Steps completed:**
- Created separate virtual environment for Label Studio
- Installed Label Studio via pip
- Downloaded aircraft video footage
- Extracted frames at 2fps for labeling
- Created project in Label Studio with `plane` class
- Drew bounding box annotations on each frame

**Labeling Setup:**
- Tool: Label Studio
- Task: Object Detection with Bounding Boxes
- Class: `plane`
- Format: YOLO (exported as class_id + normalized coordinates)
