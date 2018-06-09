### MNIST-modeling

#### Domain
This problem is drawn from the analysis of handwritten digits.


#### Problem Statement
Given an image of a handwritten digit, I will use supervised learning to develop a *[TODO: FILL IN]* model that can tell which digit the image is of. 

#### Dataset and Inputs
The training dataset contains 30,000 handwritten digits by 250 people. Those 250 people were either Census Bureau employees or high school students. *These images have been normalized so it is not necessary to clean the data. I don't know the vocab/terms to say this =/*

The data is stored in IDX file format, a very simple file format designed for storing vectors and multidimensional matrices.All the integers in the files are stored in the MSB first (high endian) format used by most non-Intel processors. Users of Intel processors and other low-endian machines must flip the bytes of the header.

The basic format is

magic number  
size in dimension 0  
size in dimension 1  
size in dimension 2  
.....  
size in dimension N  
data

The magic number is an integer (MSB first). The first 2 bytes are always 0.

The third byte codes the type of the data:  
0x08: unsigned byte  
0x09: signed byte  
0x0B: short (2 bytes)  
0x0C: int (4 bytes)  
0x0D: float (4 bytes)  
0x0E: double (8 bytes)  

The 4-th byte codes the number of dimensions of the vector/matrix: 1 for vectors, 2 for matrices....

The sizes in each dimension are 4-byte integers (MSB first, high endian, like in most non-Intel processors).

The data is stored like in a C array, i.e. the index in the last dimension changes the fastest. 

#### Solution Statement
*As of this moment, I am thinking that clustering the dataset into ten clusters, one for each digit 0-9, and then note the center of each cluster and which digit clustered around each center. Then, to determine the unknown digit in an image, my model would predict the digit is the one associated with the center closest to the unknown digit.
[The most visual model to solve a computer vision problem seems the most intuitive.]*

#### Benchmark Model
I would assume the digit is one because I think one is the most commonly written digit. It is the first digit, most do not use zero-indexing, so almost every list starts with one. We also tend to round numbers and we like to round to powers of ten, the base number in our number system.
This dataset may have just been gathered by asking people to write down digits and the digits follow a uniform distribution, but in context, I would assume one is more common.

#### Evaluation Metrics
Given that this is a classification task, I am measuring the success of my model using the F-score.
