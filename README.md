# pat2-subtask1-

#include <iostream>
#include <string>
#include <cctype>

using namespace std;

int main() {
    // Standard dot and dash characters (ASCII 46 for '.' and ASCII 45 for '-')
    char dot = 46;  
    char dash = 45; 

    // Array representing English letters A through Z
    char letters[] = {
        'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M',
        'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'
    };

    // Parallel array holding the Morse code equivalents
    string morse[] = {
        ".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---", "-.-", ".-..", "--",
        "-.", "---", ".--.", "--.-", ".-.", "...", "-", "..-", "...-", ".--", "-..-", "-.--", "--.."
    };

    string inputMessage;
    cout << "Enter a message in English (A-Z characters only): ";
    getline(cin, inputMessage);

    string fullMorseMessage = "";

    // Loop through each character of the input message
    for (size_t i = 0; i < inputMessage.length(); i++) {
        char ch = inputMessage[i];

        // Requirement: Handle spaces between words
        if (ch == ' ') {
            fullMorseMessage += "   "; 
            continue;
        }

        // Requirement: Ignore numbers and non-alphanumeric characters
        if (!isalpha(ch)) {
            continue; 
        }

        // Requirement: Convert any lowercase letters to uppercase
        ch = toupper(ch);

        // Find the character in the letters array
        for (int j = 0; j < 26; j++) {
            if (ch == letters[j]) {
                string currentMorse = morse[j];

                // Print individual breakdown format: "Letter: Morse"
                cout << ch << ": " << currentMorse << endl;

                // Add to the consolidated single line message
                fullMorseMessage += currentMorse;

                // Requirement: Separate individual letters by three spaces
                // Peek ahead to see if we should add spacing
                if (i < inputMessage.length() - 1 && inputMessage[i + 1] != ' ') {
                    fullMorseMessage += "   ";
                }
                break;
            }
        }
    }

    // Print the final aggregated Morse code output line
    cout << "\nFull Morse code with spaces:\n" << fullMorseMessage << endl;

    return 0;
}
