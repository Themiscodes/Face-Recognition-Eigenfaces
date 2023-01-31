# Face Recognition using Eigenfaces

This repository contains an implementation of a face recognition system using Eigenfaces. This approach is computationally less expensive and easy to implement, than other methods due to the reduction of the dimensions of the data through Principal Component Analysis (PCA). 

The code along with a detailed analysis can be found in the [eigenfaces.ipynb](eigenfaces.ipynb) notebook.

## Classification 

The principal components are computed by eigen decomposition of the data covariance matrix thus transforming a large set of variables into a smaller one that still contains most of the information of the large set. For normalisation, the method of removing the "mean face" and dividing by the standard deviation was selected and for classification the k-nearest neighbor classifier.  
  
```
Accuracy and Confusion Matrices. Principal Components: 9
``` 
![eigenfaces_7_1](https://user-images.githubusercontent.com/73662635/215824803-1c8ddd21-72d8-4ac9-a948-33abac54b6fd.png)

```    
Accuracy and Confusion Matrices. Principal Components:  30
``` 
![eigenfaces_7_3](https://user-images.githubusercontent.com/73662635/215824864-9497ed2b-890b-4ef9-8894-8c1dbde33560.png)
    
An increase of the eigenspace to 30 principal components had a significant improvement on the accuracy. It made the method able to generalise better by scoring close to 100% on the first test sets. This was expected since the first principal component has the largest variance and each of the subsequent ones has the largest remaining, with the restriction that they're orthogonal to each other. This means that by adding components we can extract more features from the data.

## Face Reconstruction

Sirovich and Kirby showed that principal component analysis could be used on a collection of face images to form a set of basis features. These basis images, known as eigenfaces, could be linearly combined to reconstruct images in the original training set. Reconstruction of images from the test set can be seen below.
    
![eigenfaces_13_0](https://user-images.githubusercontent.com/73662635/215825003-263e7a49-a5b8-48bc-b5fa-f55d28de0a3e.png)
    
The reconstructions with 30 principal components might look slightly worse, but this is due to the fact that there is an increase in the features, thus they carry more information and appear more sharp. Still the reconstruction of most of them was pretty close in the photos with better lighting conditions.

### Singular Vectors Representation

After performing singular value decomposition a comparison was also made to the eigen vectors of the PCA method, by plotting both of them as images using the bone colour map.

```
Eigen Vectors
``` 
![eigenfaces_17_1](https://user-images.githubusercontent.com/73662635/215825101-791f2039-62f5-420c-a48e-e06d6de17252.png)
    
``` 
Singular Vectors
``` 

![eigenfaces_17_3](https://user-images.githubusercontent.com/73662635/215825214-a259a0e3-5668-46cf-a950-46458cad697a.png)

The SVD is applied to the matrix of the first dataset, while PCA on the covariance matrix. The small differences in them are because for the PCA method the initial images were normalised. This makes the eigen vectors lack that extra bit of information that is still present in the singular vectors.

### Acknowledgements

- [Eigenfaces for Recognition](https://dl.acm.org/doi/10.1162/jocn.1991.3.1.71) paper by Turk and Pentland.
- [Principal Component Analysis](https://zenodo.org/record/1430636#.Y9lDsi8RqLc) paper by Karl Pearson.
