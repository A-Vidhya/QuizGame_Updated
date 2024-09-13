# QuizGame_Updated
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

#define QUEST 5
#define OPTIONS 4

struct Question {
    char question[100];
    char options[OPTIONS][50];
    char correctAnswer;
};

// Function prototypes
void basic();
void intermediate();

int main() {
    char info[400] = "\n\t\t\t----Welcome to QUIZ game---- \n\n\tGeneral Information about this game.\n1.This game has 3 levels of questions about C language.\n2.For each level there are 5 questions.\n3.You need to clear the current level to complete all the 3 levels";
    printf("%s", info);

    char rule[200] = "\n\n\tBelow are the rules to be followed \n1.Enter the correct option only in caps like [A or B]\n2.For each correct answer total will be calculated.\n";
    printf("%s", rule);

    // Start with basic level quiz
    printf("\nEnter 1 to play easy level quiz: ");
    char ch;
    scanf(" %c", &ch);
    
    if (ch == '1') 
	{
        basic();
    }

    return 0;
}

// Function to handle the basic level questions
void basic() {
    struct Question questions[QUEST] = {
        {"Who is the father of C language?", {"Steve Jobs", "James Gosling", "Dennis Ritchie", "Rasmus Lerdorf"}, 'C'},
        {"All keywords in C are in", {"UpperCase letters", "LowerCase letters", "CamelCase letters", "Snake-Case"}, 'B'},
        {"Which of the following cannot be a variable name in C?", {"volatile", "true", "import", "export"}, 'A'},
        {"Functions in C Language are always?", {"Internal", "External", "Void", "None of the above"}, 'B'},
        {"What is the result of logical expression in C?", {"0", "1", "True or false", "0 or 1"}, 'D'}
    };

    int sum1 = 0, i, j;
    char ans;
    for (i = 0; i < QUEST; i++) {
        printf("\nQuestion %d: %s\n", i + 1, questions[i].question);
        for (j = 0; j < OPTIONS; j++) {
            printf("%c. %s\n", 'A' + j, questions[i].options[j]);
        }
        printf("Enter your answer (A, B, C, or D): ");
        scanf(" %c", &ans);
        ans = toupper(ans);
        if (ans == questions[i].correctAnswer) {
            printf("Correct!\n");
            sum1++;
        } else {
            printf("Incorrect.\n");
        }
    }

    printf("\nYour total score is %d", sum1);
    if (sum1 >= 3) {
        printf("\nYou are eligible to play the intermediate level.\nIf you would like to play, enter 1 or 0: ");
        char ch1;
        scanf(" %c", &ch1);
        if (ch1 == '1') {
            intermediate();
        } else {
            printf("Thank you for playing! Try again to play the intermediate level.");
        }
    } else {
        printf("Thank you for playing! Try again to play the intermediate level.");
    }
}

// Function to handle the intermediate level questions
void intermediate() {
    struct Question questions[QUEST] = {
        {"Which of the following is not a storage class specifier in C?", {"extern", "static", "auto", "volatile"}, 'D'},
        {"Which of the following are correct file opening modes in C", {"r", "all", "w", "rb"}, 'B'},
        {"Which of the following is not true about structs in C?", {"Functions are allowed in struct", "no data hiding", "no constructor", "no static member"}, 'A'},
        {"How to declare a double-pointer in C?", {"**&", "int *d", "int **d", "int h"}, 'C'},
        {"How is the 3rd element in an array accessed based on pointer notation?", {"*(a+3)", "a+3", "&(*a+3)", "&(a+3)"}, 'A'}
    };

    int sum2 = 0, i, j;
    char ans;
    for (i = 0; i < QUEST; i++) {
        printf("\nQuestion %d: %s\n", i + 1, questions[i].question);
        for (j = 0; j < OPTIONS; j++) {
            printf("%c. %s\n", 'A' + j, questions[i].options[j]);
        }
        printf("Enter your answer (A, B, C, or D): ");
        scanf(" %c", &ans);
        ans = toupper(ans);
        if (ans == questions[i].correctAnswer) {
            printf("Correct!\n");
            sum2++;
        } else {
            printf("Incorrect.\n");
        }
    }
    printf("Your level 2 score is: %d\n", sum2);
}
