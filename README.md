# Pie-ESRGAN-PyTorch

## Overview

This repository contains an op-for-op PyTorch reimplementation of pieESRGAN(paper).
I referred to the site( https://github.com/Lornatang/ESRGAN-PyTorch (ESRGAN)) for this code.

### Table of contents

- [PieESRGAN-PyTorch](#pie-esrgan-pytorch)
    - [Overview](#overview)
        - [Table of contents](#table-of-contents)
        - [Download weights](#download-weights)
        - [Download dataset](#download-dataset)
            - [Download train dataset](#download-train-dataset)
            - [Download val dataset](#download-val-dataset)
        - [Test (e.g Set5)](#test-eg-set5)
        - [Train (e.g DIV2K)](#train-eg-div2k)
        - [Result](#result)
        - [Contributing](#contributing)
        - [Credit](#credit)
            - [ESRGAN: Enhanced Super-Resolution Generative Adversarial Networks](#esrgan-enhanced-super-resolution-generative-adversarial-networks)

### Download weights

- [Google Driver](https://drive.google.com/file/d/1lBT7msKjLkkAxYee80_mEby_e6pTeLMV/view?usp=sharing)


### Download dataset

#### Download train dataset

```bash
cd data/
bash download_dataset.sh
```

### Test (e.g Set14)

Modify the contents of the file as follows.

1. `config.py` line 38 `mode="train"` change to `model="valid"`;
2. `config.py` line 104 `model_path=f"results/{exp_name}/g-best.pth"` change to `model_path=f"<YOUR-WEIGHTS-PATH>.pth"`;
3. Run `python validate.py`.

### Train (e.g DIV2K)

Modify the contents of the file as follows.

1. `config.py` line 38 `mode="valid"` change to `model="train"`;
2. Run `python train.py`.

If you want to load weights that you've trained before, modify the contents of the file as follows.

1. `config.py` line 38 `mode="valid"` change to `model="train"`;
2. `config.py` line 56 `start_p_epoch=0` change to `start_p_epoch=XXX`;
3. `config.py` line 58 `resume=False` change to `resume=True`;
4. `config.py` line 59 `resume_p_weight=""` change to `resume_p_weight=<YOUR-RESUME-WIGHTS-PATH>`;
5. Run `python train.py`

### Result

Source of original paper results: [https://arxiv.org/pdf/1809.00219v2.pdf](https://arxiv.org/pdf/1809.00219v2.pdf)
our paper results: []()
In the following table, the value in `()` indicates the result of the project.
![image](https://user-images.githubusercontent.com/73474866/155973907-c7575c53-8506-4a03-b065-5d3d7faf5441.png)

Low resolution / Recovered High Resolution / Ground Truth
<span align="center"><img src="assets/result.png"/></span>

### Contributing

If you find a bug, create a GitHub issue, or even better, submit a pull request. Similarly, if you have questions,
simply post them as GitHub issues.please.

### Credit

#### ESRGAN: Enhanced Super-Resolution Generative Adversarial Networks

_Xintao Wang, Ke Yu, Shixiang Wu, Jinjin Gu, Yihao Liu, Chao Dong, Chen Change Loy, Yu Qiao, Xiaoou Tang_ <br>

**Abstract** <br>
The Super-Resolution Generative Adversarial Network (SRGAN) is a seminal work that is capable of generating realistic
textures during single image super-resolution. However, the hallucinated details are often accompanied with unpleasant
artifacts. To further enhance the visual quality, we thoroughly study three key components of SRGAN - network
architecture, adversarial loss and perceptual loss, and improve each of them to derive an Enhanced SRGAN (ESRGAN). In
particular, we introduce the Residual-in-Residual Dense Block (RRDB) without batch normalization as the basic network
building unit. Moreover, we borrow the idea from relativistic GAN to let the discriminator predict relative realness
instead of the absolute value. Finally, we improve the perceptual loss by using the features before activation, which
could provide stronger supervision for brightness consistency and texture recovery. Benefiting from these improvements,
the proposed ESRGAN achieves consistently better visual quality with more realistic and natural textures than SRGAN and
won the first place in the PIRM2018-SR Challenge. The code is available
at [this https URL](https://github.com/xinntao/ESRGAN).

[[Paper]](https://arxiv.org/pdf/1609.04802) [[Code]](https://github.com/xinntao/ESRGAN)

```bibtex
@misc{wang2018esrgan,
    title={ESRGAN: Enhanced Super-Resolution Generative Adversarial Networks},
    author={Xintao Wang and Ke Yu and Shixiang Wu and Jinjin Gu and Yihao Liu and Chao Dong and Chen Change Loy and Yu Qiao and Xiaoou Tang},
    year={2018},
    eprint={1809.00219},
    archivePrefix={arXiv},
    primaryClass={cs.CV}
}
```
