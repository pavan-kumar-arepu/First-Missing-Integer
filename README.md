# First-Missing-Integer

Problem Description
Given an unsorted integer array, A of size N. Find the first missing positive integer.

Note: Your algorithm should run in O(n) time and use constant space.


*Problem Constraints*
1 <= N <= 1000000
-10^9 <= A[i] <= 10^9

*Input Format*
First argument is an integer array A.

*Output Format*
Return an integer denoting the first missing positive integer.


// Passing ref of 'A' and index of swaping number 
void swap(vector<int> &A, int i, int j) {
    int temp;
    temp = A[i];
    A[i] = A[j];
    A[j] = temp;
}

int Solution::firstMissingPositive(vector<int> &A) {
    int size = A.size();
    for(int i=0;i<size;i++) {
        int num = A[i];
        // Obviously +Ve number should be in between [0,N] and 
        // we no need to concentrate other numbers like -ve numbers or bigger numbers 
        if (num>=0 && num<=size) {
            // Swaping is only required if num =! its position i.e 'i'
            // and also swaping is not allowed if swaping numbers are same
            // otherwise, it will go to INFINITE loop.
            if ((num != i) && (num != A[num])) {
                swap(A, i, A[i]);
                i--;
                continue;
            }
        }
    }

    for(int i=1;i<size;i++) {
        if(A[i] != i) {
            return i;
        }
    }
}
