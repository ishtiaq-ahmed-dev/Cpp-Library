<div align="center">

# Cpp-Library

**Small, self-contained C++ programs that solve everyday problems from the console.**

[![Language](https://img.shields.io/badge/language-C%2B%2B-00599C?style=flat-square&logo=cplusplus&logoColor=white)](https://isocpp.org/)
[![Standard](https://img.shields.io/badge/standard-C%2B%2B98%20and%20later-informational?style=flat-square)](#build)
[![Dependencies](https://img.shields.io/badge/dependencies-standard%20library%20only-brightgreen?style=flat-square)](#build)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey?style=flat-square)](#build)

[Programs](#programs) · [Build](#build) · [Usage](#usage) · [Project layout](#project-layout) · [Author](#author)

</div>

---

A growing set of C++ console programs, each one a single source file in its own folder. They take input from the keyboard, do the arithmetic, and print the result. Nothing outside the standard library is used, so any C++ compiler will build them.

## Programs

| Program | What it does | Source |
|---|---|---|
| Age Calculator | Takes today's date and a birth date, checks both are valid, and prints the exact age in years, months and days, followed by the total in days, weeks, months, hours, minutes and seconds. Handles leap years. | [`Age Calculator/age_calculator.cpp`](Age%20Calculator/age_calculator.cpp) |
| British Coin System | Converts pre-decimal British money (pounds, shillings, pence) into decimal pounds, using 1 pound = 20 shillings = 240 pence. Prints the result to two decimal places with a `£` sign. | [`British Coin System/code.cpp`](British%20Coin%20System/code.cpp) |

Each folder also has its own README with a short write-up of the program.

## How they work

**Age Calculator.** Two helpers do the calendar work: `isLeap(year)` applies the Gregorian rule (divisible by 4, except centuries not divisible by 400), and `monthDays(month, year)` returns 28 to 31 days, or 0 for an invalid month. The program rejects out-of-range months and days and birth dates in the future. When the day difference goes negative it borrows the length of the previous month, and when the month difference goes negative it borrows a year.

**British Coin System.** One formula: `pounds + shillings / 20 + pence / 240`. The inputs are `double`, so fractional amounts such as half-pennies work. Output goes through `std::fixed` and `std::setprecision(2)` from `<iomanip>`.

## Build

You need a C++ compiler: g++, clang++ or MSVC. There are no build files; each program is one `.cpp` file. The folder names contain spaces, so keep the quotes.

**g++ or clang++ (Linux, macOS, MinGW on Windows)**

```bash
g++ -Wall -o age_calculator "Age Calculator/age_calculator.cpp"
g++ -Wall -o british_coins "British Coin System/code.cpp"
```

**MSVC (Developer Command Prompt)**

```bat
cl /EHsc /Fe:age_calculator.exe "Age Calculator\age_calculator.cpp"
cl /EHsc /Fe:british_coins.exe "British Coin System\code.cpp"
```

## Usage

Run the binary and answer the prompts.

```text
$ ./age_calculator
Enter current year: 2025
Enter current month: 10
Enter current day: 9
Enter your birth year: 2000
Enter your birth month: 4
Enter your birth day: 15

You are 25 years, 5 months, and 24 days old.
```

The totals in other units are printed after that line.

```text
$ ./british_coins
Enter pounds: 2
Enter shillings: 15
Enter pence: 0

Total in decimal pounds: £2.75
```

The `£` sign is written as UTF-8. On the Windows console, run `chcp 65001` first if it shows up as garbled characters.

## Project layout

```text
Cpp-Library/
├── Age Calculator/
│   ├── README.md
│   └── age_calculator.cpp
├── British Coin System/
│   ├── README.md
│   └── code.cpp
└── README.md
```

## License

There is no license file in this repository yet, so the default applies: the code is visible on GitHub, but reuse needs the author's permission.

## Author

**Ishtiaq Ahmed**<br>
AI student, C++ and Python developer, data structures and problem-solving enthusiast.<br>
GitHub: [@ishtiaq-ahmed-dev](https://github.com/ishtiaq-ahmed-dev)
