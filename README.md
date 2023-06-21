//header
#include<iostream>
#include<string>
#include<iomanip>

using namespace std;

//varibles for global clock
int hours12, hours24, minutes, seconds;

//to use both options AM and PM in the clock
string ampm;

//function to add an hour to 12 hour clock
void addHour() {
	hours12 = hours12 + 1;

	//after inputting time to add
	if (hours12 >= 12) {
		hours12 = hours12 - 12;
		if (ampm == "AM")
			ampm = "PM";
		else
			ampm = "AM";
	}
}
//function to add minutes to 12 hour clock
void addMinute() {
	minutes = minutes + 1;

	//after inputting time to add as long as it is under 60 minutes
	if (minutes > 59) {
		minutes = 0;
		addHour();

	}
}
//function to add seconds to 12 hour clock
void addSecond() {
	seconds = seconds + 1;

	//after inputting time to add as long as it is under 60 seconds
	if (seconds > 59) {
		seconds = 0;
		addMinute();
	}
}

//main function
int main() {

	//variables
	int choice = 0;

	//setting the intial clock timing manually
	hours12 = 10;
	minutes = 59;
	seconds = 58;
	ampm = "PM";

	//infinite loop unless user wish to exit
	while (1) {

		//calculating the 24 hours calculation
		if (ampm == "PM") {
			hours24 = hours12 + 12;
			if (hours24 >= 24) {
				hours24 = hours24 - 24;
			}
		}
		else {
			hours24 = hours12;
		}
		//printing the clock side by side with * surrounding each clock
		cout << "****************************\t\t****************************\n";
		cout << "*      12-Hour clock       *\t\t*      24-Hour clock       *\n";
		cout << "*      " << setw(2) << setfill('0') << hours12 << ":" << setw(2) << setfill('0') << minutes << ":" << setw(2) << setfill('0') << seconds << " " << ampm << "         *";
		cout << "\t\t*        "      << setw(2) << setfill('0') << hours24 << ":" << setw(2) << setfill('0') << minutes << ":" << setw(2) << setfill('0') << seconds << " " << "         *\n";
		cout << "****************************\t\t****************************\n";
		
		//printing the option surrounded by *
		cout << "\n\n****************************\n";
		cout << "* 1-Add one hour           *\n";
		cout << "* 2-Add one minutes        *\n";
		cout << "* 3-Add one second         *\n";
		cout << "* 4-Exit program           *\n";
		cout << "****************************\n";
		cout << "Choose and option: ";
		cin >> choice;

		//for when choosing option 1
		if (choice == 1) {

			//function to add an hour
			addHour();
		}
		
		//for when choosing option 2
		else if (choice == 2) {

			//function to add a minute
			addMinute();
		}

		//for when choosing option 3
		else if (choice == 3) {

			//function to add second
			addSecond();
		}

		//for when choosing option 4
		else if (choice == 4) {

			//if user wish to exit
			cout << "Exiting program...";
			break;
		}

		//incase invalid option 
		else {

			//printing the error message
			cout << "Invalid input. Try Again...";
		}
	}
	//to return the message 
	return 0;
}

