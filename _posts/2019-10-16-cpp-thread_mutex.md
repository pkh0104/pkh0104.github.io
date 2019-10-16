---
title: "C++11 thread, mutex"
date: 2019-10-16 22:40:00 -0400
categories: c++11 thread mutex
---

```cpp
#include <iostream>
#include <thread>
#include <mutex>
#include <map>

bool stop = false;
std::mutex mtx;

void PrintCallback(int id, int& value) {
    while (true) {
        mtx.lock(); 
        std::cout << "Thread No." << id << " : " << value << std::endl;
        if (stop) {
            mtx.unlock();
            break;
        } else {
            mtx.unlock();
        }
        std::this_thread::sleep_for(std::chrono::seconds(1));
    }
}

void InputCallback(int id, int& value) {
    while (true) {
        char c = 0; 
        std::cin >> c;
        std::lock_guard<std::mutex> lg(mtx); // lg 객체가 소멸되면 unlock.
        value = static_cast<int>(c);
        std::cout << "Thread No." << id << " : " << value << " is set." << std::endl;
        if (c == 'q') {
            stop = true;
            break;
        }
    }
}  
   
int main() {
    int value = 0;
    std::thread input_thread(InputCallback, 0, std::ref(value));
    std::thread print_thread(PrintCallback, 1, std::ref(value));
   
    input_thread.join();
    print_thread.join();
   
    return 0;
}
```
Thread 사용 방법 추가  
