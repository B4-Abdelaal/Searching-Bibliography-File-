#include "FileOpsStudent.h"
#include <stdio.h>

/**
 * @brief Main function to drive the bibliography tool.
 *
 * @return int Return code.
 */
int main() {
    BibliographyEntry entries[100];
    int count = 0;
    int choice;
    char filename[] = "bibliography.txt";
    char author[256], title[256];
    int year, startYear, endYear;

    readFile(filename, entries, &count);

    while (1) {
        displayMenu();
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter Author: ");
                scanf(" %[^\n]", author);
                searchByAuthor(entries, count, author);
                break;
            case 2:
                printf("Enter Title: ");
                scanf(" %[^\n]", title);
                searchByTitle(entries, count, title);
                break;
            case 3:
                printf("Enter Year: ");
                scanf("%d", &year);
                searchByYear(entries, count, year);
                break;
            case 4:
                printf("Enter Start Year: ");
                scanf("%d", &startYear);
                printf("Enter End Year: ");
                scanf("%d", &endYear);
                searchByYearRange(entries, count, startYear, endYear);
                break;
            case 5:
                displayPublicationTypes(entries, count);
                break;
            case 6:
                displayAuthorsAlphabetically(entries, count);
                break;
            case 7:
                detectDuplicateTitles(entries, count);
                break;
            case 8:
                printf("Enter the index of the entry: ");
                scanf("%d", &year); // Using `year` as a temporary variable to store index
                if (year < count && year >= 0) {
                    displayHarvardReference(entries[year]);
                } else {
                    printf("Invalid index\n");
                }
                break;
            case 9:
                addEntry(entries, &count);
                break;
            case 10:
                return 0;
            default:
                printf("Invalid choice\n");
        }
    }

    return 0;
}
#include "FileOpsStudent.h"
#include <stdio.h>

