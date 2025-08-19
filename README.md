# Ex. No : 1

# IMPLEMENTATION OF SYMBOL TABLE

# Register Number :

# Date :

# AIM:

To write a C program to implement a symbol table.

# ALGORITHM:

1. Start the program.
2. Get the input from the user with the terminating symbol ‘$’.
3. Allocate memory for the variable by dynamic memory allocation function.
4. If the next character of the symbol is an operator then only the memory is allocated.
5. While reading, the input symbol is inserted into symbol table along with its memory address.
6. The steps are repeated till ‘$’ is reached.
7. To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8. Stop the program.

# PROGRAM:
    #include <stdio.h>
    #include <ctype.h>
    #include <string.h>
    #include <stdlib.h>
    #define MAX_EXPRESSION_SIZE 100
    int main()
    {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[5]; 
    char b[MAX_EXPRESSION_SIZE], d[15], c, srch;
    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1)
    {
        b[i++] = c;
    }
    b[i] = '\0';
    printf("Given Expression: %s\n", b);
    n = strlen(b);
    printf("\nSymbol Table\n");
    printf("Symbol\taddr\ttype\n");
    for (j = 0; j < n; j++)
    {
        c = b[j];
        if (isalpha((unsigned char)c))
        {
            if (j == n - 1)
            {
                void *p = malloc(sizeof(char));
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
            else
            {
                char ch = b[j + 1];
                if (ch == '+' || ch == '-' || ch == '*' || ch == '=')
                {
                    void *p = malloc(sizeof(char));
                    add[x] = p;
                    d[x] = c;
                    printf("%c\t%p\tidentifier\n", c, p);
                    x++;
                }
            }
        }
    }
    printf("\nThe symbol to be searched: ");
    getchar();   
    srch = getchar();
    flag = 0;
    for (i = 0; i < x; i++) 
    {
        if (srch == d[i])
        {
            printf("Symbol Found\n");
            printf("%c@address%p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }
    if (flag == 0)
        printf("Symbol Not Found\n");
    for (i = 0; i < x; i++)
    {
        free(add[i]);
    }
    return 0;
    }
# OUTPUT:

<img width="994" height="407" alt="Screenshot 2025-08-18 144021" src="https://github.com/user-attachments/assets/227795b4-0ab3-4810-8718-673eac0c07ba" />
<img width="1483" height="401" alt="Screenshot 2025-08-18 144044" src="https://github.com/user-attachments/assets/aef3235d-35ee-47e1-aff5-49ee01cb5a9f" />

# RESULT:

The program to implement a symbol table is executed and the output is verified.
