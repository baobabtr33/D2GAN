# Implementation of Dual-Discriminator GAN

This is the implementation of the D2GAN(Dual-Discriminator GAN) using pytorch, [paper](https://arxiv.org/abs/1709.03831)

![image](https://user-images.githubusercontent.com/25279765/35868536-1d145ac0-0ba0-11e8-8a88-87783989490a.png)

It uses two discriminator. One sees real data as real, however another one sees real data as fake.

According to the paper, loss function is different from ordinary GAN. Therefore, I made custom loss function. It might be unstable(e.g. explode when training, converges into inf/-inf)

Result is sames as below. I used two datasets, STL10 and CIFAR10

![fake_samples_epoch_61_600](https://user-images.githubusercontent.com/25279765/35868602-5302ee76-0ba0-11e8-9e64-4d46d34f1030.png)
> result from 64x64 STL10, generated by model

![fake_samples_epoch_46_200](https://user-images.githubusercontent.com/25279765/35868662-818caf02-0ba0-11e8-8f13-10acf05277e7.png)
> result from 64x64 CIFAR10, generated by model

In the paper, they used 32x32 size images, so I converted DCGAN's architecture, changing kernel size of Ds and G's first layers to 4.

its result is same as below.

![fake_samples_epoch_42_400](https://user-images.githubusercontent.com/25279765/35869139-bbc53904-0ba1-11e8-9c36-3fe783512ec1.png)
> result from 32x32 CIFAR10, generated by model

![image](https://user-images.githubusercontent.com/25279765/35869225-ecbb20d2-0ba1-11e8-9bfe-6cb263897e13.png)
> result from 32x32 CIFAR10, from the paper

![fake_samples_epoch_30_200](https://user-images.githubusercontent.com/25279765/35879666-216ffd94-0bbf-11e8-96c4-b7c06c2000ee.png)
> result from 32x32 STL10, generated by model

show much better result on 32x32 data. Also converges much faster than ordinary GAN

## Usage

On your console/terminal, type

````python
python main.py
````

## TODO
- revise custom loss(doesn't update its state for long iteration)
- clamp networks' gradient
- apply to more datasets
- argparser
