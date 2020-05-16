# Proper ResNet Implementation for CIFAR10/CIFAR100 in Pytorch
[Torchvision model zoo](https://github.com/pytorch/vision/tree/master/torchvision/models) provides number of implementations of various state-of-the-art architectures, however, most of them are defined and implemented for ImageNet.
Usually it is straightforward to use the provided models on other datasets, but some cases require manual setup.

For instance, very few pytorch repositories with ResNets on CIFAR10 provides the implementation as described in the [original paper](https://arxiv.org/abs/1512.03385). If you just use the torchvision's models on CIFAR10 you'll get the model **that differs in number of layers and parameters**. This is unacceptable if you want to directly compare ResNet-s on CIFAR10 with the original paper.
The purpose of this repo is to provide a valid pytorch implementation of ResNet-s for CIFAR10 as described in the original paper. The following models are provided:

| Name      | # layers | # params| Test err(paper) | Test err(this impl.)|
|-----------|---------:|--------:|:-----------------:|:---------------------:|
|[ResNet20](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet20-12fca82f.th)   |    20    | 0.27M   | 8.75%| **8.27%**|
|[ResNet32](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet32-d509ac18.th)  |    32    | 0.46M   | 7.51%| **7.37%**|
|[ResNet44](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet44-014dd654.th)   |    44    | 0.66M   | 7.17%| **6.90%**|
|[ResNet56](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet56-4bfd9763.th)   |    56    | 0.85M   | 6.97%| **6.61%**|
|[ResNet110](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet110-1d1ed7c2.th)  |   110    |  1.7M   | 6.43%| **6.32%**|
|[ResNet1202](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet1202-f3b1deed.th) |  1202    | 19.4M   | 7.93%| **6.18%**|

This implementation matches description of the original paper, with comparable or better test error.

## How to run?
```bash
git clone https://github.com/akamaster/pytorch_resnet_cifar10
cd pytorch_resnet_cifar10
chmod +x run.sh && ./run.sh
```

## Details of training
Our implementation follows the paper in straightforward manner with some caveats: **First**, the training in the paper uses 45k/5k train/validation split on the train data, and selects the best performing model based on the performance on the validation set. We *do not perform* validation testing; if you need to compare your results on ResNet head-to-head to the orginal paper keep this in mind. **Second**, if you want to train ResNet1202 keep in mind that you need 16GB memory on GPU.

## Pretrained models for download
1. [ResNet20, 8.27% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet20.th)
2. [ResNet32, 7.37% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet32.th)
3. [ResNet44, 6.90% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet44.th)
4. [ResNet56, 6.61% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet56.th)
5. [ResNet110, 6.32% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet110.th)
6. [ResNet1202, 6.18% err](https://github.com/akamaster/pytorch_resnet_cifar10/raw/master/pretrained_models/resnet1202.th)

If you find this implementation useful and want to cite/mention this page, here is a bibtex citation:

```bibtex
@misc{Idelbayev18a,
  author       = "Yerlan Idelbayev",
  title        = "Proper {ResNet} Implementation for {CIFAR10/CIFAR100} in {PyTorch}",
  howpublished = "\url{https://github.com/akamaster/pytorch_resnet_cifar10}",
  note         = "Accessed: 20xx-xx-xx"
}

```