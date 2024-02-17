https://www.geeksforgeeks.org/trie-insert-and-search/

```C++
#include<iostream>

using namespace std;

class TrieNode {
public:
	char data;
	TrieNode* children[26];
	bool isTerminal;

	TrieNode(const char data) {
		this->data = data;
		for (int i = 0; i < 26; i++)
			this->children[i] = NULL;
		isTerminal = false;
	}
};

class Trie {

private:
	TrieNode* root;

	void insertUtil(TrieNode* root, string word) {
		if (word.length() == 0) {
			root->isTerminal = true;
			return;
		}
		int index = word[0] - 'A';
		TrieNode* temp = NULL;
		if (root->children[index] != NULL) {
			temp = root->children[index];
		}
		else {
			temp = new TrieNode(word[0]);
			root->children[index] = temp;
		}
		insertUtil(temp, word.substr(1));
	}
	bool searchUtil(TrieNode* root, string word) {
		if (word.length() == 0) {
			return root->isTerminal;
		}
		int index = word[0] - 'A';
		TrieNode* temp = NULL;
		if (root->children[index] != NULL) {
			temp = root->children[index];
		}
		else {
			return false;
		}
		return searchUtil(temp, word.substr(1));

	}

	void removeUtil(TrieNode* root, string word) {
		if (word.length() == 0) {
			root->isTerminal = false;
			return;
		}
		int index = word[0] - 'A';
		TrieNode* temp = NULL;
		if (root->children[index] != NULL) {
			temp = root->children[index];
		}
		else {
			return;
		}
		removeUtil(temp, word.substr(1));
	}

public:
	Trie() {
		this->root = new TrieNode('\0');
	}

	void insertWord(string word) {
		insertUtil(this->root, word);
	}

	bool searchWord(string word) {
		return searchUtil(this->root, word);
	}

	void removeWord(string word) {
		return removeUtil(this->root, word);
	}

};
int main() {

	Trie* t = new Trie();
	t->insertWord("MAN");
	t->insertWord("ARM");
	t->insertWord("BOY");

	cout << "Present or not: " << t->searchWord("MAN") << endl;


	return 0;
}

```