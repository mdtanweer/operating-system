Welcome to the newproject wiki!
Que No:37. Consider the following four processes, with the length of the CPU burst given in milliseconds
Process       Arrival Time       Burst Time
P1                0                           8
P2                1                           4
P3                2                           9
P4                3                           5 

Write a C program to calulate average waiting time using shortest-remaining -time-first scheduling.

Solution of question no 37:-----------

#include<stdio.h>

int main()
{
	int at[10],bst[10],temp[10],wt[10],tat[10],ct[10];
	int i,j,n,smallest,count=0,t;
	float avgwt=0,avgtat=0;
	
	printf("enter the no of process ");
	scanf("%d",&n);
	
	for(i=0;i<n;i++)
	{
		printf("\nenter the details of process P%d\n",i+1);
		printf("arival time ");
		scanf("%d",&at[i]);
		printf("brust time ");
		scanf("%d",&bst[i]);
		temp[i]=bst[i];
	}
	
	bst[9]=1000;
	for(t=0;count!=n;t++)
	{
		smallest=9;
		for(j=0;j<n;j++)
		{
			if(at[j]<=t && bst[j]<bst[smallest] && bst[j]>0)
			{
				smallest=j;
			}
		}
		bst[smallest]--;
		if(bst[smallest] == 0)
  		{
   			count++;
   			ct[smallest]=t+1;
   			tat[smallest]=ct[smallest]-at[smallest];
   			wt[smallest]=tat[smallest]-temp[smallest];
  		}
 	}
	for(i=0;i<n;i++)
 	{
 	   avgwt=avgwt+wt[i];
 	   avgtat=avgtat+tat[i];
    }
 	printf("process \t At\t Bt\t Ct\t Tat\t Wt\n");
 	for(i=0;i<n;i++)
 	{
 		printf("P%d\t\t %d\t %d\t %d\t %d\t %d\n",(i+1),at[i],temp[i],ct[i],tat[i],wt[i]);
	}
	printf("Average waiting time =%f\n",avgwt/n);
	printf("Average turnaround time=%f\n",avgtat/n);
     return 0;     
}