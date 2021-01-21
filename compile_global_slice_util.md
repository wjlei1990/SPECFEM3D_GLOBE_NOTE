This note tells you how to compile the `global_slice_util` located in  `utils/Visualization/VTK_ParaView/global_slice_util`.

1. check the `Makefile`

    check the `F90`, which is the fortran 90 compiler. Set it to what you are using (`ifort` or `gfortran`).
    ```
    cd utils/Visualization/VTK_ParaView/global_slice_util
    vim Makefile (then edit the F90)
    ```
    
    
2. Create two directories
    
    You have manually create two directories in `utils/Visualization/VTK_ParaView/global_slice_util`.
    ```
    mkdir obj mod
    ```
    
3. Compile
    
    ```
    Make
    ```
    
    The executable will be located in upper level directory. Check the output of `Make`:
    ```
    gfortran -o ../xglobal_slice_number -O3 global_slice_number.f90 -J mod obj/sub_slice_number.o 
    gfortran -o ../xnormal_plane -O3 normal_plane.f90 -J mod obj/sub_slice_number.o 
    gfortran -o ../xmake_az_stations -O3 make_az_stations.f90 -J mod obj/sub_slice_number.o 

    ```
