# Proper ResNet Implementation for CIFAR10/CIFAR100 in pytorch
[Torchvision model zoo](https://github.com/pytorch/vision/tree/master/torchvision/models) provides number of implementations of various state-of-the-art architectures, however, most of them are defined and implemented for ImageNet.
Usually it is very straightforward to use them on other datasets, but sometimes these models need manual setup.

Unfortunately, none of the pytorch repositories with ResNets on CIFAR10 provides an implementation as described in the [original paper](https://arxiv.org/abs/1512.03385). If you just use the torchvision's models on CIFAR10 you'll get the model **that differs in number of layers and parameters**. This is unacceptable if you want to directly compare ResNet-s on CIFAR10 with the original paper.
The purpose of this repo is to provide a valid pytorch implementation of ResNet-s for CIFAR10 as described in the original paper. Following models are provided:

| Name      | # layers | # params| Test err(paper) | Test err(this impl.)|
|-----------|---------:|--------:|:-----------------:|:---------------------:|
|[ResNet20](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet20.th)   |    20    | 0.27M   | 8.75%| **8.27%**|
|[ResNet32](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet32.th)  |    32    | 0.46M   | 7.51%| **7.37%**|
|[ResNet44](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet44.th)   |    44    | 0.66M   | 7.17%| **6.90%**|
|[ResNet56](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet56.th)   |    56    | 0.85M   | 6.97%| **6.61%**|
|[ResNet110](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet110.th)  |   110    |  1.7M   | 6.43%| **6.32%**|
|[ResNet1202](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet1202.th) |  1202    | 19.4M   | 7.93%| **6.18%**|

The implementation matches description of the original paper, with comparable or better test error.

## How to run?
```bash
git clone https://github.com/akamaster/pytorch_resnet_cifar10
cd pytorch_resnet_cifar10
chmod +x run.sh && ./run.sh
```

## Details of training
This implementation follows the paper in straightforward manner with some caveats: **First**, training in the paper uses 45k/5k train/validation split on the train data, and selects the best performing model based on the performance on the validation set. This implementation does not do any validation testing, so if you need to compare your results on ResNet head-to-head to the orginal paper keep this in mind. **Second**, if you want to train ResNet1202 keep in mind that you need 16GB memory on GPU.

## Pretrained models for download
1. [ResNet20, 8.27% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet20.th)
2. [ResNet32, 7.37% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet32.th)
3. [ResNet44, 6.90% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet44.th)
4. [ResNet56, 6.61% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet56.th)
5. [ResNet110, 6.32% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet110.th)
6. [ResNet1202, 6.18% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet1202.th)

If you find this implementation useful and using it in your production/academic work please cite/mention this page and the author Yerlan Idelbayev.
