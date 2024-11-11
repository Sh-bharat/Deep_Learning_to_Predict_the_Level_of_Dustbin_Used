# Deep Learning to Predict the Level of Dustbin Used



This project uses deep learning techniques to analyze and predict the fill level of dustbins based on images. The system employs segmentation and classification models to assess dustbin fill percentage, angle classification, and waste segmentation, aiming to enhance waste management practices.

## Table of Contents
- [Datasets](#datasets)
  - [Dustbin Segmentation Dataset](#dustbin-segmentation-dataset)
  - [Waste Segmentation Dataset](#waste-segmentation-dataset)
  - [Dustbin Angle Classification Dataset](#dustbin-angle-classification-dataset)
- [Setup and Requirements](#setup-and-requirements)
- [Usage](#usage)
- [Results](#results)
  - [Dustbin Fill Level Segmentation](#dustbin-fill-level-segmentation)
  - [Waste Segmentation](#waste-segmentation)
  - [Dustbin Angle Classification](#dustbin-angle-classification)
- [Final Output](#final-output)
- [Contributing](#contributing)
- [License](#license)

## Datasets

### Dustbin Segmentation Dataset
This dataset provides annotated images for training models on dustbin segmentation, which defines the fill levels based on image segmentation.

- **[Download Dustbin Segmentation Dataset](https://drive.google.com/file/d/1YK3ukvof0By-y_7hj8kEKQgD0ctx1mla/view?usp=sharing)**

Alternatively, download the dataset in parts:
- Download `Dataset.zip` along with `Dataset.z01`, `Dataset.z02`, ..., `Dataset.z12`.
- Extract the dataset by opening `Dataset.zip` with [WinRAR](https://www.win-rar.com/).

### Waste Segmentation Dataset
This dataset contains labeled images for waste type segmentation, supporting the model’s ability to detect and categorize different types of waste within the images.

- **[Download Waste Segmentation Dataset](https://drive.google.com/file/d/1o6RuliAXPmmFyq0esDa5--zGH16iSs2K/view?usp=sharing)**

### Dustbin Angle Classification Dataset
Images in this dataset are classified by dustbin angle or orientation, useful for evaluating dustbin accessibility and waste visibility.

- **[Download Dustbin Angle Classification Dataset](https://drive.google.com/file/d/1pnSzSGkDCR8KBxii4r7jO3ZPsM-VU0IC/view?usp=sharing)**

## Setup and Requirements
1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/Deep_Learning_to_Predict_the_Level_of_Dustbin_Used.git
   cd Deep_Learning_to_Predict_the_Level_of_Dustbin_Used
   ```

2. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download and Organize Datasets:**
   Organize the datasets in the following structure:
   ```
   dataset/
   ├── dustbin_segmentation/
   │   ├── images/
   │   └── annotations/
   ├── waste_segmentation/
   │   ├── images/
   │   └── annotations/
   └── dustbin_angle_classification/
       ├── images/
       └── labels/
   ```

## Usage
1. **Train the Model:**
   Run the training script on the dustbin segmentation dataset.
   ```bash
   python train.py --dataset_path ./dataset/dustbin_segmentation --epochs 50
   ```

2. **Evaluate the Model:**
   Run evaluation on the saved model to check segmentation and fill-level prediction performance.
   ```bash
   python evaluate.py --model_path ./saved_models/model_best.pth
   ```

## Results

### Dustbin Segmentation
This model predicts the mask of the dustbin by segmenting the dustbin region and calculating the filled area.

**Results:**
![Dustbin Fill Level Segmentation](https://github.com/user-attachments/assets/e89b96da-33bf-4dc3-a320-3960ad29a9ee)



**Sample Output:**

![Segmented Dustbin](https://github.com/user-attachments/assets/3d93326d-e12b-4013-b041-e3ba6d1754c7)



### Waste Segmentation
The waste segmentation model classifies different types of waste present within the dustbin, enhancing waste sorting and recycling processes.

**Results:**

![Waste Segmentation Results](https://github.com/user-attachments/assets/a43e8320-d8ed-4982-8090-1fa34b1217ae)


**Sample Output:**

![Segmented Waste Types](https://github.com/user-attachments/assets/cc72ba90-31fb-4805-96d4-30c9e09b51da)



### Dustbin Angle Classification
This model classifies the orientation or angle of the dustbin, which aids in understanding its accessibility and positioning.

**Results:**

![Dustbin Angle Classification Result](https://github.com/user-attachments/assets/b2ffbd81-df97-4884-9691-5ebe490d199f)



**Sample Output:**

![Dustbin Angle Classification Outputs](https://github.com/user-attachments/assets/5ae2238b-9fee-4363-92d8-bd9b7c1f7dd8)



## Final Output
The final output displays the predicted fill percentage for the dustbin based on the segmentation model's analysis. Due to the absence of exact manual measurements, the accuracy of this prediction is approximated.

**Final Result:**

![Dustbin Fill Percentage Display](https://github.com/user-attachments/assets/f688020f-383c-405b-8203-bea039fb79e2)




## Contributing
Contributions to this project are welcome. Please feel free to open an issue or create a pull request for any improvements or suggestions.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
