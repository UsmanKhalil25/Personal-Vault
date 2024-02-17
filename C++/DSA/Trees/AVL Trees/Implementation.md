```C++
#include<iostream>
#include<queue>

using namespace std;
struct Node{
    int data;
    int height;
    Node*left;
    Node*right;
    Node(const int data){
        this->data =data;
        this->left =NULL;
        this->right = NULL;
        this->height = 1;
    }
};

class AVL{
private:
    Node*root;


    Node* leftRotation(Node* root) {
        Node* rightNode = root->right;
        Node* rightNodeLeft = rightNode->left;

        rightNode->left = root;
        root->right = rightNodeLeft;

        root->height = max(height(root->left), height(root->right)) + 1;
        rightNode->height = max(height(rightNode->left), height(rightNode->right)) + 1;
        return rightNode;
    }

    int height(Node* root) {
        if (root == NULL)
            return 0;
        return root->height;
    }
    int getBalance(Node* root) {
        if (root == NULL)
            return 0;
        return height(root->left) - height(root->right);
    }

    Node* rightRotation(Node* root) {
        Node* leftNode = root->left;
        Node* leftNodeRight = leftNode->right;

        leftNode->right = root;
        root->left = leftNodeRight;

        root->height = max(height(root->left), height(root->right))+ 1;
        leftNode->height = max(height(leftNode->left), height(leftNode->right)) + 1;
        return leftNode;

    }

    Node*insertUtil(Node*root,const int data){
        if (root == NULL) {
            root = new Node(data);
            return root;
        }

        if (root->data < data) {
            root->right = insertUtil(root->right, data);
        }
        else if (root->data > data) {
            root->left = insertUtil(root->left, data);
        }
        else {
            return root;
        }

        root->height = 1 + max(height(root->left), height(root->right));

        int balance = getBalance(root);

        // Case 1: LL
        if (balance > 1 && data < root->left->data) {
            return rightRotation(root);
        }

        // Case 2: RR
        if (balance < -1 && data > root->right->data) {
            return leftRotation(root);
        }

        // Case 3: LR
        if (balance > 1 && data > root->left->data) {
            root->left = leftRotation(root->left);
            return rightRotation(root);
        }

        // Case 4: RL
        if (balance < -1 && data < root->right->data) {
            root->right = rightRotation(root->right);
            return leftRotation(root);
        }

        return root;
    }
    Node*findMin(Node*root){
        if(root == NULL)
            return NULL;
        Node*temp  =root;
        while(temp->left!=NULL){
            temp =temp->left;

        }
        return temp;
    }

    Node*deleteUtil(Node*node,int data){

        if(node == NULL)
            return NULL;
        if(node->data == data){
            //0 child
            if( node->left == NULL && node->right == NULL){
                delete node;
                return NULL;
            }
            // one child
            if(node->left !=NULL && node->right == NULL){
                Node*leftOfRoot = node->left;
                delete node;
                return leftOfRoot;
            }
            if(node->left == NULL && node->right!=NULL){
                Node*rightOfRoot = node->right;
                delete node;
                return rightOfRoot;
            }
            // two childs
            if(node->left!=NULL && node->right!=NULL){
                int min = findMin(node->right)->data;
                node->data = min;
                node->right = deleteUtil(node->right,min);
                return node;

            }
        }
        if(node->data > data){
            node->left = deleteUtil(node->left,data);
        }
        else {
            node->right = deleteUtil(root->right,data);
        }


        node->height = max(height(node->left),height(node->right))+1;

        int balance = getBalance(node);

        // RR
        if(balance > 1 && getBalance(node->left)>=0)
            return rightRotation(node);
        // LR
        if(balance >1 && getBalance(node->left)<0){
            node->left = leftRotation(node->left);
            return rightRotation(node);
        }
        // LL
        if(balance < -1 && getBalance(node->right)<=0)
            return leftRotation(node);
        //RL
        if(balance < -1 && getBalance(node->right)>0){
            node->right = rightRotation(node->right);
            return leftRotation(node->left);
        }
        return node;
    }
    void inorderUtil(Node*node){
        if(node == NULL)
            return;
        inorderUtil(node->left);
        cout<<node->data<<" ";
        inorderUtil(node->right);
    }

    void postorderUtil(Node*node){
        if(node == NULL)
            return;
        postorderUtil(node->left);
        postorderUtil(node->right);
        cout<<node->data<<" ";
    }
    void preorderUtil(Node*node){
        if(node == NULL)
            return;
        cout<<node->data<<" ";
        preorderUtil(node->left);
        preorderUtil(node->right);
    }

    bool searchUtil(Node*node,const int data){
        if(node == NULL)
            return false;
        if(node->data == data)
            return true;
        if(node->data> data)
            return searchUtil(node->left,data);
        else
            return searchUtil(node->right,data);
    }

    void printAllPathsUtil(Node* node, int* arr, int& index) {
		if(node == NULL)
            return;
        if(node->left == NULL && node->right == NULL){
            arr[++index] = node->data;
            for(int i = 0;i<=index;i++)
                cout<<arr[i]<<"->";
            cout<<endl;
            index--;
            return;
        }
        arr[++index] = node->data;
        printAllPathsUtil(node->left,arr,index);
        printAllPathsUtil(node->right,arr,index);
        index--;
	}

public:

    AVL(){
        this->root = NULL;
    }
    void insert(const int data){
        this->root = insertUtil(this->root,data);
    }
    void deleteNode(const int data){
        this->root = deleteUtil(this->root,data);
    }
    bool search(const int data){
        return searchUtil(this->root,data);
    }
    void inorder(){
        inorderUtil(this->root);
    }
    void preorder(){
        preorderUtil(this->root);
    }
    void postorder(){
        postorderUtil(this->root);
    }
    void printAllPaths() {
        int size = 100;
        auto* arr = new int[size];
        int index = -1;
        printAllPathsUtil(this->root, arr, index);
        delete []arr;
    }

    void levelOrderTraversal() {
        if (root == NULL)
            return;
        queue<Node*>q;
        q.push(root);
        q.push(NULL);
        while (!q.empty()) {
            Node* temp = q.front();
            q.pop();
            if (temp == NULL) {
                cout << endl;
                if (!q.empty()) {
                    q.push(NULL);
                }

            }
            else {
                cout << temp->data << " ";
                if (temp->left != NULL) {
                    q.push(temp->left);
                }
                if (temp->right != NULL) {
                    q.push(temp->right);
                }
            }
        }
    }

};

int main() {
    AVL avlTree;

    avlTree.insert(5);
    avlTree.insert(12);
    avlTree.insert(14);
    avlTree.insert(15);
    avlTree.insert(19);
    avlTree.insert(20);
    avlTree.insert(51);
    avlTree.insert(1);
    avlTree.insert(2);

    cout<<"Is 10 present: "<<avlTree.search(10)<<endl;
    cout<<"Is 51 present: "<<avlTree.search(51)<<endl;

    avlTree.deleteNode(1);
    avlTree.deleteNode(20);

    cout << "Inorder Traversal: ";
    avlTree.inorder();
    cout << endl;

    cout << "Preorder Traversal: ";
    avlTree.preorder();
    cout << endl;

    cout << "Postorder Traversal: ";
    avlTree.postorder();
    cout << endl;
    cout<<"Level order traversal: \n";
    avlTree.levelOrderTraversal();
    cout<<"All paths: \n";
    avlTree.printAllPaths();


    return 0;
}

```
s