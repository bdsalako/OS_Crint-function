#include <iostream>
#include <stdlib.h>
#include <ctime>
using namespace std;

//Function declaration
void Crint(int *p);
void PrintTable();
int SpaceFounder();


//Global variable
int p [10][6];
int vacant = 0;
int* ptr[10];


int main()
{
    int counter = 0;
    int job[6];
    srand(time(0));
    int *r = job;
    while(counter < 10){

        //job creation with some random numbers
        cout << "Job[" << counter << "] ----";
        for(int i = 0; i < 6; i++){
            job[i] = rand() % 101;
            cout << job[i] << " ";
        }
        cout << endl;
        Crint(r); //send job to crint as they are created
        counter++;
    }
    
    //p[5] and p[9] are finished and change the job# to 0 to make them available
    p[5][0] = 0;
    p[9][0] = 0;
    
    
    int newJob[] = {1, 2, 3, 4, 5, 6}; //create new test job

    Crint(newJob); //send the new job to crint
    PrintTable();
    return 0;
}

//this function searches for empty space from the job table
int SpaceFounder(){
    int temp;
    for(int i =0; i<10; i++){
        if(p[i][0] == 0){
            temp = i;
            break;
        }
        else
            temp = -1; // spaceFounder return -1 if space is not found from the 50 x 6 size
    }
    return temp;
}

void Crint(int *q){

   vacant = SpaceFounder();
   if(vacant == -1)
    throw exception();
   else
    for(int j = 0; j<6; j++){
        p[vacant][j] = q[j];
    }
    cout << endl;
    vacant++;
}

void PrintTable(){
    for(int i = 0; i < 10; i++){
        cout << "Job[" << i << "] ----";
        for(int j = 0; j < 6; j++)
            cout << p[i][j] << " ";
        cout << endl;
    }

}
