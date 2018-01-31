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
