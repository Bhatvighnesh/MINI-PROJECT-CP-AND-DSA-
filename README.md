#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    int num_numbers, num_letters, num_symbols;
    printf("how many numbers do you want in a password: ");
    scanf("%d", &num_numbers);
    printf("how many  letters do you want in password: ");
    scanf("%d", &num_letters);
    printf("how many symbols do you want in a password: ");
    scanf("%d", &num_symbols);

    srand(time(0));

    char numbers[] = "0123456789";
    char letters[] = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
    char symbols[] = "!@#$%^&*()_-+=<>?";
    

    int total_length = num_numbers + num_letters + num_symbols;
    char password[total_length + 1];
    password[total_length] = '\0';
    
    

    for (int i = 0; i < num_numbers; i++) {
        password[i] = numbers[rand() % (sizeof(numbers) - 1)];
    }
    for (int i = 0; i < num_letters; i++) {
        password[num_numbers + i] = letters[rand() % (sizeof(letters) - 1)];
        
    }
    for (int i = 0; i < num_symbols; i++) {
        password[num_numbers + num_letters + i] = symbols[rand() % (sizeof(symbols) - 1)];
    }

    for (int i = total_length - 1; i > 0; i--) {
        int j = rand() % (i + 1);
        char temp = password[i];
        password[i] = password[j];
        password[j] = temp;
    }

    printf("This is your password as per your  requirments: %s\n", password);

    return ;
}
