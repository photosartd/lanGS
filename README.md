# lanGS
A repository connecting Gaussian Splatting and language commands to interact with a GS scene.

## Installation
1. Clone: `git clone --recurse-submodules git@github.com:photosartd/lanGS.git`
2. Install [a conda environment for feature-splatting](git@github.com:photosartd/feature-splatting.git) as described in it's repository.
3. In this environment, install Milvus-lite to be able to embed 3D objects: 'pip install pymilvus==2.4.10'
4. Separately, install an objaverse environment to render views of 3D objects. The intruction could be found [here](https://github.com/allenai/objaverse-xl/tree/main/scripts/rendering). For this you will need
to install blender (blender-3.2.2 worked for me) executable and make sure it's accessible via `PATH`.

## Usage
### 3D assets embeddings
1. According to the [example](https://github.com/allenai/objaverse-xl/tree/main/scripts/rendering) in the objaverse repository, render a set of 3D objects from objaverse
(which you've already chosen previously based on Objaverse csv with their descriptions) to some directory.
2. Source feature-splatting environment with the installed pymilvus. To embed your database of 3D assets, use `feature-splatting/feature_splatting/db/__init__.py` script. Provide the following argument (inside the script):
    - `db_path` - a path where milvus database will be/is initialised
    - `db_name = "objaverse-gauss.db"` - a name of the database
    - `collection_name = "subset_10k_fsp_clip"` - a name for your embedding collection
3. After the scipt finishes, you now have the database of embeddings for each 3D asset you have.

### Training
1. Prepare the data for a scene you want to train. One option would be to download some scene from nerfstudio, e.g. poster: `ns-download-data nerfstudio --capture-name=poster`.
2. In `feature_splatting/model.py` in the `FeatureSplattingModelConfig` make sure to provide the same arguments for `db_path`, `db_name`, `db_collection_name` and `meshes_path` (this one should point to the glbs direcotry in the downloaded meshes) as above.
3. Train your model: `ns-train feature-splatting --data data/nerfstudio/poster`.

### Results
1. Run the model: `ns-viewer --load-config ./outputs/<dataset_name>/feature-splatting/<date_time>/config.yml`. This will set up the ns-viewer on the 7007 port. If training locally, just go to `localhost:7007` in your browser. Otherwise, use `ssh -N -f -L localhost:7007:localhost:7007 name@server-host` locally to be able to access viewer.
2. In the viwever, do:
    - Fill in **Positive Text Queries** with some object name in the scene (e.g. 'bed').
    - Click on **Enter editing mode** and then **Estimate ground**.
    - Click on **Segment main obj** (now it should be highlighted).
    - Click on **Similarity Search**. The **Mesh Results** list menu should appear above. Choose the mesh you want to add and see it appears in the scene.
    - You can also change **Mesh addition mode** (replace, add etc.).