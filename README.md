# ll-deletion
using recursion
#include<iostream>
using namespace std;

class Node
{
    public:
    int data;
    Node* next;
    Node(int data)
    {
        this->data=data;
        next=NULL;
    }
};

Node* Take_Input()
{
    int data;
    cin>>data;

    Node* head=NULL;
    Node* tail=NULL;
    while(data!=-1)
    {
        Node* newNode=new Node(data);
        if(head==NULL)
        {
            head=newNode;
            tail=newNode;
        }
        else
        {
            tail->next=newNode;
            tail=tail->next;
        }
        cin>>data;
    }
    return head;
}
void print(Node* head)
{
    Node* temp=head;
    while(temp!=NULL)
    {
        cout<<temp->data<<" ";
        temp=temp->next;
    }
}

Node* Delete(Node* head,int i)
{
    if(head==NULL)
    {
        return NULL;
    }
    if(i<1)
    {
        return head;
    }
    if(i==1)
    {
        head=head->next;
        return head;
    }
    head->next=Delete(head->next,i-1);
    return head;
}

int main()
{
    Node* head=Take_Input();
    head=Delete(head,4);
    print(head);
}
