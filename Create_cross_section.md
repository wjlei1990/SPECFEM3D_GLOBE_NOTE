This note will document how you can create cross sections using SPECFEM utility program and binary model files.

### 1. Pre-requirement
* `bin/xcreate_cross_section`

    Compile the executable using `make xcreate_cross_section`.
    
* model files in binary format
    
    Model files should be already generated in `DATABASES_MPI/*.bin`.
    
### 2. How to generate cross-section

Please reference the [source code](https://github.com/geodynamics/specfem3d_globe/blob/master/src/tomography/postprocess_sensitivity_kernels/create_cross_section.F90#L195)
for detailed information.

The arguments are listed below:
```
xcreate_cross_section param section-param mesh-dir/ model-dir/ output-dir/ topoography-flag ellipticity-flag
```

There are two types of cross sections you can generate.

1. Vertical cross section: `-V lat1,lon1,lat2,lon2,delta-incr,depth-incr,(depth_min),(depth_max)`
    
    Cross section will be made vertically, by specifying two points on the great arc, `(lat1, lon1)` and `(lat2, lon2)`. The `delta-incr` denote the resolution
    at horizontal direction and `depth-incr` on the vertical direction. `depth_min` and `depth_max` are optional argument. For example, `-V 10,20,-50,160,1,25`
    will generate a cross section that passes two points `(10, 20)` and `(-50,160)`. The horizontal resolution is 1 degree and the vertical resolution is 25km.
  

2. Horizontal (depth) cross section: `-H depth,delta-incr`

    Cross section will be made at `depth` and resolution `delta-inc`. For example, `-H 1000,2.0`, this cross section will be made at 1000km depth and 
    the grid size (resolution) of longitude and latitude will be 2 degree.
    
You may use it to generate the cross section file one at a time. The output file will be named as `cross_section_{parameter}.bin` in the directory
specified by the user `output-dir`. If you want to generate multiple cross-section files, you may need to rename the each output file, to prevent them from being
over-written.
