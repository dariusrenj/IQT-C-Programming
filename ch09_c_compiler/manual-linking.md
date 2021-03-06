## **Manual Linking**

Definitions of a header file can be assembled into an object file

this object file can be linked with other object files to create an executable

\#include preprocessor directives are still necessary

```c
#include <stdio.h>
#include ".\my_header.h"

int main(void)
{
    printf("%d\n", add_num(1, 2));

    return 0;
}

//my_source.c (source file)
```

```c
#ifndef MY_HEADER_INCLUDED_
#define MY_HEADER_INCLUDED_

int add_num(int x, int y);
#endif

//my_header.h (header file)
```

```c
int add_num(int x, int y)
{
    return x+y;
}

//my_header.c (header file definition)
```

### \(GUI\)

**\[create a preprocessed file\]**

property pages --&gt; C/C++ --&gt; preprocessor --&gt; preprocess to a file: yes

**\[create an assembly code\]**

property pages --&gt; C/C++ --&gt; output files --&gt; asm list location: $\(IntDir\)

property pages --&gt; C/C++ --&gt; output files --&gt;assembler output: assembly-only listing /FA

**\[create an object file\]**

property pages --&gt; C/C++ --&gt; output files --&gt; object file name

**\[link an object file\]**

add the .obj to your project as an "existing item"



