# CrowdCounter

Project Gameplan:

PART 1:
- Use YOLO, Faster-RCNN or another method to produce bounding boxes around people in the mall images
- WRITE CODE to remove duplicates and to count the bounding boxes

PART 2:
- Use SVM for this
- Create the dataset:
    - To create the positives(people): crop out the image patches of people from running the images through PART 1
    - To create the negatives(not people): extract random patches from the image (potential problem: what if the random patch contains a person??)
- Once you have the dataset, compute features of the images to feed through the SVM (HoG, Harr, LBP, or other)
- Train the SVM with these features (its up to us to determine how many examples to use for training, we could test this to find the best and include in the report)
- Once the SVM is trained, use it as the person counter 



EXCERPTS FROM THE STUDY:
- Video imagery based crowd counting for population profiling remains a nontrivial problem in crowded scenes. Specifically, frequent occlusion between pedestrians and background clutter render a direct implementation of standard object segmentation and tracking infeasible. The problem is further compounded by visual ambiguities caused by varying individual appearances and body articulations, and group dynamics. External factors such as camera viewing angle, illumination changes, and distance from the region of interest also pose great challenges to the counting problem.
- The choice of classifier imposes significant impact on the speed and quality of detection, often requiring a trade-off between these two. (SVM is good but slow)
- Specifically talking about how to implement SVM: A trained classifier is then applied in a sliding window fashion across the
whole image space to detect pedestrian candidates. Less confident candidates are
normally discarded using non-maximum suppression, which leads to final detections that suggest the total number of people in a given scene. Whole body monolithic detector can generates reasonable detections in sparse scenes. However, it suffers in crowded scenes where occlusion and scene clutter are inevitable
- Talking about using only HEAD of the person for detection: Including the shoulder region to form an omegalike shape pattern tends to give better performance in real-world scenarios [47]. The detection performance can be further improved by tracking validation, i.e. associating detections over time and rejecting spurious detections that exhibit coherent motion with the head candidates
- Head and shoulders-based detection: more robust in crowded areas with lots of occlusion

