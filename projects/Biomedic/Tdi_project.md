---
layout: post
title: Digital Image Treatment Tool
---
*****
First of all, this project has been made with the collaboration of all the students signed in the 2021 Digital Image Treatment 
subject and the professor (Carlos Oscar S.Sorzano) through a collaborative repository in Github.  

The repository link is the following: [Repository Link CeuImgProc](https://github.com/cossorzano/CEUImgProc)

This project has been programmed in Matlab language.  
My contributions to this project have been developing a specific tool to increase and decrease the contrast of an image in each
of its color channels; and a tool to pixelate an image depending on a level of pixelization desired by the user.

###Increase and decrease contrast tool:

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