# ht-05-2023

#include <iostream>    
#include <fstream>
#include <bitset>
using namespace std;

class B
{
public:
    char* path = new char;
	ofstream of;
	string ch;
	
	//constructor---
	B() {};
	~B() {};
	//destructor---
	
	//file opening:
	void Completing() 
	{
		cout << "\tEnter file path - " << endl;
		cin >> path;
		of.open(path, ofstream::app);
		
		//file check
		if (of.is_open())
		{
			cout << "File opened successfully!" << endl;
			cout << "\nFile interaction options: " << endl;
			cout << "\t1 - Add to file" << endl;
			cout << "\t2 - Other" << endl;
			int c;
			do 
			{
				cout << "\nYour choice - ";
				cin >> c;
				switch (c) 
				{
    				case 1: (c == 1); 
    				{
    					string s;
    					cout << "Enter information -  ";
    					cin >> s;
    					of << s;
    					break;
    				}
    				case 2: (c == 2); 
    				{
    				    break; 
    				};
    				default: 
    				{
    				    cout << "Error!";
    				    break;
    				}
				}
				
			} 
			while (c != 2);
		}
		else
		{
		    cout << "\nSorry, I can't find this file." << endl;
		}
	}

	virtual void Display() 
	{
		ifstream ifs;
		ifs.open(path);
		
		if (ifs.is_open())
		{
		    while (!ifs.eof())
			{
				ifs >> ch;
				cout << ch << " ";
			}
		}
		else
		{
			cout << "\nSorry, I can't find this file." << endl;
		}
		
		ifs.close();
	}
	
};

class Child1:public B
{
public:
	ifstream ifs;
	string str;
	
	//constructor---
	Child1() {};
	~Child1() {};
	//destructor---
	
	void Display() 
	{
		str = B::ch;
		cout << str;
		cout << endl;

		/*for (size_t i = 0; i < str.size(); i++)
		{
			if (str[i] >= 48 && str[i] <= 57)
				cout << str[i];
			else
				cout << '<' << (int)(str[i] & 255) << '>';*/
				
			ifs.open(path);
			
			if (ifs.is_open())
			{
				while (!ifs.eof())
				{
					cout << endl << endl;
					ifs >> str;
					cout << str << " ";
				}
			}
			else
			{
				cout << "\nSorry, I can't find this file." << endl;
			}
	}
    //ifs.close();
};

class Child2 : public Child1
{
public:
    
    //constructor---
	Child2() {};
	~Child2() {};
	//destructor---
	
	void Display()
	{
		for (int i = 0; i < B::ch.size(); i++)
		{
			cout << bitset<5>(B::ch[i]) << ' ';
		}
		cout << endl << B::ch << endl;
	}
};

int main()
{
	B base;
	Child1 ch1;
	Child2 ch2;

	B* b1 = &base;
	Child1* c1 = &ch1;
	Child2* c2 = &ch2;

	base.Completing();
	b1->Display();
	c1->Display();
	b1->Display();
	c2->Display();
	b1->Display();
	return 0;
}
