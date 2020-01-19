#include <iostream>
using namespace std;
class node{
        int d;
        node* lc;
        node*rc;
        int lbit;
        int rbit;
        public:
        node(int x)
        {
       lc=NULL;
       rc=NULL;
       lbit=0;
       rbit=0;
       d=x;
        }
        friend class Tbt;
};

class Tbt{
        node* root;
        node* head;
public:
        Tbt()
        {
                root=NULL;
                head=NULL;
        };
        void Create(int);
        void preorder_trav(node*);
        void inorder_trav(node*);
        node* inorder_suc(node*);
        node* Return_head();
        node* preorder_suc(node*);
        void inorder_nonrec();
        void preorder_nonrec();
};

void Tbt::Create(int x)
{
        node* ptr=NULL;
        node* temp=NULL;

        if(root == NULL)
        {
                head=new node(-29);
                root=new node(x);
                root->lc=head;
                root->rc=head;
                head->lbit=1;
                head->lc=root;
        }
        else
        {
                ptr=root;
                while(1){

                    if(ptr->d > x)
                    {
                            if(ptr->lbit !=0)
                                ptr=ptr->lc;
                            else{
                            temp=new node(x);
                            temp->lc=ptr->lc;
                            temp->rc=ptr;
                            ptr->lbit=1;
                            ptr->lc=temp;
                            return;
                            }
                    }
                    else{
                           if(ptr->rbit !=0)
                                ptr=ptr->rc;
                            else{
                            temp=new node(x);
                            temp->lc=ptr;
                            temp->rc=ptr->rc;
                            ptr->rc=temp;
                            ptr->rbit=1;
                            return;
                            }
                    }
                }
        }
}

void Tbt::inorder_trav(node* n)
{
    node* t=head->lc;
        while(t->lbit==1)
    {
        t=t->lc;
    }
    while(t != head){
        cout<<t->d<<" ";
        t=inorder_suc(t);
    }
}

node* Tbt::inorder_suc(node* n)
{
    if(n->rbit==0)
        return n->rc;
    n=n->rc;
    while(n->lbit==1)
        n=n->lc;
    return n;
}

void Tbt::preorder_trav(node* n)
{
    n=head->lc;
    while( n != head){
        cout<<n->d<<" ";
        n=preorder_suc(n);
    }
}

node* Tbt::preorder_suc(node* n)
{
    if(n->lbit==1)
        return n->lc;
    while(n->rbit==0 && n->rc != head)
        n=n->rc;
    return n->rc;

}
node* Tbt::Return_head()
{
    return head;
}

void Tbt::inorder_nonrec()
{
        node* t=head->lc;
        while( t->lbit !=0)
                t=t->lc;
        while( t != head)
        {
                cout<<t->d<<" ";
                if(t->rbit==1)
                {
                        t=t->rc;
                        while(t->lbit != 0)
                                t=t->lc;
                }
                else
                        t=t->rc;
        }

}

void Tbt::preorder_nonrec()
{
        int flag =0;
        node* p=head->lc;
        while(p !=head)
        {
            if(flag ==0)
            {
                cout<<p->d<<" ";
            }
            if(p->lbit != 0 && flag==0){
                p=p->lc;
            }
            else
               {
                    if(p->rbit==0)
                    {
                        flag=1;
                        p=p->rc;
                    }
                    else{
                        flag=0;
                        p=p->rc;
                    }
               }
            }
 }




int main() {
        Tbt t;
        int ch=0;
        int x=0;
        do{
                cout<<"MENU\n1.CREATE\n2.INORDER REC\n3.PREORDER REC\n4.INORDER NON REC\n5.PREORDER NON REC\n6.0 EXIT\n";
                cin>>ch;
                switch(ch)
                {
                        case 1:
                        {
                                cout<<"Enter the element"<<endl;
                                cin>>x;
                                t.Create(x);
                                break;
                        }
                        case 2:
                        {
                            t.inorder_trav(t.Return_head());
                            cout<<endl;
                                break;
                        }
                        case 3:
                        {
                            t.preorder_trav(t.Return_head());
                            cout<<endl;
                                break;
                        }
                        case 4:
                        {
                                t.inorder_nonrec();
                                cout<<endl;
                                break;
                        }
                        case 5:
                        {
                                t.preorder_nonrec();
                                cout<<endl;
                                break;
                        }
                }
        }while(ch != 0);
        return 0;
}
