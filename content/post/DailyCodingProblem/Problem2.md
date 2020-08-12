---
title: "Problem2"
date: 2020-08-12T15:39:11+05:30
tags: []
---

{{< blockquote >}}
Given an array of integers, return a new array such that each element at
index i of the new array is the product of all the numbers in the original array except the one at i.
For example, if our input was [1, 2, 3, 4, 5],
the expected output would be [120, 60, 40, 30, 24]. If our input was [3, 2, 1], the expected output would be [2, 3, 6].
{{< /blockquote >}}

{{<code numbered="trur">}}
#include <iostream>
#include <vector>

using namespace std;

vector<int> newArrNoDiv(vector <int> arr){
    vector <int> prod (arr.size(), 1);

    long int temp = 1;

    for (int i = 0 ; i < arr.size() ; i++){
        prod[i]= temp;
        temp *= arr[i];
    }

    temp = 1;

    for (int i = arr.size()-1 ; i >= 0 ; i--){
        prod[i] *= temp;
        temp *= arr[i];
    }

    return prod;
}

vector <int> newArr(vector <int> arr){
    vector <int> temp ( arr.size() , 1);

    long int prod = 1;
    for (int i = 0 ; i < arr.size() ; i++) {
        prod *= arr[i];
    }

    for (int i = 0 ; i < arr.size() ; i++) {
        temp[i] = prod / arr[i];
    }

    return temp;
}

int main() {
    vector <int> arr = {3,2,1};

    vector<int> temp = newArrNoDiv(arr);

    for (auto a : temp){
        cout << a << " ";
    }
    cout << endl;
}
{{</code>}}