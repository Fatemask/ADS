#include <iostream>
#include<string.h>
using namespace std;
class Entry
{
	char word[20];
	char mean[20];
	Entry *lc;
	Entry *rc;
public:
	Entry(char* word,char* mean)
	{
			strcpy(this->word,word);
			strcpy(this->mean,mean);
			lc=NULL;
			rc=NULL;
	}
	Entry()
	{
		lc=NULL;
		rc=NULL;
	}
	friend class Dictionary;
};

class Dictionary
{
	Entry* root;
public:
	Dictionary()
    {
		root=NULL;
    }
	void Create();
	void Ascending_print(Entry *);
	void Descending_print(Entry *);
	Entry* Return_Entry();
	void Search(Entry *,char*);
	void Modify(Entry *,char*);
	void del();
	Entry* remove(Entry*,string);
};

Entry* Dictionary::Return_Entry()
{
	return root;
}

void Dictionary::Create()
{
	Entry* par=NULL;
	Entry* cur=NULL;
	int c=-1;
	Entry* n=new Entry();
	cout<<"ENTER THE KEYWORD"<<endl;
	cin>>n->word;
	cout<<"ENTER THE MEANING"<<endl;
	cin>>n->mean;
   if(root == NULL)
   {
	   root=n;
	   return;
   }
   else
   {
      cur=root;
      while(1)
      {
    	  par=cur;
    	  c=strcmp(cur->word,n->word);
    	  if(c>0)
    	  {
    		  cur=cur->lc;
    		  if(cur==NULL)
    		  {
    			  par->lc=n;
    			  return;
    		  }
    	  }
    	  if(c<0)
    	  {
    		  cur=cur->rc;
    		  if(cur==NULL)
    		  {
    			  par->rc=n;
    			  return;
    		  }
    	  }
    	  if(c==0)
    	  {
    		  cout<<"SAME KEYWORD ENCOUNTERED!!!"<<endl;
              return;
    	  }
      }
   }
}

void Dictionary::Ascending_print(Entry * e)
{
	if(e != NULL)
	{
		Ascending_print(e->lc);
		cout<<e->word<<" : "<<e->mean<<endl;
		Ascending_print(e->rc);
	}
}

void Dictionary ::Descending_print(Entry* e)
{
	if(e != NULL)
	{
		Descending_print(e->rc);
		cout<<e->word<<" : "<<e->mean<<endl;
		Descending_print(e->lc);
	}
}

void Dictionary::Search(Entry* e,char* sword)
{
    int c=0;
    if(e !=NULL)
    {
        c=strcmp(e->word,sword);
        if(c>0)
        {
            Search(e->lc,sword);
        }
        if(c<0)
        {
            Search(e->rc,sword);
        }
        if(c==0)
        {
            cout<<"KEYWORD FOUND"<<endl;
            cout<<e->word<<" : "<<e->mean<<endl;
        }
    }
    else{
        cout<<"INVALID INPUT"<<endl;
    }
}

void Dictionary::Modify(Entry* e,char* mword)
{
    int c=0;
    if(e!=NULL)
    {
        c=strcmp(e->word,mword);
         if(c>0)
        {
            Modify(e->lc,mword);
        }
        if(c<0)
        {
            Modify(e->rc,mword);
        }
        if(c==0)
        {
            cout<<"KEYWORD FOUND"<<endl;
            cout<<"Enter the  new meaning"<<endl;
            cin>>e->mean;
        }
    }
    else
    {
        cout<<"Invalid input"<<endl;
    }
}

void Dictionary::del(){
	string st;
	cout<<"Enter the keyword you want to delete\t"<<endl;
	cin>>st;
	root=remove(root,st);
	Entry* e=root;
	if(e != NULL)
	{
		Descending_print(e->rc);
		cout<<e->word<<" : "<<e->mean<<endl;
		Descending_print(e->lc);
	}
	cout<<endl;
}

Entry* Dictionary::remove(Entry* r, string s){
	if(r==NULL)
		return r;
	else if(r->word>s){
		r->lc=remove(r->lc,s);
		return r;
	}
	else if(r->word<s){
		r->rc=remove(r->rc,s);
		return r;
	}
	else{
		Entry* temp;
		if(r->lc==NULL){
			temp=r;
			r=r->rc;
			delete temp;
			return r;
		}
		else if(r->rc==NULL){
			temp=r;
			r=r->lc;
			delete temp;
			return r;
		}
		else{
			temp=root->lc;
			while(temp->rc!=NULL){
            temp=temp->rc;}
			strcpy(r->word,temp->word);
			strcpy(r->mean,temp->mean);
			r->lc=remove(r->lc,temp->word);
	}
	return NULL;
}
}


int main() {
    Dictionary d;
    char sword[20];
    char mword[20];
    char dword[20];
    int k;
    
  //creation of tree..dictionary.
  cout<<"Enter the no of elements to be added."<<endl;
  cin>>k;
	for (int i=0;i<k;i++)
	{
	 d.Create();
	}
  
  //printing of tree.
	d.Ascending_print(d.Return_Entry());
	cout<<endl;
	d.Descending_print(d.Return_Entry());

//search of key word.
    cout<<"Enter the keyword to be searched"<<endl;
    cin>>sword;
	d.Search(d.Return_Entry(),sword);

//modification of keyword.
	cout<<"Enter the word to be modified"<<endl;
   cin>>mword;
	d.Modify(d.Return_Entry(),mword);
	d.Ascending_print(d.Return_Entry());
	cout<<endl;
  
//deletion of keyword.
	d.del();
	d.Ascending_print(d.Return_Entry());
	return 0;
}
