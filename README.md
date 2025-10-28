# Inventory-Tracking-system-using-hash-table
An inventory tracking system using a hash table stores items by ID for fast add, search, update, and delete operations, ensuring efficient and quick stock management.

Authors: KUMBALINGAM R, MOHAMMED SHIMAR FAARIS N

Language: c++

SDG 12- Responsible consumption and protection.

## 📘 Overview
This project is a simple **Inventory Tracking System** implemented in **C**, using a **Hash Table** for efficient data storage and retrieval.  
It allows users to **add**, **update**, **search**, **delete**, and **display** inventory items quickly, with constant-time average complexity for operations.

## ⚙️ Features
- Add or update items by ID  
- Search items by ID  
- Delete items from the inventory  
- Display all stored items (organized by hash buckets)  
- Collision handling using **separate chaining (linked lists)**  
- Console-based interactive menu  

## 🧮 Data Structure Used
The system uses a **hash table** with a fixed number of buckets.  
Each bucket stores a linked list of items to handle collisions efficiently.

## 🧰 Technologies
- **Language:** C  
- **Compiler:** GCC (MinGW for Windows or GCC for Linux/macOS)

## 🚀 How to Run

### Windows
```bash
gcc inventory.c -o inventory.exe
inventory.exe
Linux/macOS
bash
Copy code
gcc inventory.c -o inventory
./inventory
📂 File Structure
bash
Copy code
├── inventory.c     # Main program source code
├── README.md       # Project documentation
🧑‍💻 Example Operations
mathematica
Copy code
==== Inventory Management System ====
1. Add/Update Item
2. Search Item
3. Delete Item
4. Display Inventory
5. Exit
📈 Future Improvements
Save and load inventory from a file

Add item categories and suppliers

Implement dynamic hash table resizing
