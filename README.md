# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

int main(void) {
    // Variable to store the calling function's process ID
    pid_t process_id;
    // Variable to store the parent function's process ID
    pid_t p_process_id;

    // getpid() - will return the process ID of the calling function
    process_id = getpid();
    // getppid() - will return the process ID of the parent function
    p_process_id = getppid();

    // Printing the process IDs
    printf("The process ID: %d\n", process_id);
    printf("The process ID of the parent function: %d\n", p_process_id);

    return 0;
}
















##OUTPUT


![Screenshot 2024-03-27 144156](https://github.com/pawan2006-png/Linux-Process-API-fork-wait-exec/assets/150067867/3d125dce-5360-4e80-a215-381a5b16c90c)












## C Program to create new process using Linux API system calls fork() and exit()

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main() {
    int pid;
    pid = fork();

    if (pid == 0) {
        // Child process
        printf("I am child, my pid is %d\n", getpid());
        printf("My parent pid is: %d\n", getppid());
        exit(0);
    } else {
        // Parent process
        printf("I am parent, my pid is %d\n", getpid());
        // Sleep for some time to let child process execute first
        sleep(100);
        exit(0);
    }
}











##OUTPUT
![Screenshot 2024-03-27 144219](https://github.com/pawan2006-png/Linux-Process-API-fork-wait-exec/assets/150067867/e5f093fa-9670-4b8b-babb-b16c7426ac54)









## C Program to execute Linux system commands using Linux API system calls exec() family



#include <stdlib.h>
#include <stdio.h>
#include <sys/wait.h>
#include <sys/types.h>

int main() {
    int status;

    printf("Running ps with execlp\n");
    execl("ps", "ps", "ax", NULL);
    wait(&status);

    if (WIFEXITED(status))
        printf("Child exited with status of %d\n", WEXITSTATUS(status));
    else
        puts("Child did not exit successfully");

    printf("Done.\n");

    printf("Running ps with execlp. Now with path specified\n");
    execl("/bin/ps", "ps", "ax", NULL);
    wait(&status);

    if (WIFEXITED(status))
        printf("Child exited with status of %d\n", WEXITSTATUS(status));
    else
        puts("Child did not exit successfully");

    printf("Done.\n");

    exit(0);
}






















##OUTPUT





![Screenshot 2024-03-27 144248](https://github.com/pawan2006-png/Linux-Process-API-fork-wait-exec/assets/150067867/064a58c7-5bf7-4989-a50f-819dbe49a9fd)













# RESULT:
The programs are executed successfully.
