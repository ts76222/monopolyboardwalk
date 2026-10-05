#include <iostream>
#include <string>
using namespace std;

template <typename T>
struct node {
    T data;
    node<T>* next;
    node(T value) {
        data=value;
        next=nullptr;
    }
};

template <typename T>
class circularlinkedlist {
    private:
    node<T>* head;
    node<T>* current;
    
    public:
    T currentnode;
    
    circularlinkedlist() {
        head=nullptr;
        current=nullptr;
    }
    void append(T value) {
        node<T>* nextnode=new node<T>(value);
        
        if (head==nullptr) {
            head=nextnode;
            current=nextnode;
            
            nextnode->next=head;
            currentnode=nextnode->data;
            
            return;
        }
        
        node<T>* temp=head;
        
        while (temp->next != head) {
            temp=temp->next;
        }
        temp->next=nextnode;
        
        nextnode->next=head;
    }
    
    void step() {
        current = current->next;
        currentnode=current->data;
}};
    
int main() {

circularlinkedlist<string> monopolyboard;

monopolyboard.append("Go");
monopolyboard.append("Mediteranean Avenue");
monopolyboard.append("Community Chest");
monopolyboard.append("Baltic Avenue");
monopolyboard.append("Income Tax");
monopolyboard.append("Park Lane");
monopolyboard.append("Jail");
monopolyboard.append("Boardwalk");

cout << monopolyboard.currentnode << endl;

monopolyboard.step();

cout << monopolyboard.currentnode << endl;

monopolyboard.step();
monopolyboard.step();

cout << monopolyboard.currentnode << endl;

monopolyboard.step();

cout << monopolyboard.currentnode << endl;

monopolyboard.step();
monopolyboard.step();
monopolyboard.step();

cout << monopolyboard.currentnode << endl;

for(int i = 0; i < 23; i++) {
    monopolyboard.step();
}
 
cout << monopolyboard.currentnode << endl;

for(int i = 0; i < 12; i++) {
    monopolyboard.step();
}
 
cout << monopolyboard.currentnode << endl;

for(int i = 0; i < 0; i++) {
    monopolyboard.step();
}
 
cout << monopolyboard.currentnode << endl;


return 0;
}
