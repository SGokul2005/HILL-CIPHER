## EX.3 HILL CIPHER
## Name: GOKUL S
## Reg.no: 21223040051
Hill Cipher
Hill Cipher using with different key values.
# AIM:
To develop a simple C program to implement Hill Cipher.
# DESIGN STEPS:
Step 1:
Design of Hill Cipher algorithnm
Step 2:
Implementation using C or pyhton code
Step 3:
Testing algorithm with different key values. ALGORITHM DESCRIPTION: The Hill cipher is a
substitution cipher invented by Lester S. Hill in 1929. Each letter is represented by a number modulo 26. To
encrypt a message, each block of n letters is multiplied by an invertible n × n matrix, again modulus 26. To
decrypt the message, each block is multiplied by the inverse of the matrix used for encryption. The matrix
used for encryption is the cipher key, and it should be chosen randomly from the set of invertible n × n
matrices (modulo 26). The cipher can, be adapted to an alphabet with any number of letters. All arithmetic
just needs to be done modulo the number of letters instead of modulo 26.
## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#define MOD 26
int key[3][3], invKey[3][3];
// Function to multiply the matrix for encryption/decryption
void hillCipher(char message[], int matrix[3][3]) {
char result[100];
int len = strlen(message);
// Padding if needed
while (len % 3 != 0) {
message[len++] = 'X';
message[len] = '\0';
}
for (int i = 0; i < len; i += 3) {
int x = (matrix[0][0] * (message[i] - 'A') + matrix[0][1] * (message[i + 1] - 'A') + matrix[0][2] *
(message[i + 2] - 'A')) % MOD;
int y = (matrix[1][0] * (message[i] - 'A') + matrix[1][1] * (message[i + 1] - 'A') + matrix[1][2] *
(message[i + 2] - 'A')) % MOD;
int z = (matrix[2][0] * (message[i] - 'A') + matrix[2][1] * (message[i + 1] - 'A') + matrix[2][2] *
(message[i + 2] - 'A')) % MOD;
result[i] = (x + 'A');
result[i + 1] = (y + 'A');
result[i + 2] = (z + 'A');
}
result[len] = '\0';
printf("%s\n", result);
}
int main() {
char message[100];
// Get key matrix
printf("Enter 3x3 key matrix:\n");
for (int i = 0; i < 3; i++)
for (int j = 0; j < 3; j++)
scanf("%d", &key[i][j]);
// Get inverse key matrix
printf("Enter 3x3 inverse key matrix:\n");
for (int i = 0; i < 3; i++)
for (int j = 0; j < 3; j++)
scanf("%d", &invKey[i][j]);
// Get message input
printf("Enter message (uppercase only, no spaces): ");
scanf("%s", message);
printf("Encrypted message: ");
hillCipher(message, key);
printf("Decrypted message: ");
hillCipher(message, invKey);
return 0;
}
```
# OUTPUT:
![image](https://github.com/user-attachments/assets/a1c7da68-6de7-425f-b17e-6e169cf1c006)

Simulating Hill Cipher
Encrypted Message: PJP
Decrypted Message: CAR
## RESULT:
The program is executed successfully.
