Consider a scheduler which schedules the job by considering the arrival time of the processes where arrival time if given as 0 is discarded or displayed as error. The scheduler implements the shortest job first scheduling policy, but checks the queue of the processes after the every process terminates and time taken for checking and arranging the process according to the shortest job is 2 time unit. Compute the waiting time, turnaround time and average waiting time and turnaround time of the processes. Also compute the total time taken by the processor to compute all the jobs.
The inputs for the number of requirements, arrival time and burst time should be provided by the user.
Consider the following units for reference.
Process Arrival time Burst Time
1 0 6
2 3 2
3 5 1
4 9 7
5 10 5
6 12 3
7 14 4
8 16 5
9 17 7
10 19 2
Develop a scheduler which submits the processes to the processor in the defined scenario, and compute the scheduler performance by providing the waiting time for process, turnaround time for process and average waiting time and turnaround time.
 

#include<stdio.h>
#include<conio.h>
int main()
{
	int bt[10],p[10],n,temp,i,j,wt[10],sum=0;
	float avg;
	printf("Enter total no of proces:");
	scanf("%d",&n);
	printf("\n Enter burst time for each process:-");
	for(i=0;i<n;i++)
	{
		printf("\nBurst time of process P%d:",i);
		scanf("%d",&bt[i]);
		p[i]=i;
	}
	for(i=0;i<n-1;i++)
	{
		for(j=i+1;j<n;j++)
		{
			if(bt[i]>bt[j])
			{
				temp=bt[i];
				bt[i]=bt[j];
				bt[j]=temp;
				temp=p[i];
				p[i]=p[j];
				p[j]=temp;
			}
		}
	}
	wt[0]=0;
	for(i=1;i<n;i++)
	{
		wt[i]=wt[i-1]+bt[i-1];
	}
	for(i=0;i<n;i++)
	{
		sum+=wt[i];
	}
	avg=(float)sum/n;
	printf("\n Waiting time for each process:-");
	for(i=0;i<n;i++)
	{
		printf("\n Waiting time for process P%d is %d sec.",p[i],wt[i]);
		
	}
	printf("\n Average waiting time is %f sec.",avg);
	getch();
	return 0;
}
