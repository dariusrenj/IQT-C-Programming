# storage class specifiers
a variable's storage class determines its scope, and storage duration

the user can explicitly set the storage class for a variable

scope can be either block or file

storage durations can be either *static* or *automatic*
    
    static: 
    -initialzed once before the program begins
    -exists continuously throughout the program execution
    
    automatic:
    -generated each time the program enters the block
    -memory is freed when the block is terminated

### specifier
static:
- always have a storage duration of static
- used to declare a static variable with limited scope

extern:
- declares variables with static storage duration that can be used throughout the program

|position of the declaration|storage class specifier|scope|storage duration|initialize|
|---|---|---|---|---|
|within a block|extern, static|block/local|static|once|
|outside all blocks|none, extern, static|file/global|static|once|
|within a block|none|block/local|automatic|each run|

>auto specifiers give variables have automatic storage duration. rarely used because "automatic" is the default storgae class for variables within a function

>static specifiers mean variables always have static storage duration. this specifier is used to declare static variables with a limited scope

>extern is much like a static specifier but is instead used to declare variables with static storage duration that can be used throughout the program

```c
///static variable example 1///
int i = 0;

int normVar = 1;
static int statVar = 1;

for (i = 0; i < 10; i++)
{
    printf("norm = %-2d\t", normVar);
    printf("stat = %-2d\n", statVar);

    normVar++;
    statVar++;
}

///static variable output 1///
norm = 1     stat = 1
norm = 2     stat = 2
norm = 3     stat = 3
norm = 4     stat = 4
norm = 5     stat = 5
norm = 6     stat = 6
norm = 7     stat = 7
norm = 8     stat = 8
norm = 9     stat = 9
norm = 10    stat = 10

///static variable example 2///
int i = 0;

for (i = 0; i < 10; i++)
{
    int normVar = 1;
    static int statVar = 1;

    printf(“norm = %-2d\t”, normVar);
    printf(“stat = %-2d\n”, statVar);

    normVar++
    statVar++
}

///static variable output 2///
norm = 1     stat = 1
norm = 1     stat = 2
norm = 1     stat = 3
norm = 1     stat = 4
norm = 1     stat = 5
norm = 1     stat = 6
norm = 1     stat = 7
norm = 1     stat = 8
norm = 1     stat = 9
norm = 1     stat = 10

///static variable example 3///
int i = 0;

for (i = 0; i < 10; i++)
{
    int normVar = 1;
    static int statVar = 1;

    printf(“Norm = %-2d\t”, normVar);
    printf(“Stat = %-2d\n”, statVar);

    normVar++;
    statVar++;
}

printf(“Norm = %-2d\t”, normVar);
printf(“Stat = %-2d\n”, statVar);    

///static variable output 3///
NONE...will result in a compiler error!!!!
```
### extern

this storage class specifier is used to share access to a variable across different source files by extending their "visibility"

by default, the declaration and definition of a C function includes an implicit "extern"

when extern is used with a variable, it is only declared not defined (unless the initialization of that decalartion represents the sole definition of that extern)

extern references can be referenced multiple times over multiple files but should only be defined once

not utilized for single file programs

