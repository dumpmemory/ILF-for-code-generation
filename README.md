# Improving Code Generation by Training with Natural Language Feedback
<b>Authors</b>: Angelica Chen, Jérémy Scheurer, Tomasz Korbak, Jon Ander Campos, Jun Shern Chan, Samuel R. Bowman, Kyunghyun Cho, Ethan Perez

This repository contains the code and data (human-written feedback and refinements) for running the Imitation learning from Language Feedback (ILF) algorithm 
for code generation from "Improving Code Generation by Training with Natural Language Feedback" by [Chen et al. (2023)](https://arxiv.org/abs/2303.16749). This paper has since been superceded by our TMLR publication, ["Learning from Natural Language Feedback"](https://openreview.net/forum?id=xo3hI5MwvU).

<p align="center">
<img src=https://user-images.githubusercontent.com/72049239/228312658-e44fe06d-b1fd-4974-80d4-1e712c1051a3.png />
</p>

## Installation

Our code relies upon the [`jaxformer` repository](https://github.com/salesforce/jaxformer) and open-source [CodeGen-Mono checkpoints](https://github.com/salesforce/CodeGen).

To install all dependencies and download the necessary model checkpoints:
```{bash}
git clone git@github.com:nyu-mll/ILF-for-code-generation.git
cd ILF-for-code-generation
conda env create -f environment.yml

# Install codegen repo and reset to old commit
git clone git@github.com:salesforce/CodeGen.git
cd CodeGen
git reset --hard 9cc1f971c83ad606cce5da292d3c58523dd920a2
git clean -df
pip3 install -r requirements.txt
cd ..

# To download codegen-6B-mono
wget -P checkpoints https://storage.googleapis.com/sfr-codegen-research/checkpoints/codegen-6B-mono.tar.gz && tar -xvf checkpoints/codegen-6B-mono.tar.gz -C checkpoints/

```

In our paper we use the Codegen-Mono 6B checkpoint, but you can easily replace the above `wget` command with the download links for the [other CodeGen models](https://github.com/salesforce/CodeGen#sampling-with-repository).

## To run the ILF pipeline
To run the ILF pipeline using our dataset, run (from this directory):
```{bash}
source ilf_pipeline.sh -d $(pwd) -n <EXPERIMENT_NAME>
```
with `<EXPERIMENT_NAME>` replaced with the name of the subdirectory that you wish to store results in.

## Citation
```
@article{
chen2024learning,
title={Learning from Natural Language Feedback},
author={Angelica Chen and J{\'e}r{\'e}my Scheurer and Jon Ander Campos and Tomasz Korbak and Jun Shern Chan and Samuel R. Bowman and Kyunghyun Cho and Ethan Perez},
journal={Transactions on Machine Learning Research},
issn={2835-8856},
year={2024},
url={https://openreview.net/forum?id=xo3hI5MwvU},
note={}
}
```
