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

cat > pidcheck.c
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; 
}
```

gcc -o pidcheck.o pidcheck.c

./pidcheck.o

## OUTPUT

![ex2i](https://github.com/user-attachments/assets/a28e2792-0f69-45e2-8ad8-fb191dab2640)


ps
## OUTPUT

![ex2ii](https://github.com/user-attachments/assets/8110c256-204e-439d-bada-ef0a3ae77b0b)




## C Program to create new process using Linux API system calls fork() and exit()
cat > forkcheck.c

```
#include <stdio.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
```
gcc -o forkcheck.o forkcheck.c

./forkcheck.o

## OUTPUT

![ex2iii](https://github.com/user-attachments/assets/792a9fa4-6b73-4beb-9027-dc50d107c2b2)
![ex2iv](https://github.com/user-attachments/assets/4c33e450-7816-42e5-b343-30e454b41862)

## C Program to execute Linux system commands using Linux API system calls exec() family

cat > execcheck2.c

```
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);
}
```

gcc -o execcheck2.o execcheck2.c

./execcheck2.o

## OUTPUT


![ex2v](https://github.com/user-attachments/assets/e7d3598c-81ee-4bbb-8894-84ec438d26f9)
![ex2vi](https://github.com/user-attachments/assets/554d90fa-98bf-4ed8-934e-2f43edafbc52)



# RESULT:
The programs are executed successfully.
