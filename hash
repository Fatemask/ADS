#include <iostream>
#include<string>
using namespace std;

class node
{
    string key,val;
    bool lin,prob,placed,rep;
public:
    node(){
        key="";
        val="";
        lin=false;
        prob=false;
        placed=false;
        rep=false;
    }
    friend class hashs;
};

class hashs
{
    node arr[30];
public:
    hashs();
    int index_search(string);
    int Search_element(string);
    void insert();
    void insert_replacement();
    void Delete();
    void Delete_rep();
    void disp();
};

hashs::hashs()
{
    //***
}

int hashs::index_search(string key)
{
    int num=-1;
    if(key[0]>'a' && key[0]<'z')
    {
        num=int(key[0]);
        num=num%97;
        return num;
    }
    else if(key[0]>'A' && key[0]<'Z')
    {
        num=int(key[0]);
        num=num%65;
        return num;
    }
}

int hashs::Search_element(string token)
{
	int num=-1;
	int num2=-1;
	int count=0;
	num=index_search(token);

	for(int i=num;i<26;i++)
	{
		if(arr[i].placed != false)
		{
			if(arr[i].key==token){
				num2=i;
				//cout<<num<<endl;
				cout<<"Element found with iteration count of "<<count<<endl;
				return num2;
			}
			//count++;
		}
		count++;
	}
	return -1;
}

void hashs::insert()
{
    string first,second;
    cout<<"Enter the key "<<endl;
    cin>>first;
    cout<<"Enter the value"<<endl;
    cin>>second;
    int idx=index_search(first);
    cout<<"idx : "<<idx<<endl;
    if(arr[idx].placed==false)
    {
        arr[idx].key=first;
        arr[idx].val=second;
        arr[idx].lin=true;
        arr[idx].placed=true;
    }
    else{

        while((arr[idx].placed != false) && idx<26)
        {
            idx++;
        }
        arr[idx].key=first;
        arr[idx].val=second;
        arr[idx].prob=true;
        arr[idx].placed=true;
    }
}

void hashs::insert_replacement()
{
	string first,second;
	cout<<"Enter the key "<<endl;
	cin>>first;
	cout<<"Enter the value"<<endl;
	cin>>second;
	int idx2=-1;
	int idx=index_search(first);
	if(arr[idx].placed==false)
	{
		arr[idx].key=first;
		arr[idx].val=second;
		arr[idx].lin=true;
		arr[idx].placed=true;
	}
	else
	{
		idx2=index_search(arr[idx].key); //index of element in that place
		if(idx==idx2)
		{
			while((arr[idx].placed != false) && idx<26)
			{
				idx++;
			}
			arr[idx].key=first;
			arr[idx].val=second;
			arr[idx].prob=true;
			arr[idx].placed=true;
		}
		else
		{
			node n=arr[idx];
			arr[idx].key=first;
			arr[idx].val=second;
			arr[idx].prob=true;
			arr[idx].placed=true;
			idx++;
			while((arr[idx].placed != false) && idx<26)
			{
				idx++;
			}
			arr[idx].key=n.key;
			arr[idx].val=n.val;
			arr[idx].prob=true;
		    arr[idx].placed=true;
		    arr[idx].rep=true;
		}
	}
}

void hashs::Delete()
{
    string token;
    cout<<"Enter the key to delete."<<endl;
    cin>>token;
    int n=-1;
    n=Search_element(token);
    if(n==-1)
    {
        cout<<"Invalid Key!!"<<endl;
        return;
    }
    if(arr[n].placed != false && token==arr[n].key)
    {
        arr[n].key="";
        arr[n].val="";
        arr[n].lin=false;
        arr[n].prob=false;
        arr[n].placed=false;
        arr[n].rep=false;
    }
}

void hashs::Delete_rep()
{
    string token;
    cout<<"Enter the key to delete."<<endl;
    cin>>token;
    int n=-1;
    n=Search_element(token);
    if(n==-1)
    {
        cout<<"Invalid Key!!"<<endl;
        return;
    }
    if(arr[n].placed != false && token==arr[n].key)
    {
        arr[n].key="";
        arr[n].val="";
        arr[n].lin=false;
        arr[n].prob=false;
        arr[n].placed=false;
        arr[n].rep=false;
    }
    int n2=-1,cnt=0;
    for(int i=n+1;i<26;i++)
    {
        n2=index_search(arr[i].key);
        if(n2==n && cnt==0)
        {
            arr[n2].key=arr[i].key;
            arr[n2].val=arr[i].val;
            arr[n2].lin=arr[i].lin;
            arr[n2].prob=arr[i].prob;
            arr[n2].placed=arr[i].placed;
            arr[n2].rep=arr[i].rep;

            arr[i].key="";
            arr[i].val="";
            arr[i].lin=false;
            arr[i].prob=false;
            arr[i].placed=false;
            arr[i].rep=false;
            cnt++;
        }

    }

}

void hashs::disp()
{
    for(int i=0;i<26;i++)
    {
        if(arr[i].placed==true){
        cout<<i<<" :: ";
        cout<<arr[i].key<<" : "<<arr[i].val<<endl;
        cout<<"Linear : "<<arr[i].lin<<" ";
        cout<<"Probed : "<<arr[i].prob<<" ";
        cout<<"Replaced : "<<arr[i].rep<<endl;
        }
    }
    cout<<"\n";
}

int main()
{
    hashs h;
    int ch=0,idx=-1;
    string search;
    do{
        cout<<"MENU\n1.INSERT W/O REPLACEMENT\n2.INSERT W REPLACEMENT\n3.SEARCH ELEMENT\n4.DELETE\n5.DELETE W REPLACEMENT\n6.DISPLAY\n7.EXIT 0"<<endl;
        cin>>ch;
        switch(ch)
        {
        case 1:
            {
                h.insert();
                break;
            }
        case 2:
			{
				h.insert_replacement();
				break;
			}
        case 3:
			{
				cout<<"Enter the key to search"<<endl;
				cin>>search;
				idx=h.Search_element(search);
				if(idx==-1){
					cout<<"Element not found"<<endl;
				}
				else{
					cout<<"Element Found at location "<<idx<<endl;
				}
				break;
			}
        case 4:
            {
                h.Delete();
                h.disp();
                break;
            }
        case 5:
            {
                h.Delete_rep();
                h.disp();
                break;
            }
        case 6:
            {
                h.disp();
                break;
            }
        }
    }while(ch != 0);
    return 0;
}

