# Proper ResNet Implementation for CIFAR10/CIFAR100 in pytorch
[Torchvision model zoo](https://github.com/pytorch/vision/tree/master/torchvision/models) provides number of implementations of various state-of-the-art architectures, however, most of them are defined and implemented for ImageNet.
Usually it is very straightforward to use them on other datasets, but sometimes this models needs manual setup.

Unfortunately, none of the pytorch repositories with ResNets on CIFAR10 provides an implementation as described in  [original paper](https://arxiv.org/abs/1512.03385). If you just use torchvision's models on CIFAR10 you'll get the model **that differs in number of layers and parameters**. That is unacceptable if you want to directly compare ResNets on CIFAR10.
The purpose of this repo is to provide a valid pytorch implementation of ResNet-s for CIFAR10. Following models are provided:

| Name      | # layers | # params|
|-----------|---------:|-------:|
|ResNet20   |    20    | 0.27M  |
|ResNet32   |    32    | 0.46M  |
|ResNet44   |    44    | 0.66M  |
|ResNet56   |    56    | 0.85M  |
|ResNet110  |   110    |  1.7M  |
|ResNet1202 |  1202    | 19.4M  |

And their implementation matches description in original paper.

If you find this implementation is useful and used it in your production/academic work please cite/mention this page and author Yerlan Idelbayev.