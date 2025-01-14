# Adversarial Robustness

This repository contains the code needed to evaluate models trained in
[Doing More with Less: Improving Robustness using Generated Data](https://storage.googleapis.com/dm-adversarial-robustness/gowal2021doing.pdf)
which has been accepted at
[ICLR 2021 Security and Safety in Machine Learning Systems Workshop](https://aisecure-workshop.github.io/aml-iclr2021/).


## Contents

We have released our top-performing models in two formats compatible with
[JAX](https://github.com/google/jax) and [PyTorch](https://pytorch.org/).
This repository also contains our model definitions.

## Running the example code

### Downloading a model

Download a model from links listed in the following table.
Clean and robust accuracies are measured on the full test set.
The robust accuracy is measured using
[AutoAttack](https://github.com/fra31/auto-attack).

| dataset | norm | radius | architecture | extra data | clean | robust | link |
|---|:---:|:---:|:---:|:---:|---:|---:|:---:|
| CIFAR-10 | &#8467;<sub>&infin;</sub> | 8 / 255 | WRN-70-16 | &#x2717; | 86.94% | 63.62% | [jax](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_linf_wrn70-16_ddpm_v2.npy), [pt](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_linf_wrn70-16_ddpm_v2.pt)
| CIFAR-10 | &#8467;<sub>&infin;</sub> | 8 / 255 | WRN-28-10 | &#x2717; | 85.97% | 60.73% | [jax](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_linf_wrn28-10_ddpm_v2.npy), [pt](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_linf_wrn28-10_ddpm_v2.pt)
| CIFAR-10 | &#8467;<sub>2</sub> | 8 / 255 | WRN-70-16 | &#x2717; | 90.83% | 78.39% | [jax](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_linf_wrn70-16_ddpm_v2.npy), [pt](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_l2_wrn70-16_ddpm_v2.pt)
| CIFAR-10 | &#8467;<sub>2</sub> | 8 / 255 | WRN-28-10 | &#x2717; | 90.24% | 77.44% | [jax](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_linf_wrn28-10_ddpm_v2.npy), [pt](https://storage.googleapis.com/dm-adversarial-robustness/cifar10_l2_wrn28-10_ddpm_v2.pt)
| CIFAR-100 | &#8467;<sub>&infin;</sub> | 8 / 255 | WRN-70-16 | &#x2717; | 60.46% | 33.49% | [jax](https://storage.googleapis.com/dm-adversarial-robustness/cifar100_linf_wrn70-16_ddpm.npy), [pt](https://storage.googleapis.com/dm-adversarial-robustness/cifar100_linf_wrn70-16_ddpm.pt)
| CIFAR-100 | &#8467;<sub>&infin;</sub> | 8 / 255 | WRN-28-10 | &#x2717; | 59.18% | 30.81% | [jax](https://storage.googleapis.com/dm-adversarial-robustness/cifar100_linf_wrn28-10_ddpm.npy), [pt](https://storage.googleapis.com/dm-adversarial-robustness/cifar100_linf_wrn28-10_ddpm.pt)

### Using the model

Once downloaded, a model can be evaluated (clean accuracy) by running the
`eval.py` script in either the `jax` or `pytorch` folders. E.g.:

```
cd jax
python3 eval.py \
  --ckpt=${PATH_TO_CHECKPOINT} --depth=70 --width=16 --dataset=cifar10
```


## Citing this work

If you use this code or these models in your work, please cite the complete
version which combines data augmentation with generated samples:

```
@article{rebuffi2021fixing,
  title={Fixing Data Augmentation to Improve Adversarial Robustness},
  author={Rebuffi, Sylvestre-Alvise and Gowal, Sven and Calian, Dan A. and Stimberg, Florian and Wiles, Olivia and Mann, Timothy},
  journal={arXiv preprint arXiv:2103.01946},
  year={2021},
  url={https://arxiv.org/pdf/2103.01946}
}
```

## Disclaimer

This is not an official Google product.
