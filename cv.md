# Anita Balasanyan

## Contact Information
- **Phone:** +995 579 50 33 22
- **LinkedIn:** [Anita Balasanian](https://www.linkedin.com/in/anita-balasanyan-3b61b0251/)
- **Gmail:** [balasanyananita@gmail.com](mailto:balasanyananita@gmail.com)
- **GitHub:** [AnitaA19](https://github.com/AnitaA19)

## Summary
I’m a motivated Junior Developer with a foundation in web development and a quick learning mindset. Currently studying at Tbilisi State University, I’ve gained skills in HTML, CSS, JavaScript, and I am diving into React and Node.js. My three-month internship in Spain strengthened my adaptability and problem-solving abilities, and I’m eager to keep growing. I thrive in dynamic, collaborative environments, where I can both contribute and learn. I’m passionate about creating impactful digital experiences and am ready to bring my skills and curiosity to a team that values innovation and continuous growth.

## Skills
- [ ] HTML/CSS
- [ ] JavaScript
- [ ] React(Currently learning)
- [ ] PHP
- [ ] MySQL
- [ ] C++ (Algorithms, Data Structures)
- [ ] Git/GitHub
- [ ] Bitbucket/Sourcetree

## Code Examples

### To-Do List (JavaScript)
```
const addTaskContainer = document.querySelector('.add-task'); 
const addTaskFormContainer = document.querySelector('.add-task-form');
const taskInput = document.querySelector('.task-input');
const addTaskBtn = document.querySelector('.add-task-button');
const toDoList = document.querySelector('.tasks-list');
const emptyList = document.querySelector('.empty-list');
const scoreElement = document.querySelector('.score');
const themeToggleButton = document.querySelector('.theme-toggle-button'); 
const deleteAllButton = document.querySelector('.delete-all-button'); 

let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
let editingTaskId = null; 

function saveTasks() {
    localStorage.setItem('tasks', JSON.stringify(tasks));
}

function renderTasks() {
    toDoList.innerHTML = '';
    tasks.forEach(task => {
        let html = `
        <li class="task-list-item ${task.done ? 'done' : ''}" data-id="${task.id}">
            <div class="task-content">
                <p class="task-text">${task.text}</p>
            </div>
            <div class="buttons">
                <button class="edit-button">
                    <ion-icon class="edit-btn" name="pencil-outline"></ion-icon>
                </button>
                <button class="delete-button">
                    <ion-icon class="delete-btn" name="trash-outline"></ion-icon>
                </button>
                <button class="done-button">
                    <ion-icon class="done-btn" name="checkmark-outline"></ion-icon>
                </button>
            </div>
        </li>`;    
        toDoList.insertAdjacentHTML('beforeend', html);
    });

    if (toDoList.children.length > 0) {
        toDoList.parentElement.classList.remove('hidden');
        emptyList.classList.add('hidden');
    } else {
        toDoList.parentElement.classList.add('hidden');
        emptyList.classList.remove('hidden');
    }

    scoreElement.textContent = `To Do - ${tasks.length}`;
}

function updateButtonLabel() {
    if (editingTaskId) {
        addTaskBtn.textContent = 'Edit Task';
    } else {
        addTaskBtn.textContent = 'Add Task';
    }
}

function applyTheme(theme) {
    document.body.classList.remove('light-theme', 'dark-theme');
    document.body.classList.add(theme);
    localStorage.setItem('theme', theme);
}

function loadTheme() {
    const savedTheme = localStorage.getItem('theme') || 'light-theme';
    applyTheme(savedTheme);
}

document.addEventListener('DOMContentLoaded', function() {
    loadTheme();
    renderTasks();
    updateButtonLabel(); 
});

addTaskContainer.addEventListener('click', function() {
    addTaskContainer.classList.add('hidden');
    addTaskFormContainer.classList.remove('hidden');
    taskInput.value = ''; 
    editingTaskId = null; 
    updateButtonLabel(); 
});

addTaskBtn.addEventListener('click', function(e) {
    e.preventDefault();
    const taskValue = taskInput.value.trim();
    
    if (taskValue === '') return;

    if (editingTaskId) {
        tasks = tasks.map(task => 
            task.id === editingTaskId ? { ...task, text: taskValue } : task
        );
        editingTaskId = null; 
    } else {
        const newTask = {
            id: Date.now(), 
            text: taskValue,
            done: false
        };
        tasks.push(newTask);
    }

    saveTasks();
    renderTasks();
    addTaskContainer.classList.remove('hidden');
    addTaskFormContainer.classList.add('hidden');
    updateButtonLabel(); 
});

toDoList.addEventListener('click', function(e) {
    const target = e.target.closest('button');
    if (!target) return;

    const listItem = target.closest('.task-list-item');
    const itemId = listItem.dataset.id;

    if (target.classList.contains('edit-button')) {
        const taskText = tasks.find(task => task.id == itemId).text;
        taskInput.value = taskText;
        addTaskContainer.classList.add('hidden');
        addTaskFormContainer.classList.remove('hidden');
        editingTaskId = Number(itemId); 
        updateButtonLabel(); 
    } else if (target.classList.contains('delete-button')) {
        tasks = tasks.filter(task => task.id != itemId);
        saveTasks();
        renderTasks();
    } else if (target.classList.contains('done-button')) {
        tasks = tasks.filter(task => task.id != itemId);
        saveTasks();
        renderTasks();
    }
});

deleteAllButton.addEventListener('click', function() {
    if (confirm('Are you sure you want to delete all tasks?')) {
        tasks = [];
        saveTasks();
        taskInput.value = ''; 
        renderTasks();
    }
});

themeToggleButton.addEventListener('click', function() {
    const currentTheme = document.body.classList.contains('light-theme') ? 'light-theme' : 'dark-theme';
    const newTheme = currentTheme === 'light-theme' ? 'dark-theme' : 'light-theme';
    applyTheme(newTheme);
});
```

### C++ Code example. Task from University

```
#include <iostream>
#include <string>

using namespace std;

void encode(string* phrase, int* shift) {                          
    for (char* letter = &(*phrase)[0]; *letter != '\0'; ++letter) {   
        if ((*letter >= 'a' && *letter <= 'z') || (*letter >= 'A' && *letter <= 'Z')) {  
            char* base = new char;
            if (*letter >= 'a' && *letter <= 'z') {                      
                *base = 'a';
            }
            else if (*letter >= 'A' && *letter <= 'Z') {
                *base = 'A';
            }
            //(*letter - *base + *shift) 
            *letter = ((*letter - *base + *shift) % 26 + 26) % 26 + *base;
            delete base;          
        }
    }
}

void decode(string* phrase, int* shift) {   
    for (char* letter = &(*phrase)[0]; *letter != '\0'; ++letter) {
        if ((*letter >= 'a' && *letter <= 'z') || (*letter >= 'A' && *letter <= 'Z')) {
            char* base = new char;
            if (*letter >= 'a' && *letter <= 'z') {
                *base = 'a';
            }
            else if (*letter >= 'A' && *letter <= 'Z') {
                *base = 'A';
            }
            *letter = ((*letter - *base - *shift) % 26 + 26) % 26 + *base;
            delete base;
        }
    }
}

int main() {
    int* choice = new int;
    int* shift = new int;
    string* phrase = new string;

    while (true) {   
        cout << "Enter a passphrase (q to quit): ";
        getline(cin, *phrase);  
        if (phrase->empty()) {
            cout << "Please enter a passphrase!" << endl;
            continue;
        }

        if (*phrase == "q") {         
            cout << "EXITING. BYE, HONEY!" << endl;
            break;
        }

        cout << "Select an operation :" << endl;
        cout << "1. Encode" << endl;
        cout << "2. Decode" << endl;

        cout << "Enter your choice (1/2): ";

        while (!(cin >> *choice) || (*choice != 1 && *choice != 2)) {   
            cout << "Invalid choice. Please enter 1 or 2." << endl;
            cin.clear();
            cin.ignore(1000, '\n');
        }

        cout << "Enter a shift: ";

        while (!(cin >> *shift)) {
            cout << "Error, the shift input should be an integer!" << endl;
            cin.clear();
            cin.ignore(1000, '\n');
        }

        switch (*choice) {
        case 1:
            encode(phrase, shift);
            cout << "Encoded passphrase: " << *phrase << endl;
            break;
        case 2:
            decode(phrase, shift);
            cout << "Decoded passphrase: " << *phrase << endl;
            break;
        }

        cin.ignore(); 
    }

    delete choice;
    delete shift;
    delete phrase;

    return 0;
}
```

### Experience:
- Web Development Projects: Built multiple projects during my coursework, including interactive websites using HTML, CSS, and JavaScript, and more dynamic applications with React and Node.js. Courses from Udemy.

- Coding Tests & Challenges: Regularly solve coding challenges to sharpen my skills in algorithms and problem-solving. Write codes in the platforms like LeetCode and CodeWars.

- Internship in Spain: Completed a three-month web development internship, where I collaborated on real projects, worked with APIs, and gained hands-on experience in a professional setting.

- University Projects: Developed applications for various academic projects, implementing best practices in web development and data structures.

### Education:
- Tbilisi State University
Bachelor’s Degree in Computer Science
Courses include data structures, algorithms, and software development principles, with a focus on web technologies.

- Online Learning
Completed courses on platforms like Udemy and Coursera, covering React, Node.js, and advanced JavaScript concepts to strengthen my practical skills.

## Languages:
- English(B1-B2);
- Russian(native);
- Georgian(native);