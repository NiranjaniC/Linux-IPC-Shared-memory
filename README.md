# Linux-IPC-Shared-memory
Ex06-Linux IPC-Shared-memory

# AIM:
To Write a C program that illustrates two processes communicating using shared memory.

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - Shared Memory

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## Write a C program that illustrates two processes communicating using shared memory.

#include <stdio.h>

#include <sys/ipc.h>

#include <sys/shm.h>

int main()

{

// Generate a unique key using ftok

key_t key = ftok("shmfile", 65);

// Get an identifier for the shared memory segment using shmget

int shmid = shmget(key, 1024, 0666 | IPC_CREAT);

  printf("Shared memory id = %d \n",shmid);
// Attach to the shared memory segment using shmat

char* str = (char*)shmat(shmid, (void*)0, 0);

printf("Write Data : ");

fgets(str, 1024, stdin);

printf("Data written in memory: %s\n", str);

// Detach from the shared memory segment using shmdt

shmdt(str);

return 0;
}



## OUTPUT
![320187135-c9e5ec48-831a-4a84-8af4-a5af3e05a76c](https://github.com/NiranjaniC/Linux-IPC-Shared-memory/assets/145742800/05868b5f-41a7-4112-8830-f90c0a602b9d)



# RESULT:
The program is executed successfully.
