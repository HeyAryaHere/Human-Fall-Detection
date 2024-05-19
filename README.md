**Human Fall Detection with YOLOv3, SPPE, and TSS-GT**

This project implements a human fall detection system that leverages the strengths of three deep learning models:

- **YOLOv3:** A real-time object detection model for efficiently locating humans in video frames.
- **SPPE (Spatial Pose Estimation):** Accurately estimates human pose (keypoints) from the detected human bounding boxes.
- **TSS-GT (Temporal Shift-Scale Gated Network):** Analyzes the temporal changes in human pose keypoints to identify potential falls.

**Project Structure**

```
human-fall-detection/
├── Actionsrecognition/
│   ├── Models.py
│   └── Utils.py
│   └── train.py
├── data/
│   ├── create_datasets_1.py 
│   └── create_datasets_2.py
│   └── create_datasets_3.py 
├── Detection/
│   ├── Models.py  
│   └── Utils.py
├── Models/
│   ├── TSSTG/ (Pretrained for post estimiaton)  
│   └── Sppe/ (Pretrained for making skeleton)
│   └── yolo-tiny-opencls/ (Pretrained for human detection)
├── SPPE/ (Refer more to Alphapose : https://github.com/Amanbhandula/AlphaPose)
│   ├── src/ 
│   └── LICENSE
│   └── README.md
├── Track/
│   ├── Tracker.py 
│   └── iou_matching.py
│   └── kalman_filter.py
│   └── linear_assignment.py
├── ActionsEstloader.py
├── App.py
├── CamerLoader.py
├── DetectorLader.py
├── PoseEstimateLoader.py      
├── requirements.txt  
├── fn.py   
├── main.py 
├── pPose_nms.py 
├── pose_utils.py 
└── requirements.txt            (Main script to run the pipeline)
```

**Installation**

1. Clone this repository:

   ```bash
   git clone https://github.com/HeyAryaHere/Human-Fall-Ddetection.git
   ```

2. Create a virtual environment (recommended):

   ```bash
   python -m venv env
   source env/bin/activate  # Activate on Linux/macOS
   env\Scripts\activate.bat  # Activate on Windows
   ```

3. Install dependencies from `requirements.txt`:

   ```bash
   pip install -r requirements.txt
   ```

4. Mail Me for getting pretrained weights for Yolo, SPPE, and TSSTG `heyaryahere@gmail.com`


**Usage**

1. Put your video files source in main.py or use `python3 main.py -c SOURCE`. Ensure they are compatible video formats (e.g., MP4, AVI).

2. Run the main script:

   ```bash
   python main.py
   ```

This will process videos in the `source` folder, detect humans using YOLOv3, estimate their poses with SPPE, and analyze pose changes with TSS-GT to identify potential falls. Classified videos will be saved in the `data/output_videos` folder. Potential falls will be indicated visually (e.g., by highlighting the bounding box or adding a label).

**Dependencies**

- Deep learning frameworks (e.g., PyTorch, TensorFlow) - specified in `requirements.txt`
- YOLOv3 pre-trained weights
- SPPE pre-trained weights

**Contributing**

We encourage contributions to improve this project! Feel free to submit pull requests for bug fixes, enhancements, or new features.


**Disclaimer**

The accuracy of fall detection depends on factors like video quality, lighting conditions, and the capabilities of the underlying models. This project is intended for educational and research purposes only. It's recommended to thoroughly evaluate its performance before deploying it in real-world scenarios.
