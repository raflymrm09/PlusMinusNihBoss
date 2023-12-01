# PlusMinus
Nama : Moch Rafli Muchibbin <br>
Nim : 23422029 <br>
Kelas : TIF22A

# Tugas Metode Numerik
Menyelesaikan problem pada HackerRank tentang plus minus(https://www.hackerrank.com/challenges/plus-minus/problem) dengan cetak rasio dari nilai-nilai positif, negatif, dan nol dalam array. Setiap nilai harus dicetak pada baris terpisah dengan 6 angka di belakang desimal. Fungsi tidak boleh mengembalikan nilai.

# Penyelesaian
Berikut adalah penyelesaian dari tugas tersebut dalam bahasa pemrograman C++
```C++

'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'plusMinus' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function plusMinus(arr) {
    // Write your code here
     let positives = 0, negatives = 0, zeros = 0;
     const len = arr.length || 0;
      
     if (len > 0 && len <= 100) {
          arr.map((elem, key) => {
               if (elem > 0) {
                    positives++;
               } else if (elem < 0) {
                    negatives++; 
               } else {
                    zeros++;
               }
                  
               return elem; 
          }); 
     } 
     
     console.log((positives / len) || 0);
     console.log((negatives / len) || 0);
     console.log((zeros / len) || 0);      
}



function main() {
    const n = parseInt(readLine().trim(), 10);

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    plusMinus(arr);
}
