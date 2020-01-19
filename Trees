#include<iostream>

using namespace std;

class stack;
class queue;

class node
{
    int d;
    node* lc;
    node* rc;
    public:
    node(int x)
    {
        d=x;
        lc=NULL;
        rc=NULL;
    }
    friend class tree;
    friend class queue;
    friend class stack;
};

class queue
{
    int f,r;
    node *q[25];
    public:
    queue()
    {
        f=r=-1;
    }
    void push(node* n)
    {
        if(full())
        {
            cout<<"QUEUE FULL!!"<<endl;
        }
        else if(f==-1 || r==-1)
        {
            f++;
            r++;
            q[f]=n;
        }
        else
        {
            r++;
            q[r]=n;
        }
    }
    node* pop()
    {
        if(empty())
        {
            cout<<"EMEPTY QUEUE!!"<<endl;
        }
        else
        {
            node* n=q[f];
            f++;
            return n;
        }
    }

    int empty()
    {
        if(r==-1|| f>r )
        {
            return 1;
        }
        else
        {
            return 0;
        }

    }

    int full()
    {
        if(r==24)
        {
            return 1;
        }
        else
        {
            return 0;
        }

    }
};

class stack
{
    int top;
    node *s[25];
    public:
    stack()
    {
        top=-1;
        for(int i=0;i<24;i++)
        {
            s[i]=NULL;
        }
    }

    void push(node* t)
    {
        if(top==24)
        {
            cout<<"STACK FULL"<<endl;
        }
        else
        {
            top++;
            s[top]=t;
        }
    }

    node* pop()
    {
        if(top==-1)
        {
            cout<<"STACK EMPTY"<<endl;
        }
        else
        {
            node* n=s[top];
            top--;
            return n;
        }
    }

    int empty()
    {
        if(top==-1)
        {
            return 1;
        }
        else
        {
            return 0;
        }
    }

    int full()
    {
        if(top==24)
        {
            return 1;
        }
        else
        {
            return 0;
        }
    }

    void display()
    {
        while(!empty())
        {
        node* t=pop();
        cout<<t->d<<" ";
        }
    }
};
class tree
{
private:
    node* root;
public:
queue q;
    tree();
    void create();
    node* create_rec();
    void inorder_rec(node*);
    void preorder_rec(node*);
    void postorder_rec(node*);
    node* return_root();
    void create_non_rec();
    node* create_node_non_rec();
    void insert_val();
    void left_node(node*);
    void right_node(node*);
    void inorder_non_rec(stack );
    void preorder_non_rec(stack);
    void postorder_non_rec(stack,stack);
    void delete_tree(node*);
    void internal_nodes(node*);
    void leaf_nodes(node*);
    void height_tree(node*);
    node* copy_tree(node*);
   void operator =(tree &);
    void assign_root(node*);
    bool check_equal(node*,node*);
    node* mirror( node*);

};

    tree::tree()
    {
        root=NULL;
    }

    void tree::create()
    {
        root=create_rec();
    }

    node* tree::create_rec()
    {
        cout<<"enter the value for node"<<endl;
        int x=0;
        cin>>x;
        node* temp=new node(x);
        char ans;
        cout<<"Enter left node y?n for "<<temp->d<<endl;
        cin>>ans;
        if(ans=='y' || ans=='Y')
        {
            temp->lc=create_rec();
        }
        cout<<"Enter right node y?n for "<<temp->d<<endl;
        cin>>ans;
         if(ans=='y' || ans=='Y')
        {
            temp->rc=create_rec();
        }
        return temp;
    }

    void tree::inorder_rec(node* t)
    {
        if(t !=NULL)
        {
			inorder_rec(t->lc);
			cout<<t->d<<" ";
			inorder_rec(t->rc);
        }
    }

    void tree::preorder_rec(node* t)
    {
        if(t != NULL)
        {
            cout<<t->d<<" ";
            preorder_rec(t->lc);
            preorder_rec(t->rc);
        }
    }

    void tree:: postorder_rec(node* t)
    {
        if( t!=NULL)
        {
            postorder_rec(t->lc);
            postorder_rec(t->rc);
            cout<<t->d<<" ";
        }
    }

    node* tree::return_root()
    {
        return root;
    }

    void tree::create_non_rec()
    {
        root=create_node_non_rec();
        q.push(root);
    }

    node* tree::create_node_non_rec()
    {
        cout<<"Enter the value"<<endl;
        int x=0;
        cin>>x;
        node* temp=new node(x);
        return temp;
    }

    void tree::insert_val()
    {
        while( !q.empty() )
        {
            node* t;
            t=q.pop();
            char ans;
            cout<<"Left y?n for "<<t->d<<endl;
            cin>>ans;
            if(ans=='Y' || ans=='y')
            {
            left_node(t);
            }
            cout<<"Right y?n for "<<t->d<<endl;
            cin>>ans;
            if(ans=='Y' || ans=='y')
            {
            right_node(t);
            }
        }
    }

    void tree::left_node(node* t)
    {
        if(t->lc!=NULL)
        {
            cout<<"INVALID OPERATION"<<endl;
        }
        else
        {
            t->lc=create_node_non_rec();
            q.push(t->lc);
        }
    }

    void tree::right_node(node* t)
    {
        if(t->rc != NULL)
        {
            cout<<"INVALID OPERATION"<<endl;
        }
        else
        {
            t->rc=create_node_non_rec();
            q.push(t->rc);
        }
    }

    void tree::inorder_non_rec(stack s1)
    {
        node* t=root;
        while(1)
        {
            while( t!=NULL)
            {
                s1.push(t);
                t=t->lc;
            }
            if(s1.empty()){return; }
            t=s1.pop();
            cout<<t->d<<" ";
            t=t->rc;
        }
    }

    void tree::preorder_non_rec(stack s1)
    {
        node* t=root;
        while(1)
        {
            while( t!=NULL)
            {
                cout<<t->d<<" ";
                if(t->rc != NULL)
                {
                    s1.push(t->rc);
                }
                t=t->lc;
            }
            if(s1.empty()){return; }
            t=s1.pop();
        }
    }

    void tree::postorder_non_rec(stack s1,stack s2)
    {
        node* t=root;
        node* temp=NULL;
        s1.push(t);
        while( !s1.empty())
        {
            temp=s1.pop();
            s2.push(temp);
            if(temp->lc != NULL)
            {
                s1.push(temp->lc);
            }
            if(temp->rc != NULL)
            {
                s1.push(temp->rc);
            }
        }
            s2.display();
    }

    void tree::delete_tree(node* t)
    {
        if(t != NULL)
        {
            delete_tree(t->lc);
            delete_tree(t->rc);
            delete t;
        }
    }

    void tree::internal_nodes(node* t)
    {
            if((t->lc!=NULL) || (t->rc != NULL))
            {
                cout<<t->d<<" ";
            }
            if(t->lc != NULL)
            internal_nodes(t->lc);

            if(t->rc !=NULL)
            internal_nodes(t->rc);
    }

    void tree::leaf_nodes(node* t)
    {
        if(t==NULL)
        return;
        if(t->lc==NULL && t->rc==NULL)
        {
            cout<<t->d<<" ";
            return;
        }
        if(t->lc != NULL)
        {
            leaf_nodes(t->lc);
        }
        if(t->rc != NULL)
        {
            leaf_nodes(t->rc);
        }
    }

    node* tree::copy_tree(node* n)
    {
        node* temp=NULL;
        if( n != NULL)
        {
            temp=new node(0);
            temp->d=n->d;
            temp->lc=copy_tree(n->lc);
            temp->rc=copy_tree(n->rc);
        }
        return temp;
    }

   void tree::operator =(tree &t)
    {
    	node* n1=t.root;
    	root=copy_tree(n1);

    }

    void tree::assign_root(node* t)
    {
        root=t;
    }

   /* bool tree::check_equal(node* n1,node* n2)
    {
    	if( n1 !=NULL && n2 !=NULL)
    	{
    		if(n1->d==n2->d)
    		{
    			check_equal(n1->lc,n2->lc);
    			check_equal(n1->rc,n2->rc);
    			return true;
    		}
    		else
    		{
    			return false;
    		}
    	}
    	else
    	{
    		if((n1 !=NULL && n2 ==NULL) || (n1==NULL && n2!=NULL))
    			return false;
    	}
    	return true;
    }*/

    bool tree:: check_equal(node* n1,node* n2)
    {
    	if( n1 != NULL && n2!=NULL)
    	{
    		if(n1->d==n2->d)
    		{
    			return true;
    		}
    		else
    		{
    			return false;
    		}
    		check_equal(n1->lc,n2->lc);
    		check_equal(n1->rc,n2->rc);
    	}
    	else
    	{
    		if((n1 != NULL && n2==NULL) || (n1 == NULL && n2!=NULL))
    		{
    			return false;
    		}
    		else
    			return true;
    	}
    }

    node* tree::mirror (node* t)
    {
    	node* n=NULL;
		if( t!=NULL)
		{
			n=new node(0);
			n->d=t->d;
			n->lc=mirror(t->rc);
			n->rc=mirror(t->lc);
		}
		return n;
    }

    int main()
    {
        tree t;
        tree t3;
        tree t4;
        node* n2;
        bool check;
        stack s,s1,s2,s3;
        int a=0,b=0,c=0;
        do{
        	cout<<"MENU\n1.RECURSION\n2.NON RECURSION\n3.LEAF NODES\n4.INTERNAL NODES\n5.COPY\n6.EQUAL\n7.MIRROR\n8.DELETE\n9. 0 EXIT\n";
        	cin>>a;
        			switch(a)
        			{
						case 1:
						{
							cout<<"MENU\n1.CREATE\n2.INORDER\n3.PREORDER\n4.POSTORDER\n";
							cin>>b;
							switch(b)
							{
								case 1:
								{
									t.create();
									break;
								}
								case 2:
								{
									t.inorder_rec(t.return_root());
									cout<<'\n';
									break;
								}
								case 3:
								{
									t.preorder_rec(t.return_root());
									 cout<<'\n';
									 break;
								}
								case 4:
								{
									t.postorder_rec(t.return_root());
									cout<<'\n';
									break;
								}
							}
							break;
						}
						case 2:
						{
							cout<<"MENU NON REC.\n1.CREATE\n22.INORDER\n3.PREORDER\n4.POSTORDER\n";
							cin>>c;
							switch(c)
							{
								case 1 :
								{
									 t.create_non_rec();
									 t.insert_val();
									 break;
								}
								case 2 :
								{
									 t.inorder_non_rec(s);
									 cout<<endl;
									 break;
								}
								case 3 :
								{
									t.preorder_non_rec(s1);
									cout<<endl;
                                    break;
								}
								case 4 :
								{
									t.postorder_non_rec(s2,s3);
									cout<<endl;
									break;
								}
							}
							break;
						}
						case 3:
						{
							t.leaf_nodes(t.return_root());
						    cout<<endl;
							break;
						}
						case 4:
						{
							t.internal_nodes(t.return_root());
							cout<<endl;
							break;
						}
						case 5:
						{
							tree t2;
							t2=t;
							t2.inorder_rec(t2.return_root());
							cout<<endl;
							break;
						}
						case 6:
						{
							cout<<"ENETR THE TREE "<<endl;
							t3.create();
							check=t.check_equal(t.return_root(), t3.return_root());
							if(check==true)
							{
								cout<<"Equal tree"<<endl;
							}
							else
							{
								cout<<"Trees are not equal\n";
							}
							break;
						}
						case 7:
						{
							n2=t.mirror(t.return_root());
							t4.assign_root(n2);
							t4.inorder_rec(t4.return_root());
							break;
						}
						case 8:
						{
							t.delete_tree(t.return_root());
							cout<<"TREE IS DELETED"<<endl;
							break;
						}
        			}
        }while(a != 0);

        return 0;
    }







