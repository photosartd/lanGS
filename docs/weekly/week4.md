# Week 4: Objaverse
## New pipeline
1. Language conditioned selection of a group of GS via Feature Splatting
2. Having a (local) database with embeddings of meshes
    - [Milvus](https://milvus.io) for the vector search
    - Embeddings
      - (Relatively) easy option: text embeddings of meshes description
      - Basic CLIP (from Feature Splatting) for processing image embeddings of GS/meshes
      - [DuoduoCLIP](https://github.com/3dlg-hcvc/DuoduoCLIP/tree/main?tab=readme-ov-file) embeddings
      for more efficient multi-view embeddings

## For now:
1. Got to know how to create embeddings via blender cmd
2. Looked into the Objaverse dataset and found a lot of rubbish and lack of categories/classes in description.
