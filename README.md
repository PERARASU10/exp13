# Message Authentication Code (MAC)

This project implements the Message Authentication Code (MAC) algorithm using XOR encryption. It is a simple implementation to demonstrate the concept of encrypting and decrypting a message with a symmetric key.

## Aim
To write a program to implement Message Authentication Code (MAC).

## Algorithm
1. Input the plaintext message and symmetric key.
2. Input the MAC value.
3. Perform XOR encryption.
4. Display the encrypted message.
5. Perform XOR decryption.
6. Display the decrypted message.

## Author
Name: PERARASU M
Registration Number: 212222100033

##Program:

```
#include <stdio.h>
#include <string.h>

#define MAX_LEN 256  // Maximum length of the message

// Function to perform XOR encryption
void encrypt(const char *input, const char *key, char *output) {
    int len = strlen(input);
    int key_len = strlen(key);
    for (int i = 0; i < len; i++) {
        output[i] = input[i] ^ key[i % key_len];  // XOR operation
    }
    output[len] = '\0';  // Null-terminate the output string
}

// Function to perform XOR decryption
void decrypt(const char *input, const char *key, char *output, int len) {
    int key_len = strlen(key);
    for (int i = 0; i < len; i++) {
        output[i] = input[i] ^ key[i % key_len];  // XOR operation
    }
    output[len] = '\0';  // Null-terminate the output string
}

int main() {
    char message[MAX_LEN];      // Plaintext message
    char key[MAX_LEN];          // Symmetric key
    char input_mac[3];          // MAC input from the user
    char encrypted[MAX_LEN];    // Encrypted message
    char decrypted[MAX_LEN];    // Decrypted message

    printf("\n          **Simulation of MAC Algorithm**\n\n");

    // Get plaintext message from the user
    printf("Enter the plaintext message: ");
    fgets(message, MAX_LEN, stdin);
    message[strcspn(message, "\n")] = 0;  // Remove newline character

    // Get symmetric key from the user
    printf("Enter the symmetric key: ");
    fgets(key, MAX_LEN, stdin);
    key[strcspn(key, "\n")] = 0;  // Remove newline character

    // Get MAC value from the user
    printf("Enter the MAC value (in hex format): ");
    scanf("%2s", input_mac);  // Read the MAC input from the user

    // Perform encryption
    encrypt(message, key, encrypted);
    int encrypted_length = strlen(message);

    printf("Encrypted message (raw bytes): ");
    for (int i = 0; i < encrypted_length; i++) {
        printf("%02x ", (unsigned char)encrypted[i]);
    }
    printf("\n");

    // Perform decryption
    decrypt(encrypted, key, decrypted, encrypted_length);  // Pass the length of the encrypted message
    printf("Decrypted message: %s\n", decrypted);

    return 0;
}

```

## Output: 

![image](https://github.com/user-attachments/assets/1a84bd32-fc3c-49a6-942a-b374b389c7d5)

## Result:
 This program is verified and executed.
