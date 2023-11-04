# Multidimensional arrays
### Declaration and initialization of an array
```c
/* the array with two rows and three columns                          */
int tab[2][3] = {
	{0,1,2},
	{3,4,5}
}; 
```
### The elements of an array are placed in consecutive memory cells
```c		
for(int i = 0; i<2;i++){
	for(int j = 0; j<3;j++){
		printf("address tab=%p tab=%d\n", (void *)&tab[i][j], tab[i][j]);
	}
}
```
### Ways to initialize an array
```c
int tab[2][2][3] = {
	{ {0,1,2},{0,4,5} },
	{ {10,11,12},{0,0,0} },
	}; 


/* It is possible to omit some elements of the basic array
   initialization syntax, but then the code is no longer as
   read-friendly.  For example, you can omit the size of the first
   dimension if it is derived from the initialization list           */

   int tab[][2][3] = { 
	{ {1,2,},{0,4,5} },
	{ {10,11,12} }, 
	};

/* The above array initialization corresponds to this one            */
int tab[2][2][3] = { 
	{ {1,2,0},{0,4,5} },
	{ {10,11,12},{0,0,0} }, 
	};

/* You can skip some curly brackets in the initialization list       */
int tab[2][2][3] = {0,1,2,0,4,5,10,11,12}; 
int tab[2][2][3] = { {0,1,2,0,4,5},{10,11,12} }; 

/* The above array initializations correspond to this one:           */
int tab[2][2][3] = { 
	{ {0,1,2},{0,4,5} },
	{ {10,11,12},{0,0,0} }, 
	};

/* Array initialization based on the indicated element               */
int tab[2][2][3] = {[0][0][2]=100};

/* The above array initialization corresponds to this on             */
int tab[2][2][3] = { 
	{ {0,0,100},{0,0,0} },
	{ {0,0,0},{0,0,0} }, 
	};

int tab[2][2][3] = {1,[0][0][2]=100,1}; 

/* The above array initialization corresponds to this one            */
int tab[2][2][3] = { 
	{ {1,0,100},{1,0,0} },
	{ {0,0,0},{0,0,0} }, 
	};

```

### Assignment
Implement a one-dimensional cellular automaton that operates on a
32x65 array.  Each row of the array corresponds to one iteration in
*t* time. The behavior of of the array is determined by rules:

0 < 0 > 0 —> 0

0 < 0 > 1 —> 1

0 < 1 > 0 —> 0

0 < 1 > 1 —> 0

1 < 0 > 0 —> 1

1 < 0 > 1 —> 0

1 < 1 > 0 —> 0

1 < 1 > 1 —> 0

`0 < 0 > 1` -> 1: means that if the system for *t*=a is in the state `<
0 >` and the left side is `0`, and the right side is `1`, then for *t*=a+1
switch to the state 1. The other rules works analogously.

Initial value for *t*=0:
00000000000000000000000000000000100000000000000000000000000000000

You need to properly replace the number 0 with a space symbol, and the
number 1 with a '#' symbol

The outcome of the program is to be a graphical representation of the
behavior of the system for *t* from 0 to 31, i.e. a Sierpiński
triangle.

```zsh
                                #                                
                               # #                               
                              #   #                              
                             # # # #                             
                            #       #                            
                           # #     # #                           
                          #   #   #   #                          
                         # # # # # # # #                         
                        #               #                        
                       # #             # #                       
                      #   #           #   #                      
                     # # # #         # # # #                     
                    #       #       #       #                    
                   # #     # #     # #     # #                   
                  #   #   #   #   #   #   #   #                  
                 # # # # # # # # # # # # # # # #                 
                #                               #                
               # #                             # #               
              #   #                           #   #              
             # # # #                         # # # #             
            #       #                       #       #            
           # #     # #                     # #     # #           
          #   #   #   #                   #   #   #   #          
         # # # # # # # #                 # # # # # # # #         
        #               #               #               #        
       # #             # #             # #             # #       
      #   #           #   #           #   #           #   #      
     # # # #         # # # #         # # # #         # # # #     
    #       #       #       #       #       #       #       #    
   # #     # #     # #     # #     # #     # #     # #     # #   
  #   #   #   #   #   #   #   #   #   #   #   #   #   #   #   #  
```
