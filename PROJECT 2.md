
# CODSOFT project 2
---

This is a code for making TO-DO-LIST using C++ Language
---
```C++
#include<bits/stdc++.h>
using namespace std;

class todolist {
    vector<string> tasks;
    vector<string> completed_tasks;

public:
    // to add tasks
    void addtask(string task) {
        tasks.push_back(task);
    }

    // to remove tasks
    void removetask(int number) {
        if (number > 0 && number <= tasks.size()) {
            tasks.erase(tasks.begin() + number - 1);
            cout << "Task removed!" << endl;
        } else if (number > tasks.size() && number <= tasks.size() + completed_tasks.size()) {
            completed_tasks.erase(completed_tasks.begin() + (number - tasks.size()) - 1);
            cout << "Task removed!" << endl;
        } else {
            cout << "Invalid task number." << endl;
        }
    }

    // mark task as completed
    void marktask(int number) {
        if (number > 0 && number <= tasks.size()) {
            completed_tasks.push_back(tasks[number - 1]);
            cout << "Marked task as completed: " << tasks[number - 1] << endl;
            tasks.erase(tasks.begin() + number - 1);
        } else {
            cout << "Invalid task number." << endl;
        }
    }

    // display tasks
    void printtask() {
        cout << "Pending tasks:" << endl;
        for (int i = 0; i < tasks.size(); i++) {
            cout << i + 1 << ". " << tasks[i] << endl;
        }
        cout << "Completed tasks:" << endl;
        for (int i = 0; i < completed_tasks.size(); i++) {
            cout << i + 1 + tasks.size() << ". " << completed_tasks[i] << " (Completed)" << endl;
        }
    }
};

int counter = 1;

void taskadding(todolist &list) {
    cout << "Task : " << counter << endl;
    counter++;
    string name;
    cout << "Task is: ";
    cin >> name;
    list.addtask(name);
}

void taskremoving(todolist &list) {
    int num;
    list.printtask();
    cout << endl;
    cout << "Remove task number: ";
    cin >> num;
    list.removetask(num);
    if (num > 0 && num <= counter - 1) {
        counter--;
    }
    cout << endl;
}

void markingtask(todolist &list) {
    int x;
    list.printtask();
    cout << endl;
    cout << "Mark for Completion: ";
    cin >> x;
    list.marktask(x);
    cout << endl;
}

void starting(todolist &list) {
    int x;
    cout << "Welcome to your TO-Do list" << endl;
    cout << "1. Add task" << endl;
    cout << "2. Delete task" << endl;
    cout << "3. Mark tasks" << endl;
    cout << "4. View tasks" << endl;
    cout << "5. Exit to do list" << endl;
    cout << "Enter choice: ";
    cin >> x;
    cout << endl;

    if (x == 1) {
        taskadding(list);
        cout << endl;
        starting(list);
        cout << endl;
    } else if (x == 2) {
        taskremoving(list);
        cout << endl;
        starting(list);
        cout << endl;
    } else if (x == 3) {
        markingtask(list);
        cout << endl;
        starting(list);
        cout << endl;
    } else if (x == 4) {
        list.printtask();
        cout << endl;
        starting(list);
        cout << endl;
    } else if(x==5){
        cout<<"Thank You !"<<endl;
        return;
    }
}

void makinglist() {
    todolist list;
    starting(list);
    return;
}

int main() {
    makinglist();
    return 0;
}
```
---



## Authors

 [@chitrangv27](https://github.com/chitrangv27)

