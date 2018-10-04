# CIS-7---Discrete-Structures---Assignment-6

#include <iostream>
#include <ratio>
#include <ctime>
#include <chrono>

int GCDCalc(int, int);

int main()
{
	int a;
	int b;
	int gcd;
	bool again = true;
	char answer;
	using namespace std::chrono;

	do
	{
		a = -1;
		b = -1;

		while (a < 0 || b < 0)
		{
			std::cout << "\nPlease enter integer 1 : ";
			std::cin >> a;

			std::cout << "Please enter integer 2 : ";
			std::cin >> b;

			if (a < 0 || b < 0)
			{
				std::cout << "\nPlease enter positive integers." << std::endl;
			}
		}
		high_resolution_clock::time_point t1 = high_resolution_clock::now();

		gcd = GCDCalc(a, b);
		std::cout << "The GCD is : " << gcd << std::endl;

		high_resolution_clock::time_point t2 = high_resolution_clock::now();
		duration<long long, std::nano> time_span = duration_cast<duration<long long, std::nano>>(t2 - t1);
		std::cout << "The time it took to calculate was " << time_span.count() << " nanoseconds." << std::endl;

		std::cout << "Would you like to run this program again? Enter y or n : ";
		
		std::cin >> answer;
		while (answer != 'n' && answer != 'y')
		{
			std::cout << "Invalid entry. Enter y or n : ";
			std::cin >> answer;
		}
		if (answer == 'n')
		{
			again = false;
			std::cout << "\nAdios friendo." << std::endl;
		}
		
		system("pause");
	} while (again == true);

	return 0;
}

int GCDCalc(int a, int b)
{
	int gcd;
	int r;

	if (a == 0 || b == 0)
		gcd = 1;
	else
	{
		r = (a%b);

		while (r < 0 || r > 0)
		{
			a = b;

			b = r;

			r = (a%b);
		}

		gcd = b;
	}

	return gcd;
}
