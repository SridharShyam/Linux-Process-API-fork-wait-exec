# Linux-Process-API-fork-wait-exec-
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise
#### Name: SHYAM S
#### Reg.No: 212223240156

## AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

## DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

## PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls

```
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

int main() {
    pid_t pid;

    pid = fork();

    if (pid < 0) {
        perror("fork failed");
        return 1;
    } 
    else if (pid == 0) {
        printf("Child Process:\n");
        printf("Child PID: %d\n", getpid());
        printf("Parent PID: %d\n", getppid());
    } 
    else {
        printf("Parent Process:\n");
        printf("Parent PID: %d\n", getpid());
        printf("Child PID: %d\n", pid);
    }

    return 0;
}

```
## OUTPUT
<img width="242" height="138" alt="image" src="https://github.com/user-attachments/assets/5ec3e9c4-23bb-4f32-92f0-be4be17a12e7" />

## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main() {
    pid_t pid;
    int status;

    pid = fork();

    if (pid < 0) {
        perror("fork failed");
        return 1;
    } 
    else if (pid == 0) {
        printf("Child process executing 'ls -l' command:\n");
        execl("/bin/ls", "ls", "-l", NULL);

        perror("exec failed"); // runs only if exec fails
        return 1;
    } 
    else {
        wait(&status);
        printf("Parent process: Child finished execution.\n");
    }

    return 0;
}


## OUTPUT
<img width="527" height="147" alt="image" src="https://github.com/user-attachments/assets/6e2d44ed-461c-4c5e-bf24-dd8a0dc1394d" />

## RESULT:
The programs are executed successfully.
