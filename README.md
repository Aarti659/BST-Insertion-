//C++ Program to implement BST-insertion 

#include <iostream.h>

#include <vector.h>

using std::cout; using std::vector;
using std::endl; using std::string;

struct TreeNode {
    int key;
    struct TreeNode *lef{};
    struct TreeNode *rig{};
};

void insertNode(TreeNode *&root, const int p) {
    if (root == nullptr) {
        root = new TreeNode;
        root->key = p;
        root->lef = nullptr;
        root->rig = nullptr;
    } else {
        if (p < root->key)
            insertNode(root->lef, p);
        else
            insertNode(root->rig, p);
    }
}

TreeNode *findNode(TreeNode *root, const int p) {
    if (root == nullptr)
        return nullptr;

    if (p == root->key)
        return root;

    if (p < root->key)
        return findNode(root->lef, p);
    else
        return findNode(root->rig, p);
}

void printTree(TreeNode *n) {
    if (n != nullptr) {
        printTree(n->lef);
        cout << n->key << "; ";
        printTree(n->rig);
    }
}

int main() {
    std::vector<int> v1 {11, 23, 3, 5, 9, 15, 2, 20};

    TreeNode *root = nullptr;

    for (const auto &item : v1) {
        insertNode(root, item);
    }
    printTree(root);
    cout << endl;

    std::vector<int> v2 {1, 22, 4, 16};
    for (const auto &item : v2) {
        insertNode(root, item);
    }
    printTree(root);
    cout << endl;

    return EXIT_SUCCESS;
}
