#include <tchar.h>
#include <iostream>
#include <string>
#include <ctime>
using namespace std;

int _tmain(int argc, wchar_t argv[]) // функция поддержки символов юникода и нет
{
	srand(time(NULL)); // генератор псевдослучайных чисел основывающийся на временной дате 
	setlocale(LC_ALL, "Russian"); // возможность работы с русскими символами
	int arr[30];
	for (int i = 0; i < 30; i++)
	{
		arr[i] = rand() % 2000 - 1000;
		cout << " " << arr[i]; // заполнение элементов массива рандомными числами от -1000 до 1000
	}
	int sum = 0;
	int m = 0;
	for (int j = 0; j<30; j++)
	{
		if (arr[j] < 0)
		{ 
			sum = sum + 1; 
		}
		else
		{ 
			if (m < sum) // приостановка и обнуление счетчика при положительном элементе массива
			{ 
				m = sum; 
			}
			sum = 0; 
		}
	}
	cout << endl;
	cout << "Максимальное количество подряд идущих отрицательных элементов в массиве равно " << m;
	cin.get();
	return 0;
}