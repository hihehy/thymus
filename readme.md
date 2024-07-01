# Multi-Instance Learning for Whole-Slide Image Classification
Divide the 5 thymoma categories (A, AB, B1, B2, B3) into 0 and 1 classes. 0 class contains slides from A and B3 categories. 1 class contains slides from AB, B1, and B2 categories.  
Steps:  
1. Use OTSU method to slide the whole-slide images.
2. Extract features for 0 and 1 class slides using the [CLAM](https://github.com/mahmoodlab/CLAM.git) method. 
3. Use the [HIPT](https://github.com/mahmoodlab/HIPT.git) multi-instance classification for the first step. 
4. Extract features for specific 0 class (A, B3) and 1 class (AB, B1, B2) whole-slide images, and perform [BCL](https://github.com/Zero-We/BCL.git) classification.
5. Integrate the results of the two-step classification.  
  
# HoverNet for Cell Feature Analysis
Apply the trained HoverNet model to all whole-slide images, segment and classify different cell types in the patches. Extract features such as cell type proportion and pixel area for analysis.  
Steps:
1. Train and test the [HoverNet](https://github.com/vqdang/hover_net.git) model using annotated patches. 
2. Use the trained HoverNet model to segment and classify cells in all whole-slide images.
3. Extract cell features (e.g., cell type, pixel area, curvature, perimeter) for each patch in a slide using `Cell_feature.py`. If a slide has multiple patch types, save multiple files (one row per cell).
4. Summarize and compare the tumor and endothelial cell features (e.g., count, pixel area) for the 5 categories based on the multi-instance prediction (one row per slide).