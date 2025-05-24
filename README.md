# 🧠 DeepVision Classic Models

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?logo=pytorch)](https://pytorch.org/)
[![Stars](https://img.shields.io/github/stars/morsetechlab/deepvision-classic-models?style=social)](https://github.com/morsetechlab/deepvision-classic-models)

โปรเจกต์นี้รวบรวมสถาปัตยกรรมของโมเดล Deep Learning แบบคลาสสิกที่ใช้งานในงานด้าน Computer Vision  
เน้นการเขียนโค้ดด้วย PyTorch อย่างเข้าใจง่าย เพื่อศึกษา ทบทวน และทดลองได้ด้วยตนเอง เริ่มต้นจาก LeNet-5 ที่ออกแบบมาสำหรับชุดข้อมูล MNIST

---

## Project Objective

- ศึกษาสถาปัตยกรรม CNN พื้นฐานแบบดั้งเดิม
- เข้าใจการไหลของข้อมูลภายในโมเดลผ่านแต่ละชั้น
- ทดลองฝึกโมเดลด้วยชุดข้อมูลมาตรฐาน 
- ประเมินผลด้วย Accuracy, Loss, Confusion Matrix, F1-score
- นำผลลัพธ์ไปใช้ต่อยอดในการเรียนรู้ขั้นสูง

---

## Feature

```
- ฝึกโมเดลด้วย PyTorch
- แสดงผล Accuracy / Loss ต่อ Epoch
- แสดง Confusion Matrix, Precision, Recall, F1
- ทำ Inference แบบสุ่มจาก test set พร้อมแสดงผลภาพ
- Export โมเดลเป็น `.pt` ไฟล์สำหรับใช้งานจริง
```

---

## การอ่านค่า Evaluation Metrics (Precision / Recall / F1-score)

### Recall (ความครอบคลุม)

**"ในบรรดาตัวอย่างทั้งหมดที่เป็นคลาสนั้นจริง ๆ — โมเดลหาเจอครบหรือไม่?"**

\[
\text{Recall} = \frac{TP}{TP + FN}
\]

- **TP (True Positive)** = ทำนายถูกว่าคลาสนี้
- **FN (False Negative)** = จริง ๆ เป็นคลาสนี้ แต่โมเดลทำนายเป็นคลาสอื่น

#### เช่น:
ถ้ามีภาพแมว 100 ภาพจริง ๆ แต่โมเดลทายว่าเป็นแมวแค่ 60 ภาพ → Recall = 60%

### Precision (ความแม่นยำ)
**"ในบรรดาตัวอย่างทั้งหมดที่โมเดลบอกว่าเป็นคลาสนี้ — มันถูกกี่ภาพ?"**

\[
\text{Precision} = \frac{TP}{TP + FP}
\]

- **FP (False Positive)** = โมเดลทำนายว่าเป็นคลาสนี้ แต่จริง ๆ ไม่ใช่

#### เช่น:
โมเดลบอกว่ามีภาพแมวทั้งหมด 80 ภาพ แต่จริง ๆ ถูกแค่ 60 ภาพ → Precision = 75%

### ⚖️ F1-Score (สมดุลของ Recall + Precision)
**"ถ่วงดุลระหว่างความแม่นยำ (Precision) และความครอบคลุม (Recall)"**

\[
\text{F1} = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}
\]

- ใช้ในกรณีที่ต้องการความสมดุลของทั้งสองด้าน
- เหมาะกับข้อมูลไม่สมดุล (imbalanced dataset)

### Confusion Matrix

ตารางที่แสดงจำนวนการทำนายของโมเดลในแต่ละคลาส เพื่อดูว่าโมเดลสับสนระหว่างคลาสใดบ้าง

|               | Predicted Positive | Predicted Negative |
|---------------|--------------------|--------------------|
| **Actual Positive** | ✅ True Positive (TP) | ❌ False Negative (FN) |
| **Actual Negative** | ❌ False Positive (FP) | ✅ True Negative (TN) |

ในกรณี Multi-Class เช่น CIFAR-10 → Confusion Matrix จะเป็นตาราง NxN (10x10)  
โดยที่แกน X = ทำนาย, แกน Y = ความจริง

### Comparative summary

 Metric       | คำถามหลัก             | เป้าหมาย             |
|--------------|------------------------|------------------------|
| **Recall**   | "เจอครบหรือยัง?"       | ลดการพลาด (FN)       |
| **Precision**| "ทายถูกมากแค่ไหน?"    | ลดการเดามั่ว (FP)    |
| **F1-Score** | "สมดุลระหว่างสองด้าน?"| ประเมินโมเดลแบบยุติธรรม |

> ⚠️ **หมายเหตุ**: ตัวอย่างและสูตรทั้งหมดในเอกสารนี้ใช้สำหรับ **Computer Vision Task แบบ Multi-Class Classification เท่านั้น**  
> ไม่สามารถใช้แทนตรง ๆ ในงานประเภท **Object Detection**, **Segmentation**, หรือ **Natural Language Processing (NLP)** ได้โดยตรง เนื่องจากนิยามของ TP / FP / FN ในงานเหล่านั้นแตกต่างกัน

---

## Attribution

Presented by [MorseTech Lab](https://github.com/morsetechlab)

## 🛡️ License

Distributed under the MIT License. See [`LICENSE`](./LICENSE) for more information.

---

> หากโปรเจกต์นี้มีประโยชน์ อย่าลืม ⭐️ Repo เพื่อเป็นกำลังใจให้เราด้วยนะครับ!

<meta name="keywords" content="deep-learning, cnn, pytorch, lenet5, classic-models, mnist, computer-vision, image-classification, ai-education, deep-learning-tutorial, vision-models">
