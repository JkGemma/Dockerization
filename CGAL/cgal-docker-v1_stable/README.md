### Build
```bash
docker build docker build -t upfactor/cgal:test .
```

### Run
```bash
docker run -v /data/from/path/:/data --rm -it upfactor/cgal:test bash
```

### How to compile example ?
```bash
cd CGALFOLDER/examples/EXAMPLEFOLDER
make -j $(grep --count ^processor /proc/cpuinfo)
```
- e.g.:
```bash
cd CGAL-4.13/examples/Poisson_surface_reconstruction_3
make -j $(grep --count ^processor /proc/cpuinfo)
```

### Example compiled by default docker build
- examples/Poisson_surface_reconstruction_3
- examples/Point_set_processing_3
- examples/Alpha_shapes_2
- examples/Alpha_shapes_3


### Non-usefull informations
- DEP: OpenMesh
    - Polygon_mesh_processing
    - BGL_Openmesh
    - BGL_Polyhedron
    - Convex_hull_3
    -  Surface_mesh_deformation
    -  Surface_mesh_segmentation
    -  Surface_mesh_shortest_path
    -  Surface_mesh_simplification
- DEP: OpenCV (non-used)
    - Classification
- DEP: VTK (non-used)
    - Mesh_3
- DEP: ESBTL : (non-used) last update 2015
     - Skin_surface_pdb_reader
