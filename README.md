# input
The C++ input function allows you to declare variables and initialize them values loaded from cin or a file stream.

```c++
#include "input"
#include <iostream>
#include <fstream>

int main() {
  std::cin.exceptions(std::ios_base::badbit | std::ios_base::failbit);
  try {

    auto n=input<int>(); // input one integer
    auto [x,y]=input<double,double>(); // pair<double,double>
    auto v=input<double>(n); // vector<double>(n)
    auto t=input<int,char,double>(); // tuple<int,char,double>

  } catch(const std::ios_base::failure& e) {
    std::cerr << "Input error: " << e.what() << std::endl;
    std::cin.clear();
    std::cin.ignore(256, '\n');
  }
  
  std::ifstream fs("input.txt");
  // file contains
  // 5
  // 10 20 30 40 50
  auto m=input<int>(fs); // m=5
  auto a=input<int>(fs,m); // a={10,20,30,40,50}
}
```