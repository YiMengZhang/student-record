student-record
==============
#include<iostream>
using namespace std;
int stuCount;
struct Student{
	char name[40];
	long num;
	int choose;
	int grade;
    }student[50];
void list();
void ChooseSubject();
void DropSubject();
void InputGrade();
int find(long);
int main(){
	int action;
	RETURN:
	cout<<"1 查看学生"<<endl;
	cout<<"2 选课(添加学生)"<<endl;
	cout<<"3 推选（删除学生）"<<endl;
	cout<<"4 输入成绩"<<endl;
	cout<<"5 退出"<<endl;
	cout<<"输入要操作的步骤代码"<<endl<<endl;
	cin>>action;
	do{ switch (action)
		{case 1:
			list();
			break;
		case 2:
			ChooseSubject();
			break;
		case 3:
			DropSubject();
			break;
		case 4:
			InputGrade();
			break;
		case 5:
			return 0;
		default:
			cout<<"错误"<<endl;
			break;
		}
		goto return;
	}while (1);
}
void list(){
	cout<<"学生姓名\t"<<"学号 \t\t"<<"是否选课(1代表选课，0代表没选)\t"<<"学生成绩"<<endl;
	for (int i = 0;i<stuCount;i++)
	{
		cout<<student[i].name<<"  \t";
		cout<<student[i].num<<"\t";
		cout<<student[i].choose<<"\tt";
		cout<<student[i].grade<<endl;
	}
		cout<<"   "<<endl;
}

void ChooseSubject(){
	struct Student studenttemp;
	studenttemp.choose=0;
	studenttemp.grade=0;
	cout<<"输入学生姓名"<<endl;
	cin>>studenttemp.name;
	cout<<"输入学生学号"<<endl;
	cin>>studenttemp.num;
	cout<<"输入学生是否选课"<<endl;
	cin>>studenttemp.choose;
	int i=0;
	i=find(studenttemp.num);
	if (i==stuCount)
	{
		strcpy(student[i].name,studenttemp.name);
		student[i].num=studenttemp.num;
		student[i].choose=studenttemp.choose;
		stuCount++;
	}
	else
	{
		cout<<"ERROE"<<endl;
		}
}
void DropSubject(){
	int i,j,l;
	cout<<"输入学号"<<endl;
	cin>>j;
	i=find(j);
	if(i>=stuCount)
		cout<<"输入学号有误"<<endl;
	else
		{
	cout<<"核对学生信息"<<endl;
	cout<<student[i].name<<endl;
	cout<<student[i].num<<endl;
	cout<<student[i].choose<<endl;
	cout<<student[i].grade<<endl;
	cout<<"确认退选输入1，取消输入0"<<endl;
	cin>>l;
		if(l==1)
		{   student[i].choose=0;
			student[i].grade=0;
		}
		}
}
void InputGrade(){
	int i,j,l,n;
	n=1;
	do{
		cout<<"请输入学生学号"<<endl;
		cin>>j;
		i=find(j);
		if(i>=stuCount)
			cout<<"学号有误"<<endl;
		else
		{
			cout<<"请核对学生信息"<<endl;
			cout<<student[i].name<<endl;
			cout<<student[i].num<<endl;
			cout<<student[i].choose<<endl;
			cout<<student[i].grade<<endl;
			cout<<"确认输入1，取消输入0"<<endl;
			cin>>l;
		if(l==1){
			int n;
			cout<<"输入成绩"<<endl;
			cin>>n;
			student[i].grade=n;
			}
		}
		cout<<"是否继续添加成绩？是输入1,不是输入0"<<endl;
		cin>>n;
    }while(n);
}
int find(long b){
	int m;
	for (m = 0; m < stuCount; m++)
	{       if(student[m].num==b)
			    break;
	}
	        return m;
}
