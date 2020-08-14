---
title: "Problem4"
date: 2020-08-14T21:03:27+05:30
tags: []
---

{{<blockquote>}}
Given an array of integers, find the first missing positive integer in linear time and constant space. 
In other words, find the lowest positive integer that does not exist in the array.
The array can contain duplicates and negative numbers as well.
For example, the input [3, 4, -1, 1] should give 2. The input [1, 2, 0] should give 3.
You can modify the input array in-place.
{{</blockquote>}}

{{<code numbered="true">}}
#include <iostream>

using namespace std;

void swap(int *a, int *b){
    int temp = *a;
    *a = *b;
    *b = temp;
}
int findMisUtil(int arr[], int size);

int splitter(int arr[] , int size){

    int j = 0;
    for (int i = 0 ; i < size; i++){
        if (arr[i] <= 0){
            swap(&arr[i], &arr[j]);
            j++;
        }
    }

    return j;
}

int  findMissing(int arr[], int size){
    int sh = splitter(arr, size);

   return findMisUtil(arr+sh , size-sh);
}

int findMisUtil(int arr[], int size){

    for (int i = 0 ; i < size ; i++){

        if (abs(arr[i]) - 1 < size && arr[abs(arr[i]) - 1] > 0)
            arr[abs(arr[i])-1] = -arr[abs(arr[i])-1];
    }

    for (int i = 0 ; i < size ; i++)
        if (arr[i] > 0)
            return i+1;

    return size+1;
        
}


int main() {

    int arr[] = {3,4,-1,1};

    int arr2[] = {5,2,4,3};

    cout << findMissing(arr, 4) << " " << findMissing(arr2, 4) << endl;
}
{{</code>}}