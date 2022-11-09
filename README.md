[English](./README.md) / [Spanish](./README_es.md) / [Korean](./README_ko.md) / [Chinese](./README_zh.md) / [Bengali](./README_bn.md) / [Indonesian](./README_id.md) / [Italian](./README_it.md) / [Portuguese](./README_pt.md) / [Vietnamese](./README_vn.md)

# The fastai book

These notebooks cover an introduction to deep learning, [fastai](https://docs.fast.ai/), and [PyTorch](https://pytorch.org/). fastai is a layered API for deep learning; for more information, see [the fastai paper](https://www.mdpi.com/2078-2489/11/2/108). Everything in this repo is copyright Jeremy Howard and Sylvain Gugger, 2020 onwards. A selection of chapters is available to [read online here](https://fastai.github.io/fastbook2e/).

The notebooks in this repo are used for [a MOOC](https://course.fast.ai) and form the basis of [this book](https://www.amazon.com/Deep-Learning-Coders-fastai-PyTorch/dp/1492045527), which is currently available for purchase. It does not have the same GPL restrictions that are on this repository.

The code in the notebooks and python `.py` files is covered by the GPL v3 license; see the LICENSE file for details. The remainder (including all markdown cells in the notebooks and other prose) is not licensed for any redistribution or change of format or medium, other than making copies of the notebooks or forking this repo for your own private use. No commercial or broadcast use is allowed. We are making these materials freely available to help you learn deep learning, so please respect our copyright and these restrictions.

If you see someone hosting a copy of these materials somewhere else, please let them know that their actions are not allowed and may lead to legal action. Moreover, they would be hurting the community because we're not likely to release additional materials in this way if people ignore our copyright.

## Colab

Instead of cloning this repo and opening it on your machine, you can read and work with the notebooks using [Google Colab](https://research.google.com/colaboratory/). This is the recommended approach for folks who are just getting started -- there's no need to set up a Python development environment on your own machine, since you can just work directly in your web-browser.

You can open any chapter of the book in Colab by clicking on one of these links: [Introduction to Jupyter](https://colab.research.google.com/github/fastai/fastbook/blob/master/app_jupyter.ipynb) | [Chapter 1, Intro](https://colab.research.google.com/github/fastai/fastbook/blob/master/01_intro.ipynb) | [Chapter 2, Production](https://colab.research.google.com/github/fastai/fastbook/blob/master/02_production.ipynb) | [Chapter 3, Ethics](https://colab.research.google.com/github/fastai/fastbook/blob/master/03_ethics.ipynb) | [Chapter 4, MNIST Basics](https://colab.research.google.com/github/fastai/fastbook/blob/master/04_mnist_basics.ipynb) | [Chapter 5, Pet Breeds](https://colab.research.google.com/github/fastai/fastbook/blob/master/05_pet_breeds.ipynb) | [Chapter 6, Multi-Category](https://colab.research.google.com/github/fastai/fastbook/blob/master/06_multicat.ipynb) | [Chapter 7, Sizing and TTA](https://colab.research.google.com/github/fastai/fastbook/blob/master/07_sizing_and_tta.ipynb) | [Chapter 8, Collab](https://colab.research.google.com/github/fastai/fastbook/blob/master/08_collab.ipynb) | [Chapter 9, Tabular](https://colab.research.google.com/github/fastai/fastbook/blob/master/09_tabular.ipynb) | [Chapter 10, NLP](https://colab.research.google.com/github/fastai/fastbook/blob/master/10_nlp.ipynb) | [Chapter 11, Mid-Level API](https://colab.research.google.com/github/fastai/fastbook/blob/master/11_midlevel_data.ipynb) | [Chapter 12, NLP Deep-Dive](https://colab.research.google.com/github/fastai/fastbook/blob/master/12_nlp_dive.ipynb) | [Chapter 13, Convolutions](https://colab.research.google.com/github/fastai/fastbook/blob/master/13_convolutions.ipynb) | [Chapter 14, Resnet](https://colab.research.google.com/github/fastai/fastbook/blob/master/14_resnet.ipynb) | [Chapter 15, Arch Details](https://colab.research.google.com/github/fastai/fastbook/blob/master/15_arch_details.ipynb) | [Chapter 16, Optimizers and Callbacks](https://colab.research.google.com/github/fastai/fastbook/blob/master/16_accel_sgd.ipynb) | [Chapter 17, Foundations](https://colab.research.google.com/github/fastai/fastbook/blob/master/17_foundations.ipynb) | [Chapter 18, GradCAM](https://colab.research.google.com/github/fastai/fastbook/blob/master/18_CAM.ipynb) | [Chapter 19, Learner](https://colab.research.google.com/github/fastai/fastbook/blob/master/19_learner.ipynb) | [Chapter 20, conclusion](https://colab.research.google.com/github/fastai/fastbook/blob/master/20_conclusion.ipynb)


## Contributions

If you make any pull requests to this repo, then you are assigning copyright of that work to Jeremy Howard and Sylvain Gugger. (Additionally, if you are making small edits to spelling or text, please specify the name of the file and a very brief description of what you're fixing. It's difficult for reviewers to know which corrections have already been made. Thank you.)

## How to install the damned thing locally next to your GPU
Installing dependencies for this repository via `conda` has been hairy.
Hopefully, this will help me and whoever is reading this to set it up
without flaws. Keep in mind, that it's targeted for GPU set up. So
plan accordingly for your CPU set up. Furtheremore, it's done for
Linux OS by a Linux user. If you ain't using this platform, go
elsewhere for info ;). Steps:

1. Install necessary sub-dependencies outside conda like nvidia
   drivers and graphviz.
  - `graphviz` can be installed by running `apt install graphviz`.
  - Install normal nvidia drivers as if it was a gaming PC. It should
    be simple depending on your distro and their support for easy
    driver installation.
  - You need to install CUDA drivers. This step is target for
    Ubuntu-based distros, so you need to look for info else for any
    other distro:
    * For Pop os, read [this](https://support.system76.com/articles/cuda/).
    * For elementary OS (plus any distro _hopefully_), run `apt
      install nvidia-cuda-toolkit`. It seems to set up everything. To
      check, run `nvcc --version` and `nvidia-smi` and it should
      inform you everything you need to know.
2. Installing dependencies for the fastbook.
  - Unless you are using my patched `environment.yml`, you should edit
    it so `pip`'s argument of `requirements.txt` file doesn't have
    `file:` prefix. This is because `pip` has some updated URI
    protocol interface that doesn't like it.
  - Ok, you will need to execute the following lines when you are
    inside the repo's root directory:
```bash
conda env create --file environment.yml
conda install -n fastbook -c fastchan fastai
conda install -n fastbook jupyter
conda run -n fasbook pip install graphviz
```
Why executing this set of lines than running a one liner? Basically:
- Installing an older version of `fastai` whilst installing newest
  `pytorch` produces a runtime error that a particular function
  doesn't exist. Thus, forcing to install the latest `fastai` library.
- For some odd reason, after doing the above, it removes the
  `notebook` and `graphviz` libraries. Thus, installing the `jupyter`
  and then running graphviz via isolated `pip install` command. That
  should fix not finding the notebook as well as inability to generate
  graphs (which are useful for studying afterall).

## Citations

If you wish to cite the book, you may use the following:

```
@book{howard2020deep,
title={Deep Learning for Coders with Fastai and Pytorch: AI Applications Without a PhD},
author={Howard, J. and Gugger, S.},
isbn={9781492045526},
url={https://books.google.no/books?id=xd6LxgEACAAJ},
year={2020},
publisher={O'Reilly Media, Incorporated}
}
```

