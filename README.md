# Stratify or Die: Rethinking Data Splits in Image Segmentation

This repository contains the official implementation of our NeurIPS 2025 submission:  
**“Stratify or Die: Rethinking Data Splits in Image Segmentation.”**  
[[Preprint Link]](https://arxiv.org/abs/2509.21056)

---

## Setup

We recommend using a virtual environment to manage dependencies:

```bash
python -m venv venv
source venv/bin/activate  # Use `venv\Scripts\activate` on Windows
pip install -r requirements.txt
```
## Dataset Setup

We demonstrate training on the `CamVid` dataset using different stratification algorithms.

To download and extract the `CamVid` dataset from a publicly hosted instance:
```bash
mkdir datasets
wget https://datasets.cms.waikato.ac.nz/ufdl/data/camvid/camvid-bluechannel.zip -O ./datasets/camvid.zip
unzip -q ./datasets/camvid.zip -d dataset/camvid
```

## Training

To reproduce our `CamVid` experiments using the `UNet` model with `WDES` stratification (fold `0`):

```train
python train.py -d camvid -p ./datasets  -m unet -s wdes -ns 10 -f 0 -e 50 -bs 4 -lr 2e-4
```

## Stratification Options
Use the `-s` flag to select one of the following strategies:

* random — standard random splits
* ips — Iterative Pixel Stratification (ours)
* wdes — Wasserstein Distance Evolutionary Stratification (ours)

For additional datasets and models, refer to the scripts and configuration options in the repository.

## License
This project is licensed under the **[PolyForm Noncommercial License 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0/)**.

### What does this mean?
- **Free for non-commercial use:** You are free to use, modify, and distribute this software for non-commercial purposes.
- **Commercial use requires a license:** If you intend to use this software for commercial purposes (e.g., as part of a product or service that generates revenue), you must obtain a commercial license.

### How to obtain a commercial license
If you are interested in using this software for commercial purposes, please contact me at **jitin [dot] jami [at] fau [dot] de** to discuss licensing options.
