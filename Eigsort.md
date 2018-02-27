[home](/README.md)

### Here's our eigsort function 
When we call upon the eig function on a certain matrix, in our case the total energy matrix, in matlab, we produce two matrices: vecs and vals. 
Vecs is defined as a matrix which has the corresponding eigenvectors of the original matrix as the columns of vecs. 
Vals is defined as a diagonal matrix which has the corresponding eigenvalues on the diagonal. 
This eigsort function sorts the eigenvalues, the diagonals of vals, in ascending order and retains this order to sort the eigenvectors, or columns of vecs, such that each eigenvalue still matches up with its corresponding eigenvector. Ultimately, the eigenvectors and values are sorted into ascending order of eigenvalues. 

---- 

#### Actual matlab code: 

```Matlab

function [srtvecs, srtvals] = eigsort(vecs, vals)

%Sorts the vecs and vals 

%d is a vector composed of the diagonal entries of vals
d = diag(vals);

%the sort command creates a sorted vector containing the entries of vals in ascending order which are indexed by this ord value

[dsort, ord] = sort(d);

%we now sort the columns of the vecs matrix in the same order as the index from the sort(d) command

srtvecs = vecs(:, ord); 

%create a new matrix which puts the sorted entries of vecs on the diagonal of a new matrix, srtvals

srtvals = diag(dsort);

end
```
