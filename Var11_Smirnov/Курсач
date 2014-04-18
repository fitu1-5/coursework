//Не забываем включить шрифт ЛюсидаКонсоль в свойствах приложения!
//Вы же любите русский шрифт?
#include "stdafx.h"
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <fstream>
#include <string>
#include <iomanip>
#include <vector>
#include <algorithm>
#include <windows.h>
using namespace std;

class Company
{
	public:
		void store(string name, int staff, double area);
		void show();
		string showName();
		int showStaff();
		double showArea();

	private:
		string name;
		int staff;
		double area;
};

void Company::store(string itsName, int itsStaff, double itsArea)
{
	name=itsName;
	staff=itsStaff;
	area=itsArea;
}

void Company::show()
{
	cout<<"|"<<setw(24)<<name<<" |"<<setw(14)<<staff<<" |"<<setw(25)<<area<<" |"<<endl; // setw() - устанавливаем ширину строки для нужного форматирования
	for(int i=0; i<76; i++)  cout<<"=";
	cout<<endl;
}

string Company::showName()
{
	return name;
}

int Company::showStaff()
{
	return staff;
}

double Company::showArea()
{
	return area;
}

void showTable();
void enterElement();
void sortTableMenu();
void sortByName();
void sortByStaff();
void sortByArea();
void eraseElement();
void writeTable();

vector<Company> companyVector;

int _tmain(int argc, _TCHAR* argv[])
{
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);
	int choice;
	do
	{
		system("cls");
		companyVector.clear();
		showTable();
		cout<<"Выберите пункт меню:"<<endl<<"1. Ввод новых элементов таблицы"<<endl<<"2. Отсортировать данные таблицы"<<endl;
		cout<<"3. Удаление элементов таблицы"<<endl<<"4. Завершить работу программы "<<endl<<"Ваш выбор: ";
		cin>>choice;
		switch(choice)
		{
		case 1:	
			enterElement();
			break;
		case 2:	
			sortTableMenu();
			break;
		case 3:	
			eraseElement();
			break;
		case 4:
			cout<<"Вы покидаете матрицу и отправляетесь в реальную жизнь. Счастливого пути!"<<endl;
			break;
		default: 
				cout<<"Вы ввели неизвестную команду. Пожалуйста, перечитайте пункты меню"<<endl;
		}
	}
	while(choice!=4);
	system("PAUSE");
	return 0;
}

void enterElement()
{
	ofstream newData("Таблица.csv",ios_base::app);
	string newLine;
	string newName;
	string newStaff;
	string newArea;

	cout<<"Введите имя компании: ";
	cin>>newName;
	cout<<"Введите количество сотрудников: ";
	cin>>newStaff;
	cout<<"Введите площадь: ";
	cin>>newArea;

	newLine.append("\n");
	newLine.append(newName);
	newLine.append(";");
	newLine.append(newStaff);
	newLine.append(";");
	newLine.append(newArea);
	newLine.append(";");
	newData<<newLine;

	newData.close();
}

void sortTableMenu()
{
	int sortChoice;
	do
	{
		system("cls");
		cout<<"Выберите пункт меню:"<<endl<<"1. Сортировка по названию"<<endl<<"2. Сортировка по количеству сотрудников"<<endl;
		cout<<"3. Сортировка по занимаемой площади"<<endl<<"4. Выйти в главное меню "<<endl<<"Ваш выбор: ";
		cin>>sortChoice;
		switch(sortChoice)
		{
		case 1:	
			sortByName();
			break;
		case 2:	
			sortByStaff();
			break;
		case 3:	
			sortByArea();
			break;
		case 4:
			break;
		default: 
				cout<<"Вы ввели неизвестную команду. Пожалуйста, перечитайте пункты меню"<<endl;
		}
	}
	while(sortChoice!=4);
}

void sortByName()
{
	int i, j;
	Company tempFirst;
	Company tempSecond;
	int size=companyVector.size();
	system("PAUSE");
	for(i=0; i<size-1; ++i)
	{
		for(j=0; j<size-1; ++j)
		{
			tempFirst=companyVector[j+1];
			tempSecond=companyVector[j];
			if(tempFirst.showName()< tempSecond.showName())
			{
				companyVector[j+1]=companyVector[j];
				companyVector[j]=tempFirst;
			}
		}
	}
	writeTable();
}

void sortByStaff()
{
	int i, j;
	Company tempFirst;
	Company tempSecond;
	int size=companyVector.size();
	system("PAUSE");
	for(i=0; i<size-1; ++i)
	{
		for(j=0; j<size-1; ++j)
		{
			tempFirst=companyVector[j+1];
			tempSecond=companyVector[j];
			if(tempFirst.showStaff() > tempSecond.showStaff())
			{
				companyVector[j+1]=companyVector[j];
				companyVector[j]=tempFirst;
			}
		}
	}
	writeTable();
}

void sortByArea()
{
	int i, j;
	Company tempFirst;
	Company tempSecond;
	int size=companyVector.size();
	system("PAUSE");
	for(i=0; i<size-1; ++i)
	{
		for(j=0; j<size-1; ++j)
		{
			tempFirst=companyVector[j+1];
			tempSecond=companyVector[j];
			if(tempFirst.showArea() > tempSecond.showArea())
			{
				companyVector[j+1]=companyVector[j];
				companyVector[j]=tempFirst;
			}
		}
	}
	writeTable();
}

void showTable()
{
	Company Array;
	int occupancy=1;
	string line;
	ifstream fileData("Таблица.csv"); // создаем объект для вывода файлов из "Таблицы"

	string thisName;
	string buff;
	int itsStaff;
	double itsArea;

	cout<<"|"<<setw(4)<<"Номер"<<"|"<<setw(24)<<"Название организации"<<" |"<<setw(14)<<"Сотрудники"<<" |"<<setw(25)<<"Площадь"<<" |"<<endl;	//выводим заголовок форматирования
	for(int i=0; i<76; i++)  cout<<"=";
	cout<<endl;

	while (! fileData.eof())
	{ 
		getline(fileData, line); //выдираем первую строку из файла
		char endchr= ';'; // символ окончания поиска

		size_t pos = line.find(endchr, 0); // позиция на которой находится символ окончания поиска
		thisName.resize(pos); //пересоздаем объект нужного размера
		copy( line.begin(), line.begin()+pos, thisName.begin() ); // копируем
		line.erase(0, (pos+1)); // удаляем все скопированное + знак ";"

		pos = line.find(endchr, 0);
		buff.resize(pos);
		copy( line.begin(), line.begin()+pos, buff.begin() );
		itsStaff=atoi(buff.c_str() ); // преобразование string в int
		line.erase(0, (pos+1));

		pos = line.find(endchr, 0);
		buff.resize(pos);
		copy( line.begin(), line.begin()+pos, buff.begin() );
		itsArea=atof(buff.c_str() ); // преобразование string в float
		
		Array.store(thisName, itsStaff, itsArea);
		companyVector.push_back(Array);
		cout<<"|"<<setw(5)<<occupancy<<"|";
		Array.show();
		occupancy++;

	}
	int record=(occupancy-1);
	cout<<"В таблице находится "<<record<<" записей!"<<endl;
}

void eraseElement()
{
	int delLine;
	cout<<"Введите номер удаляемой строки: ";
	cin>>delLine;
	int size=companyVector.size();
	companyVector.erase(companyVector.begin() + (delLine-1));
	writeTable();
	system("PAUSE");
}

void writeTable()
{
	int i;
	int size=companyVector.size();
	ofstream writeData("Таблица.csv", ios_base::trunc); //открываем файл, удаляем его содержимое.
	for(i=0; i<size; i++)
	{

		Company Temp = companyVector[i];
		string newLine;
		string newName;
		int newStaff;
		string newStaffStr;
		double newArea;
		string newAreaStr;
		string buff;

		newName=Temp.showName();
		newStaff=Temp.showStaff();
		newArea=Temp.showArea();

		ofstream BuffData("Buff.txt", ios_base::trunc);
		BuffData<<newStaff;
		BuffData<<";";
		BuffData<<newArea;
		BuffData<<";";
		BuffData.close();

		ifstream DelData("Buff.txt");
		while (! DelData.eof())
		{ 
			getline(DelData, buff);
			char endchr= ';';
			size_t pos = buff.find(endchr, 0); // позиция на которой находится символ окончания поиска
			newStaffStr.resize(pos); //пересоздаем объект нужного размера
			copy( buff.begin(), buff.begin()+pos, newStaffStr.begin() ); // копируем
			buff.erase(0, (pos+1)); // удаляем все скопированное + знак ";"
			pos = buff.find(endchr, 0);
			newAreaStr.resize(pos);
			copy( buff.begin(), buff.begin()+pos, newAreaStr.begin() );
			buff.erase(0, (pos+1));
		}
		DelData.close();

		newLine.append(newName);
		newLine.append(";");
		newLine.append(newStaffStr);
		newLine.append(";");
		newLine.append(newAreaStr);
		newLine.append(";");
		if(i!=(size-1))	newLine.append("\n");
		writeData<<newLine;
	}
	writeData.close();
}
