# Tablice wielowymiarowe
### Deklaracja i inicjacja tablicy 
```c
/* tablica o dwóch wierszach i trzech kolumnach                      */
int tab[2][3] = {
	{0,1,2},
	{3,4,5}
}; 
```
### Elementy tablicy są umieszczana w następujących po sobie komórkach pamięci
```c		
for(int i = 0; i<2;i++){
	for(int j = 0; j<3;j++){
		printf("adres tab=%p tab=%d\n", (void *)&tab[i][j], tab[i][j]);
	}
}
```
### Sposoby na inicjację tablicy
```c
int tab[2][2][3] = {
	{ {0,1,2},{0,4,5} },
	{ {10,11,12},{0,0,0} },
	}; 

/* Można pomijać niektóre elementy podstawowej składni inicjacji     */
/* tablicy, ale wtedy kod nie jest już tak przyjazny w odczycie.     */
/* Na przykład można pominąć wielkość pierwszego wymiaru, 
/* jeśli wynika ona z listy inicjacyjnej                             */ 
int tab[][2][3] = { 
	{ {1,2,},{0,4,5} },
	{ {10,11,12} }, 
	};

/* Powyższa incjacja odpowiada tej:                                  */
int tab[2][2][3] = { 
	{ {1,2,0},{0,4,5} },
	{ {10,11,12},{0,0,0} }, 
	};

/* Można pominąć nawiasy klamrowe w liście inicjacyjnej              */
int tab[2][2][3] = {0,1,2,0,4,5,10,11,12}; 
int tab[2][2][3] = { {0,1,2,0,4,5},{10,11,12} }; 

/* Powyższe incjacje odpowiadają tej:                                */
int tab[2][2][3] = { 
	{ {0,1,2},{0,4,5} },
	{ {10,11,12},{0,0,0} }, 
	};

/* Inicjacja na podstawie wskazanego elementu                        */
int tab[2][2][3] = {[0][0][2]=100};

/* Powyższa inicjacja odpowiada tej:                                 */
int tab[2][2][3] = { 
	{ {0,0,100},{0,0,0} },
	{ {0,0,0},{0,0,0} }, 
	};

int tab[2][2][3] = {1,[0][0][2]=100,1}; 

/* Powyższa inicjacja odpowiada tej:                                 */
int tab[2][2][3] = { 
	{ {1,0,100},{1,0,0} },
	{ {0,0,0},{0,0,0} }, 
	};

```

### Zadanie
Zaimplementuj jednowymiarowy automat komórkowy działający na tablicy 32x65.
Każdy wiersz tablicy odpowiada jednej iteracji po czasie *t*. Zachowanie
układu określają reguły:

0 < 0 > 0 —> 0

0 < 0 > 1 —> 1

0 < 1 > 0 —> 0

0 < 1 > 1 —> 0

1 < 0 > 0 —> 1

1 < 0 > 1 —> 0

1 < 1 > 0 —> 0

1 < 1 > 1 —> 0

0 < 0 > 1 —> 1: oznacza, że jeśli układ dla *t*=a jest w stanie < 0 > i
po lewej stronie jest 0, a po prawej jest 1, to dla *t*=a+1 przejdź do
stanu 1. Pozostałe reguły analogicznie.

Wartość początkowa dla t=0:
00000000000000000000000000000000100000000000000000000000000000000

W programie trzeba odpowiednio zamienić cyfrę 0 na symbol spacji, a cyfrę 1 na
symbol #

Rezultatem działania programu ma być graficzna reprezentacja zachowania się
układu dla t od 0 do 31 tj. trójkąt Sierpińskiego.

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
