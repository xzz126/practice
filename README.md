/*加号
#include<iostream>
using namespace std;

class Person
{public:
	Person operator+(Person& p)
	{
		Person temp;
		temp.m_a = this->m_a + p.m_a;
		temp.m_b = this->m_b + p.m_b;
		return temp;
	}
	int m_a;
	int m_b;
};
Person operator+(Person&p1,Person& p)
{
	Person temp;
	temp.m_a = p1.m_a + p.m_a;
	temp.m_b = p1.m_b + p.m_b;
	return temp;
}
void test01()
{
	Person p1;
	Person p2;
	p1.m_a = 10;
	p1.m_b = 20;
	p2.m_a = 20;
	p2.m_b = 10;
	Person p3 = p1 + p2;
	cout << p3.m_a << endl;
	cout << p3.m_b << endl;
}
int main()
{
	test01();

	system("pause");
	return 0;
}*/

/*<<
#include<iostream>
using namespace std;

class Person
{
	friend ostream&operator<<(ostream& cout, Person& p);
public:
	Person(int a, int b)
	{
		this->m_A = a;
		this->m_B = b;
	}


private:
	int m_A;
	int m_B;
};

ostream& operator<<(ostream& cout, Person& p)
{
	cout << p.m_A << "   " << p.m_B ;
	return cout;
}

void test01()
{
	Person p(10, 20);
	cout << p << "hello" ;
}
int main()
{
	test01();
	system("pause");
	return 0;
}
*/

/*递增
#include<iostream>
using namespace std;

class Person
{
	friend ostream& operator<<(ostream& cout, Person p);

public:
	Person()
	{		
	    m_a = 0;
	}
	Person operator++(int)
	{
		Person temp = *this;
		m_a++;
        return temp;
	}
private:
	int m_a;
};

ostream& operator<<(ostream& cout, Person p)
{
	cout << p.m_a;
	return cout;
}

void test01()
{
	Person person;
	cout << person++ << endl;
	cout << person << endl;
}
int main()
{
	test01();
	system("pause");
	return 0;
}*/

/*
#include<iostream>
using namespace std;

class Person
{
	Person(int age)
	{
		m_age = new int(age);
	}
	Person(const Person& p)
	{
		m_age = new int(*p.m_age);
	}
	Person& operator=(const Person& p)
	{
		if (this == &p)
		{
			return*this;
		}
		if (m_age != NULL)
		{
			delete m_age;
			m_age = NULL;
		}
		m_age = new int(*p.m_age);
		return *this;
	}
	~Person()
	{
		if (m_age != NULL)
		{
			delete m_age;
			m_age = NULL;
		}
	}
private:
	int *m_age;
};

void test01()
{
	Person p1(18);
	
	Person p2
	
	Person p3	
}
int main()
{

}*/

/*关系
#include<iostream>
using namespace std;

class Person
{
public:
	Person(string name, int age)
	{
		m_name = name;
		m_age = age;
	}
	bool operator==(Person& p)
	{
		if (this->m_name == p.m_name;this->m_age == p.m_age)
		{
			return true;
		}
		return false;
	}
private:
	int m_age;
	string m_name;
};

void test01()
{
	Person p1 = { "张三",20 };
	Person p2 = { "李四",25 };
	if (p1 == p2)
	{
		cout << "p1和p2是相等的" << endl;
	}
	else
	{
		cout << "不相等" << endl;
	}
}

int main()
{
	test01();
	return 0;
	}*/

/*函数
#include<iostream>
using namespace std;

class print
{
public:
    int  operator()(int &a,int& b)
	{
		return a + b;
	}
};
void test01()
{
	print myprint;
	int a = 100;
	int b = 200;
	int ret = myprint(a, b);
	cout << ret << endl;
}

int main()
{
	test01();
	return 0;

}*/

/*
class father
{
public:
	void father01()
	{
		cout << "我是你爸" << endl;
	}
	void father02()
	{
		cout << "我是你爹" << endl;
	}
};

class son :public father
{
public:
	void son01()
	{
		cout << "我是你儿子" << endl;
	}

};
class daut:public father
{
public:
	void daut01()
	{
		cout << "我是你女儿" << endl;
	}
};

int main()
{
	son son;
	son.father01();
	son.son01();
	daut daut;
	daut.father02();
	daut.daut01();
}*/

/*
class father
{
public:
	static void test01()
	{
		cout << 1 << endl;
	}
};

class son :public father
{
public:
	static void test01()
	{
		cout << "a" << endl;
	}
};
int main()
{
	son b;
	b.father::test01();
	son::father::test01();
}*/

/*
#include<iostream>
using namespace std;
class animal
{
public:
	int m_a;
};

class sheep :virtual public animal
{

};

class tuo :virtual public animal
{

};

class sheeptuo :public sheep, public tuo
{

};

int main()
{
	sheeptuo st;
	st.sheep::m_a = 18;
	st.tuo::m_a = 28;
	cout << st.sheep::m_a << endl;
	cout << st.tuo::m_a << endl;
	cout << st.m_a << endl;
}*/


class animal
{
public:
	virtual void speak()
	{
		cout << "动物在说话" << endl;
	}
};
class cat : public animal
{
public:
	void speak()
	{
		cout << "小猫在说话" << endl;
	}
};
void dospeak(animal&animal)
{
	animal.speak();
}
int main()
{
	cat cat;
	dospeak(cat);
}
/* 纯虚函数和抽象类
#include<iostream>
using namespace std;

class Base
{
public:
	virtual void func() = 0;
};

class Son :public Base
{
public :
	virtual void func()
	{
		cout << "你是给吧" << endl;
	}
	/*Son(int a)
	{
		this->m_A = a;
	}
	int m_A;
};

int main()
{
	//Son s(20);
	Base* base = new Son;
	base->func();
	//s.func();
	return 0;
}*/
/*
#include<iostream>
using namespace std;

class Animal
{
public:
	Animal()
	{
		cout << "a" << endl;
	}
	//virtual ~Animal()
	//{
	//	cout << "b" << endl;
	//}
	virtual ~Animal() = 0;
	virtual void speak() = 0;
};
Animal:: ~Animal()
{
	cout << "b" << endl;
}
class Cat :public Animal
{
public:
	virtual void speak()
	{
		cout << "小猫在说话" << endl;
	}
	Cat(string name)
	{
		m_name=new string(name);
		cout << 1 << endl;
	}
	~Cat()
	{
		if (m_name != NULL)
		{
			cout << 2 << endl;
			delete m_name;
			m_name = NULL;
		}
	}

	string* m_name;
};

int main()
{
	Animal* animal = new Cat("Tom");
	animal->speak();
	delete animal;

}*/
/*模板
#include<iostream>
using namespace std;

template<class T>
T myswap(T a, T b)
{
	//T temp = a;
	return a + b;
	//b = temp;
}

int main()
{
	int a = 10;
	int b = 20;
	char c = 's';
	cout << myswap<int>(a, c) << endl;
}*/
/*模板具体化实现
#include<iostream>
using namespace std;
#include<string>

class Person
{
public:
	Person(string name, int age)
	{
		this->m_name = name;
		this->m_age = age;
	}
	string m_name;
	int m_age;
};

template<class T>
bool mycompare(T a, T b)
{
	if (a == b)
	{
		return true;
	}
	else
	{
		return false;
	}
}
template<>
bool mycompare(Person& a, Person &b)
{
	if (a.m_name==b.m_name&&a.m_age==b.m_age)
	{
		return true;
	}
	else
	{
		return false;
	}
}
int main()
{
	Person p1("yi", 20);
	Person p2("er", 26);

	
	bool ret = mycompare(p1, p2);
	cout << ret << endl;

	return 0;
}*/
/*类模板
#include<iostream>
using namespace std;
#include<string>

template<class T1,class T2>
class father
{public:
	father(T1 a,T2 b)
	{
		m_name = a;
		m_age = b;
		cout << m_name << "   " << m_age << endl;
	}

	T1 m_name;
	T2 m_age;
};

int main()
{
	string a = "your father";
	int b = 18;
	father<string, int>father(a, b);
}
*/
/*类模板对象做函数参数
#include<iostream>
using namespace std;

template<class T1>
class Person
{
public:
	T1 age;
	
	Person(T1 a)
	{
		age = a;
	}
	void show()
	{
		cout << age << endl;
	}
};

void print(Person<int>& p)
{
	p.show();
}

template<class T1>
void print02(Person<T1>& p)
{
	p.show();
}

template<class T1>
void print03(T1& p)
{
	p.show();
}

int main()
{
	Person<int>p1(18);
	print(p1);
	print02(p1);
	print03(p1);
	return 0;
}*/

/*类模板和继承
#include<iostream>
using namespace std;
#include<string>

template<class T1>
class father
{
public:
	T1 name;
};
template<class T1>
class son :public father<T1>
{
public:
	void print(T1 a)
	{
		this->name = a;
		cout << this->name << endl;
	}
};
void test01()
{
	string b = "geiba";
	son<string> a;
	a.print(b);
}
int main()
{
	test01();
	return 0;
}*/
/*类模板成员函数类外实现
#include<iostream>
using namespace std;
#include<string>

template<class T1,class T2>
class Person
{
public:
	Person(T1 a, T2 b);
	void print();
	T1 age;
	T2 name;
};
template<class T1,class T2>
Person<T1, T2>::Person(T1 a, T2 b)
{
	this->age = a;
	this->name = b;
}
template<class T1,class T2>
void Person<T1, T2>::print()
{
	cout << name << "  " << age;
}

int main()
{
	Person<int, string>p(18, "laodou");
	p.print();

}*/
/*类模板和友元
#include<iostream>
using namespace std;

template<class T>
class Person;//类声明
template<class T>
void print(Person<T>& p);//函数声明
template<class T>
class Person
{
	T age;
public:
	Person(T a)
	{
		this->age = a;
	}
	friend void print<T>(Person<T>& p);
    {
		cout << p.age << endl;
	}
};
template<class T>
void print(Person<T>& p)
{
	cout << p.age << endl;
}

int main()
{
	Person<int>p(18);
	print(p);
	return 0;
}*/

/*类模板分文件编写
#include<iostream>
using namespace std;
#include"test.hpp"

template<class T>
class Person
{
public:
	Person(T a)
	{
		this->age = a;
	}
	
	T age;
};
template<class T>
void test(Person<T>&p)
{
	cout << p.age <<endl;
}

int main()
{
	Person<int>p(18);
	test(p);
}*/
/*vector存放内置数据类型和遍历
#include<iostream>
using namespace std;
#include<vector>
#include<algorithm>

void print(int val)
{
	cout << val << endl;
}

void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(20);
	v.push_back(30);
	v.push_back(40);
	v.push_back(50);
	for (vector<int>::iterator it=v.begin();it!=v.end();it++)
	{
		cout << *it << endl;
	}

	for_each(v.begin(), v.end(), print);
}



int main()
{
	test01();

	return 0;
}
*/
/*存放自定义数组
#include<iostream>
using namespace std;
#include<vector>
#include<string>
class Person
{public:
	Person(string name, int age)
	{
		m_name = name;
		m_age = age;
	}
	string m_name;
	int m_age;
};
void test01()
{
	vector<Person>v;
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);

	for (vector<Person>::iterator it = v.begin();it != v.end();it++)
	{
		cout<<(*it).m_name<<"   "<<(*it).m_age << endl;
	}
}

void test02()
{
	vector<Person*>v1;

	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);

	v1.push_back(&p1);
	v1.push_back(&p2);
	v1.push_back(&p3);
	v1.push_back(&p4);
	v1.push_back(&p5);

	for (vector<Person*>::iterator vit = v1.begin();vit != v1.end();vit++)
	{
		cout << (**vit).m_name << "   " << (**vit).m_age << endl;
	}

}

int main()
{
	test01();
	test02();

	return 0;
}*/
