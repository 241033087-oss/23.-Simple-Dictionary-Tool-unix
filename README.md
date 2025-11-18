SIMPLE DICTIONARY TOOL


nano dictionary.txt

linux: an open-source operating system kernel
hello: a greeting
tcp: transmission control protocol
cpu: central processing unit


nano dict.cpp

#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main() {
    string word, line;
    cout << "Enter word: ";
    cin >> word;

    ifstream file("dictionary.txt");
    if (!file) {
        cout << "Dictionary file not found.\n";
        return 1;
    }

    bool found = false;
    while (getline(file, line)) {
        if (line.rfind(word + ":", 0) == 0) {   // starts with "word:"
            cout << "Meaning -> " << line.substr(word.length() + 1) << "\n";
            found = true;
            break;
        }
    }

    if (!found) cout << "Word not found.\n";

    return 0;
}


g++ dict.cpp -o dict

./dict
