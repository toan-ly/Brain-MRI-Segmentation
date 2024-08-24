# Brain MRI Segmentation
This project focuses on brain MRI segmentation implementing a U-Net architecture. The dataset used includes MRI scans and their corresponding ground truth masks, representing regions with and without the presence of tumors. 

## Dataset
The dataset used is the [Kaggle LGG Segmentation Dataset](https://www.kaggle.com/datasets/mateuszbuda/lgg-mri-segmentation/data), which consists of MRI scans from multiple patients with corresponding segmentation masks outlining tumor regions.
- Images: MRI scans in `.tif` format.
- Masks: Binary masks indicating tumor regions.

## Data Preprocessing
1. **Image and Mask Sorting**: The dataset is organized into images and corresponding masks, with sorting implemented based on file paths.
2. **Diagnosis Classification**: A binary classification (positve and negative) is applied based on the presence of tumor pixels in the masks.
3. **Visualization**: Several visualizations are created to inspect the dataset.

Sample images and masks are visualized with color mapping and side by side comparisons.
![image](https://github.com/user-attachments/assets/5a35f0ac-6855-40ee-8ff7-8e7bf08cdab0)
![image](https://github.com/user-attachments/assets/0200b664-f7cf-443f-bf3c-3c309b4f10e5)

![image](https://github.com/user-attachments/assets/544bbda5-c694-41c2-ae2f-c2d823286763)

## Model Architecture
The U-Net architecture is implemented for the segmentation task. U-Net consists of an encoder-decoder structure with skip connections between layers of the same resolution.
![image](https://github.com/user-attachments/assets/9ffc02c8-7f19-42e6-a6c5-d4af10711635)
- **Encoder**: Comprised of a series of convolutional and max-pooling layers to capture features at various spatial scales.
- **Decoder**: Upsampling layers paired with skip connections from the encoder layers to recover spatial resolution.
- **Output Layer**: Produces a single-channel binary mask for each input image.

## Training and Validation
The model is trained with a training set and validated on a separate validation set. A test set is reserved for final evaluation. Data augmentation techniques like random rotations, flips, and elastic transformations are applied to improve generalization.

### Hyperparameters:
- **Batch Size**: 32
- **Path Size**: 128x128
- **Optimizer**: Adam
- **Loss Function**: Binary Cross Entropy with Dice Coefficient

The model performance is monitored using validation loss and Dice coefficient metrics.

