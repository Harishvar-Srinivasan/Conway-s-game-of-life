#include <stdio.h>
#include <stdbool.h>


#include "life.h"

 /* The first argument is a starting state in one of the Life formats supported by parse_life(), and the second
 * is a number of generations to run before printing output and stopping.
 */
 
 int parseint(char *str)
{
    int size=0;
    
    for(int j=0;str[j]!='\0';j++)
        {
            size=size+1;
        }
    
         int finalvalue=0;
         if(size>1){
         for(int i=0;i<size;i++)
              {
                   int con = str[i]-'0';
                   finalvalue = (finalvalue*10) + con;
              }
    }else{
        finalvalue=str[0]-'0';
    }
    
    return finalvalue;
    
    }

int livecount(char grid[GRIDY+2][GRIDX+2],int a,int b)
{
    int livecells=0;
    if(grid[a-1][b-1]=='X')
        {
            livecells=livecells+1;
        }
    if(grid[a-1][b]=='X')
        {
            livecells=livecells+1;
        }
    if(grid[a-1][b+1]=='X')
        {
            livecells=livecells+1;
        }
    if(grid[a][b-1]=='X')
        {
            livecells=livecells+1;
        }
    if(grid[a][b+1]=='X')
        {
            livecells=livecells+1;
        }
    if(grid[a+1][b-1]=='X')
        {
            livecells=livecells+1;
        }
    if(grid[a+1][b]=='X')
        {
            livecells=livecells+1;
        }
    if(grid[a+1][b+1]=='X')
        {
            livecells=livecells+1;
        }
    return livecells;
    }


void assigndead(char a[GRIDY+2][GRIDX+2])
{
    
    for(int i=0;i<GRIDY+2;i++)
        {
            for(int j=0;j<GRIDX+2;j++)
                {
                    a[i][j]=DEAD;
                }
        } 
}




int main(int argc, char *argv[])
{
    //checking and returning an error message if it has invalid no of arguments

    if(argc > 3 || argc < 2)
        {
            printf("Invalid Argument");
            return 1;
        }
    


    //for printing the generation 0
   
    char inigrid[GRIDY][GRIDX];
    /*for(int x=0; x<GRIDY;x++)
        {
            for(int y=0; y<GRIDX;y++)
                {
                    inigrid[x][y]=DEAD;
                }
                }*/
    char ** harish = parse_life(argv[1]);

    
   
    for(int i=0;i<GRIDY;i++)
        {
            for(int j=0;j<GRIDX;j++)
                {
                   inigrid[i][j]=harish[i][j];  
                }   
        }


    
     //rules of game of life
    
    char grids[2][GRIDY+2][GRIDX+2];
      
    int generation = 0;
    

    for(int current=0; generation<=parseint(argv[2]); current = (current +1) % 2)
        {
            if(current == 0)
                {
                  assigndead(grids[current]);
                    
                  for(int i1 = 1; i1 < GRIDY+1; i1++)
                      {
                        for(int j1 = 1; j1 < GRIDX+1; j1++)
                            {
                                          grids[current][i1][j1] = inigrid[i1-1][j1-1];             
                            }
                      }
                  generation = generation+1;
                }
            else if(current == 1)
                {
                    assigndead(grids[current]);
                    int alive=0;

            for(int a = 1; a< GRIDY+1; a++)
                {
                    for(int b = 1; b< GRIDX+1; b++)
                        {
                         alive= livecount(grids[current-1],a,b);
                         
                            if(grids[current-1][a][b]==LIVE)
                                {
                                    if(alive < 2 || alive > 3)
                                        {
                                            grids[current][a][b]=DEAD;   
                                        }
                                    else if(alive ==2 || alive ==3)
                                        {
                                            grids[current][a][b]=LIVE;
                                        }
                                    inigrid[a-1][b-1] = grids[current][a][b];
                                }
                            else if((grids[current-1][a][b]==DEAD))
                                {
                                    if(alive == 3)
                                        {
                                            grids[current][a][b]=LIVE;       
                                        }
                                    else {
                                        grids[current][a][b]=DEAD;
                                    }   
                                    inigrid[a-1][b-1] = grids[current][a][b];
                                  }   
                        }      
                }       
         }
        }
     for(int i=1;i<GRIDY+1;i++)
        {
            for(int j=1;j<GRIDX+1;j++)
                {
                    printf("%c",grids[0][i][j]);
                   
                }
            printf("\n");
            
            }
    return 0;
}
