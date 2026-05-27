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

### Task 2 — Label Studio Setup & Custom Dataset Creation

**Object detected:**  Planes / Aircraft
**Video source:** [London Heathrow Airport Plane Spotting](https://www.youtube.com/watch?v=GjWstrGp9XI)

#### Steps Completed:
- Created separate virtual environment for Label Studio (`C:\labelstudio\venv`) using Python 3.11
- Installed Label Studio via pip
- Downloaded London Heathrow airport footage using yt-dlp
- Extracted 600 frames at 10fps using ffmpeg
- Organized into train (100), val (40), test (remaining) folders
- Synced images to Label Studio via Local File Storage
- Created `Plane Detection` project with `airplane` class
- Manually annotated bounding boxes on 140 images (100 train + 40 val)
- Exported labels in YOLO format
- Created `data.yaml`, `train.txt`, `val.txt` metadata files
- Trained YOLOv8n on custom labeled dataset

#### Dataset Details:
| Property | Value |
|----------|-------|
| Total Images Labeled | 140 |
| Train Images | 100 |
| Val Images | 40 |
| Total Instances | 201+ |
| Classes | airplane |
| Label Format | YOLO (normalized bbox) |

#### Training Run  — All images for training (120 images)
| Metric | Value |
|--------|-------|
| Precision | 0.957 |
| Recall | 0.553 |
| mAP@50 | 0.795 |
| mAP@50:95 | 0.546 |
| Epochs | 10 |
| Training Time | 0.321 hours |

#### Metadata Files:
- `data.yaml` — dataset configuration
- `train.txt` — paths to all training images
- `val.txt` — paths to all validation images
- `labels/train/` — 100 YOLO format annotation files
- `labels/val/` — 40 YOLO format annotation files

#### Tools Used:
- Label Studio — image annotation
- yt-dlp — video download
- ffmpeg — frame extraction
- YOLOv8n (Ultralytics) — object detection training
- Python 3.11 — scripting

## Week 5 — Custom Model Training & Inference
### Tasks 1–5 — End-to-End Vehicle Detection Pipeline

**Objects detected:** Cars & Trucks  
**Video source:** Royalty-free traffic footage (Pexels)

#### Steps Completed:
- Collected traffic footage and extracted 107 frames at 5fps using ffmpeg
- Organized into train (75), val (21), test (11) folders following 70-20-10 split
- Set up Label Studio and annotated bounding boxes on 96 images (75 train + 21 val)
- Exported labels in YOLO format and created `data.yaml`
- Resized all images from 4K (3840×2160) to 384px width using ffmpeg, preserving aspect ratio
- Fine-tuned YOLOv8n pretrained model on custom dataset for 100 epochs on Google Colab (T4 GPU)
- Ran inference on 11 unseen test images using trained weights
- Stitched detected frames into video and added royalty-free background music

#### Dataset Details:
| Property | Value |
|----------|-------|
| Total Images | 107 |
| Train Images | 75 |
| Val Images | 21 |
| Test Images | 11 |
| Classes | car, truck |
| Label Format | YOLO (normalized bbox) |

#### Training Results:
| Metric | Value |
|--------|-------|
| Precision | 0.905 |
| Recall | 0.647 |
| mAP@50 | 0.662 |
| mAP@50:95 | 0.460 |
| Epochs | 100 |
| Training Time | ~0.031 hours |

#### Per-Class Performance:
| Class | mAP@50 |
|-------|--------|
| car | 0.989 |
| truck | 0.336 |

#### Output:
 [Week 5 Results](https://drive.google.com/drive/folders/1pvqnRdJ_MNLk-HIKN1Su20DgV3n_WqXE?usp=drive_link)

#### Tools Used:
- Label Studio — image annotation
- ffmpeg — frame extraction & video stitching
- YOLOv8n (Ultralytics) — custom model training & inference
- Python, OpenCV — video processing
- Google Colab (T4 GPU) — model training
