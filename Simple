#include <stdio.h>
#include <stdlib.h>

struct Student {
    int roll;
    char name[50];
    float marks;
    struct Student *next;
};

struct Student *head = NULL;

void addStudent() {
    struct Student *newNode, *temp;

    newNode = (struct Student *)malloc(sizeof(struct Student));

    if (newNode == NULL) {
        printf("Memory allocation failed!\n");
        return;
    }

    printf("Enter roll number: ");
    scanf("%d", &newNode->roll);

    temp = head;
    while (temp != NULL) {
        if (temp->roll == newNode->roll) {
            printf("Roll number already exists!\n");
            free(newNode);
            return;
        }
        temp = temp->next;
    }

    printf("Enter student name: ");
    scanf(" %49[^\n]", newNode->name);

    printf("Enter marks: ");
    scanf("%f", &newNode->marks);

    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
    } else {
        temp = head;
        while (temp->next != NULL) {
            temp = temp->next;
        }
        temp->next = newNode;
    }

    printf("Student added successfully!\n");
}

void displayStudents() {
    struct Student *temp = head;

    if (temp == NULL) {
        printf("No student records found.\n");
        return;
    }

    printf("\n--- Student Records ---\n");

    while (temp != NULL) {
        printf("Roll Number: %d\n", temp->roll);
        printf("Name: %s\n", temp->name);
        printf("Marks: %.2f\n\n", temp->marks);
        temp = temp->next;
    }
}

void searchStudent() {
    int roll;
    struct Student *temp = head;

    printf("Enter roll number to search: ");
    scanf("%d", &roll);

    while (temp != NULL) {
        if (temp->roll == roll) {
            printf("Student found!\n");
            printf("Name: %s\n", temp->name);
            printf("Marks: %.2f\n", temp->marks);
            return;
        }
        temp = temp->next;
    }

    printf("Student not found.\n");
}

void deleteStudent() {
    int roll;
    struct Student *temp = head;
    struct Student *prev = NULL;

    printf("Enter roll number to delete: ");
    scanf("%d", &roll);

    while (temp != NULL && temp->roll != roll) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL) {
        printf("Student not found.\n");
        return;
    }

    if (prev == NULL) {
        head = temp->next;
    } else {
        prev->next = temp->next;
    }

    free(temp);
    printf("Student deleted successfully!\n");
}

int main() {
    int choice;

    do {
        printf("\n=== Student Record Management ===\n");
        printf("1. Add Student\n");
        printf("2. Display Students\n");
        printf("3. Search Student\n");
        printf("4. Delete Student\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");

        if (scanf("%d", &choice) != 1) {
            printf("Invalid input. Please enter a number.\n");
            break;
        }

        switch (choice) {
            case 1:
                addStudent();
                break;
            case 2:
                displayStudents();
                break;
            case 3:
                searchStudent();
                break;
            case 4:
                deleteStudent();
                break;
            case 5:
                printf("Thank you for using the system!\n");
                break;
            default:
                printf("Invalid choice. Try again.\n");
        }
    } while (choice != 5);

    while (head != NULL) {
        struct Student *temp = head;
        head = head->next;
        free(temp);
    }

    return 0;
}
