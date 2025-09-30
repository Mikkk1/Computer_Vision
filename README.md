```markdown
# 🚪 CeVeDoor Project - YOLOv8 Training

This project trains a **YOLOv8 object detection model** on the **CeVeDoor dataset** stored in Google Drive.  
The model is fine-tuned with custom augmentations and validated to measure accuracy (mAP@50).  
Training results and experiment runs are saved back to Google Drive for later analysis.

---

## 📂 Project Structure
```

CeVeDoorProject.v1i (1).yolov8/
│── data.yaml                # Dataset configuration file
│── train/                   # Training images and labels
│── val/                     # Validation images and labels

````

---

## 🚀 Features
- **Google Drive Integration** – Dataset and model runs are stored on Google Drive.
- **YOLOv8 Training** – Fine-tunes YOLOv8n model on custom dataset.
- **Albumentations** – Adds augmentations (flip, brightness/contrast, rotation).
- **Evaluation** – Validates model and prints mAP@50 accuracy.
- **Experiment Logging** – Saves training results (`/runs/`) to Drive.

---

## 🛠️ Requirements
Install dependencies inside Google Colab:
```bash
!pip install ultralytics
!pip install albumentations
````

---

## 📖 Usage

### 1. Mount Google Drive

```python
from google.colab import drive
drive.mount('/content/drive')
```

### 2. Train Model

```python
from ultralytics import YOLO
model = YOLO("yolov8n.pt")

train_params = {
    'data': '/content/drive/MyDrive/CeVeDoorProject.v1i (1).yolov8/data.yaml',
    'epochs': 70,
    'imgsz': 640,
    'batch': 16,
    'device': 0
}

model.train(**train_params, augment=True)
```

### 3. Evaluate Model

```python
results = model.val(data=data_config_path)
print(results)
print(f"mAP@50: {results.box.map50 * 100:.2f}%")
```

### 4. Save Runs to Drive

```python
import shutil
shutil.copytree('/content/runs', '/content/drive/My Drive/yl_runss')
```

---

## 📊 Results

* Model training runs are saved in Google Drive under:
  `/content/drive/My Drive/yl_runss/`

* Example output:

  ```
  mAP@50: 87.52%
  ```

---

## 📌 Next Steps

* Try larger models (`yolov8s.pt`, `yolov8m.pt`) for better accuracy.
* Experiment with additional augmentations.
* Export trained model for inference.

---

## 👤 Author

**Sarim Zahid**

* 🔗 GitHub: [Mikkk1](https://github.com/Mikkk1)
* 🔗 LinkedIn: [Sarim Zahid](https://www.linkedin.com/in/sarim-zahid-4b3636265/)

---

```
```
