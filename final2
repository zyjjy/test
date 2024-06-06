#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <time.h>

#define WIDTH 80
#define HEIGHT 24

void clear_screen() {
    printf("\033[H\033[J");
}

void move_cursor(int x, int y) {
    printf("\033[%d;%dH", y, x);
}

void set_color(int color) {
    printf("\033[1;%dm", color);
}

char random_char() {
    const char charset[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
    return charset[rand() % (sizeof(charset) - 1)];
}

int main() {
    srand(time(NULL));
    char screen[HEIGHT][WIDTH + 1];
    int i, j;

    
    for (i = 0; i < HEIGHT; i++) {
        for (j = 0; j < WIDTH; j++) {
            screen[i][j] = ' ';
        }
        screen[i][WIDTH] = '\0';
    }

    clear_screen();


    while (1) {
        for (i = HEIGHT - 1; i > 0; i--) {
            for (j = 0; j < WIDTH; j++) {
                screen[i][j] = screen[i - 1][j];
            }
        }

        
        for (j = 0; j < WIDTH; j++) {
            if (rand() % 4 == 0) {
                screen[0][j] = random_char();
            } else {
                screen[0][j] = ' ';
            }
        }

       
        set_color(32); 
        for (i = 0; i < HEIGHT; i++) {
            move_cursor(0, i + 1);
            printf("%s\n", screen[i]);
        }

        usleep(100000); 
    }

    return 0;
}
