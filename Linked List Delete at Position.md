## 01. Linked List Delete at Position

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/delete-a-node-in-single-linked-list/1)

### Problem Description

**Task:** Given the head of a linked list and an integer x, delete the node at position x and return the updated head of the linked list.Note: Positions use 1-based indexing.Examples: Input: x = 4,Output: 1 - > 2 - > 3 - > 5Explanation: After deleting the node at the 4th position, the linked list is asInput: x = 6,Output: 2 - > 5 - > 7 - > 8 - > 99Explanation: After deleting the node at 6th position, the linked list is as

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (3)

#### Solution 1 (C++)

- **Submitted:** 2026-09-30 00:04:00
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Linked List Node
class Node {
public:
    int data;
    Node* next;
    Node(int data) {
        this->data = data;
        this->next = nullptr;
    }
};
*/
class Solution {
  public:
    Node* deleteNode(Node* head, int x) {
        // code here
        if(x==1){
            if(head!=NULL){
           Node* temp=head;
           head=head->next;
           delete temp;
           return head;}
           else{
               return NULL;
           }
        }
        if(head==NULL){
            return NULL;
        }
        if(head->next==NULL){
            delete head;
            return NULL;
        }
        Node* cur=head;
        int count=1;
        while(count!=x-1){
            cur=cur->next;
            count++;
        }
        Node* temp=cur->next;
        cur->next=temp->next;
        delete temp;
        return head;
    }
};
```

#### Solution 2 (C++)

- **Submitted:** 2026-09-29 23:54:54
- **Status:** Correct
- **Marks:** 0

```cpp
/* Structure of Linked List Node
class Node {
public:
    int data;
    Node* next;
    Node(int data) {
        this->data = data;
        this->next = nullptr;
    }
};
*/
class Solution {
  public:
    Node* deleteNode(Node* head, int x) {
        // code here
        if(x==1){
            if(head!=NULL){
           Node* temp=head;
           head=head->next;
           delete temp;
           return head;}
           else{
               return NULL;
           }
        }
        if(head==NULL){
            return NULL;
        }
        if(head->next==NULL){
            delete head;
            return NULL;
        }
        Node* cur=head;
        int count=1;
        while(count!=x-1){
            cur=cur->next;
            count++;
        }
        Node* temp=cur->next;
        cur->next=temp->next;
        delete temp;
        return head;
    }
};
```

#### Solution 3 (C++)

- **Submitted:** 2025-11-21 17:39:15
- **Status:** Correct
- **Marks:** 2

```cpp
/*
class Node {
public:
    int data;
    Node* next;

    Node(int data) {
        this->data = data;
        this->next = nullptr;
    }
};
*/
class Solution {
  public:
    Node* deleteNode(Node* head, int x) {
        // code here
        if(head->next==NULL){
            head=NULL;
            return head;
        }
        if(x==1){
            Node * temp=head;
            head=head->next;
            delete temp;
            return head;
        }
        int pos=1;
        Node * prev=NULL;
        Node * temp=head;
        while(pos<x){
            prev=temp;
            temp=temp->next;
            pos++;
        }
        prev->next=temp->next;
        delete temp;
        return head;
    }
};
```

*Generated on: 9/30/2026, 12:04:23 AM*