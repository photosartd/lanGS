# Week 5: Experiments
1. **Objaverse:** downloaded ~1000 meshes of different classes (laptop, table, chair etc.), extracted 12 multi-view
images from ~ 750 of them (some could not be processed, problems with the script).
2. **Code**:
   - Played with their CLIP
   - Looked up how they store lang embeddings for Gaussians
     - Compress to 13 dimensions then decompress and use SAM/CLIP/DINO features - Autoencoder
   - 

**Plan for the next week:**
1. Extract embeddings for the stored Objaverse meshes and puth them into a local DB
2. Find 2-3 scenes and train Feature GS on them
3. Aggregate chosen GS blob embeddings into a single one and calculate some metrics e.g precision/recall/f1-score
