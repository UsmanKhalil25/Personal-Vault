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


Node*solve(int in[],int pre[],int n ,int& index,int inorderStart,int inorderEnd ){
    if(index>= n || inorderStart > inorderEnd){
        return NULL;
    }
    Node*root =new Node(pre[index]);
    int position = findPosition(in,n,pre[index]);
    index++;
    root->left =solve(in,pre,n,index,inorderStart,position-1);
    root->right =solve(in,pre,n,index,position+1,inorderEnd);
    return root;
}
Node* buildTree(int in[],int pre[], int n){
    int preorderIndex = 0;
    Node*ans = solve(in,pre,n,preorderIndex,0,n-1);
    return ans;
}
int main(){

    return 0;

}

```

