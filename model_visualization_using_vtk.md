# Model Visualization Using VTK

This note will walk you through how to convert the binary model files in SPECFEM3D_GLOBE to VTK files. The VTK files can then be used in Paraview or Visit for 3D model visualization.

### 1. Pre-requirement
* `bin/xcombine_vol_data_vtk`.
    
    Compile the executable for model data conversion using `make xcombine_vol_data_vtk`. The executable is located in `bin/xcombine_vol_data_vtk`.
    
* Binary model files in `DATABASES_MPI/*.bin`


### 2. How to generage vtk files

Please reference the [source code](https://github.com/geodynamics/specfem3d_globe/blob/master/src/auxiliaries/combine_vol_data.F90#L156) for detailed information. 

The argument is listed below:
```
xcombine_vol_data slice_list filename input_topo_dir input_file_dir output_dir high/low-resolution [region]
```
One example would be:
```
./bin/xcombine_vol_data all vs ./DATABASES_MPI/ ./DATABASES_MPI/ output_dir 0 1
```

Notice if you set the resolution to high (1), the output file size would be very large. Please start with low resolution (0) first.

Then you should be able to check the outputfile in the `output_dir` specified in your running command. The outputfile should have suffix "*.vtk".

### 3. Visualization

Load the vtk file generagedd into Paraview for 3D visulization.
