This program reads a full sentence (including spaces), then counts words by detecting transitions between spaces and non-space characters.
```c
#include <stdio.h>
#include <ctype.h>

int main() {
    char sentence[1000];
    int i = 0, words = 0, inWord = 0;
    printf("Enter a sentence: ");
    fgets(sentence, sizeof(sentence), stdin);

    while (sentence[i] != '\0') {
        if (isspace(sentence[i])) {
            if (inWord) {
                words++;
                inWord = 0;
            }
        } else {
            inWord = 1;
        }
        i++;
    }
    if (inWord) words++;
    printf("Number of words: %d\n", words);
    return 0;
}
