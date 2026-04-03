#  IT549: Deep Learning

## Lab Assignment 4: Object Detection Evolution (R-CNN → YOLO)

---

## Student Details

* **Name:** Patel Vatsal Sureshbhai
* **Student ID:** 202511040

---

## Objective

This lab explores the evolution of object detection models from traditional region-based methods like R-CNN to modern real-time detectors like YOLO. The goal is to understand architectural differences, computational efficiency, and practical implementation of different object detection approaches.

---

## Dataset

* **Dataset:** Fruit Images Dataset (Kaggle)
* **Classes:** Apple, Banana, Orange
* **Annotations:**

  * YOLO format (x_center, y_center, width, height)
  * Pascal VOC format (xmin, ymin, xmax, ymax)

---

## Tasks Performed

---

###  Task 1: Intersection over Union (IoU)

* Implemented IoU function from scratch
* Tested on:

  * High overlap
  * Partial overlap
  * No overlap

 **Observation:**
IoU effectively measures overlap between predicted and ground truth boxes.

---

###  Task 2: Selective Search (R-CNN Step 1)

* Used OpenCV Selective Search
* Generated ~200 region proposals
* Visualized bounding boxes

 **Observation:**

* Many candidate regions generated
* Includes irrelevant regions → computational overhead

---

###  Task 3: R-CNN Bottleneck

* Used pretrained ResNet18
* Cropped 100 regions
* Passed each crop independently through CNN

**Observation:**

* Very slow due to repeated CNN computation
* Same image processed multiple times

---

###  Task 4: Fast R-CNN (RoI Pooling)

* Passed full image once through CNN
* Used RoI Pooling on feature map

**Observation:**

* Significant speed improvement
* Eliminates redundant convolution operations

---

###  Task 5: Faster R-CNN

* Used pretrained Faster R-CNN (ResNet50 + FPN)
* Generated predictions with confidence filtering

*Observation:**

* No need for Selective Search
* Internal Region Proposal Network (RPN) improves efficiency

 **Conceptual Insight:**
RPN generates region proposals directly from feature maps, eliminating external algorithms and enabling end-to-end learning.

---

### Task 6: Non-Maximum Suppression (NMS)

* Implemented custom NMS using IoU
* Removed overlapping duplicate boxes

 **Observation:**

* Before NMS → multiple overlapping detections
* After NMS → clean final predictions

 **Conceptual Insight:**

* High IoU threshold → keeps more boxes
* Low IoU threshold → aggressive suppression (may remove valid objects)

---

###  Task 7: YOLO Fine-Tuning

* Used YOLOv8 Nano model
* Fine-tuned on fruit dataset (10 epochs)
* Evaluated using mAP

**Evaluation Metrics:**

*mAP@50: 0.856807769210727
*mAP@50-95: 0.6239368248415158

 **Observation:**

* YOLO is significantly faster than Faster R-CNN
* Fine-tuned YOLO performs best on dataset

---

##  Performance Comparison

| Model                     | Inference Time (ms) | Precision | Recall |
| ------------------------- | ------------------- | --------- | ------ |
| Faster R-CNN (Pretrained) | 3828.93             | Medium    | Medium |
| YOLO (Pretrained)         | 35.70               | Medium    | Medium |
| YOLO (Fine-tuned)         | 21.07               | High      | High   |

---

##  Key Insights

* Faster R-CNN is accurate but slow due to its two-stage pipeline
* YOLO performs detection in a single forward pass → much faster
* Fine-tuning significantly improves model performance on custom datasets
* NMS is essential to remove duplicate detections
* Fast R-CNN eliminates redundant CNN computations

---

##  Conclusion

This lab demonstrates the evolution of object detection models:

* **R-CNN:** Accurate but slow
* **Fast R-CNN:** Improved efficiency
* **Faster R-CNN:** End-to-end detection with RPN
* **YOLO:** Real-time detection with high speed

Overall, YOLO provides the best balance between speed and accuracy, especially when fine-tuned on a specific dataset.

---



---

## ✅ Final Note

All tasks were implemented and tested successfully, demonstrating both theoretical understanding and practical application of object detection techniques.

---
