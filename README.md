
#include <stdio.h>
#include <string.h>

#define MAX 100

typedef struct {
    char name[50];
    int age;
    char disease[50];
} Patient;

Patient patients[MAX];
int count = 0;

void addPatient() {
    if (count < MAX) {
        printf("Enter Name: ");
        scanf(" %[^\n]", patients[count].name);
        printf("Enter Age: ");
        scanf("%d", &patients[count].age);
        printf("Enter Disease: ");
        scanf(" %[^\n]", patients[count].disease);
        count++;
        printf("Patient added successfully!\n");
    } else {
        printf("Patient list is full!\n");
    }
}

void viewPatients() {
    if (count == 0) {
        printf("No patients to display.\n");
    } else {
        printf("\nPatient List:\n");
        for (int i = 0; i < count; i++) {
            printf("%d. Name: %s, Age: %d, Disease: %s\n", i + 1, patients[i].name, patients[i].age, patients[i].disease);
        }
    }
}

void searchPatient() {
    char name[50];
    printf("Enter name to search: ");
    scanf(" %[^\n]", name);
    for (int i = 0; i < count; i++) {
        if (strcmp(patients[i].name, name) == 0) {
            printf("Found: Name: %s, Age: %d, Disease: %s\n", patients[i].name, patients[i].age, patients[i].disease);
            return;
        }
    }
    printf("Patient not found.\n");
}

int main() {
    int choice;
    while (1) {
        printf("\n1. Add Patient\n2. View Patients\n3. Search Patient\n4. Exit\nEnter choice: ");
        scanf("%d", &choice);
        if (choice == 1) addPatient();
        else if (choice == 2) viewPatients();
        else if (choice == 3) searchPatient();
        else if (choice == 4) break;
        else printf("Invalid choice!\n");
    }
    return 0;
}
