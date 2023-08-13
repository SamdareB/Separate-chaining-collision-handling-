#include <bits/stdc++.h>
using namespace std;

class hashing{
	int size;//size of hash bucket.
	list<int>*table;//Array List.
	public:
	hashing(int a);
	void insertItemIntoHash(int x);
	void deleteItemFromHash(int key);
	void displayHash();
	int hashFunction(int x){
		return x%size;
	}
};
hashing::hashing(int b){
	this->size = b;
	table = new list<int>[size];
}
void hashing::insertItemIntoHash(int x){
	int ind = hashFunction(x);
	table[ind].push_back(x);
}
void hashing::deleteItemFromHash(int key){
	int ind = hashFunction(key);
	list<int>::iterator i;
	for(i = table[ind].begin(); i!= table[ind].end(); i++){
		if(*i == key)
		  break;
	}
	  if(i!= table[ind].end())
	  table[ind].erase(i);
}
void hashing::displayHash(){
	for(int i =0;i<size;i++){
		cout<<i;
	for(auto x:table[i])
		cout<<"-->"<<x;
		cout<<endl;
	}
}
int main() {
	// your code goes here
	int arr[] ={4, 7, 6, 8, 11};
	int size = sizeof(arr)/sizeof(arr[0]);
	hashing h(6);
	for(int i =0;i<size;i++)
	h.insertItemIntoHash(arr[i]);
	h.deleteItemFromHash(12);
	h.displayHash();
	return 0;
}
