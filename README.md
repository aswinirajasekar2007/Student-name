
#include <stdio.h>

// Function declarations
int add(int a, int b) { return a + b; }
int sub(int a, int b) { return a - b; }
int mul(int a, int b) { return a * b; }
int divide(int a, int b) { 
    if (b != 0) 
        return a / b; 
    else {
        printf("Error: Division by zero!\n");
        return 0;
    }
}

int main() {
    int choice, x, y, result;
    // Array of function pointers
    int (*operations[])(int, int) = {add, sub, mul, divide};

    while (1) {
        printf("\n--- Calculator using Function Pointers ---\n");
        printf("1. Addition\n");
        printf("2. Subtraction\n");
        printf("3. Multiplication\n");
        printf("4. Division\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 5) {
            printf("Exiting...\n");
            break;
        }

        if (choice < 1 || choice > 5) {
            printf("Invalid choice! Try again.\n");
            continue;
        }

        printf("Enter two numbers: ");
        scanf("%d %d", &x, &y);

        // call the selected function using function pointer
        result = (*operations[choice - 1])(x, y);
        printf("Result = %d\n", result);
    }

    return 0;
}
