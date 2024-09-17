//SJF Pre-emptive
#include <stdio.h>
#include <stdarg.h>
#include <string.h>
void swap(int* arr,int p, int q){
	int temp=arr[p];
	arr[p]=arr[q];
	arr[q]=temp;

}

//Sorts the first input array and reorders the values in the variable number of subsequent arrays
void sort(int n, int argcount, ...){
	va_list argptr;
	va_start(argptr, argcount);
	int* arrayToSort=va_arg(argptr, int*);
	va_start(argptr, argcount);
	for(int i=0;i<n-1;i++){
		for(int j=0;j<n-i-1;j++){
			if(arrayToSort[j]>arrayToSort[j+1]){
				for(int k=0;k<argcount;k++)
					swap(va_arg(argptr, int*), j, j+1);
				va_start(argptr, argcount);
			}
		}
	}
}

int findRT(int p_num, int* process, int* RT, int n){
	for(int i=0;i<n;i++){
		if(process[i]==p_num)
			return RT[i];
	}
	return 0;
}

int findi(int p_num, int* process, int n){
	for(int i=0;i<n;i++){
		if(p_num==process[i]){
			return i;
		}
	}
	return 0;
}
int main(){

int len=5;
int AT[]={3,2,4,5,0};

int BT[]={4,2,6,2,3};

int process[]={1,2,3,4,5};

int CT[5];
memset(CT, 0, len*sizeof(int));
int TAT[5];

int RT[5];
memcpy(RT, BT, len*sizeof(int));

int WT[5];

sort(5,4, RT, process, AT, BT);
printf("\nThe processes sorted based on initial Remaining Time\n\nBurst Time\tProcess\t    Arrival Time\n----------------------------------------------\n");
for(int i=0;i<len;i++){
	printf("    %d\t\t    %d\t\t%d\n----------------------------------------------\n", BT[i], process[i], AT[i]);
}

int num=0;
int time=0;
int currentProcess=-1;
while(num!=5){
	int i=0;
	sort(5,7,RT,process,BT,AT,CT,TAT,WT);
	while(time<AT[i] || RT[i]==0){
		if(i==4){
			time++;
			i=0;
			continue;
		}
		i++;
	}
	if(currentProcess!=process[i]){
		if(currentProcess!=-1 && RT[i]==findRT(currentProcess, process, RT, len))
			i=findi(currentProcess, process, len);	
		else
			currentProcess=process[i];
	}
	time++;
	RT[i]--;
	if(RT[i]==0){
		num++;
		CT[i]=time;
		TAT[i]=CT[i]-AT[i];
		WT[i]=TAT[i]-BT[i];
	}	
}

sort(5, 6, process, AT, BT, CT, TAT, WT);
printf("\nThe Completion times, Turn Around Times and Waiting Times of the processes are\n\nProcess   |   Arrival Time   |   Burst Time   |   Completion Time   |   Turn Around Time   |   Waiting Time\n-----------------------------------------------------------------------------------------------------------\n");

for(int i=0;i<len;i++){
	printf("  %d\t\t  %d\t\t   %d\t\t\t%d\t\t\t%d\t\t\t%d\n-----------------------------------------------------------------------------------------------------------\n", process[i], AT[i], BT[i], CT[i],TAT[i], WT[i]);
}
} 
