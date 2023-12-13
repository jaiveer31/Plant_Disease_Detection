The key to reducing losses in agricultural product output and quantity is early detection of plant diseases. The study of plant diseases entails the examination of visually discernible patterns on the plant. Plant health monitoring and disease detection are crucial for long-term agriculture. Manually monitoring plant diseases is quite tough. It necessitates a great deal of effort, knowledge of plant diseases, and an inordinate length of processing time. As a result, image processing is utilized to detect plant illnesses. Picture acquisition, image pre-processing, image segmentation, feature extraction, and classification are all processes in the disease detection process.


IMPLEMENTATION

Steps Involved:


Data Preprocessing

1 ) Load Original Image. A total of 800 images for each class Diseased and Healthy is fed for the machine.

Conversion of image from RGB to BGR. Since Open CV (python library for Image Processing), accepts images in RGB coloring format so it needs to be converted to the original format that is BGR format.

Conversion of image from BGR to HSV. The simple answer is that unlike RGB, HSV separates luma, or the image intensity, from chroma or the color information. This is very useful in many applications. For example, if you want to do histogram equalization of a color image, you probably want to do that only on the intensity component, and leave the color components alone. Otherwise you will get very strange colors. In computer vision you often want to separate color components from intensity for various reasons, such as robustness to lighting changes, or removing shadows. Note, however, that HSV is one of many color spaces that separate color from intensity (See YCbCr, Lab, etc.). HSV is often used simply because the code for converting between RGB and HSV is widely available and can also be easily implemented.

Image Segmentation for extraction of Colors. In order to separate the picture of leaf from the background segmentation has to performed, The color of the leaf is extracted from the image.

Applying Global Feature Descriptor. Global features are extracted from the image using three feature descriptors namely :
• Color : Color Channel Statistics (Mean, Standard Deviation) and Color Histogram
• Shape : Hu Moments, Zernike Moments
• Texture : Haralick Texture, Local Binary Patterns (LBP)

After extracting the feature of images the features are stacked together using numpy function “np.stack”.

According to the images situated in the folder the labels are encoded in numeric format for better understanding of the machine.

The Dataset is splitted into training and testing set with the ratio of 80/20 respectively.

Feature Scaling Feature Scaling is a technique to standardize the independent features present in the data in a fixed range. It is performed during the data pre-processing to handle highly varying magnitudes or values or units. If feature scaling is not done, then a machine learning algorithm tends to weigh greater values, higher and consider smaller values as the lower values, regardless of the unit of the values.

Here, we have used Min-Max Scaler. This scaling brings the value between 0 and 1.

Saving the Features. After features are extracted from the images they are saved in HDF5 file. The Hierarchical Data Format version 5 (HDF5), is an open source file format that supports large, complex, heterogeneous data. HDF5 uses a "file directory" like structure that allows you to organize data within the file in many different structured ways, as you might do with files on your computer.

Modeling The Model is trained over 7 machine learning models named :
• Logistic Regression
• Linear Discriminant Analysis
• K Nearest Neighbours
• Decision Trees
• Random Forest
• Naïve Bayes
• Support Vector Machine

And the model is validated using 10 k fold cross validation technique.

9 ) Prediction The models with best performance is them trained with whole of the dataset and score for testing set is predicted using Predict function.

An accuracy of 98.125% is achieved using Randomm Forest Classifier.
