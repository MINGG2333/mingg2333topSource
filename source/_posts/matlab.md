---
title: matlab
date: 2021-06-10 13:00:21
tags:
---





# about mat

```matlab
% create
A = magic(4)
1:5
% [1,2,3,4,5]
% transpose
B = A.'
A = transpose(B)
% stack by horizon, have the same rows
# A * [B C] = [A*B A*C]
c = [a b]
c = [a, b]
% stack by verticalness, have the same columns
c = [a; b]
```



# about struct

```matlab
A.b
```



# save

```matlab
save('data2.mat', 'descr');
save('data2.mat', 'label','-append');
```



# read minist dataset

refer to [【机器学习】MATLAB读取mnist数据库_心所愿，力必坚！-程序员宅基地 - 程序员宅基地 (cxyzjd.com)](http://www.cxyzjd.com/article/tracer9/51253604):

```matlab
% loadMNISTImages.m
function images = loadMNISTImages(filename)
%loadMNISTImages returns a 28x28x[number of MNIST images] matrix containing
%the raw MNIST images

fp = fopen(filename, 'rb');
assert(fp ~= -1, ['Could not open ', filename, '']);

magic = fread(fp, 1, 'int32', 0, 'ieee-be');
assert(magic == 2051, ['Bad magic number in ', filename, '']);

numImages = fread(fp, 1, 'int32', 0, 'ieee-be');
numRows = fread(fp, 1, 'int32', 0, 'ieee-be');
numCols = fread(fp, 1, 'int32', 0, 'ieee-be');

images = fread(fp, inf, 'unsigned char');
images = reshape(images, numCols, numRows, numImages);
images = permute(images,[2 1 3]);

fclose(fp);

% Reshape to #pixels x #examples
images = reshape(images, size(images, 1) * size(images, 2), size(images, 3));
% Convert to double and rescale to [0,1]
images = double(images) / 255;

end


% loadMNISTLabels.m
function labels = loadMNISTLabels(filename)
%loadMNISTLabels returns a [number of MNIST images]x1 matrix containing
%the labels for the MNIST images

fp = fopen(filename, 'rb');
assert(fp ~= -1, ['Could not open ', filename, '']);

magic = fread(fp, 1, 'int32', 0, 'ieee-be');
assert(magic == 2049, ['Bad magic number in ', filename, '']);

numLabels = fread(fp, 1, 'int32', 0, 'ieee-be');

labels = fread(fp, inf, 'unsigned char');

assert(size(labels,1) == numLabels, 'Mismatch in label count');

fclose(fp);

end
```

