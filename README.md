# Military Objects Recognition

This project implements a system for automatic recognition and classification of military objects (tanks, aircrafts, helicopters, etc.) from images captured in natural environments using the YOLOv8 architecture.

The goal is to develop a robust model that:
- Detects object locations (bounding boxes)
- Classifies them into one of 12 classes
- Operates efficiently in real-time

## Authors

- Faris Kasapović
- Dževad Madžak 
- Mika Bjelobrk

## Key Technologies

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- Python 3.11
- PyTorch
- Google Colab

---

##  Dataset Used

**Military Assets Dataset (12 Classes – YOLOv8 Format)**  
 [Download from Kaggle](https://www.kaggle.com/datasets/rawsi18/military-assets-dataset-12-classes-yolo8-format)

- 26,315 images
- 43,336 labeled objects
- 12 classes (e.g., `military_tank`, `soldier`, `weapon`, etc.)
- Format: YOLOv8 (`.txt` annotations + `.jpg` images)

---

## Data Preprocessing

- Converted annotation paths from Kaggle to Google Colab environment
- Created `data.yaml` configuration file
- Validated annotation format and image-label consistency
- Generated cache files for faster data loading

---

## Model Training

The **YOLOv8n** (nano version) model was used with the following parameters:
-  Epochs: 3
-  Batch size: 2
-  Image size: 256px
-  Optimizer: AdamW
-  Pretrained weights: `yolov8n.pt`

> Note: Training was conducted on CPU due to resource limitations (Colab).

---

## Results

| Metric         | Value   |
|----------------|---------|
| mAP@0.5        | 25.7%   |
| mAP@0.5:0.95   | 14.6%   |
| Precision      | 37.5%   |
| Recall         | 31.8%   |
| Inference time | 1.8 ms  |

Best performing classes:
- `military_tank`: 35.1% mAP50
- `military_aircraft`: 32.3% mAP50

---

## Testing

The model was tested on:
- A validation set of 2,941 images
- Random internet images

It demonstrated generalization ability and solid results on unseen data (e.g., aircraft detected with 0.71 confidence).

---

## Limitations

-  Class imbalance (`trench` has only 4 instances)
-  Short training time (3 epochs)
-  CPU-only training (no GPU access)

---

## Recommendations for Future Work

- Longer training (20–50 epochs) with GPU support
- Class balancing techniques
- Testing larger models (YOLOv8m/l)
- Advanced data augmentation
- Ensemble methods for better performance

---

## Conclusion

This project demonstrates how YOLOv8 can be effectively applied to the challenging problem of military object detection. Despite limited training resources, the model showed potential for real-time use in military intelligence applications.

---

  
