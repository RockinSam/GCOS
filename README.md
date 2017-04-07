#include <stdio.h>
#include <conio.h>
#include <string.h>
#include <windows.h>
#include <stdlib.h>
#define space "\t\t\t"


/* Number puzzle */
int right(int array[6][6],int n)// Used to move 0 to the right side in number puzzle.
{
    int i,j,c;

    //replace 0 with right side value
    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
        {
            if(array[i][j]==0&&j!=(n-1))
            {
                c=array[i][j];
                array[i][j]=array[i][j+1];
                array[i][j+1]=c;
                break;
            }
        }
    }
    return 0;
}


int left(int array[6][6],int n)// Used to move 0 to the left side in number puzzle.
{
    int i,j,c;

    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
        {
            if(array[i][j]==0&&j!=0)
            {
                c=array[i][j-1];
                array[i][j-1]=array[i][j];
                array[i][j]=c;
                break;
            }
        }
    }
    return 0;
}


int up(int array[6][6],int n)// Used to move 0 to the up side in number puzzle.
{
    int i,j,c;

    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
        {
            if(array[i][j]==0&&i!=0)
            {
                c=array[i][j];
                array[i][j]=array[i-1][j];
                array[i-1][j]=c;
                break;
            }
        }
    }
    return 0;
}


int down(int array[6][6],int n)// Used to move 0 to the down side in number puzzle.
{

  int i,j,c,d,e;

    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
        {
            if(array[i][j]==0)
            {
                d=i;
                e=j;
            }
        }
    }
    if(d!=(n-1))
    {
        array[d][e]=array[d+1][e];
        array[d+1][e]=0;
    }
    return 0;
}


// Printing the number puzzle
int displayNumberPuzzle(int array[6][6], int n)
{
    int i, j, k = 1;
    char choice;
    system("cls");

    if(n == 4)
    {
        printf("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 218, 196, 196, 196, 194, 196, 196, 196, 194, 196, 196, 196 , 194, 196, 196, 196, 191);
    }
    if(n == 3)
    {
        printf("%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 218, 196, 196, 196, 194, 196, 196, 196, 194, 196, 196, 196, 191);
    }
    if(n == 5)
    {
        printf("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 218, 196, 196, 196, 194, 196, 196, 196, 194, 196, 196, 196, 194, 196, 196, 196, 194, 196, 196, 196, 191);
    }
    for(i = 0; i < n; i++)
    {
        for(j = 0; j < n; j++)
        {
            if(array[i][j] == 0)
            {
                printf("%c   ", 179);
            }
            else
            {
                printf("%c%2d ", 179, array[i][j]);
            }
        }
        printf("%c\n", 179);
        if(i == 4 && n == 5)
        {
            printf("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 192, 196, 196, 196, 193, 196, 196, 196, 193, 196, 196, 196, 193, 196, 196, 196, 193, 196, 196, 196, 217);
        }
        else
        {
            if(n == 5)
            {
                printf("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 195, 196, 196, 196, 197, 196, 196, 196, 197, 196, 196, 196, 197, 196, 196, 196, 197, 196, 196, 196, 180);
            }
        }
        if(i == 2 && n == 3)
        {
            printf("%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 192, 196, 196, 196, 193, 196, 196, 196, 193, 196, 196, 196 , 217);
        }
        else
        {
            if(n == 3)
            {
                printf("%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 195, 196, 196, 196, 197, 196, 196, 196, 197, 196, 196, 196 , 180);
            }
        }
        if(i == 3 && n == 4)
        {
            printf("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 192, 196, 196, 196, 193, 196, 196, 196, 193, 196, 196, 196 , 193, 196, 196, 196, 217);
        }
        else
        {
            if(n == 4)
            {
                printf("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c\n", 195, 196, 196, 196, 197, 196, 196, 196, 197, 196, 196, 196 , 197, 196, 196, 196, 180);
            }
        }
    }
    for(i = 0; i < n; i++)
    {
        for(j = 0; j < n; j++)
        {
            if(array[i][j] == k)
            {
                k = k + 1;
            }
            else
            {
                break;
            }
        }
    }
    if(k == (n * n) && array[n - 1][n - 1] == 0)
    {
	printf("Game over you win\n");
    system("color a0");
    return 1;
    }
    return 0;
}


// Number puzzle.
int numberPuzzle(int n)
{
    int array[6][6];
    int rows, columns;
    int random, i;
    int randvalues[30], m = 0;
    int t, j;
    int choice;

    for(i=0;i<(n*n);i++)     //assigning values 0 to 8
         randvalues[i]=i;

    for(i=0;i<(n*n);i++)      //shuffle logic i.e., arrange all values but not in sequence
    {
         j=i+rand()/(RAND_MAX/((n*n)-i) + 1);
         t=randvalues[j];
         randvalues[j] = randvalues[i];
         randvalues[i] = t;
    }

    for(rows=0;rows<n;rows++) //converting from 1d array to 2d array
    {
        for(columns=0;columns<n;columns++)
        {
            array[rows][columns] = randvalues[m++];

        }
    }

    while(1)
    {
    if(displayNumberPuzzle(array, n))
    {
        label1 :
        if(27 != _getch())
        {
            goto label1;
        }
        else
        {
            return 0;
        }
    }
    choice = _getch();
    if(27 == choice)
    {
        return 0;
    }
    if(224 == choice)
    {
        switch(_getch())
        {
        case 77:
            right(array, n);
	    break;
        case 75:
            left(array, n);
        break;
        case 72:
            up(array, n);
        break;
        case 80:
            down(array, n);
	    break;
        }
    }
    }
    return 0;
}


/* Towers of Hanoi */
// Used to print the Hanoi towers.
int printHanoi(int *tower1, int *tower2, int *tower3)
{
    int i, j;
    char array[4][23];
    system("cls");

    for(i = 0; i < 4; i++)
    {
        for(j = 0; j < 23; j++)
        {
            array[i][j] = 255;
        }
    }
    array[0][3] = array[0][11] = array[0][19] = 186;
    array[1][3] = array[1][11] = array[1][19] = 186;
    array[2][3] = array[2][11] = array[2][19] = 186;
    array[3][3] = array[3][11] = array[3][19] = 186;


    // Top bars of the tower.
    if(tower1[2] == 1)
    {
        array[1][2] = array[1][3] = array[1][4] = 219;
    }
    if(tower2[2] == 1)
    {
        array[1][10] = array[1][11] = array[1][12] = 219;
    }
    if(tower3[2] == 1)
    {
        array[1][18] = array[1][19] = array[1][20] = 219;
    }


    // Middle bars of the tower.
    if(tower1[1] == 2)
    {
        array[2][1] = array[2][2] = array[2][3] = array[2][4] = array[2][5] = 219;
    }
    if(tower2[1] == 2)
    {
        array[2][9] = array[2][10] = array[2][11] = array[2][12] = array[2][13] = 219;
    }
    if(tower3[1] == 2)
    {
        array[2][17] = array[2][18] = array[2][19] = array[2][20] = array[2][21] = 219;
    }

    if(tower1[1] == 1)
    {
        array[2][2] = array[2][3] = array[2][4] = 219;
    }
    if(tower2[1] == 1)
    {
        array[2][10] = array[2][11] = array[2][12] = 219;
    }
    if(tower3[1] == 1)
    {
        array[2][18] = array[2][19] = array[2][20] = 219;
    }


    //Bottom bars of the tower.
    if(tower1[0] == 3)
    {
        array[3][0] = array[3][1] = array[3][2] = array[3][3] = array[3][4] = array[3][5] = array[3][6] = 219;
    }
    if(tower2[0] == 3)
    {
        array[3][8] = array[3][9] = array[3][10] = array[3][11] = array[3][12] = array[3][13] = array[3][14] = 219;
    }
    if(tower3[0] == 3)
    {
        array[3][16] = array[3][17] = array[3][18] = array[3][19] = array[3][20] = array[3][21] = array[3][22] = 219;
    }

    if(tower1[0] == 2)
    {
        array[3][1] = array[3][2] = array[3][3] = array[3][4] = array[3][5] = 219;
    }
    if(tower2[0] == 2)
    {
        array[3][9] = array[3][10] = array[3][11] = array[3][12] = array[3][13] = 219;
    }
    if(tower3[0] == 2)
    {
        array[3][17] = array[3][18] = array[3][19] = array[3][20] = array[3][21] = 219;
    }

    if(tower1[0] == 1)
    {
        array[3][2] = array[3][3] = array[3][4] = 219;
    }
    if(tower2[0] == 1)
    {
        array[3][10] = array[3][11] = array[3][12] = 219;
    }
    if(tower3[0] == 1)
    {
        array[3][18] = array[3][19] = array[3][20] = 219;
    }



    printf("\n\n\n\n\n");
    for(i = 0; i < 4; i++)
    {
        printf("\t");
        for(j = 0; j < 23; j++)
        {
            printf("%c",array[i][j]);
        }
        printf("\n");
    }
    printf("       %c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c", 205, 205, 205, 205, 202, 205, 205, 205, 205, 205, 205, 205, 202, 205, 205, 205, 205, 205, 205, 205, 202, 205, 205, 205, 205);

    return 0;
}


// Towers of Hanoi.
int towersOfHanoi()
{
    int tower1[3] = {3, 2, 1}, tower2[3] = {0}, tower3[3] = {0}; // Declaring stacks for towers.
    int i, top1 = 2, top2 = 0, top3 = 0; // Declaring top of the stacks.
    char from, to; // Declaring from and to positions.
    while(1)
    {
        printHanoi(tower1, tower2, tower3);


        // Scanning from and to position.
        printf("\n\tfrom = ");
        from = _getche();
        printf("\n\t  to = ");
        to = _getche();
        Sleep(250);


        // Converting alphabets from uppercase to lowercase.
        if(from == 'A' || from == 'B' || from == 'C')
        {
            from += 32;
        }
        if(to == 'A' || to == 'B' || to == 'C')
        {
            to += 32;
        }
        if(from == 'a' || from == 'b' || from == 'c'
           && to == 'a' || to == 'b' || to == 'c'){}
        else
        {
            printf("\n\tInvalid Move : \n");
            Sleep(500);
        }


        // Moving bar from A to B.
        if(from == 'a' && to == 'b')
        {
            if(top2 != 2)
            {
                if(tower2[top2] == 0)
                {
                    tower2[top2] = tower1[top1];
                    tower1[top1] = 0;
                    if(top1 != 0)
                    {
                        top1--;
                    }
                }
                else if(tower2[top2] > tower1[top1])
                {
                    tower2[++top2] = tower1[top1];
                    tower1[top1] = 0;
                    if(top1 != 0)
                    {
                        top1--;
                    }
                }
                else
                {
                    printf("\n\tInvalid Move : \n");
                    Sleep(500);
                }
            }
        }


        // Moving bar from A to C.
        if(from == 'a' && to == 'c')
        {
            if(top3 != 2)
            {
                if(tower3[top3] == 0)
                {
                    tower3[top3] = tower1[top1];
                    tower1[top1] = 0;
                    if(top1 != 0)
                    {
                        top1--;
                    }
                }
                else if(tower3[top3] > tower1[top1])
                {
                    tower3[++top3] = tower1[top1];
                    tower1[top1] = 0;
                    if(top1 != 0)
                    {
                        top1--;
                    }
                }
                else
                {
                    printf("\n\tInvalid Move : \n");
                    Sleep(500);
                }
            }
        }


        // Moving bar from B to A.
        if(from == 'b' && to == 'a')
        {
            if(top1 != 2)
            {
                if(tower1[top1] == 0)
                {
                    tower1[top1] = tower2[top2];
                    tower2[top2] = 0;
                    if(top2 != 0)
                    {
                        top2--;
                    }
                }
                else if(tower1[top1] > tower2[top2])
                {
                    tower1[++top1] = tower2[top2];
                    tower2[top2] = 0;
                    if(top2 != 0)
                    {
                        top2--;
                    }
                }
                else
                {
                    printf("\n\tInvalid Move : \n");
                    Sleep(500);
                }
            }
        }


        // Moving bar from B to C.
        if(from == 'b' && to == 'c')
        {
            if(top3 != 2)
            {
                if(tower3[top3] == 0)
                {
                    tower3[top3] = tower2[top2];
                    tower2[top2] = 0;
                    if(top2 != 0)
                    {
                        top2--;
                    }
                }
                else if(tower3[top3] > tower2[top2])
                {
                    tower3[++top3] = tower2[top2];
                    tower2[top2] = 0;
                    if(top2 != 0)
                    {
                        top2--;
                    }
                }
                else
                {
                    printf("\n\tInvalid Move : \n");
                    Sleep(500);
                }
            }
        }


        // Moving bar from C to A.
        if(from == 'c' && to == 'a')
        {
            if(top1 != 2)
            {
                if(tower1[top1] == 0)
                {
                    tower1[top1] = tower3[top3];
                    tower3[top3] = 0;
                    if(top3 != 0)
                    {
                        top3--;
                    }
                }
                else if(tower1[top1] > tower3[top3])
                {
                    tower1[++top1] = tower3[top3];
                    tower3[top3] = 0;
                    if(top3 != 0)
                    {
                        top3--;
                    }
                }
                else
                {
                    printf("\n\tInvalid Move : \n");
                    Sleep(500);
                }
            }
        }


        // Moving bar from C to B.
        if(from == 'c' && to == 'b')
        {
            if(top2 != 2)
            {
                if(tower2[top2] == 0)
                {
                    tower2[top2] = tower3[top3];
                    tower3[top3] = 0;
                    if(top3 != 0)
                    {
                        top3--;
                    }
                }
                else if(tower2[top2] > tower3[top3])
                {
                    tower2[++top2] = tower3[top3];
                    tower3[top3] = 0;
                    if(top3 != 0)
                    {
                        top3--;
                    }
                }
                else
                {
                    printf("\n\tInvalid Move : \n");
                    Sleep(500);
                }
            }
        }

    }
    return 0;
}


/* Find the pairs */
// This function prints the array of Find the Pair.
int printThePairs(char Array2[4][4], char Array1[4][4], int posOfBox)
{
    int i = 0, j, k = 0, ch = 0;
    system("cls");
    printf("\n\n\n");

    while(i < 4)
    {

        // Printing the first line.
        if(posOfBox >=1 && posOfBox <=4)
        {
            printf("   ");
            for(k = 0; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
              }
            printf("\n");
            printf("   ");
            for(k = 0; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
            }
            printf("\n");
        }
        i++;


        // Printing the second line.
        if(posOfBox >=5 && posOfBox <=8)
        {
            printf("   ");
            for(k = 4; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
              }
            printf("\n");
            printf("   ");
            for(k = 4; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
            }
            printf("\n");
        }
        i++;


        // Printing the third line.
        if(posOfBox >=9 && posOfBox <=12)
        {
            printf("   ");
            for(k = 8; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
              }
            printf("\n");
            printf("   ");
            for(k = 8; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
            }
            printf("\n");
        }
        i++;


        // Printing the fourth line.
        if(posOfBox >=13 && posOfBox <=16)
        {
            printf("   ");
            for(k = 12; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
              }
            printf("\n");
            printf("   ");
            for(k = 12; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or letter.
            }
            printf("\n");
        }
        i++;
    }


    // Checking if won or not.
    if(posOfBox != -1)
    {
        for(i = 0; i < 4; i++)
        {
            for(j = 0; j < 4; j++)
            {
                if(Array1[i][j] == Array2[i][j])
                {
                    ch++;
                }
            }
            printf("\n");
        }
        if(ch == 16)
        {
            system("color a0");
            printf("\n Game over You win\n");
            return 1;
        }
    }
    return 0;
}


// This function reveals the the letter behind the block in the game for finding the pairs.
int revealThePair(char array_2[4][4], char array_1[4][4], int box_Pos, int *prevI, int *prevJ)
{
    static int chance = 0, tempVar;
    chance++;

    if(tempVar == -37 || chance == 1)
    {
        if(box_Pos >= 1 && box_Pos <= 4)
        {
            tempVar = array_2[0][box_Pos - 1];
            array_2[0][box_Pos - 1] = array_1[0][box_Pos - 1];
            if(chance == 1)
            {
                *prevI = 0;
                *prevJ = box_Pos - 1;
            }
            if(chance == 2 && tempVar == -37)
            {
                if(array_2[*prevI][*prevJ] == array_2[0][box_Pos - 1])
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    Beep(1000, 700);
                    *prevI = -1;
                    *prevJ = -1;
                }
                else
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    array_2[0][box_Pos - 1] = 219;
                    array_2[*prevI][*prevJ] = 219;
                    Sleep(500);
                }
                chance = 0;
            }
            else if(chance == 2)
            {
                chance = 0;
                array_2[*prevI][*prevJ] = 219;
            }
        }
    }
    else
    {
        chance = 0;
    }
    if(tempVar == -37 || chance == 1)
    {
        if(box_Pos >= 5 && box_Pos <= 8)
        {
            tempVar = array_2[1][box_Pos - 5];
            array_2[1][box_Pos - 5] = array_1[1][box_Pos - 5];
            if(chance == 1)
            {
                *prevI = 1;
                *prevJ = box_Pos - 5;
            }
            if(chance == 2 && tempVar == -37)
            {
                if(array_2[*prevI][*prevJ] == array_2[1][box_Pos - 5])
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    *prevI = -1;
                    *prevJ = -1;
                    Beep(1000, 700);
                }
                else
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    array_2[1][box_Pos - 5] = 219;
                    array_2[*prevI][*prevJ] = 219;
                    Sleep(500);
                }
                chance = 0;
            }
            else if(chance == 2)
            {
                chance = 0;
                array_2[*prevI][*prevJ] = 219;
            }
        }
    }
    else
    {
        chance = 0;
    }
    if(tempVar == -37 || chance == 1)
    {
        if(box_Pos >= 9 && box_Pos <= 12)
        {
            tempVar = array_2[2][box_Pos - 9];
            array_2[2][box_Pos - 9] = array_1[2][box_Pos - 9];
            if(chance == 1)
            {
                *prevI = 2;
                *prevJ = box_Pos - 9;
            }
            if(chance == 2 && tempVar == -37)
            {
                if(array_2[*prevI][*prevJ] == array_2[2][box_Pos - 9])
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    *prevI = -1;
                    *prevJ = -1;
                    Beep(1000, 700);
                }
                else
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    array_2[2][box_Pos - 9] = 219;
                    array_2[*prevI][*prevJ] = 219;
                    Sleep(500);
                }
                chance = 0;
            }
            else if(chance == 2)
            {
                chance = 0;
                array_2[*prevI][*prevJ] = 219;
            }
        }
    }
    else
    {
        chance = 0;
    }
    if(tempVar == -37 || chance == 1)
    {
        if(box_Pos >= 13 && box_Pos <= 16)
        {
            tempVar = array_2[3][box_Pos - 13];
            array_2[3][box_Pos - 13] = array_1[3][box_Pos - 13];
            if(chance == 1)
            {
                *prevI = 3;
                *prevJ = box_Pos - 13;
            }
            if(chance == 2 && tempVar == -37)
            {
                if(array_2[*prevI][*prevJ] == array_2[3][box_Pos - 13])
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    *prevI = -1;
                    *prevJ = -1;
                    Beep(1000, 700);
                }
                else
                {
                    printThePairs(array_2, array_1,  box_Pos);
                    array_2[3][box_Pos - 13] = 219;
                    array_2[*prevI][*prevJ] = 219;
                    Sleep(500);
                }
                chance = 0;
            }
            else if(chance == 2)
            {
                chance = 0;
                array_2[*prevI][*prevJ] = 219;
            }
        }
    }
    else
    {
        chance = 0;
    }
    if(printThePairs(array_2, array_1,  box_Pos))
    {
        return 1;
    }
    return 0;
}


// Find the pair.
int findThePairs()
{
    char array1[4][4]; // This array contains the pairs.
    char array2[4][4]; // This array contains blocks(█) which hide the pairs.
    int i, j, i1 = 0, j1 = 0, k, ch, boxPos = 1,as;
    int *prev_i, *prev_j; // Using pointers for storing position of previous letter.


    // Assigning blocks(█) to array2.
    for(i = 0; i < 4; i++)
    {
        for(j = 0; j < 4; j++)
        {
            array2[i][j] = 219;
        }
    }


    //Assigning empty space to array1.
    for(i = 0; i < 4; i++)
    {
        for(j = 0; j < 4; j++)
        {
            array1[i][j] = 0;
        }
    }


    // Assigning pairs to array1.
    k = 0;
    while(k < 16)
    {
        i = rand()%4;
        j = rand()%4;
        if(j1 == 2)
        {
            i1++;
            j1 = 0;
        }
        if(array1[i][j] == 0)
        {
            array1[i][j] = 65 + i1; // Assigning pairs.
            j1++;
            k++;
        }
    }

    // pointers to store position of first of the pair.
    prev_i = &i1;
    prev_j = &j1;
    *prev_i = -1;
    *prev_j = -1;

    printThePairs(array1, array1, -1);
    Sleep(1500);
    while(1)
    {
        printThePairs(array2, array1, boxPos);
        ch = _getch();
        if(ch == 13)
        {
            if(revealThePair(array2, array1, boxPos, prev_i, prev_j))
            {
                Sleep(2500);
                return 0;
            }
        }
        if(ch == 27)
        {
            return 0;
        }
        if(ch == 224)
        {
            switch(_getch())
            {

                // Moving box up.
                case 72 :
                    if(boxPos >=1 && boxPos <= 4)
                    {
                    }
                    else
                    {
                        boxPos -= 4;
                    }
                break;


                // Moving box left.
                case 75 :
                    if(boxPos == 1
                       || boxPos == 5
                       || boxPos == 9
                       || boxPos == 13)
                    {
                    }
                    else
                    {
                        boxPos -= 1;
                    }
                break;


                // Moving box down.
                case 80 :
                    if(boxPos >=13 && boxPos <= 16)
                    {
                    }
                    else
                    {
                        boxPos += 4;
                    }
                break;


                // Moving box right.
                case 77 :
                    if(boxPos == 4
                       || boxPos == 8
                       || boxPos == 12
                       || boxPos == 16)
                    {
                    }
                    else
                    {
                        boxPos += 1;
                    }
                break;
            }
        }
    }

    return 0;
}


/* Minesweeper */
// This function prints the array of minesweeper.
int printMinesweeper(char Array2[4][4], char Array1[4][4], int posOfBox)
{
    int i = 0, j, k = 0, ch = 0;
    system("cls");
    printf("\n\n\n");


    while(i < 4)
    {

        // Printing the first line.
        if(posOfBox >=1 && posOfBox <=4)
        {
            printf("   ");
            for(k = 0; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
              }
            printf("\n");
            printf("   ");
            for(k = 0; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
            }
            printf("\n");
        }
        i++;


        // Printing the second line.
        if(posOfBox >=5 && posOfBox <=8)
        {
            printf("   ");
            for(k = 4; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
              }
            printf("\n");
            printf("   ");
            for(k = 4; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
            }
            printf("\n");
        }
        i++;


        // Printing the third line.
        if(posOfBox >=9 && posOfBox <=12)
        {
            printf("   ");
            for(k = 8; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
              }
            printf("\n");
            printf("   ");
            for(k = 8; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
            }
            printf("\n");
        }
        i++;


        // Printing the fourth line.
        if(posOfBox >=13 && posOfBox <=16)
        {
            printf("   ");
            for(k = 12; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c\n", 218, 196, 196, 196, 191); // Printing box.
            printf("        ");
            for(j = 0; j < 4; j++)
              {
                  printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
              }
            printf("\n");
            printf("   ");
            for(k = 12; k < posOfBox; k++)
            {
                printf("     ");
            }
            printf("%c%c%c%c%c", 192, 196, 196, 196, 217); // Printing box.
        }
        else
        {
            printf("\n");
            printf("        ");
            for(j = 0; j < 4; j++)
            {
                printf(" %2c  ", Array2[i][j]); // Printing the block or mine or number.
            }
            printf("\n");
        }
        i++;


        // Checking if won or not.
        for(i = 0; i < 4; i++)
        {
            for(j = 0; j < 4; j++)
            {
                if(Array1[i][j] != Array2[i][j])
                {
                    ch++;
                }
            }
            printf("\n");
        }
        if(ch == 4)
        {
            system("color a0");
            printf("\n Game over You win\n");
            return 1;
        }
        else
        {
            return 0;
        }
    }
}


// This function reveals the the number or mine behind the block in minesweeper.
int revealMinesweeper(char array_2[4][4], char array_1[4][4], int box_Pos)
{
    if(box_Pos >= 1 && box_Pos <= 4)
    {
        array_2[0][box_Pos - 1] = array_1[0][box_Pos - 1];
        if(array_2[0][box_Pos - 1] == 42)
        {
            system("color c0");
            printMinesweeper(array_2, array_1,  box_Pos);
            printf("\nGame over you lose\n");
            Beep(700, 700);
            return 1;
        }
    }
    if(box_Pos >= 5 && box_Pos <= 8)
    {
        array_2[1][box_Pos - 5] = array_1[1][box_Pos - 5];
        if(array_2[1][box_Pos - 5] == 42)
        {
            system("color c0");
            printMinesweeper(array_2, array_1,  box_Pos);
            printf("\nGame over you lose\n");
            Beep(700, 700);
            return 1;
        }
    }
    if(box_Pos >= 9 && box_Pos <= 12)
    {
        array_2[2][box_Pos - 9] = array_1[2][box_Pos - 9];
        if(array_2[2][box_Pos - 9] == 42)
        {
            system("color c0");
            printMinesweeper(array_2, array_1,  box_Pos);
            printf("\nGame over you lose\n");
            Beep(700, 700);
            return 1;
        }
    }
    if(box_Pos >= 13 && box_Pos <= 16)
    {
        array_2[3][box_Pos - 13] = array_1[3][box_Pos - 13];
        if(array_2[3][box_Pos - 13] == 42)
        {
            system("color c0");
            printMinesweeper(array_2, array_1,  box_Pos);
            printf("\nGame over you lose\n");
            Beep(700, 700);
            return 1;
        }
    }
    return 0;
}


// Minesweeper
int minesweeper()
{
    char array1[4][4]; // This array contains numbers and mines(*).
    char array2[4][4]; // This array contains blocks(█) which hide the numbers and mines(*).
    int i, j, k, ch, boxPos = 1;


    // Assigning blocks(█) to array2.
    for(i = 0; i < 4; i++)
    {
        for(j = 0; j < 4; j++)
        {
            array2[i][j] = 219;
        }
    }


    // Assigning numbers and mines to array1.
    k = 0;
    while(k < 4)
    {
        i = rand()%4;
        j = rand()%4;
        if(array1[i][j] != 42)
        {
            array1[i][j] = 42; // Assigning mines.
            k++;
        }
    }
    k = 0;
    while(k < 2)
    {
        i = rand()%4;
        j = rand()%4;
        if(array1[i][j] != 52
           && array1[i][j] != 42)
        {
            array1[i][j] = 52; // Assigning 4.
            k++;
        }
    }
    k = 0;
    while(k < 4)
    {
        i = rand()%4;
        j = rand()%4;
        if(array1[i][j] != 50
           && array1[i][j] != 42
           && array1[i][j] != 52)
        {
            array1[i][j] = 50; // Assigning 2.
            k++;
        }
    }
    k = 0;
    while(k < 6)
    {
        i = rand()%4;
        j = rand()%4;
        if(array1[i][j] != 50
           && array1[i][j] != 42
           && array1[i][j] != 52
           && array1[i][j] != 49)
        {
            array1[i][j] = 49; // Assigning 1.
            k++;
        }
    }
    printMinesweeper(array2, array1, boxPos);
    while(1)
    {
        ch = _getch();
        if(ch == 13)
        {
            Beep(1500, 70);
            if(revealMinesweeper(array2, array1, boxPos))
            {
                label1 :
                if(27 != _getch())
                {
                    goto label1;
                }
                else
                {
                    return 0;
                }
            }
            if(printMinesweeper(array2, array1, boxPos))
            {
                if(27 != _getch())
                {
                    goto label1;
                }
                else
                {
                    return 0;
                }
            }
        }
        if(ch == 27)
        {
            return 0;
        }
        if(ch == 224)
        {
            switch(_getch())
            {

                // Moving box up.
                case 72 :
                    if(boxPos >=1 && boxPos <= 4)
                    {
                    }
                    else
                    {
                        boxPos -= 4;
                    }
                break;


                // Moving box left.
                case 75 :
                    if(boxPos == 1
                       || boxPos == 5
                       || boxPos == 9
                       || boxPos == 13)
                    {
                    }
                    else
                    {
                        boxPos -= 1;
                    }
                break;


                // Moving box down.
                case 80 :
                    if(boxPos >=13 && boxPos <= 16)
                    {
                    }
                    else
                    {
                        boxPos += 4;
                    }
                break;


                // Moving box right.
                case 77 :
                    if(boxPos == 4
                       || boxPos == 8
                       || boxPos == 12
                       || boxPos == 16)
                    {
                    }
                    else
                    {
                        boxPos += 1;
                    }
                break;
            }
            printMinesweeper(array2, array1, boxPos);

        }
    }

    return 0;
}


/* */
// Menu of the main function.
int mainMenu()
{
    int i;
    system("cls");
    printf("\n\n\n\n\n\n\n");
    printf(space "\t\t1. find the pairs\n");
    printf(space "\t\t2. minesweeper\n");
    printf(space "\t\t3. towers of hanoi\n");
    printf(space "\t\t4. number puzzle\n");
    return 0;
}


// Main function.
int main()
{
    int i=0, j, k, level, choice;
    char ch;
    while(1)
    {
        system("color f0");
        mainMenu();
        ch = getche();
        switch(ch)
        {
            case '1' :  findThePairs();
            break;
            case '2' :  minesweeper();
            break;
            case '3' :  towersOfHanoi();
            break;
            case '4' :
                        label:
                        printf("\nlevel 1: easy\n level 2: medium\n level 3:hard\n 4.exit\n");
                        printf(" enter level");
                        fflush(stdin);
                        scanf("%d", &choice);
                        switch(choice)
                        {
                        case 1 :
                                printf(" level 1");
                                level = 3;
                        break;

                        case 2 :
                                printf("level 2");
                                level = 4;
                        break;

                        case 3 :
                                printf(" level 3");
                                level = 5;
                        break;

                        case 4:
                            printf(" exit");
                            return 0;
                        break;

                        default:
                            printf("\nInvalid choice\n");
                            goto label;
                        break;
                        }
                        numberPuzzle(level);
            break;
        }
    }
    return 0;
}
