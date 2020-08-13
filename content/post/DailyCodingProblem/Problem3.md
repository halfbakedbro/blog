---
title: "Problem3"
date: 2020-08-13T21:40:06+05:30
tags: []
---

{{<blockquote>}}
Given the root to a binary tree, implement serialize(root), 
which serializes the tree into a string, 
and deserialize(s), which deserializes the string back into the tree.
{{</blockquote>}}

{{<code numbered="true">}}
#include <iostream>
#include <vector>
#include <stack>
#include <sstream>
using namespace std;


typedef struct Node {
    int val;
    struct Node *left;
    struct Node *right;
    Node(){};

    Node(int val): val(val), left(NULL) , right(NULL){}
}node;


class SerialDes : public node
{
public:
    SerialDes() {};
    string serialize(node *root){

        ostringstream out;
        searilizer(root, out);
        return out.str();
    }

    node* deserialize(string data){
        istringstream in(data);
        return deserializer(in);
    }

private:
    void searilizer(node* root, ostringstream& out) {
        if (root) {
            out << root->val << ' ';
            searilizer(root->left, out);
            searilizer(root->right, out);
        } else {
            out << "# ";
        }
    }

    node* deserializer(istringstream& in) {
        string val;
        in >> val;
        if (val == "#")
            return nullptr;
        node* root = new node(stoi(val));
        root->left = deserializer(in);
        root->right = deserializer(in);
        return root;
    }
};

void Insert(node *& root, int val){

    if (root == NULL){
        root = new node(val);
    }else if (root->val > val){
        Insert(root->left , val);
    }else{
        Insert(root->right, val);
    }
}

void Inorder(node *root){
    if (root == NULL)
        return;
    
    Inorder(root->left);
    cout << root->val << " ";
    Inorder(root->right);
}


int main() {
    node *root = NULL;
    SerialDes s;

    Insert(root, 12);
    Insert(root, 4);
    Insert(root, 6);
    Insert(root, 1);
    Insert(root, 8);
    Insert(root, 3);
    Insert(root, 31);
    Insert(root, 13);

    Inorder(root);
    cout << endl;

    string str = s.serialize(root);

    for (auto a: str){
        cout << a;
    }
    cout << endl;
    node *temp = s.deserialize(str);
    Inorder(temp);
    cout << endl;
}
{{</code>}}