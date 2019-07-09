## Informations
  XYZ = Base Input File = Echantillon.xyz
  PWN = Normal Estimation Output File
  RWXYZP = Read Write XYZ Point Output File
  FSR = Front Surface Reconstruction Output File

## ADVANCING_FRONT_SURFACE_RECONSTRUCTION
  -> Advancing_front_surface_reconstruction/ ./reconstruction_structured
  Input: XYZ | Output : Echantillon_XYZ.off (FSR)

## POISSON_SURFACE_RECONSTRUCTION_3
  -> Poisson_surface_reconstruction_3/ ./poisson_reconstruction
  Input : XYZ | Output: No normals

  -> Poisson_surface_reconstruction_3/ ./poisson_reconstruction
  Input : PWN | Output: Infinite loading (?)





## POINT_SET_PROCESSING_3
  -> Point_set_processing_3/ ./normal_estimation
  Input: XYZ | Output : Echantillon_XYZ.pwn (PWN)
  -> Point_set_processing3/ ./read_write_xyz_point_set_example
  Input: XYZ | Output : EchantillonRWXYZP.xyz (RWXYZP)

## POINT_SET_SHAPE_DETECTION_3
  -> Point_set_shape_detection_3 ./efficient_RANSAC_custom_shape
  Input: PWN | Output:
  ```
    16 shapes detected.
  ```
  -> Point_set_shape_detection_3 ./efficient_RANSAC_parameters
  Input: PWN | Output:
  ```
    50000 points
    25 detected shapes, 4552 unassigned points.
    Plane with normal 0 0 1
    Kernel::Plane_3: 0 0 1 -0.320513
    Plane with normal -1 0 0
    Kernel::Plane_3: -1 0 0 -0.5
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 0.371795
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 -0.371795
    Plane with normal -1 -0 0
    Kernel::Plane_3: -1 -0 0 0.5
    Plane with normal 0 -0 1
    Kernel::Plane_3: 0 -0 1 0.371795
    Plane with normal 0 -0 1
    Kernel::Plane_3: 0 -0 1 0.333333
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 -0.294872
    Plane with normal -0 -1 0
    Kernel::Plane_3: -0 -1 0 0.294872
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 -0.371795
    Plane with normal 0 0 1
    Kernel::Plane_3: 0 0 1 -0.371795
    Plane with normal 0 0 -1
    Kernel::Plane_3: 0 0 -1 0.320513
    Plane with normal 1 0 0
    Kernel::Plane_3: 1 0 0 -0.141109
    Cylinder with axis -0.00063835 -0.330142 -0.0809345 -0.00063835 -0.330142 0.919065 and radius 0.449356
    Plane with normal -0 1 0
    Kernel::Plane_3: -0 1 0 0.294872
    Type: torus center(-2.68113, 0.936024, -0.185459) axis(0.356817, 0.934167, 0.00375993) major radius = 2.62331 minor radius = 0.0435577 #Pts: 275
    Cylinder with axis 0.230308 0.000719627 -0.243213 0.240287 0.0146577 -1.24307 and radius 0.0376767
    Cylinder with axis 0.000844175 0.00118042 0.356916 0.000844175 0.00118042 1.35692 and radius 0.204547
    Plane with normal -1 0 -0
    Kernel::Plane_3: -1 0 -0 -0.141154
    Cylinder with axis -0.231015 0.00129447 -0.291121 -0.236582 -0.007181 0.708828 and radius 0.0443875
    Plane with normal 1 -0 0
    Kernel::Plane_3: 1 -0 0 0.448718
    Plane with normal 1 0 -0
    Kernel::Plane_3: 1 0 -0 -0.141026
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 -0.294872
    Cylinder with axis 0.132451 -0.000680185 0.356597 0.161264 -0.0779294 1.35319 and radius 0.251889
    Cylinder with axis -0.118771 0.00323417 0.359987 -0.131034 -0.0090287 -0.639863 and radius 0.26514
  ```
  -> Point_set_shape_detection_3 ./efficient_RANSAC_point_access
  Input: PWN | Output:
  ```
    preprocessing took: 141.902ms
    time: 3375.64ms
    16 primitives, 0.85588 coverage
    time: 3158.37ms
    16 primitives, 0.85604 coverage
    time: 3116.62ms
    16 primitives, 0.85656 coverage
    Type: plane (0, 0, 1)x - -0.320513= 0 #Pts: 3832 average distance: 9.38674e-07
    Type: plane (-1, 0, 0)x - -0.5= 0 #Pts: 5227 average distance: 3.14712e-07
    Type: plane (-0, -1, 0)x - 0.371795= 0 #Pts: 4933 average distance: 2.85222e-07
    Type: plane (0, 1, 0)x - 0.371795= 0 #Pts: 2435 average distance: 0
    Type: plane (0, -0, 1)x - 0.371795= 0 #Pts: 7544 average distance: 0.0161429
    Type: plane (1, 0, 0)x - -0.5= 0 #Pts: 4621 average distance: 6.72582e-07
    Type: plane (0, 1, 0)x - 0.294872= 0 #Pts: 2332 average distance: 0.00305142
    Type: plane (0, 1, 0)x - -0.294872= 0 #Pts: 2943 average distance: 0.00204613
    Type: plane (-0, -1, 0)x - -0.371795= 0 #Pts: 2397 average distance: 7.65123e-07
    Type: plane (0, 0, 1)x - -0.371795= 0 #Pts: 2291 average distance: 4.67918e-07
    Type: plane (0, -0, -1)x - 0.320513= 0 #Pts: 1512 average distance: 1.24603e-06
    Type: plane (-1, 0, -0)x - 0.141026= 0 #Pts: 570 average distance: 0
    Type: plane (-1, 0, 0)x - -0.141154= 0 #Pts: 564 average distance: 0
    Type: plane (-1, 0, 0)x - 0.448718= 0 #Pts: 560 average distance: 2.98929e-06
    Type: plane (1, 0, 0)x - -0.141109= 0 #Pts: 554 average distance: 1.66065e-07
    Type: plane (1, 0, 0)x - 0.448718= 0 #Pts: 513 average distance: 2.82261e-06
  ```
  -> Point_set_shape_detection_3 ./plane_regularization
  Input: PWN | Output: null

  -> Point_set_shape_detection_3 ./shape_detection_basic
  Input: PWN | Output:
  ```
    Region Growing
    0 shapes detected.
  ```
  -> Point_set_shape_detection_3 ./shape_detection_with_callback
  Input: PWN | Output
  ```
    Region Growing
    Algorithm takes too long, exiting (0% done)
  ```
  __________________________________________________________________

  -> Point_set_shape_detection_3 ./efficient_RANSAC_custom_shape
  Input: XYZ | Output:
  ```
    16 shapes detected.
  ```
  -> Point_set_shape_detection_3 ./efficient_RANSAC_parameters
  Input: XYZ | Output:
  ```
    50000 points
    24 detected shapes, 4022 unassigned points.
    Plane with normal -0 0 1
    Kernel::Plane_3: -0 0 1 -0.320513
    Plane with normal -1 0 0
    Kernel::Plane_3: -1 0 0 -0.5
    Plane with normal 0 -1 -0
    Kernel::Plane_3: 0 -1 -0 0.371795
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 -0.371795
    Plane with normal 1 0 0
    Kernel::Plane_3: 1 0 0 -0.5
    Plane with normal -0 -0 1
    Kernel::Plane_3: -0 -0 1 0.371795
    Plane with normal 0 0 1
    Kernel::Plane_3: 0 0 1 0.333333
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 -0.294872
    Plane with normal -0 -1 0
    Kernel::Plane_3: -0 -1 0 0.294872
    Plane with normal -0 1 0
    Kernel::Plane_3: -0 1 0 0.371795
    Plane with normal 0 -0 -1
    Kernel::Plane_3: 0 -0 -1 0.371795
    Plane with normal -0 0 -1
    Kernel::Plane_3: -0 0 -1 0.320513
    Plane with normal 1 0 -0
    Kernel::Plane_3: 1 0 -0 -0.141026
    Cylinder with axis 0.153796 -0.331695 -0.259777 0.153796 -0.331695 0.740223 and radius 0.294922
    Cylinder with axis -0.230966 -0.000103565 -0.194156 -0.222922 0.0138157 -1.19403 and radius 0.0433918
    Cylinder with axis 0.230976 -0.000361864 -0.172808 0.224946 -0.000789741 0.827173 and radius 0.0384967
    Plane with normal 0 -1 0
    Kernel::Plane_3: 0 -1 0 -0.294872
    Cylinder with axis 1.04029 -0.329115 -0.0918798 1.04029 -0.359009 -1.09143 and radius 1.18144
    Plane with normal 1 -0 0
    Kernel::Plane_3: 1 -0 0 -0.141109
    Type: cone apex: (0.0847624, -0.19324, -6.01082) axis: (-0.0133163, 0.0305328, 0.999445) angle:0.0323139 #Pts: 681
    Cylinder with axis 0.459074 -0.322285 0.0668849 0.459074 -0.322285 -0.933115 and radius 0.907792
    Type: cone apex: (-0.357724, 0.147503, -759.732) axis: (0.000302339, -0.000194313, 1) angle:0.000336744 #Pts: 304
    Plane with normal 0 1 0
    Kernel::Plane_3: 0 1 0 0.294872
    Cylinder with axis 0.173113 -0.48748 -0.344754 1.16964 -0.48748 -0.261515 and radius 0.718377
  ```
  -> Point_set_shape_detection_3 ./efficient_RANSAC_point_access
  Input: XYZ | Output:
  ```
    preprocessing took: 140.869ms
    time: 3350.64ms
    16 primitives, 0.8566 coverage
    time: 2954.74ms
    16 primitives, 0.8555 coverage
    time: 3166.49ms
    16 primitives, 0.856 coverage
    Type: plane (0, 0, -1)x - 0.320513= 0 #Pts: 3832 average distance: 9.38674e-07
    Type: plane (-1, 0, 0)x - -0.5= 0 #Pts: 5227 average distance: 3.14712e-07
    Type: plane (0, -1, 0)x - 0.371795= 0 #Pts: 4933 average distance: 2.85222e-07
    Type: plane (0, 1, 0)x - 0.371795= 0 #Pts: 2435 average distance: 0
    Type: plane (-1, 0, 0)x - 0.5= 0 #Pts: 4621 average distance: 6.72582e-07
    Type: plane (0, 0, 1)x - 0.371795= 0 #Pts: 7544 average distance: 0.0161429
    Type: plane (0, -1, 0)x - -0.294872= 0 #Pts: 2332 average distance: 0.00305142
    Type: plane (-0, -1, -0)x - 0.294872= 0 #Pts: 2943 average distance: 0.00204613
    Type: plane (0, -1, 0)x - -0.371795= 0 #Pts: 2397 average distance: 7.65123e-07
    Type: plane (0, 0, 1)x - -0.371795= 0 #Pts: 2291 average distance: 4.67918e-07
    Type: plane (0, 0, 1)x - -0.320513= 0 #Pts: 1512 average distance: 1.24603e-06
    Type: plane (1, 0, -0)x - -0.141109= 0 #Pts: 570 average distance: 8.3e-05
    Type: plane (-0.999897, -0.0138326, -0.00379433)x - 0.137265= 0 #Pts: 556 average distance: 0.000939635
    Type: plane (1, 0, 0)x - 0.141154= 0 #Pts: 564 average distance: 0
    Type: plane (1, 0, 0)x - -0.448718= 0 #Pts: 560 average distance: 2.98929e-06
    Type: plane (-1, 0, 0)x - -0.448718= 0 #Pts: 513 average distance: 2.82261e-0
  ```
  -> Point_set_shape_detection_3 ./plane_regularization
  Input: XYZ | Output: null

  -> Point_set_shape_detection_3 ./shape_detection_basic
  Input: XYZ | Output:
  ```
    Region Growing
    16 shapes detected.
  ```
  -> Point_set_shape_detection_3 ./shape_detection_with_callback
  Input: XYZ | Output
  ```
    Region Growing
    Algorithm takes too long, exiting (78.5086% done)
  ```
