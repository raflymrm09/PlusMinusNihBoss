# PlusMinus
Nama : Moch Rafli Muchibbin <br>
Nim : 23422029 <br>
Kelas : TIF22A

# Tugas Metode Numerik
Menyelesaikan problem pada HackerRank tentang plus minus(https://www.hackerrank.com/challenges/plus-minus/problem) dengan cetak rasio dari nilai-nilai positif, negatif, dan nol dalam array. Setiap nilai harus dicetak pada baris terpisah dengan 6 angka di belakang desimal. Fungsi tidak boleh mengembalikan nilai.

# Penyelesaian
Berikut adalah penyelesaian dari tugas tersebut dalam bahasa pemrograman C++
```C++
#include <bits/stdc++.h>

using namespace std;

string ltrim(const string &);
string rtrim(const string &);
vector<string> split(const string &);

/*
 * Complete the 'plusMinus' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

void plusMinus(vector<int> arr) {
    // Initialize variables to count positive, negative, and zero elements
    float p = 0, n = 0, z = 0;

    // Iterate through the array and count positive, negative, and zero elements
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] < 0) {
            n += 1;
        } else if (arr[i] > 0) {
            p += 1;
        } else if (arr[i] == 0) {
            z += 1;
        }
    }

    // Calculate the ratios of positive, negative, and zero elements
    float s = arr.size(); // Total number of elements
    float pos, neg, zer;
    pos = p / s;
    neg = n / s;
    zer = z / s;

    // Print the ratios with a precision of 6 decimal places
    cout << pos << setprecision(6) << "\n" << neg << setprecision(6) << "\n" << zer << setprecision(6) << "\n";
}

int main() {
    // Read the input for the size of the array
    string n_temp;
    getline(cin, n_temp);
    int n = stoi(ltrim(rtrim(n_temp)));

    // Read the array elements
    string arr_temp_temp;
    getline(cin, arr_temp_temp);
    vector<string> arr_temp = split(rtrim(arr_temp_temp));

    // Convert array elements to integers
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        int arr_item = stoi(arr_temp[i]);
        arr[i] = arr_item;
    }

    // Call the plusMinus function with the input array
    plusMinus(arr);

    return 0;
}

// Utility functions for trimming whitespace from the beginning and end of a string

string ltrim(const string &str) {
    string s(str);
    s.erase(
        s.begin(),
        find_if(s.begin(), s.end(), not1(ptr_fun<int, int>(isspace)))
    );
    return s;
}

string rtrim(const string &str) {
    string s(str);
    s.erase(
        find_if(s.rbegin(), s.rend(), not1(ptr_fun<int, int>(isspace))).base(),
        s.end()
    );
    return s;
}

// Utility function for splitting a string into a vector of strings

vector<string> split(const string &str) {
    vector<string> tokens;
    string::size_type start = 0;
    string::size_type end = 0;

    // Split the string at spaces
    while ((end = str.find(" ", start)) != string::npos) {
        tokens.push_back(str.substr(start, end - start));
        start = end + 1;
    }

    // Add the last token
    tokens.push_back(str.substr(start));
    return tokens;
}
```
