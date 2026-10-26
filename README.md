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
