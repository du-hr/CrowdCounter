# CrowdCounter
Course Project: Counting People in a Shopping Mall ECSE 415 (Fall 2020) @ McGill University

##List of Parameters to Play with (so far)

1. Number of images used in the dataset for creating the training data
2. Number of random non-people used for each image for creating the training data
3. The size of the windows of people (maybe try to get just their head+shoulders?)
4. The size of the windows of non-People

## Importing the Frames Dataset

1. Please un-zip the "frames.zip" file in this repository.
2. Upload the un-zipped folder called "frames" directly to the home directory of your Goole Drive.
3. Open the Jupyter Notebook in Google Colab. Make sure you use the same Google account as the previous step.
4. Run the Jupyter Notebook in Google Colab. Please follow the instrcutions given by Google Colab at runtime in order to grant the program access to the "frames" dataset saved in your Google Drive.

## Loading Private Notebooks

Loading a notebook from a private GitHub repository is possible, but requires an additional step to allow Colab to access your files.
Do the following:

1. Navigate to http://colab.research.google.com/github.
2. Click the "Include Private Repos" checkbox.
3. In the popup window, sign-in to your Github account and authorize Colab to read the private files.
4. Your private repositories and notebooks will now be available via the github navigation pane.

## Saving Notebooks To GitHub or Drive

Any time you open a GitHub hosted notebook in Colab, it opens a new editable view of the notebook. You can run and modify the notebook without worrying about overwriting the source.

If you would like to save your changes from within Colab, you can use the File menu to save the modified notebook either to Google Drive or back to GitHub. Choose **File→Save a copy in Drive** or **File→Save a copy to GitHub** and follow the resulting prompts. To save a Colab notebook to GitHub requires giving Colab permission to push the commit to your repository.


## Project Gameplan

### PART 1:
- Use YOLO, Faster-RCNN or another method to produce bounding boxes around people in the mall images
- WRITE CODE to remove duplicates and to count the bounding boxes

### PART 2:
- Use SVM for this
- Create the dataset:
    - To create the positives(people): crop out the image patches of people from running the images through PART 1
    - To create the negatives(not people): extract random patches from the image (potential problem: what if the random patch contains a person??)
- Once you have the dataset, compute features of the images to feed through the SVM (HoG, Harr, LBP, or other)
- Train the SVM with these features (its up to us to determine how many examples to use for training, we could test this to find the best and include in the report)
- Once the SVM is trained, use it as the person counter

### EXCERPTS FROM THE STUDY:
- Video imagery based crowd counting for population profiling remains a nontrivial problem in crowded scenes. Specifically, frequent occlusion between pedestrians and background clutter render a direct implementation of standard object segmentation and tracking infeasible. The problem is further compounded by visual ambiguities caused by varying individual appearances and body articulations, and group dynamics. External factors such as camera viewing angle, illumination changes, and distance from the region of interest also pose great challenges to the counting problem.
- The choice of classifier imposes significant impact on the speed and quality of detection, often requiring a trade-off between these two. (SVM is good but slow)
- Specifically talking about how to implement SVM: A trained classifier is then applied in a sliding window fashion across the
whole image space to detect pedestrian candidates. Less confident candidates are
normally discarded using non-maximum suppression, which leads to final detections that suggest the total number of people in a given scene. Whole body monolithic detector can generates reasonable detections in sparse scenes. However, it suffers in crowded scenes where occlusion and scene clutter are inevitable
- Talking about using only HEAD of the person for detection: Including the shoulder region to form an omegalike shape pattern tends to give better performance in real-world scenarios [47]. The detection performance can be further improved by tracking validation, i.e. associating detections over time and rejecting spurious detections that exhibit coherent motion with the head candidates
- Head and shoulders-based detection: more robust in crowded areas with lots of occlusion
