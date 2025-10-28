#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define TABLE_SIZE 10
#define NAME_SIZE 50

typedef struct Item {
    int id;
    char name[NAME_SIZE];
    int quantity;
    float price;
    struct Item* next;
} Item;

Item* hashTable[TABLE_SIZE];

unsigned int hash(int id) {
    return id % TABLE_SIZE;
}

Item* createItem(int id, const char* name, int quantity, float price) {
    Item* newItem = (Item*)malloc(sizeof(Item));
    newItem->id = id;
    strcpy(newItem->name, name);
    newItem->quantity = quantity;
    newItem->price = price;
    newItem->next = NULL;
    return newItem;
}

void insertItem(int id, const char* name, int quantity, float price) {
    unsigned int index = hash(id);
    Item* current = hashTable[index];
    while (current != NULL) {
        if (current->id == id) {
            current->quantity = quantity;
            current->price = price;
            printf("Updated existing item: %s\n", name);
            return;
        }
        current = current->next;
    }
    Item* newItem = createItem(id, name, quantity, price);
    newItem->next = hashTable[index];
    hashTable[index] = newItem;
    printf("Inserted item: %s\n", name);
}

Item* searchItem(int id) {
    unsigned int index = hash(id);
    Item* current = hashTable[index];
    while (current != NULL) {
        if (current->id == id)
            return current;
        current = current->next;
    }
    return NULL;
}

void deleteItem(int id) {
    unsigned int index = hash(id);
    Item* current = hashTable[index];
    Item* prev = NULL;
    while (current != NULL && current->id != id) {
        prev = current;
        current = current->next;
    }
    if (current == NULL) {
        printf("Item not found.\n");
        return;
    }
    if (prev == NULL)
        hashTable[index] = current->next;
    else
        prev->next = current->next;
    free(current);
    printf("Item deleted successfully.\n");
}

void displayInventory() {
    printf("\n--- Inventory List ---\n");
    for (int i = 0; i < TABLE_SIZE; i++) {
        Item* current = hashTable[i];
        if (current == NULL)
            continue;
        printf("Bucket %d:\n", i);
        while (current != NULL) {
            printf("  ID: %d | Name: %s | Qty: %d | Price: %.2f\n",
                   current->id, current->name, current->quantity, current->price);
            current = current->next;
        }
    }
}

int main() {
    int choice, id, quantity;
    char name[NAME_SIZE];
    float price;
    while (1) {
        printf("\n==== Inventory Management System ====\n");
        printf("1. Add/Update Item\n");
        printf("2. Search Item\n");
        printf("3. Delete Item\n");
        printf("4. Display Inventory\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice) {
        case 1:
            printf("Enter ID: ");
            scanf("%d", &id);
            printf("Enter Name: ");
            scanf("%s", name);
            printf("Enter Quantity: ");
            scanf("%d", &quantity);
            printf("Enter Price: ");
            scanf("%f", &price);
            insertItem(id, name, quantity, price);
            break;
        case 2:
            printf("Enter ID to search: ");
            scanf("%d", &id);
            Item* found = searchItem(id);
            if (found)
                printf("Found -> Name: %s | Qty: %d | Price: %.2f\n",
                       found->name, found->quantity, found->price);
            else
                printf("Item not found.\n");
            break;
        case 3:
            printf("Enter ID to delete: ");
            scanf("%d", &id);
            deleteItem(id);
            break;
        case 4:
            displayInventory();
            break;
        case 5:
            printf("Exiting...\n");
            exit(0);
        default:
            printf("Invalid choice. Try again.\n");
        }
    }
}
