

---

# 🧾 SIMPLE CASHIER PROGRAM - C++ OOP

---

A. COMPLETE SYNTAX CODE (main.cpp)

```cpp
/*
===================================================
SIMPLE CASHIER PROGRAM - C++ OOP
===================================================
Features:
- Input item name, price, quantity
- Calculate total shopping
- Apply automatic discount
- Display shopping receipt

Created by : Faris
Date       : June 25, 2026
===================================================
*/

#include <iostream>
#include <iomanip>
using namespace std;

class Cashier {
private:
    string itemName;
    int price;
    int quantity;
    int total;
    double discount;
    double finalTotal;

public:
    Cashier() {
        itemName = "";
        price = 0;
        quantity = 0;
        total = 0;
        discount = 0;
        finalTotal = 0;
        cout << "==========================================" << endl;
        cout << "   🧾 SIMPLE CASHIER PROGRAM v1.0        " << endl;
        cout << "==========================================\n" << endl;
    }

    void inputData() {
        cout << "📦 Enter Item Name      : ";
        cin.ignore();
        getline(cin, itemName);

        cout << "💰 Enter Price          : Rp ";
        cin >> price;

        cout << "🔢 Enter Quantity       : ";
        cin >> quantity;

        cout << endl;
    }

    int calculateTotal() {
        total = price * quantity;
        return total;
    }

    double calculateDiscount() {
        if (total >= 100000) {
            discount = total * 0.10;
            cout << "🎉 Congratulations! You get 10% discount" << endl;
        } else if (total >= 50000) {
            discount = total * 0.05;
            cout << "🎉 Congratulations! You get 5% discount" << endl;
        } else {
            discount = 0;
            cout << "😊 No discount. Minimum purchase Rp50.000" << endl;
        }
        return discount;
    }

    double calculateFinalTotal() {
        finalTotal = total - discount;
        return finalTotal;
    }

    void displayReceipt() {
        cout << "\n==========================================" << endl;
        cout << "            🧾 SHOPPING RECEIPT          " << endl;
        cout << "==========================================" << endl;
        cout << "  Item Name     : " << itemName << endl;
        cout << "  Unit Price    : Rp " << price << endl;
        cout << "  Quantity      : " << quantity << " pcs" << endl;
        cout << "------------------------------------------" << endl;
        cout << "  Total         : Rp " << total << endl;
        cout << "  Discount      : Rp " << discount << endl;
        cout << "------------------------------------------" << endl;
        cout << "  FINAL TOTAL   : Rp " << finalTotal << endl;
        cout << "==========================================" << endl;
        cout << "  Thank you for shopping! 🛒             " << endl;
        cout << "==========================================\n" << endl;
    }

    void process() {
        inputData();
        calculateTotal();
        calculateDiscount();
        calculateFinalTotal();
        displayReceipt();
    }
};

int main() {
    Cashier cashier1;
    cashier1.process();
    return 0;
}
```

---

B. CODE EXPLANATION (Separated)

1. Header and Library

```cpp
#include <iostream>
#include <iomanip>
using namespace std;
```

· iostream → for input/output (cin, cout)
· iomanip → for formatting output (optional, used for creating tables)
· using namespace std → allows us to write cout instead of std::cout

---

2. Cashier Class

```cpp
class Cashier {
private:
    ...
public:
    ...
};
```

· Class is a blueprint for creating objects.
· private → attributes that can only be accessed from inside the class (encapsulation).
· public → methods/functions that can be accessed from outside the class.

---

3. Attributes (Private)

```cpp
private:
    string itemName;
    int price;
    int quantity;
    int total;
    double discount;
    double finalTotal;
```

· itemName → name of the item (can contain spaces)
· price → unit price of the item
· quantity → number of items purchased
· total → total price before discount
· discount → discount amount in rupiah
· finalTotal → final amount to be paid after discount

---

4. Constructor

```cpp
Cashier() {
    itemName = "";
    price = 0;
    quantity = 0;
    total = 0;
    discount = 0;
    finalTotal = 0;
    cout << "==========================================" << endl;
    cout << "   🧾 SIMPLE CASHIER PROGRAM v1.0        " << endl;
    cout << "==========================================\n" << endl;
}
```

· Constructor is a method that runs automatically when an object is created.
· Used to initialize all attributes with default values.
· Also displays the program header.

---

5. inputData() Method

```cpp
void inputData() {
    cout << "📦 Enter Item Name      : ";
    cin.ignore();
    getline(cin, itemName);

    cout << "💰 Enter Price          : Rp ";
    cin >> price;

    cout << "🔢 Enter Quantity       : ";
    cin >> quantity;

    cout << endl;
}
```

· cin.ignore() → clears the input buffer so getline() can read spaces.
· getline(cin, itemName) → reads text that contains spaces.
· cin >> price and cin >> quantity → input numbers.

---

6. calculateTotal() Method

```cpp
int calculateTotal() {
    total = price * quantity;
    return total;
}
```

· Calculates total shopping amount using formula price * quantity.
· Stores result in the total attribute and returns it.

---

7. calculateDiscount() Method

```cpp
double calculateDiscount() {
    if (total >= 100000) {
        discount = total * 0.10;
        cout << "🎉 Congratulations! You get 10% discount" << endl;
    } else if (total >= 50000) {
        discount = total * 0.05;
        cout << "🎉 Congratulations! You get 5% discount" << endl;
    } else {
        discount = 0;
        cout << "😊 No discount. Minimum purchase Rp50.000" << endl;
    }
    return discount;
}
```

· Discount logic:
  · Total ≥ 100.000 → 10% discount
  · Total ≥ 50.000 → 5% discount
  · Total < 50.000 → no discount

---

8. calculateFinalTotal() Method

```cpp
double calculateFinalTotal() {
    finalTotal = total - discount;
    return finalTotal;
}
```

· Calculates the final amount to be paid after deducting the discount.

---

9. displayReceipt() Method

```cpp
void displayReceipt() {
    cout << "\n==========================================" << endl;
    cout << "            🧾 SHOPPING RECEIPT          " << endl;
    // ... (print all data)
}
```

· Displays a neat and professional shopping receipt.

---

10. process() Method

```cpp
void process() {
    inputData();
    calculateTotal();
    calculateDiscount();
    calculateFinalTotal();
    displayReceipt();
}
```

· Calls all methods in the correct sequence.
· Makes it easier to run the program by just calling process() once.

---

11. main() Function

```cpp
int main() {
    Cashier cashier1;
    cashier1.process();
    return 0;
}
```

· Creates an object cashier1 from the Cashier class.
· Calls the process() method to run the entire program.

---

C. SAMPLE OUTPUT

Input from User:

```
📦 Enter Item Name      : Notebook
💰 Enter Price          : Rp 5000
🔢 Enter Quantity       : 25
```

Discount Process:

```
🎉 Congratulations! You get 5% discount
```

Receipt Output:

```
==========================================
   🧾 SIMPLE CASHIER PROGRAM v1.0        
==========================================

📦 Enter Item Name      : Notebook
💰 Enter Price          : Rp 5000
🔢 Enter Quantity       : 25

🎉 Congratulations! You get 5% discount

==========================================
            🧾 SHOPPING RECEIPT          
==========================================
  Item Name     : Notebook
  Unit Price    : Rp 5000
  Quantity      : 25 pcs
------------------------------------------
  Total         : Rp 125000
  Discount      : Rp 6250
------------------------------------------
  FINAL TOTAL   : Rp 118750
==========================================
  Thank you for shopping! 🛒             
==========================================
```

---

D. OOP CONCEPTS USED

Concept Explanation
Class class Cashier → blueprint for creating objects
Object Cashier cashier1; → real instance of the class
Encapsulation Attributes are declared private so they cannot be accessed directly from outside
Constructor Cashier() → automatically executed when an object is created
Method Functions inside the class → inputData(), calculateTotal(), etc.
Abstraction The process() method hides the complexity from main()

---

E. HOW TO RUN & COMPILE

```bash
# Compile
g++ -o cashier main.cpp

# Run
./cashier
