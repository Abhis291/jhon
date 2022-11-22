#include<stdio.h>
void menu()
{
printf("\n\n\t\t\t!!BANKERS ALGORITHM!!");
printf("\n\n\t\t1.ACCEPT");
printf("\n\n\t\t2.DISPLAY");
printf("\n\n\t\t3.SAFE SEQUENCE");
printf("\n\n\t\t4.ENTER REQUEST");
printf("\n\n\t\t5.QUIT");
}
void accept(int a[][40],int p,int r)
{
int i,j;
for(i=0;i<p;i++)
{
for(j=0;j<r;j++)
{
printf("\nENTER RESOURCE R%d FOR PROCESS P%d : ",j,i);
scanf("%d",&a[i][j]);
}
}
}
void display(int a[][40],int p,int r)
{
int i,j;
printf("\n\t");
for(i=0;i<r;i++)
printf("\tR%d ",i);
for(i=0;i<p;i++)
{
printf("\n\n\tP%d ",i);
for(j=0;j<r;j++)
{
printf("\t%d",a[i][j]);
}
}
}
void accept_total(int total[],int r)
{
int i;
for(i=0;i<r;i++)
{
printf("\nENTER R%d: ",i);
scanf("%d",&total[i]);
}
}
void disp_total(int total[],int r)
{
int i;
printf("\n\t");
for(i=0;i<r;i++)
printf("\tR%d ",i);
printf("\n\n\t");
for(i=0;i<r;i++)
{
printf("\t%d",total[i]);
}
}
void cal_need(int all[][40],int max[][40],int need [][40],int p,int r)
{
int i,j;
for(i=0;i<p;i++)
{
for(j=0;j<r;j++)
{
need[i][j]=max[i][j]-all[i][j];
}
}
}
void cal_avail(int all[][40],int total[],int avail [],int p,int r)
{
int i,j,sum;
for(i=0;i<r;i++)
{
sum=0;
for(j=0;j<p;j++)
{
sum=sum+all[j][i];
}
avail[i]=total[i]-sum;
}
}
int safe_seq(int all[][40],int need[][40],int avail [],int p,int r)
{
int seq[15],work[40],i,j,flag=0,k=0;
int finish[20]={0};
for(i=0;i<r;i++)
work[i]=avail[i];
while(flag==0)
{
flag=1;
for(i=0;i<p;i++)
{
if(finish[i]==0)
{
for(j=0;j<r;j++)
{
if(need[i][j]>work[j])
break;
}
if(j==r)
{
finish[i]=1;
for(j=0;j<r;j++)
work[j]=work[j]+all[i][j];
seq[k++]=i; //store proc no. in seq
flag=0;
}
}
}
}
if(k==p)
{
printf("\n\nSYSTEM IS IN SAFE SEQUENCE & SAFE SEQUENCE IS::\n\n");
for(i=0;i<k;i++)
printf("\tP%d",seq[i]);
return 1;
}
return 0;
}
void request(int all[][40],int need[][40],int avail [],int p,int r)
{
int dall[40][40],dneed[40][40],davail[40];
int req[20],n,i,j;
printf("\n\nENTER PROCESS NO.:: ");
scanf("%d",&n);
printf("\n\nENTER REQUEST:: ");
for(i=0;i<r;i++)
{
printf("\nENTER R%d: ",i);
scanf("%d",&req[i]);
}
for(i=0;i<r;i++)
{
if(req[i]>avail[i] || req[i]>need[n][i])
{
printf("\n\nREQUEST CANNOT BE GRANTED");
return;
}
}
for(i=0;i<p;i++)
{
for(j=0;j<r;j++)
{
dall[i][j]=all[i][j];
dneed[i][j]=need[i][j];
}
}
for(i=0;i<r;i++)
{
davail[i]=avail[i];
}
for(i=0;i<r;i++)
{
dall[n][i]=dall[n][i]+req[i];
dneed[n][i]=dneed[n][i]-req[i];
davail[i]=davail[i]-req[i];
}
if(safe_seq(dall,dneed,davail,p,r)==1)
printf("\n\nREQUEST SHOULD BE GRANTED");
else
printf("\n\nREQUEST SHOULD NOT BE GRANTED");
}
int main()
{
int all[40][40],need[40][40],max[40][40],p,r;
int avail[40],total[40];
int ch,x;
while(ch!=5)
{
menu();
printf("\n\nENTER YOUR CHOICE::");
scanf("%d",&ch);
switch(ch)
{
case 1:
printf("\nENTER NO. OF PROCESSES:: ");
scanf("%d",&p);
printf("\nENTER NO. OF RESOURCES:: ");
scanf("%d",&r);
printf("\n\nENTER ALLOCATION MATRIX::");
accept(all,p,r);
printf("\n\nENTER MAXIMUM MATRIX::");
accept(max,p,r);
printf("\n\nENTER TATAL NO. OF RESOURCES:\n");
accept_total(total,r);
cal_need(all,max,need,p,r);
cal_avail(all,total,avail,p,r);
break;
case 2:
printf("\n\nALLOCATION MATRIX::");
display(all,p,r);
printf("\n\nMAXIMUM MATRIX::");
display(max,p,r);
printf("\n\nNEED MATRIX::");
display(need,p,r);
printf("\n\nTOTAL RESOURCES ARE:");
disp_total(total,r);
printf("\n\nTOTAL AVAILABLE RESOURCES ARE:");
disp_total(avail,r);
break;
case 3:
x=safe_seq(all,need,avail,p,r);
if(x==0)
printf("\n\nSYSTEM IS NOT IN SAFE SEQUENCE");
else
printf("\n");
break;
case 4:
request(all,need,avail,p,r);
break;
}
}
}
