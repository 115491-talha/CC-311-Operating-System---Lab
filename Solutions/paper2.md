
---

# CC-311L - Paper 2

---

## Question #1

> Write a **Linux shell script** to demonstrate file and process management. Perform the following tasks:
1. Display the contents of the current directory using the `ls` command.
2. Create a directory named `MyDirectory`.
3. Inside this directory, create three files: `file1.txt`, `file2.txt`, and `file3.txt`.
4. Display the details of all files using `ls -l`. 
5. Create **a hard link and a symbolic link** for `file2.txt`.

### Solution

```bash
#!/bin/bash

echo "1. Display contents of current directory:"
ls

# 2. Create a directory
mkdir -p MyDirectory

# Move into the directory
cd MyDirectory

# 3. Create three files
touch file1.txt file2.txt file3.txt

# 4. Display file details
echo "File details:"
ls -l

# 5. Create hard link and symbolic link for file2.txt
ln file2.txt file2_hardlink.txt
ln -s file2.txt file2_symlink.txt

echo "After creating links:"
ls -l
```

### Explanation

- `ls` → lists files in current directory
- `mkdir -p MyDirectory` → creates directory
- `cd MyDirectory` → navigates into directory
- `touch` → creates empty files
- `ls -l` → shows detailed file info (permissions, size, owner)
- `ln file2.txt file2_hardlink.txt` → creates **hard link**
- `ln -s file2.txt file2_symlink.txt` → creates **symbolic (soft) link**

---

## Question #2

> Write a C program demonstrating process synchronization where a **parent process prints numbers from 6–10** and **the child process prints 1–5** using `fork()` and `wait()`.

### Solution

```c
#include <stdio.h>
#include <unistd.h>     // fork(), getpid()
#include <sys/types.h>
#include <sys/wait.h>   // wait()

int main() {
    pid_t pid;

    pid = fork(); // Create child process

    if (pid < 0) {
        printf("Fork failed!\n");
        return 1;
    }
    else if (pid == 0) {
        // Child process
        printf("Child Process (PID: %d)\n", getpid());
        for (int i = 1; i <= 5; i++) {
            printf("Child: %d\n", i);
        }
    }
    else {
        // Parent process waits for child
        wait(NULL);

        printf("Parent Process (PID: %d)\n", getpid());
        for (int i = 6; i <= 10; i++) {
            printf("Parent: %d\n", i);
        }
    }

    return 0;
}
```

### Explanation

- `fork()` → creates a **child process**
    - `0` → child process executes
    - `>0` → parent process executes
- Child prints numbers **1 to 5**
- `wait(NULL)` → ensures **parent waits until child finishes**
- Parent prints numbers **6 to 10 after child completes**

---

## Question #3

> Write a **multithreaded C program** using **POSIX threads**.

Create two threads that **print numbers from 1 to 5**. Synchronize the threads using `pthread_join()`.

### Solution

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

// Thread function
void* printNumbers(void* arg) {
    int thread_num = *(int*)arg;

    for (int i = 1; i <= 5; i++) {
        printf("Thread %d: %d\n", thread_num, i);
    }

    return NULL;
}

int main() {
    pthread_t t1, t2;
    int id1 = 1, id2 = 2;

    // Create threads
    pthread_create(&t1, NULL, printNumbers, &id1);
    pthread_create(&t2, NULL, printNumbers, &id2);

    // Wait for threads to finish
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);

    printf("Both threads have finished execution.\n");

    return 0;
}
```

### Explanation

- `pthread_create()` → creates threads
- Both threads run the same function `printNumbers()`
- Each thread prints numbers **1 to 5**
- `pthread_join()` → ensures the main program waits until both threads complete

---
