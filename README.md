# Currency-Converter


#include <iostream>
#include <vector>
using namespace std;

class Product {
public:
    string name;
    double price;

    Product(string n, double p) : name(n), price(p) {}
};

class ShoppingCart {
private:
    vector<Product> cart;

public:
    void addProduct(Product product) {
        cart.push_back(product);
    }

    void displayCart() {
        double total = 0;
        cout << "Cart Contents:" << endl;
        for (Product product : cart) {
            cout << product.name << " - $" << product.price << endl;
            total += product.price;
        }
        cout << "Total: $" << total << endl;
    }
};

void menu() {
    cout << "\nMenu:\n";
    cout << "1. Add Product to Cart\n";
    cout << "2. Display Cart Contents\n";
    cout << "3. Exit\n";
    cout << "Enter your choice: ";
}

int main() {
    ShoppingCart cart;

    while (true) {
        int choice;
        menu();
        cin >> choice;

        switch (choice) {
            case 1: {
                string name;
                double price;
                cout << "Enter product name: ";
                cin >> name;
                cout << "Enter product price: ";
                cin >> price;
                Product newProduct(name, price);
                cart.addProduct(newProduct);
                break;
            }
            case 2:
                cart.displayCart();
                break;
            case 3:
                return 0;
            default:
                cout << "Invalid choice. Please try again." << endl;
                break;
        }
    }

    return 0;
}


