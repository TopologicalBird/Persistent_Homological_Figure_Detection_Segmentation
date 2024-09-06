# Persistent_Homological_Figure_Detection_Segmentation
## Description
Persistent homology tool for the detection and segmentation of overlapping disk-like objects.

This is based on the following articles:

https://doi.org/10.14495/jsiaml.15.33

https://doi.org/10.1038/s41598-023-37760-3

https://doi.org/10.14495/jsiaml.16.25

The image is taken from BBBC005v1

(Broad Bioimage Benchmark Collection; Ljosa, V., Sokolnicki, K. L. & Carpenter, A. E. Annotated high-throughput microscopy image sets for validation. Nat. Methods 9, 637 (2012)).

The latter part is the slight modification of the detection method to the segmentation method.

This code uses HomCloud for the calculation of persistent homology available at https://homcloud.dev/index.en.html

## Parameter tuning tips
The main parameters are death_threshold and lifethres.
### death_threshold
should be the minimum internal radius of the figures to be detected.
### lifethres
should be the minimum life (persistence) of the figures to be detected. Persistence is the difference of birth and death. When detecting overlapping figures, if we set lifethres smaller, we will separate figures with larger overlaps.
### BDsizethreshold
should be the minimum length of the boundary of the connected components that will be processed. This parameter is meant to reduce the unnecessary calculation of PH for too small connected components (coming from noise).

When you change death_threshold, please make sure you also change BDsizethreshold accordingly. (When we want to detect smaller figures, we can decrease death_threshold. However, if we forget to make BDsizethreshold smaller, the small figure of interest might not get into PH calculation.)
### death_upper_threshold
should be the maximum internal radius of the figures to be detected. This parameter is meant to reduce the non-existing figures formed by multiple different boundaries. There are several ways to get out of this problem (e.g. using different filtrations) other than this parameter.
