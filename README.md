# Proper ResNet Implementation for CIFAR10/CIFAR100 in pytorch
[Torchvision model zoo](https://github.com/pytorch/vision/tree/master/torchvision/models) provides number of implementations of various state-of-the-art architectures, however, most of them are defined and implemented for ImageNet.
Usually it is very straightforward to use them on other datasets, but sometimes this models needs manual setup.

Unfortunately, none of the pytorch repositories with ResNets on CIFAR10 provides an implementation as described in  [original paper](https://arxiv.org/abs/1512.03385). If you just use torchvision's models on CIFAR10 you'll get the model **that differs in number of layers and parameters**. That is unacceptable if you want to directly compare ResNets on CIFAR10.
The purpose of this repo is to provide a valid pytorch implementation of ResNet-s for CIFAR10. Following models are provided:

| Name      | # layers | # params| Test err(paper) | Test err(this impl.)|
|-----------|---------:|--------:|:-----------------:|:---------------------:|
|ResNet20   |    20    | 0.27M   | 8.75%| 8.27%|
|ResNet32   |    32    | 0.46M   | 7.51%| 7.37%|
|ResNet44   |    44    | 0.66M   | 7.17%| |
|ResNet56   |    56    | 0.85M   | 6.97%| 6.61%|
|ResNet110  |   110    |  1.7M   | 6.43%| |
|ResNet1202 |  1202    | 19.4M   | 7.93%| |

And their implementation matches description in original paper, with comparable or better test error.

## How to run?
```bash
git clone https://github.com/akamaster/pytorch_resnet_cifar10
cd pytorch_resnet_cifar10
chmod +x run.sh && ./run.sh
```

## Details of training
This implementation follows paper in straightforward manner with some caveats. **Firstly**, original paper uses 45k/5k train/validation split to train data, and selects best performing model based on performance on validation set. This implementation does not do any validation testing, so if you need to compare your results on ResNet head-to-head to orginal paper's keep this in mind. **Secondly**, if you want to train ResNet1202 keep in mind that you need 16GB memory on GPU.

## Pretrained models for download
1. [ResNet20, 8.27% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet20.th)
2. [ResNet32, 7.37% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet32.th)
3. ResNet44
4. [ResNet56, 6.61% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet20.th)
5. ResNet1202

If you find this implementation is useful and used it in your production/academic work please cite/mention this page and author Yerlan Idelbayev.