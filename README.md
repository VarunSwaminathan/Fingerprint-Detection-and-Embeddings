# Fingerprint-Detection-and-Embeddings

Part 1 – Data Collection 
More than 15 images of my hand were photographed under different light conditions and background, 
and all have been stored and submitted along with the submission file. The entire palm of the hand was 
taken. The camera specifications are as follows:
Device – Mobile Phone
Device name – OnePlus 6T
Camera Specifications:
Focal Length - 4.25mm
Megapixel – 16MP
The data is available at the folder Train_dataset in the submission file. 
Part 2 – Annotation 
The hand images were then annotated using labelImg. The json file of every image is stored into the 
annotated image folder in the submission file. 
Part 3 – Detection 
The algorithm used to detect fingerprint regions is given below:
1. Import necessary libraries: os, cv2, and mediapipe
2. Initialize mediapipe hands model
3. Set input folder and output folder paths
4. Check if output folder exists, if not, create it
5. Loop through each file in the input folder:
a. Check if file is an image file (jpg, jpeg, or png)
b. Load the image using cv2.imread
c. Convert the image to RGB color space.
d. Process the image using mediapipe hands model to obtain hand landmarks.
e. If hand landmarks are detected:
i. Create a copy of the image.
ii. ii. Loop through each detected hand:
f. Loop through each landmark in the hand:
g. Check if the landmark is a fingertip (at index 4, 8, 12, 16, or 20)
h. Compute the coordinates of the bounding box around the fingertip.
i. Draw a rectangle around the fingertip using the computed coordinates.
ii. Save the annotated image to the output folder with the same filename.
A sample image after detection is given below.
Part 4 – Validation 
For the validation purpose, the IoU value was calculated. The images were annotated and then saved 
also as a txt file. The x and y values from the output and the txt were compared manually and the final 
IoU value was calculated to be 0.9464(rounded to .4f digits).
The value could have been a lot higher but during annotation, the fingers overlapped and then there was 
a slight error during the detection phase. 
Part 5 – Testing 
The model that was created was used to detect fingerprint regions in the given dataset. The accuracy of 
the algorithm was not perfect. The detected fingertip regions were only detected from photos that had a 
full picture of the hand. As my algorithm was based on that, some photos in the test dataset were only 
pictures of the fingers without any palm region so the accuracy of my model dropped in some images 
and the algorithm was able to detect in certain images. To try and counter this problem, I first 
augmented my train dataset by rotating and shearing as well and tried it again with my algorithm and 
the algorithm detected the fingertip regions with a similar accuracy as last time. So, due to the 
discrepancy of the test dataset, the algorithm was not able to accurately detect fingertip regions. 
A sample image after detection is given below.
In some cases, like above, other parts of the fingers were also detected. This is also due to the same 
reason given above.
