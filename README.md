# DLP-Author-Recognizer

Datasets Used
We used the IAM Sentences Dataset from Kaggle:  IAM Sentences – Kaggle Dataset .  It’s a collection of handwritten English sentence images derived from the IAM Handwriting Database. It comprises approximately 16,800 image files, each representing a handwritten sentence.
Each image in the dataset corresponds to a sentence written by a specific writer, providing a diverse range of handwriting styles.
Dataset Overview:
Source: IAM Handwriting Database
Format: Image files (.png) labeled by writer ID
Language: English
Labels: Each image is annotated with the writer's identity (used as the class label)
Number of Classes: 25 unique writers (after filtering)
Preprocessing:
Grayscale normalization
Image resizing and padding
Patch extraction for better feature representation
Model(s) Used
We implemented a Deep Convolutional Neural Network (CNN) architecture for writer identification. Key features of the model are:
Patch-Based Input Processing: Handwritten images are divided into smaller patches. These local patches are used to train the CNN, enabling it to learn fine-grained features of handwriting.
CNN Layers:
Convolution → ReLU → MaxPooling
Fully Connected Layer → ReLU → Dropout
Final output through a Softmax Layer (for classification into 25 writer classes)
Loss Function: Categorical Cross-Entropy
Results
The final trained model achieved robust performance on the test set, demonstrating its ability to distinguish between handwriting styles from different individuals.
Key Metrics:
Test Accuracy (Word-level): ~74%
Inference Time: < 0.5 seconds per sample (GPU)
Confusion Matrix:
 A detailed confusion matrix was generated to visualize the model's performance across all 25 classes (writer identities). The matrix revealed that most misclassifications occurred between writers with very similar handwriting patterns, while strong diagonal dominance showed high precision for many classes.


Precision, Recall, and F1-score for each class
Macro and Weighted Averages for overall performance


Visualization:
The Confusion Matrix was plotted using seaborn.heatmap to visually assess correct and incorrect predictions across all writer classes.

The matrix showed dominant diagonal elements (e.g., for classes 0, 7, 13, 23) confirming accurate classifications.
Discussion on Results
The classification report and confusion matrix reveal important insights:
Strong Model Generalization:
The CNN model demonstrated consistent classification performance across most writer classes, with higher scores in well-represented classes.


Handling Writer Similarities:
Some classes showed notable confusion due to high intra-class similarity in handwriting (e.g., classes 1 and 14, 20 and 23), which is expected in biometric handwriting recognition.


F1-Score Balance:
The macro F1-score indicated relatively balanced precision and recall across classes, even with class imbalance in the dataset.


Patch-Based Strategy Strength:
The use of patch-level CNN inference improved model robustness for variable-length handwriting inputs, which was especially helpful given the diversity of the IAM dataset.


