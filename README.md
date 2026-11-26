# 5.-Menu-Driven-String-Operations-Using-In-Built-Functions-
#include <stdio.h>
#include <string.h>

#define MAX 100

static void strip_newline(char *str) {
    size_t len = strlen(str);
    if (len > 0 && str[len - 1] == '\n') {
        str[len - 1] = '\0';
    }
}

int main() {
    int choice;
    char str1[MAX], str2[MAX], temp[MAX];

    do {
        printf("\n--- String Operations Menu ---\n");
        printf("1. String Length (strlen)\n");
        printf("2. String Copy (strcpy)\n");
        printf("3. String Concatenation (strcat)\n");
        printf("4. String Comparison (strcmp)\n");
        printf("5. Substring Search (strstr)\n");
        printf("6. Exit\n");
        printf("Enter your choice (1-6): ");
        scanf("%d", &choice);
        getchar(); // Consume trailing newline

        switch (choice) {
            case 1:
                printf("Enter a string: ");
                fgets(str1, MAX, stdin);
                strip_newline(str1);
                printf("Length of \"%s\" is %zu.\n", str1, strlen(str1));
                break;

            case 2:
                printf("Enter source string: ");
                fgets(str1, MAX, stdin);
                strip_newline(str1);
                strcpy(temp, str1);
                printf("Copied string: \"%s\"\n", temp);
                break;

            case 3:
                printf("Enter first string: ");
                fgets(str1, MAX, stdin);
                strip_newline(str1);
                printf("Enter second string: ");
                fgets(str2, MAX, stdin);
                strip_newline(str2);
                strcpy(temp, str1);
                strcat(temp, str2);
                printf("Concatenated string: \"%s\"\n", temp);
                break;

            case 4: {
                printf("Enter first string: ");
                fgets(str1, MAX, stdin);
                strip_newline(str1);
                printf("Enter second string: ");
                fgets(str2, MAX, stdin);
                strip_newline(str2);
                int cmp = strcmp(str1, str2);
                if (cmp == 0) {
                    printf("Both strings are equal.\n");
                } else if (cmp < 0) {
                    printf("\"%s\" comes before \"%s\".\n", str1, str2);
                } else {
                    printf("\"%s\" comes after \"%s\".\n", str1, str2);
                }
                break;
            }

            case 5: {
                printf("Enter main string: ");
                fgets(str1, MAX, stdin);
                strip_newline(str1);
                printf("Enter substring to find: ");
                fgets(str2, MAX, stdin);
                strip_newline(str2);
                char *pos = strstr(str1, str2);
                if (pos != NULL) {
                    printf("Substring found at index %ld.\n", pos - str1);
                } else {
                    printf("Substring not found.\n");
                }
                break;
            }

            case 6:
                printf("Exiting program.\n");
                break;

            default:
                printf("Invalid choice! Please select between 1 and 6.\n");
        }
    } while (choice != 6);

    return 0;
}
