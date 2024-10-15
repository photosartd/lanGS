# Week 2: setup + figuring out some answers
1. How to query a set of Gaussians? [This issue answer](https://github.com/minghanqin/LangSplat/issues/26#issuecomment-2029074810) 
explains two ways to try to do it:
    - **Main used:** Render 2D image from 3D Gaussian Splatting scene and then query it:
      - We have precomputed lower dim pixel-wise features that do not weigh a ton
      - We have a decoder to decompress them
      - Now we can query each pixel on some level
      - Note: this does not give us explicit information on which Gaussians do we need. We will still need to 
      somehow backproject. Backprojection can't assess volume etc (problem if we want to manipulate Gaussians).
      - This method is used to produce all the visualisations [per the author](https://github.com/minghanqin/LangSplat/issues/22#issuecomment-2053893426).
    - **Direct queries to 3DGS:** not used at all since even the loss there includes only 2D loss on language features + a mask,
    not the loss between Gaussians and lang feats.
      - This may be one direction to make a research into
