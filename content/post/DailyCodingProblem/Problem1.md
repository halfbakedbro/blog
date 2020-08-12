---
title: "Problem1"
date: 2020-08-12T15:38:16+05:30
tags: []
---

{{< blockquote >}}
Given a list of numbers and a number k, return whether any two numbers 
from the list add up to k. So
For example, given [10, 15, -4, 7] and k of 17, return true since 10 + 7 is 17.
{{< /blockquote >}}


{{< code numbered="true" >}}
#include <iostream>
#include <vector>
#include <unordered_set>

using namespace std;

bool checkSum(vector <int> arr, int k){

    int sum = 0;
    unordered_set<int> set;

    for (int i = 0 ; i < arr.size() ; i++){

        if (set.find(arr[i]) != set.end()){
            cout << arr[i] << endl;
            return true;
        }else {
            set.insert(k-arr[i]);
        }
    }

    return false;
}

int main() {

    vector<int> arr = {10,15,-4,7};

    cout << checkSum(arr, 6) << endl;

    return 0;
}
{{< /code >}}
