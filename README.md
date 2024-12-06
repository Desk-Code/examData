# examData
1---------------------------

const http = require('http');

const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello, Node.js Server!');
});

server.listen(3000, () => {
    console.log('Server running on http://localhost:3000');
});


2 ----------------------------

const express = require('express');
const app = express();

app.get('/user', (req, res) => {
    const username = req.query.username;
    res.send(`Hello, ${username || 'Guest'}`);
});

app.listen(3000, () => {
    console.log('Server running on http://localhost:3000');
});


3 -------------------------------

const jwt = require('jsonwebtoken');

const payload = { id: 1, username: 'testuser' };
const secretKey = 'your_secret_key';
const token = jwt.sign(payload, secretKey, { expiresIn: '1h' });

console.log('Generated JWT:', token);

4 ------------------------------

import React from 'react';

function HelloWorld() {
    return <h1>Hello, World!</h1>;
}

export default HelloWorld;

5 ---------------------------

const timestamp = Math.floor(Date.now() / 1000); // Current timestamp in seconds
console.log('Unix Timestamp:', timestamp);

6 -------------------------------

use myDatabase
db.createCollection("myCollection")
db.myCollection.insertOne({ name: "John Doe", age: 30, city: "New York" })
db.myCollection.find()
use admin
db.dropDatabase()



--------------------------------------------------------------------------------------------------


1. Write a C++ program to create an integer array of size 5. Use a for loop to take user input for the array elements.

#include <iostream>
using namespace std;

int main() {
    int arr[5];
    cout << "Enter 5 integers:" << endl;
    for (int i = 0; i < 5; i++) {
        cout << "Element " << i + 1 << ": ";
        cin >> arr[i];
    }

    cout << "You entered: ";
    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    return 0;
}


2. Write a C++ program to implement a linear search on the array. Search for the number 7. If it is found, return its index; otherwise, return -1.

#include <iostream>
using namespace std;

int main() {
    int arr[5];
    cout << "Enter 5 integers:" << endl;
    for (int i = 0; i < 5; i++) {
        cin >> arr[i];
    }

    int searchValue = 7, index = -1;
    for (int i = 0; i < 5; i++) {
        if (arr[i] == searchValue) {
            index = i;
            break;
        }
    }

    if (index != -1) {
        cout << "Number 7 found at index: " << index << endl;
    } else {
        cout << "Number 7 not found." << endl;
    }
    return 0;
}

3. Write a menu-driven C++ program with the following two choices:
     Add two numbers.
     Subtract two numbers.

#include <iostream>
using namespace std;

int main() {
    int choice, num1, num2;
    do {
        cout << "\nMenu:\n";
        cout << "1. Add two numbers\n";
        cout << "2. Subtract two numbers\n";
        cout << "3. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        if (choice == 1 || choice == 2) {
            cout << "Enter two numbers: ";
            cin >> num1 >> num2;
        }

        switch (choice) {
            case 1:
                cout << "Result: " << (num1 + num2) << endl;
                break;
            case 2:
                cout << "Result: " << (num1 - num2) << endl;
                break;
            case 3:
                cout << "Exiting program." << endl;
                break;
            default:
                cout << "Invalid choice!" << endl;
        }
    } while (choice != 3);
    return 0;
}

4. Write a C++ program to dynamically allocate memory for an array. Take the array size and elements from the user and then display the elements.

#include <iostream>
using namespace std;

int main() {
    int size;
    cout << "Enter the size of the array: ";
    cin >> size;

    int* arr = new int[size];
    cout << "Enter " << size << " integers:" << endl;
    for (int i = 0; i < size; i++) {
        cin >> arr[i];
    }

    cout << "You entered: ";
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    delete[] arr; // Free allocated memory
    return 0;
}

5. Write a C++ program to create and manage a simple singly linked list. The program should include functions for inserting, deleting, and displaying elements.

#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

class LinkedList {
private:
    Node* head;

public:
    LinkedList() : head(nullptr) {}

    void insert(int value) {
        Node* newNode = new Node{value, nullptr};
        if (!head) {
            head = newNode;
        } else {
            Node* temp = head;
            while (temp->next) {
                temp = temp->next;
            }
            temp->next = newNode;
        }
    }

    void remove(int value) {
        if (!head) return;
        if (head->data == value) {
            Node* temp = head;
            head = head->next;
            delete temp;
            return;
        }
        Node* temp = head;
        while (temp->next && temp->next->data != value) {
            temp = temp->next;
        }
        if (temp->next) {
            Node* toDelete = temp->next;
            temp->next = temp->next->next;
            delete toDelete;
        }
    }

    void display() {
        Node* temp = head;
        while (temp) {
            cout << temp->data << " ";
            temp = temp->next;
        }
        cout << endl;
    }

    ~LinkedList() {
        while (head) {
            Node* temp = head;
            head = head->next;
            delete temp;
        }
    }
};

// Example Usage
int main() {
    LinkedList list;
    list.insert(10);
    list.insert(20);
    list.insert(30);
    list.display();

    list.remove(20);
    list.display();

    return 0;
}

6. Write a C++ program to implement a stack using arrays. The program should include operations for push, pop, and displaying the stack contents.

#include <iostream>
using namespace std;

class Stack {
private:
    int* stack;
    int top;
    int size;

public:
    Stack(int size) {
        this->size = size;
        stack = new int[size];
        top = -1;
    }

    void push(int value) {
        if (top == size - 1) {
            cout << "Stack Overflow" << endl;
            return;
        }
        stack[++top] = value;
    }

    int pop() {
        if (top == -1) {
            cout << "Stack Underflow" << endl;
            return -1;
        }
        return stack[top--];
    }

    void display() {
        if (top == -1) {
            cout << "Stack is empty" << endl;
            return;
        }
        cout << "Stack elements: ";
        for (int i = top; i >= 0; i--) {
            cout << stack[i] << " ";
        }
        cout << endl;
    }

    ~Stack() {
        delete[] stack;
    }
};

// Example Usage
int main() {
    Stack stack(5);
    stack.push(10);
    stack.push(20);
    stack.display();

    stack.pop();
    stack.display();

    return 0;
}
