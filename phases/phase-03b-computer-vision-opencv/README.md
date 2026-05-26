# Phase 03B -- Computer Vision + OpenCV

> **Time estimate:** 3-4 weeks  
> **Rule:** Every concept has a Quick Quiz. Every 3-4 concepts has a Mini Assignment.

---

## Section 1 -- Classical OpenCV

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| CV.1 | Image loading, color spaces, BGR vs RGB | [freeCodeCamp -- OpenCV full course](https://www.youtube.com/watch?v=oXlwWbU8l2o) | Why does OpenCV load images as BGR instead of RGB? What does `cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)` do? |
| CV.2 | Thresholding and morphological operations | [freeCodeCamp -- OpenCV full course](https://www.youtube.com/watch?v=oXlwWbU8l2o) | What does binary thresholding do to pixel values? What does dilation vs erosion do to binary masks? |
| CV.3 | Edge detection: Canny and Sobel | [freeCodeCamp -- OpenCV full course](https://www.youtube.com/watch?v=oXlwWbU8l2o) | What two thresholds does Canny edge detection use? What does the Sobel operator compute in x vs y direction? |
| CV.4 | Contours, moments, and shape analysis | [freeCodeCamp -- OpenCV full course](https://www.youtube.com/watch?v=oXlwWbU8l2o) | What does `cv2.findContours` return? How do you compute the centroid of a contour using moments? |

> **Mini Assignment CV.1 -- Object detection with classical CV:** Using only OpenCV (no deep learning): (1) Load a video or webcam feed. (2) Detect a colored object (e.g., a red ball) using HSV color thresholding. (3) Draw a bounding box and centroid on every frame. (4) Track the object's trajectory across frames. (5) Print the object's position every 10 frames. This is how robots navigated before deep learning existed.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| CV.5 | Feature detection: ORB, SIFT, keypoint matching | [OpenCV -- feature matching tutorial](https://docs.opencv.org/4.x/dc/dc3/tutorial_py_matcher.html) | What is a keypoint descriptor? What makes ORB faster than SIFT? What is Lowe's ratio test used for? |
| CV.6 | Homography estimation and perspective transform | [OpenCV -- homography tutorial](https://docs.opencv.org/4.x/d9/dab/tutorial_homography.html) | What is a homography matrix? What does `cv2.findHomography` compute? What does `cv2.warpPerspective` do? |
| CV.7 | Camera calibration: intrinsics and distortion | [OpenCV -- calibration tutorial](https://docs.opencv.org/4.x/dc/dbb/tutorial_py_calibration.html) | What are the camera intrinsic parameters (fx, fy, cx, cy)? What does lens distortion cause and how is it corrected? |
| CV.8 | Optical flow: Lucas-Kanade and Farneback | [OpenCV -- optical flow tutorial](https://docs.opencv.org/4.x/d4/dee/tutorial_optical_flow.html) | What does optical flow estimate between two frames? What is the aperture problem? |

> **Mini Assignment CV.2 -- Document scanner:** (1) Take a photo of a document at an angle. (2) Detect the four corners using edge detection and contour finding. (3) Compute the homography from the four corners to a rectangle. (4) Apply warpPerspective to get a flat top-down view. (5) Apply adaptive thresholding to get a clean black-and-white scan. This is a complete CV pipeline.

---

## Section 2 -- Deep learning for vision

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| CV.9 | Object detection: YOLO vs DETR comparison | [Two Minute Papers -- YOLO vs DETR](https://www.youtube.com/watch?v=NrO2aqASwPo) | What is the difference between single-stage (YOLO) and two-stage (Faster R-CNN) detection? When would you use DETR instead of YOLO? |
| CV.10 | YOLOv8 in practice: inference and fine-tuning | [Ultralytics -- YOLO tutorials](https://docs.ultralytics.com) | How do you run YOLOv8 inference in 3 lines of Python? What format must your custom dataset be in for fine-tuning? |
| CV.11 | Instance segmentation: SAM and Mask R-CNN | [Two Minute Papers -- SAM explained](https://www.youtube.com/watch?v=HX3GvpnuJKk) | What makes SAM "zero-shot"? What input does SAM accept (point, box, mask)? When would you use Mask R-CNN instead? |
| CV.12 | Semantic segmentation: SegFormer and DeepLab | [Two Minute Papers -- segmentation overview](https://www.youtube.com/watch?v=_JGFb2Ik8iY) | What is the difference between semantic and instance segmentation? What does each pixel get assigned in semantic segmentation? |

> **Mini Assignment CV.3 -- Real-time object detection pipeline:** (1) Run YOLOv8 on a webcam or video file. (2) Filter detections to only show objects above 60% confidence. (3) Count the number of each object class per frame. (4) Fine-tune YOLOv8 on a custom dataset of 100 images (label using LabelImg). (5) Compare detection performance before and after fine-tuning.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| CV.13 | Depth estimation: DepthAnything v2 | [Two Minute Papers -- DepthAnything](https://www.youtube.com/watch?v=8noiJJnZUAQ) | What is monocular depth estimation? Why is the depth estimate "relative" not "metric"? When do you need stereo cameras? |
| CV.14 | Human pose estimation: RTMPose | [Two Minute Papers -- pose estimation](https://www.youtube.com/watch?v=Qmhbc7IBE-A) | What does a pose estimation model output? What are "keypoints" and how many does a standard human pose model predict? |
| CV.15 | Object tracking: DeepSORT and ByteTrack | [Two Minute Papers -- object tracking](https://www.youtube.com/watch?v=NrO2aqASwPo) | What does a tracker add on top of a detector? What is the assignment problem that tracking solves between frames? |
| CV.16 | NeRF: 3D scene reconstruction from 2D images | [Two Minute Papers -- NeRF explained](https://www.youtube.com/watch?v=JuH79E8rdKc) | What does a NeRF represent? What are the inputs and outputs of a NeRF network? Why does it need many views? |

> **Mini Assignment CV.4 -- Depth-aware object picking simulation:** (1) Use DepthAnything v2 to estimate depth on a scene with objects. (2) Use YOLO to detect objects in the same image. (3) For each detected object, use the depth map to estimate its rough distance from the camera. (4) Rank objects by distance and draw bounding boxes colored by depth (red=near, blue=far). This mimics how a robot perceives a workspace.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| CV.17 | Video action recognition: SlowFast, Video Swin | [Two Minute Papers -- video understanding](https://www.youtube.com/watch?v=Z80PeAhpqBQ) | Why does video understanding require both spatial and temporal modeling? What does the "Slow" pathway capture that the "Fast" pathway misses? |
| CV.18 | Data augmentation: albumentations | [Albumentations -- official tutorial](https://albumentations.ai/docs) | Why is domain-specific augmentation important for robot perception? Name 5 augmentation types from albumentations and when each helps. |
| CV.19 | Stereo vision and 3D reconstruction | [OpenCV -- stereo tutorial](https://docs.opencv.org/4.x/dd/d53/tutorial_py_depthmap.html) | What is disparity? How do you convert disparity to depth given the baseline distance and focal length? |

> **Mini Assignment CV.5 -- Human activity recognition:** (1) Using a webcam or video, detect human pose keypoints per frame using RTMPose or MediaPipe. (2) Extract the joint angles from keypoints. (3) Train a simple LSTM on sequences of joint angles to classify 3 activities (e.g., waving, walking, sitting). (4) Run inference in real-time. This is the foundation of gesture-based HRI.
