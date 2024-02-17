```C++
#include<iostream>

using namespace std;

class Node{
public:
    int data;
    Node*left;
    Node*right;
    Node(const int data){
        this->data =data;
        this->left = NULL;
        this->right =NULL;
    }
};

int findPosition(int arr[],int size,int element){
    for(int i = 0;i<size;i++){
        if(arr[i] == element)
            return i;
    }
    return -1;
}

Node*solve(int in[],int post[],int n,int&index,int inorderStart,int inorderEnd){
    if(index<0 || inorderStart> inorderEnd)
        return NULL;
    Node*root =new Node(post[index]);
    int position = findPosition(in,n,post[index]);
    index--;
    root->right = solve(in,post,n,index,position+1,inorderEnd);
    root->left =solve(in,post,n,index,inorderStart,position-1);
    return root;


}

Node *buildTree(int in[], int post[], int n) {
    int postorderIndex =n-1;
    Node*ans = solve(in,post,n,postorderIndex,0,n-1);
    return ans;
}

int main(){

    return 0;
}

```
