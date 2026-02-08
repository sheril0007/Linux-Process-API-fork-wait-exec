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

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
if (pid == 0) { 
    printf("I am child, my PID is %d\n", getpid()); 
    printf("My parent PID is: %d\n", getppid()); 
    sleep(2);  // Keep child alive for verification
} else { 
    printf("I am parent, my PID is %d\n", getpid()); 
    wait(NULL); 
}
```












##OUTPUT



<img width="356" height="124" alt="image" src="https://github.com/user-attachments/assets/1128a638-e0b6-417b-8115-c13cfc14e80f" />








## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
```
printf("Running ps with execl\n");
if (fork() == 0) {
    execl("ps", "ps", "-f", NULL);
    perror("execl failed");
    exit(1);
}
wait(&status);
{
if (WIFEXITED(status)) {
    printf("Child exited with status: %d\n", WEXITSTATUS(status));
} else {
    printf("Child did not exit successfully\n");
}
{
printf("Running ps with execlp (without full path)\n");
if (fork() == 0) {
    execlp("ps", "ps", "-f", NULL);
    perror("execlp failed");
    exit(1);
}
wait(&status);
{
if (WIFEXITED(status)) {
    printf("Child exited for execlp with status: %d\n", WEXITSTATUS(status));
} else {
    printf("Child did not exit successfully\n");
}
{
printf("Done.\n");
return 0;
```


























##OUTPUT




<img width="666" height="312" alt="image" src="https://github.com/user-attachments/assets/329ee66b-e888-41d1-a61b-786c55fd1ae6" />


















# RESULT:
The programs are executed successfully.
