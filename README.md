##Unsupervised Learning of Visual Representions by solving Jigsaw Puzzles.

This is the author implementaion of Unsupervised Learning of Visual Representaions by Solving Jigsaw Puzzles.

```bash
@inproceedings{norooziECCV16,
    Author = {Mehdi Noroozi and Paolo Favaro},
    Title = {Unsupervised Learning of Visual Representions by solving Jigsaw Puzzles},
    Booktitle = {ECCV},
    Year = {2016}
}
```

### Requirements
This software has all the same requirements as [Caffe](http://caffe.berkeleyvision.org/installation.html).

### Training Jigsaw Puzzle Solver

At first generate the imagenet dataset in a way described in paper.
Make the data generation
```bash
cd generate_jps_dataset
make
```
Execute data generation
```bash
generate_jps_dataset /path/to/original/imagenet/lmdb/dataset /output/peth/to/jps/datastet
```
The first argument is the path to ImageNet lmdb dataset includes shuffled images with original size. Caffe indludes scripts to generate this dataset.

Then you need to make the customized caffe version that generates puzzles on the fly.
```bash
cd caffe-maste-jps
make all matcaffe
```

To train jigsaw puzzle solver use solver_cfn_jps.prototxt. You need to set dataset produced above in train_val_cfn_jps.prototxt.

To train CFN for recognition use solver_cfn_rec.prototxt. You need to set ImageNet lmdb path which includes rezied 256x256 images in train_val_cfn_rec.prototxt.

You can use cfn_jps_test.m and cfn_rec_test.m to test the trained models in matlab. You can find trained models from project webpage.

To regenerate ImageNet classfication experiment results(Table 2). You need to train CFN for recognition initialized with jigsaw puzzle task weights and locked desired convolutinal layers. 




