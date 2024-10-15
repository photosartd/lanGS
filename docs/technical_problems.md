# A list of technical problems and how to solve them
1. Problems with installation of libraries/submodules (vanilla GS, GS lightning, diff-rasterizer, simple-knn etc.):
   - Try creating an empty conda env firstly, then install cuda-toolkit/dev:
     - `conda install -c "nvidia/label/cuda-11.8.0" cuda-toolkit` (change for the needed version according to pytorch)
   - 