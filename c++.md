## C++ Concepts and Syntax



### C/C++ Preprocessors : 
      Preprocessors are programs that processes our source code before compilation.
      
      
### Stages in compilation of C/C++ programs :
     1)The source code written by programmers is stored in the file program.c. 
     2)This file is then processed by preprocessors and an expanded source code file is generated named program. 
     3)This expanded file is compiled by the compiler and an object code file is generated named program.obj . 
     4)Finally the linker links this object code file to the object code of the library functions to generate the executable file program.exe .


### There are 4 main types of preprocessor directives:
     1)Macros
     2)File Inclusion
     3)Conditional Compilation
     4)Other directives



### Object Oriented Programming :

1) Inheritance : The capability of a class to derive properties and characteristics from another class is called Inheritance.
```
   Sub Class   :  class which inherits.
   Super Class :  class who properties are inherited. Also called Base Class
   
   syntax:
   
     class subclass_name : access_mode base_class_name
     {
        //body of subclass
      };
 ```
      
### Access modifiers :
   
           class A  
          { 
               public: 
                   int x; 
               protected: 
                   int y; 
               private: 
                   int z; 
          }; 

          class B : public A 
          { 
              // x is public 
              // y is protected 
              // z is not accessible from B 
          }; 

          class C : protected A 
          { 
              // x is protected 
              // y is protected 
              // z is not accessible from C 
          }; 

          class D : private A    // 'private' is default for classes 
          { 
              // x is private 
              // y is private 
              // z is not accessible from D 
          }; 
     


