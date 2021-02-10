---
layout: post
title: Electrocardiogram Data Comparer
---
*****
First of all, this project has been made with the collaboration of other two college mates: Ignacio Méndez de Vigo and Gonzalo Álvarez García. 

To start with, an ECG sample is given us to work. This sample have been proportionated with the help of a MCU (microcontroller unit) that measure the heartbeat. This data is stored in an .h file. 
We developed a code in C language to handle the input data stored in the .h file, and to give as result 3 arrays data:
1.	An array of the maximum values read in range of 100, for example the program read the first 100 values a determine which is the maximum value and store it in the “maxa” array, then increase the loop in one value, take other sample of 100 values, the same that the previous, but in this case let outside the first value (1), and take the next value of the final previous range  (the value 101). When the maximum value of this range is determined, and stored in “maxa” array, the next loop round let outside the first value of the previous range (value 2) and increase in one the final value (102) … This will be repeated until the final 100 range take as last value the last value of the sample.
2.	An array of the minimum values stored with the same algorithm than the maximum values, but in this case stored the minimum values in an array called “mina”
3.	An array with the mean value of the 100 range data taken in each loop round of the sample given.

This is the code in C:

```c
//*----------------------------------------------------------------------------------------------------------------------------------------
 //*  Lab 2B
// *  Students: Ignacio Méndez de Vigo Iriarte, Gonzalo Álvarez García & Jaime Bermejo Torres
// *
// *  Call the function from the main program and check that the result is correct
// *----------------------------------------------------------------------------------------------------------------------------------------/


//#include <MKL25Z4.H> //This library is commented because we is not available.
#include "ecg.h"
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
extern uint8_t ECG[SIZE];
uint8_t maxa[SIZE-99]; //We are taking uint8_t because the data processing don't overflow 255
uint8_t mina[SIZE-99];
uint8_t mean[SIZE-99];

 // The ECG array is delared in "ecg.h"
void get_stats( uint8_t *ecg, uint8_t *maxa, uint8_t *mina, uint8_t *mean){ //is passed an array of chars 
  //uint8_t ecg[SIZE];
 // for (int i = 0; i < SIZE; i++){
    //ecg[i] = (uint8_t) ecgc[i];// to cast to uint8_t 
  //}
  
  uint8_t max;
  uint8_t min;
  uint16_t sum; //We are taking an uint16_t because the summatory of some values can be higher than 255
  uint8_t mean1;
for(int j=0;j<SIZE-100;j++){
 sum=ecg[j];  
 min=ecg[j];
 max=ecg[j];
for(int i=j+1;i<j+100;i++){
  if(ecg[i]>max){ //if there is a higher value is stored in max
    max=ecg[i];
  }
  if(ecg[i]<min){ //if there is a lower value is stored in min
    min=ecg[i];
  }
  sum=sum+ecg[i];
}
mean1=sum/100; //the mean must be done by a range of 100 numbers
//The values max, min and mean1 are temporal variables, so they are stored in the arrays of maxa mina and mean
maxa[j]=max;
mina[j]=min;
mean[j]=mean1;
}
}

int main(void)
{
  get_stats(ECG, maxa, mina, mean);
  //this for loops are to watch that the program work propertly
  printf("\nArray of max values:-------------");
  for(int i=0; i<(SIZE-100);i++){
  printf("%d, ",maxa[i]);
  }
  printf("\nArray of min values:-------------");
  for(int i=0; i<(SIZE-100);i++){
  printf("%d, ",mina[i]);
  }
  printf("\nArray of mean values:-------------");
  for(int i=0; i<(SIZE-100);i++){
  printf("%d, ",mean[i]);
  }
	return 0;
}
// *******************************ARM University Program Copyright � ARM Ltd 2013*************************************
```

After develop the program in C, it can be changed into an Assembly code to handle the data directly from the MCU. And we did it:
```assembly
PUSH [R0,R1,R2,R3]
MOVS R0,#0       
loop  					
LDRB R1[pos(ecg),R0]
MOVS R5,R1   
MOVS R6,R1
MOVS R4,R1   
ADDS R1,R0,#1

loopi
LDRB  R2[pos(ecg),R1]
CMP R2,R6                                                                                                                                                                                                                  
BLE not__found
MOV R6,R2
B not_found2
not_found           	
CMP R2,R5    
BGE not_found2
MOV R5,R2
not_found2     
SUB   R1,R1#1
LDRB  R2[pos(ecg),R1]  
ADDS R4,R2 
ADDS R1,#2   
CMP R1 ,#100
BLT loopi
ADDS R4,R2     
ADDS R1,#1    
CMP R1 ,#100
MUL R3,#0A
LSRS R3,#10 					
STR R6,[pos(maxa),R0]		
STR R5,[pos(mina),R0]
STR R3,[pos(mean), R0]
ADDS R0,R0,#1
CMP R0,#900
BLT loop
B 0x00000
```