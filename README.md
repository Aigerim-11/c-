#include <iostream>
#include <string>
using namespace std;

struct Product {
    string name;
    int quantity;
    double price;
};

int main() {
    Product products[100];
    int count = 0;
    int choice;

    do {
        cout << "\n=== INVENTORY SYSTEM ===\n";
        cout << "1. Add Product\n";
        cout << "2. Show Products\n";
        cout << "3. Sell Product\n";
        cout << "0. Exit\n";
        cout << "Choose: ";
        cin >> choice;

        if (choice == 1) {
            cout << "Product name: ";
            cin >> products[count].name;
            cout << "Quantity: ";
            cin >> products[count].quantity;
            cout << "Price: ";
            cin >> products[count].price;
            count++;
            cout << "Product added!\n";
        }

        else if (choice == 2) {
            cout << "\n--- Product List ---\n";
            for (int i = 0; i < count; i++) {
                cout << i + 1 << ". "
                     << products[i].name
                     << " | Qty: " << products[i].quantity
                     << " | Price: " << products[i].price << endl;
            }
        }

        else if (choice == 3) {
            int index, qty;
            cout << "Enter product number: ";
            cin >> index;
            cout << "Enter quantity to sell: ";
            cin >> qty;

            if (products[index - 1].quantity >= qty) {
                products[index - 1].quantity -= qty;
                cout << "Sold successfully!\n";
            } else {
                cout << "Not enough stock!\n";
            }
        }

    } while (choice != 0);

    return 0;
}
