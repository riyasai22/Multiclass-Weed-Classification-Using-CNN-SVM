## Abstract
Early identification and removal of plant and weed seedlings is crucial for efficient crop management and weed control. Unwanted weed growth can have a negative impact on crop yield and quality, as they compete with the main crop for nutrients. This paper focuses on a hybrid methodology of using image processing, deep learning and machine learning techniques for the multiclass classification of plant and weeds seedlings. Using a combination of color-based segmentation, contrast enhancement, morphological operations, and CNN-SVM classifier, the proposed technique achieves high accuracy while being computationally ef icient. The proposed technique achieved a test accuracy of 88.45%, outperforming the existing technique that relied solely on CNNs for feature extraction and classification, which achieved a lower test accuracy of 80%. Comparison is done with existing transfer learning techniques MobileNet and VGG16 for classification, and the proposed model outperforms their performance results. Overall, the proposed technique shows great potential for improving the accuracy and ef iciency of multiclass classification of plant and weed seedlings, which has important implications for plant science and agriculture.

## Segmentation Algorithm

For each image i in testset:
1. Apply Gaussian blur to i with kernel size of (5,5) and sigma=0, store result in blurr
2. Convert blur from BGR color space to HSV color space, store result in hsv
3. Define lower and upper thresholds for HSV color space
4. Apply inRange function to hsv with lower and upper thresholds to create a binary mask, store result in mask
5. Define a structuring element for morphological closing with an elliptical kernel of size (11,11), store result in struc
6. Apply morphological closing to mask with struc, store result in mask
7. Create a boolean mask by checking if the pixel values in mask are greater than 0, store result in boolean
8. Create a new image array of zeros with same dimensions as i, of data type uint8, store result in new
9. Copy pixels from i to new where boolean mask is True
10. Apply Contrast Limited Adaptive Histogram Equalization (CLAHE) to new with clip limit=2.0 and tile size of (8,8), store result in clahe_img
11. Yield clahe_img

## Classification Algorithm

Algorithm
Initialize a Sequential CNN model
- insert Conv2D layer with 64 filters and kernel size of (5,5) with ReLU activation
- add BatchNormalization layer
- insert Conv2D layer with 64 filters and kernel size of (5,5) with ReLU activation
- add MaxPooling2D layer with pool size of (2,2)
- add BatchNormalization layer
- add Dropout layer with rate of 10%
- insert Conv2D layer with 128 filters and kernel size of (5,5) with ReLU activation
- add BatchNormalization layer
- insert Conv2D layer with 128 filters and kernel size of (5,5) with ReLU activation
- add MaxPooling2D layer with pool size of (2,2)
- add BatchNormalization layer
- add Dropout layer with rate of 10%
- insert Conv2D layer with 256 filters and kernel size of (5,5) with ReLU activation
- add BatchNormalization layer
- insert Conv2D layer with 256 filters and kernel size of (5,5) with ReLU activation
- add MaxPooling2D layer with pool size of (2,2)
- add BatchNormalization layer
- add Dropout layer with rate of 10%
- insert Flatten layer
- insert Dense layer with 256 units and ReLU activation
- add BatchNormalization layer
- add Dropout layer with rate of 50%
- insert Dense layer with 256 units and ReLU activation
- add BatchNormalization layer
- add Dropout layer with rate of 50%
- insert Dense layer with 12 units and softmax activation with L2 regularization term


## Results

![image](https://user-images.githubusercontent.com/80235375/236328538-0338f6ba-892d-48c0-a80c-45809a869a5d.png)

