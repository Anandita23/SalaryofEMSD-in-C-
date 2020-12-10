# SalaryofEMSD-in-C-
An organization needs to develop a salary processing application for its staff members. At present it has an engineering division only where engineers and managers work ]. Every engineer reports to some Manager. Every Manager can also work like engineer. In future, it may add director to the team. It can also have a sales executive and they will come under the category of employee. The salary processing logic will be different for all the positions. I learnt about this problem from the "Programming of Java" from  NPTEL.
#include<iostream>
#include<string>
using namespace std;
class Employee{ protected: string name_;
public: virtual void ProcessSalary()=0;
};
class Engineer: public Employee { 
public: Engineer(const string& name){
	name_=name;}
	void ProcessSalary(){
		cout<<name_<<": Process Salary for Engineer"<<endl;
	}
};
class Manager: public Engineer {
	Engineer *reports_[10];
    public: Manager(const string& name): Engineer(name){
	}
		void ProcessSalary(){
		cout<<name_<<": Process Salary for Manager"<<endl;
	}
};
class Director: public Manager {
	Manager *reports_[10];
    public: Director(const string& name): Manager(name){
	}
		void ProcessSalary(){
		cout<<name_<<": Process Salary for Director"<<endl;
	}
};
class SalesExecutive: public Employee {
	
    public: SalesExecutive(const string& name){
    	name_=name;
	}
		void ProcessSalary(){
		cout<<name_<<": Process Salary for Sales Executive"<<endl;
	}
};
int main(){
	Engineer e1("Rohit"),e2("Ram"),e3("Ronit");
	Manager m1("Kamal"),m2("Rahul");
	SalesExecutive s1("Harish"), s2("Vishnu");
	Director d1("Anu");
	Employee *staff[]={&e1,&m1,&m2,&e2,&s1,&e3,&d1,&s2};
	for(int i=0;i<sizeof(staff)/sizeof(Employee*); ++i)
	staff[i]->ProcessSalary();
	return 0;
}
