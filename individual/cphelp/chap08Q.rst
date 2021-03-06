


Chapter 8:Review Questions
==========================

::

    
     T  F    1.   A pointer contains the address of the object
                  to which it points.
    
     T  F    2.   The  ***** character, when defining a 
                  declaring a pointer, is read "pointer to".
    
     T  F    3.   Any pointer can point at anything; the type 
                  specifier is merely used for documentation.
    
     T  F    4.   If  **msg** is a character pointer, then
                   **msg = "A Literal"**; will copy the 
                  string literal  **"A Literal"** into the 
                  area pointed to by  **msg**.
    
     T  F    5.  All arithmetic done with pointers is scaled to 
                 the size of the object being pointed to.
    
     T  F    6.  If a pointer variable is used as an actual 
                 argument when calling a function, then the 
                 compiler passes the address of where the 
                 pointer is located, not a copy of the pointer 
                 itself.
    
     T  F    7.  If two  ***** characters are used when 
                 defining a variable, it is a pointer to 
                 another pointer.
    
     T  F    8.  The variable names  **argc** and  **argv** 
                 are reserved and can only be used with the 
                  **main()function**.
    
     T  F    9.  The type of the expression  **(*++argv)[0]** 
                 is character.
    
     T  F    10. Code that subscripts a pointer outside the 
                 defined boundaries of the array may compile, 
                 but logically be in error.
    
     T  F    11. The definition  **(*what_is_this())()** is 
                 that of a function returning a pointer to an 
                 array of integers.
    
    12. Which pair of the following statements are equivalent?
    
        a.   *value[1];
             *(value + 1);
        b.   **value;
             *value;
        c.   *value[2];
             (*value++)++;
        d.   *value;
             
    
    13. What is wrong with the following code fragment?
    
        char code[] = "This is a secret message...";
    
        main()
        {
        int checksum = 0;
    
             while ( *code )
             {
                  checksum += *code;
                  ++code;
             }
        }
    
        a.   The array name "code" cannot be incremented.
        b.   Characters cannot be added.
        c.   The  ***** operator cannot be used with a 
             character array name.
        d.   The loop will not terminate since a logical FALSE 
             will never occur.
    
    14. A null pointer can be described as:
    
        a.   The same as  **void ***.
        b.   A "special" pointer that is typically used to flag 
             an error or a termination indicator for arrays.
        c.   A pointer that points to a binary zero in memory.
        d.   Exactly the same as a logical FALSE value.
     
    15. A good application for using an array of pointers is 
        when:
    
        a.   The objects pointed to are different data types.
        b.   One of the objects must be passed to a function.
        c.   The design indicates indirect addressing of the 
             objects pointed to.
        d.   The objects are integers, which are always the 
             same as pointers.
    
    16. When the variable  **argv** is passed to 
         **main()** it references:
    
        a.   A string array.
        b.   An array of pointers to the command line arguments 
             (strings).
        c.   Characters passed from the command line.
        d.   All command line arguments beginning with the 
             character "-".




