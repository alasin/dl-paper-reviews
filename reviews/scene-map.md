# Scene Structure Inference through Scene Map Estimation

**Problem**

Constructing a top-down representation of an indoor scene given a single RGB image.

**Key Points**

1. Introduce *scene map* as a representation for holistic scene understanding. Present a rendering pipeline for synthesizing new scenes. Use modified VGG to learn end-to-end.
2. Describe *scene map* as a combination of binary 2D grids (one grid each per object class) where a value of 1 represents presence of an object at that grid. Here, a grid cell represents 37.5 cm in real life.

![Scene-Map](http://geometry.cs.ucl.ac.uk/projects/2016/scenemap/paper_docs/scenemap_example.png)

3. Use a modified VGG-11 (with batch-norm) with an output size of *r * r * N* where r is grid dimension and N is the number of object classes. A sigmoid activation gives probablities for each point in the grid. Training is done on synthetic data with limited object classes and textures.
4. Use a combination of semantic segmentation and depth estimation as a baseline. 

**Results**

1. Performs extremely well compared to baseline.
2. 82% true positives on train and 71% true positives on test set when off-by-two errors allowed.
3. Heavy performance degradation on increasing the object density.

**Notes**

1. Novel application of a simple technique.
2. Very limited in terms of experiments. Authors address absence of real data but could have rendered synthetic data in a better way to make it look more realistic.
3. Approach doesn't take care of object orientation.
4. Approach doesn't look scalable and genaralizable to varied scenes and object densities.