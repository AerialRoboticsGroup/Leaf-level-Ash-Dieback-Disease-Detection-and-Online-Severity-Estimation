# **Leaf-Level Ash Dieback Disease Detection and Severity Estimation**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](#license)
[![Paper](https://img.shields.io/badge/IEEE-Paper-blue.svg)](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10884769)
[![Dataset](https://img.shields.io/badge/Dataset-Zenodo-brightgreen.svg)](https://zenodo.org/records/13964157)

Welcome to the **Ash Dieback Leaf Detection** repository! This project demonstrates how to detect and classify ash tree leaves at various stages of infection using **YOLOv5** and a **synthetic dataset**.

---

## **Table of Contents**
1. [Overview](#overview)
2. [Repository Structure](#repository-structure)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Dataset](#dataset)
6. [Citation](#citation)
7. [License](#license)
8. [Acknowledgments](#acknowledgments)

---

## **Overview**
Ash dieback disease (Chalara) is a fungal infection causing severe damage to ash trees. **Early detection—particularly at the leaf level—can significantly aid conservation efforts.** Our work:

- **Generates a synthetic leaf dataset** (healthy, early-stage infection, mid-stage infection) to train YOLOv5.
- Demonstrates **disease detection and severity estimation** at the leaf level, with emphasis on **Google Colab** workflows.
- Provides **`.ipynb` notebooks** tailored for Colab that let you experiment, train, and test quickly.

For more details, see our IEEE publication:  
> [Leaf Level Ash Dieback Disease Detection and Online Severity Estimation with UAVs](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10884769)

---

## **Repository Structure**

Below is a snapshot of the project folders (with the most relevant files):

<pre>
Ash_dieback_detection_leaf/
├── AllLeaves/
├── Experimentation/
    ├── Exploring_CV_techniques.ipynb
    └──  More_CV_trial&error.ipynb
├── YOLOv5_nobackground/
│   ├── images/
│   │   ├── train/
│   │   ├── val/
│   │   └── test/
│   ├── labels/
│   │   ├── train/
│   │   ├── val/
│   │   └── test/
│   └── dataset.yaml
├── Image_Processing.ipynb
└── YOLOv5.ipynb
</pre>

- **AllLeaves/**: (Optional) Contains various leaf images or backups.  
- **YOLOv5_nobackground/**: Main folder for YOLOv5 training scripts & notebooks.  
  - **images/** and **labels/**: Where your training, validation, and test sets reside (subfolders: `train`, `val`, `test`).  
  - **dataset.yaml**: YOLOv5 configuration file (paths & classes).  
- **Experimentation/**: Additional notebooks for image processing and cv trial and error. 
- **YOLOv5.ipynb**: Primary notebook for training in Google Colab.  
- **Image_Processing.ipynb**: Notebook for image processing and augmentation.

---

## **Colab Setup**
1. **Copy the repository structure to Google Drive**  
   - The recommended approach is to replicate this entire folder structure in your own Google Drive.  
   - For example, create a folder in your Drive called `Ash_dieback_detection_leaf`, and place all subfolders (`AllLeaves`, `YOLOv5_nobackground`, etc.) inside it.  

2. **Mount Google Drive in Colab**  
   - In your Colab notebook, you can use:
     ```python
     from google.colab import drive
     drive.mount('/content/drive')
     ```
   - Navigate to your new project folder in Drive (`/content/drive/MyDrive/Ash_dieback_detection_leaf/...`).

3. **Open the notebooks in Colab**  
   - Upload or open `YOLOv5.ipynb` (and any other `.ipynb` you wish) directly in Colab.
   - Colab will allow you to run the cells (installing required libraries, training YOLOv5, etc.).

---
   
## **Usage**

### **1. Acquire the Dataset**
The leaf images are **too large** to host on GitHub, so please download them from Zenodo:
- **[Zenodo Dataset Link](https://zenodo.org/records/13964157)**

This dataset is a series of folders containing the train, test and validation images and labels.

Place these folders inside `YOLOv5_nobackground/` so the structure matches:
<pre>
YOLOv5_nobackground/
├── dataset.yaml
├── images/
│   ├── train
│   ├── val
│   └── test
└── labels/
    ├── train
    ├── val
    └── test
</pre>

### **2. Configure `dataset.yaml`**
Open `dataset.yaml` and update the path:
```yaml

path:   # Root directory of dataset
train: train  # Folder containing training images
val: val  # Folder containing validation images
test: test  # Updated path for test labels
nc: 4  # Number of classes (excluding high_level_infection)
names: ["healthy","low_level_infection", "mid_level_infection","high_level_infection"]
```

### **3. Run `Yolov5.ipynb`**
If you would like to retrain the model, open `YOLOv5.ipynb` in Google Colab and follow through the notebook to 
install Yolov5, train the model and test the model. 


## **Citation**

(To be updated after publication...)

If you use this code or our synthetic dataset, please cite our paper:

**Citation**  
Bates, E., Popović, M., Marsh, C., Clark, R., Kovac, M. and Kocer, B.B., 2025. Leaf Level Ash Dieback Disease 
Detection and Online Severity Estimation with UAVs. IEEE Access, Available at: 
(to be updated with link) (Accessed: [date]).

**BibTeX**:
```bibtex
@ARTICLE{Bates2025AshDieback,
  author={Bates, Elizabeth and Popović, Marija and Marsh, Conor and Clark, Ronald and Kovac, Mirko and Kocer, Basaran Bahadir},
  journal={IEEE Access},
  title={Leaf Level Ash Dieback Disease Detection and Online Severity Estimation with UAVs},
  year={2025},
  doi={10.1109/ACCESS.2025.3541980}
}
```
**Dataset Citation**  
Bates, E., Kocer, B. B., Marsh, C., Kovac, M., Clark, R., & Popović, M. (2024). Infected Leaves Synthetic Dataset - Ash Tree Dieback [Data set]. Zenodo. https://doi.org/10.5281/zenodo.13964157