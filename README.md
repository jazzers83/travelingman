
#include<iostream>

using namespace std;

int a[10][10],visited[10],n,cost=0;

void get()
{
   cout<< "Enter No. of Cities: ";
   cin>> n;
   cout<<"---Cost Matrix--- \n";
   for( int i=0;i<n;i++)
   {
      cout<<"\n Enter Elements of Row #"<<i+1<<": ";
      for( int j=0;j<n;j++)
         cin>>a[i][j];
      visited[i]=0;
   }
}
int least(int c)
{
   int i,nc=999;
   int min=999,kmin = 0;
   for(i=0;i<n;i++)
   {
      if((a[c][i]!=0)&&(visited[i]==0))
         if(a[c][i]<min)
         {
            min=a[i][0]+a[c][i];
            kmin=a[c][i];
            nc=i;
         }
   }
   if(min!=999)
      cost+=kmin;
   return nc;
}
void mincost(int city)
{
   int ncity;
   visited[city]=1;
   cout<<city+1<<" –>";
   ncity=least(city);
   if(ncity==999)
   {
      ncity=0;
      cout<<ncity+1;
      cost+=a[city][ncity];
      return;
   }
   mincost(ncity);
}
void put()
{
   cout<<"  Minimum cost: ";
   cout<<cost;
}
int main()
{
   get();
   cout<<"\nThe Path is:\n\n";
   mincost(0);
   put();
   return 0;
}

