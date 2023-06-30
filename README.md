# Bank-Management-in-C-
#include <iostream>
#include <string>

using namespace std;

class Account {
public:
    string customer_name, atype, user, pass;
    int customer_acc_no;

    Account() {
        customer_acc_no = 0;
        customer_name = "";
        atype = "";
        user = "";
        pass = "";
    }
};

class Customer {
public:
    string customer_address, customer_mobile;
    int customer_id;
    Account data[10];
    int total;

public:
    Customer() {
        total = 0;
        customer_id = 1;
        customer_mobile = "7879942595";
        customer_address = "DD nagar";
    }

    void getcustomer() {
    	cout<<"Enter  Userdata "<<total+1<<endl;
        cout << "Enter Name: ";
        cin >> data[total].customer_name;
        cout << "Enter Account number: ";
        cin >> data[total].customer_acc_no;
        cout << "Account Type: ";
        cin >> data[total].atype;
        cout << "Create Username: ";
        cin >> data[total].user;
        cout << "Create Password: ";
        cin >> data[total].pass;
        total++;
    }

   void display_acc() {
    for (int i = 0; i < total; i++) {
        cout << "Data of user " << i + 1 << endl;
        cout << "******************************** "<<endl;
        cout << "*                              * "<<endl;
        cout << "*    Name: " << data[i].customer_name << endl;
        cout << "*    Account Number : " << data[i].customer_acc_no << endl;
        cout << "*    Account Type : " << data[i].atype << endl;
        cout << "*                              *" <<endl; 
        cout << "******************************** "<<endl;
    }
}

    void user_login() {
        cout << "Enter Username: ";
        cin >> data[total].user;
        cout << "Enter Password: ";
        cin >> data[total].pass;
    }
};

class Saving : public Customer {
private:
    double sav;

public:
    Saving() {
        sav = 0;
    }

    void sav_details() {
    	
        cout << "*    Bank Balance : " << sav << endl;
        cout << "********************************"<<endl;
    }

    void s_deposite() {
        double dep;
        cout << "Enter amount to deposit: ";
        cin >> dep;
        sav = sav + dep;
        cout << "Bank Balance: " << sav << endl;
    }

    void s_withdraw() {
        double wid;
        cout << "Balance: " << sav << endl;
        cout << "Enter Withdraw amount: ";
        cin >> wid;
        if (sav >= wid) {
            sav = sav - wid;
            cout << "Bank Balance: " << sav << endl;
        }
        else {
            cout << "Insufficient balance" << endl;
        }
    }
};

class Current : public Customer {
public:
    double cur;

    Current() {
        cur = 0;
    }

    void cur_details() {
        cout << "*    Balance : " << cur << endl;
        cout << "********************************"<<endl;
    }

    void c_deposite() {
        double deposit;
        cout << "Enter deposit Amount: ";
        cin >> deposit;
        cur = cur + deposit;
    }

    void c_withdraw() {
        double wid;
        cout << "Balance: " << cur << endl;
        cout << "Enter Withdraw amount: ";
        cin >> wid;
        if (cur >= wid) {
            cur = cur - wid;
            cout << "Bank Balance: " << cur << endl;
        }
        else {
            cout << "Insufficient balance" << endl;
        }
    }
};
int main() {
    cout << "                                                               **************************************" << endl;
    cout << "                                                               *                                    *" << endl;
    cout << "                                                               *   Amity University Madhya Pradesh  *" << endl;
    cout << "                                                               *                                    *" << endl;
    cout << "                                                               *      Project For End Sem Exam      *" << endl;
    cout << "                                                               *                                    *" << endl;
    cout << "                                                               *        Welcome To our Bank         *" << endl;
    cout << "                                                               *                                    *" << endl;
    cout << "                                                               **************************************" << endl;
    cout << "                                                                -: WE ARE CREATING A VIRTUAL BANK :-" << endl;
    cout << "                                                                 ----------------------------------" << endl;
    cout << "                                                                         -: Group Members :- " << endl;
    cout << "                                                                           ---------------" << endl;
    cout << "                                                   ________________________________________________________________" << endl;
    cout << "                                                   |                                                               |" << endl;
    cout << "                                                   | Dhruv Gupta             A60205222357                          |" << endl;
    cout << "                                                   | Priya Rajput            A60205222350                          |" << endl;
    cout << "                                                   | Harshit Singh Jat       A60205222359                          |" << endl;
    cout << "                                                   |_______________________________________________________________|" << endl;
    Saving s1;
    Current c1;
    Customer d[10];
    string a_key;
    cout << "Enter any key and press enter for banking :-" << endl;
    cin >> a_key;
    system("cls");

    int choice1;
    while (1) {
        cout << "Enter your choice :-" << endl;
        cout << "1. Create New Account ." << endl;
        cout << "2. Accounts Details ." << endl;
        cout << "3. For Banking ." << endl;
        cout << "4. Transaction ." << endl;
        cin >> choice1;
        system("cls");
        switch (choice1) {
        case 1:
            s1.getcustomer();
            break;
        case 2:
            s1.user_login();
            s1.display_acc();
            break;
        case 3:
            char type;
            cout << "Enter S for saving and C for current account :- " << endl;
            cin >> type;
            int choice;
            if (type == 'S' || type == 's') {
                s1.user_login();
                while (1) {
                    cout << "Enter your choice :- " << endl;
                    cout << "1. Deposit" << endl;
                    cout << "2. Withdraw" << endl;
                    cout << "3. Details" << endl;
                    cout << "4. Exit" << endl;
                    cin >> choice;
                    system("CLS");
                    switch (choice) {
                    case 1:
                        s1.s_deposite();
                        break;
                    case 2:
                        s1.s_withdraw();
                        break;
                    case 3:
                        s1.display_acc();
                        s1.sav_details();
                        break;
                    case 4:
                        cout << "Thank you for Banking" << endl;
                        break;
                    default:
                        cout << "Invalid Information" << endl;
                        break;
                    }
                }
            }
            else if (type == 'C' || type == 'c') {
                c1.user_login();
                while (1) {
                    cout << "Enter your choice :- " << endl;
                    cout << "1. Deposit" << endl;
                    cout << "2. Withdraw" << endl;
                    cout << "3. Details" << endl;
                    cout << "4. Exit" << endl;
                    cin >> choice;
                    switch (choice) {
                    case 1:
                        c1.c_deposite();
                        break;
                    case 2:
                        c1.c_withdraw();
                        break;
                    case 3:
                        c1.display_acc();
                        c1.cur_details();
                        break;
                    case 4:
                        cout << "Thank You for Banking" << endl;
                        break;
                    default:
                        cout << "Invalid Information" << endl;
                        break;
                    }
                }
            }
            else {
                cout << "Wrong Information. Try again later." << endl;
            }
            break;
        case 4:
            cout << "Transaction Details are :- " << endl;
            break;
        default:
            cout << "Invalid Information." << endl;
            break;
        }
    }

    return 0;
}
