# HW2
#include <iostream>
#include <cassert>
using namespace std;
template <class T>
struct node
{
    T info;
    node <T>* link;
    node(T elem,node <T>* ptr=NULL):
    info(elem),link(ptr){}
};
template <class T>
class stack
{
private:
    node <T>* Top;
    int Size;
public:
    stack(){Top=NULL;Size=0;} //default constructor
    ~stack();
    void push(T&);
    void pop();
    T& get_top();
    bool is_empty();
    void print();
};

template <class T>
void stack<T> ::push(T& elem)
{
    
    
    
    Top=new node<T> (elem,Top);
    Size++;
}

template <class T>
void stack<T> :: pop()
{
    assert(! is_empty() );
    node<T>* tmp=Top;
    Top=Top->link;
    delete tmp;
   
}

template <class T>
T& stack<T> :: get_top()
{
    assert(!is_empty() );
    return Top->info;
}

template <class T>
bool stack<T> :: is_empty()
{
    return (Top==NULL);
}
template <class T>
void stack<T> :: print()
{
    for(int i=0;i<=Size;i++)
    {
        cout<<get_top()<<" ";
        pop();
    };
};
const int maxsize=100;
template <class T>
stack<T>:: ~stack()
{
};




const int MaxSize =100;
class queue{
private:
    int front,rear,count;
    int qlist[MaxSize];
public:
    queue();
    ~queue();
    bool is_empty();
    int get_front();
    void enqueue(int &);
    void dequeue();
    void print_queue();
};

bool queue:: is_empty()
{
    if(count==0)
        return true;
    return false;
}

int queue:: get_front()
{
    return front;
}

queue::queue()
{
    front=0;
    rear=0;
    count=0;
}
queue::~queue()
{
    while(count)
    {
        dequeue();
        count--;
    }
    rear=0;
}

void queue::enqueue(int& item)
{
    if(count==maxsize)
        cout<<"Queue is full !!!"<<endl;
    count++;
    qlist[rear]=item;
    rear=(rear+1)%maxsize;
}

void queue::dequeue()
{
    if(count==0)
        return;
    count--;
    front=(front+1)%maxsize;
}

void queue :: print_queue()
{
    for(int i=0;i<count;i++)
        cout<<qlist[i]<<" ";
    cout<<endl;
}





int main()
{       queue A;
        stack <int> St;
        int k;
        for(int i=0;i<15;i++)
        {
            cin>>k;
            St.push(k);
            A.enqueue(k);
        };
    cout<<" The queue is"<<endl;
           A.print_queue();
    cout<<endl;
        cout<<"The stack is"<<endl;
        St.print();
    
         };
