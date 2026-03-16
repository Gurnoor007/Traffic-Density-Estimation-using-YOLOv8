#  Traffic Density Estimation using YOLOv8

A computer vision project that fine-tunes **YOLOv8** on top-view aerial vehicle images to detect vehicles and classify traffic density in real time. Built and evaluated on Kaggle using the **Top-View Vehicle Detection Image Dataset**.

---

##  Overview

This project uses a fine-tuned YOLOv8 object detection model to:
- Detect vehicles from aerial/top-view images
- Count the number of vehicles per scene
- Classify traffic density as **Low**, **Medium**, or **High**
- Visualize traffic distribution across a validation set


---

##  Pipeline

```
Top-View Images
      ↓
YOLOv8n Fine-tuning (100 epochs, imgsz=640, batch=32)
      ↓
Vehicle Detection + Bounding Box Count
      ↓
Density Classification (Low / Medium / High)
      ↓
Distribution Analysis & Visualization
```

---

##  Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.10+ |
| Model | YOLOv8n (Ultralytics) |
| Computer Vision | OpenCV, PIL |
| Data Handling | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Platform | Kaggle Notebooks (GPU) |
| Dataset | Top-View Vehicle Detection Image Dataset |

---

##  Density Classification Logic

Vehicle count per image is classified into three levels:

| Level | Vehicle Count |
|-------|--------------|
| 🟢 Low | < 4 vehicles |
| 🟡 Medium | 4 – 7 vehicles |
| 🔴 High | ≥ 8 vehicles |

---

## Training Configuration

| Parameter | Value |
|-----------|-------|
| Base Model | YOLOv8n |
| Epochs | 100 |
| Image Size | 640×640 |
| Batch Size | 32 |
| Optimizer | Auto |
| Learning Rate | 0.0001 |
| Dropout | 0.1 |
| Early Stopping Patience | 50 |
| Device | GPU (Kaggle) |

---

##  Evaluation

The fine-tuned model is evaluated using:
- **Box Loss** — bounding box regression accuracy
- **Classification Loss** — vehicle class prediction
- **Distribution Focal Loss (DFL)** — localization refinement
- **Confusion Matrix** (normalized)
- Standard YOLO metrics: mAP50, mAP50-95, Precision, Recall

---

##  Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/Gurnoor007/traffic-density-estimation.git
cd traffic-density-estimation
```

### 2. Install dependencies
```bash
pip install ultralytics opencv-python pandas matplotlib seaborn pillow pyyaml
```

Or:
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
- Dataset: [Top-View Vehicle Detection Image Dataset on Kaggle](https://www.kaggle.com/datasets/)
- See `data/README.md` for folder placement instructions.

### 4. Run the notebook
Open `CV_Code_TrafficDensityEstimation.ipynb` in Kaggle or Jupyter and run all cells in order.

---

##  Dataset

**Top-View Vehicle Detection Image Dataset** (Kaggle)

- Aerial/top-view images of roads and intersections
- Annotated with bounding boxes in YOLO format
- Split into `train/` and `valid/` sets
- All images are uniform in size


##  Sample Output

The model predicts bounding boxes around each detected vehicle and overlays them on the image. Each scene is then assigned a density level based on total vehicle count.

---

##  Author

**Gurnoor Singh Mander**
B.Tech CSE, Lovely Professional University (2022–2026)
- GitHub: [@Gurnoor007](https://github.com/Gurnoor007)
- Email: gurnoorgaby@gmail.com

---
