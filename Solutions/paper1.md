
---

# CC-311L - Paper 1

---

## Question #1

> A university laboratory maintains project files for different student groups on a Linux system.

**Task:** Write a Linux shell script to perform the following tasks:
1. Create a directory named `StudentProjects`.
2. Inside this directory, create three files: `group1.txt`, `group2.txt`, and `group3.txt`.
3. Display the details of all files using the command `ls -l`. 
4. Modify the permissions of `group1.txt` so that:
    - The **owner has read and write permissions**.
    - The **group has read permission**.
    - Others have no permission.
5. Create both a hard link and a symbolic link for `group2.txt`.

### Solution

```bash
#!/bin/bash

# 1. Create a directory named StudentProjects
mkdir -p StudentProjects

# Move into the directory
cd StudentProjects

# 2. Create three files
touch group1.txt group2.txt group3.txt

# 3. Display file details
echo "File details:"
ls -l

# 4. Modify permissions of group1.txt
# Owner: read & write (rw-)
# Group: read (r--)
# Others: no permission (---)
chmod 640 group1.txt

echo "Updated permissions for group1.txt:"
ls -l group1.txt

# 5. Create hard link and symbolic link for group2.txt
ln group2.txt group2_hardlink.txt
ln -s group2.txt group2_symlink.txt

echo "After creating links:"
ls -l
```

### Explanation

- `mkdir -p` → creates directory (avoids error if it exists)
- `touch` → creates empty files
- `ls -l` → shows file permissions, owner, size, etc.
- `chmod 640 group1.txt` →
    - **6** (owner) = read + write
    - **4** (group) = read
    - **0** (others) = no permission
- `ln` → creates a **hard link**
- `ln -s` → creates a **symbolic (soft) link**

---

## Question #2

> A system administrator wants to monitor the creation of processes in Linux.

Write a C program using system calls to demonstrate process creation.

Display the **process ID** and **parent process ID** using `getpid()` and `getppid()`. Create a **child process** using the `fork()` system call. Print **different messages from the parent and child processes** and use `wait()` so that the **parent waits for the child process to finish execution**.

### Solution

```c
#include <stdio.h>
#include <unistd.h>   // for fork(), getpid(), getppid()
#include <sys/types.h>
#include <sys/wait.h> // for wait()

int main() {
    pid_t pid;

    // Create a child process
    pid = fork();

    if (pid < 0) {
        // Fork failed
        printf("Process creation failed!\n");
        return 1;
    }
    else if (pid == 0) {
        // Child process
        printf("=== Child Process ===\n");
        printf("Child PID: %d\n", getpid());
        printf("Parent PID: %d\n", getppid());
    }
    else {
        // Parent process
        wait(NULL); // Parent waits for child to finish

        printf("**** Parent Process ****\n");
        printf("Parent PID: %d\n", getpid());
        printf("Child PID: %d\n", pid);
    }

    return 0;
}
```

### Explanation

- `fork()` → creates a **new child process**
    - Returns:
        - `0` → in **child process**
        - `>0` → in **parent process** (returns child PID)
        - `<0` → failure
- `getpid()` → returns current process ID
- `getppid()` → returns parent process ID
- `wait(NULL)` → makes **parent wait until child finishes**

---

## Question #3

> Write a **multithreaded C program** using **POSIX threads** where three threads perform different tasks and display their thread IDs. Use `pthread_create()` to create the threads and `pthread_join()` to synchronize their execution.

### Solution

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

// Thread function 1
void* task1(void* arg) {
    printf("Thread 1 is running\n");
    printf("Thread 1 ID: %lu\n", pthread_self());
    return NULL;
}

// Thread function 2
void* task2(void* arg) {
    printf("Thread 2 is running\n");
    printf("Thread 2 ID: %lu\n", pthread_self());
    return NULL;
}

// Thread function 3
void* task3(void* arg) {
    printf("Thread 3 is running\n");
    printf("Thread 3 ID: %lu\n", pthread_self());
    return NULL;
}

int main() {
    pthread_t t1, t2, t3;

    // Create threads
    pthread_create(&t1, NULL, task1, NULL);
    pthread_create(&t2, NULL, task2, NULL);
    pthread_create(&t3, NULL, task3, NULL);

    // Wait for threads to finish
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    pthread_join(t3, NULL);

    printf("All threads have finished execution.\n");

    return 0;
}
```

### Explanation

- `pthread_create()` → creates a new thread
    - Syntax:
    ```c
    pthread_create(&thread_id, NULL, function_name, argument);
    ```
- `pthread_self()` → returns **current thread ID**
- `pthread_join()` → makes main thread **wait for other threads to finish**

---
