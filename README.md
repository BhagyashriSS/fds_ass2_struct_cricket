# fds_ass2_struct_cricket




#include<stdio.h>
#include<string.h>


struct Player
{
	char name[20];
	int age;
	char country[20];
	char category[20];
	int ODI;
	int T_20;
	float batting_avg;
	int wicket;
};
typedef  struct Player player;


void input(player  c[]);
void display_all(player c[]);
void no_batsman( player c[]);
void high_avg_score( player c[]);
void no_bowler(player c[]);
void max_wicket(player c[]);
void particular_player(player c[]);
static int i=0;


int main()
{
    player c[11];
	int choice;
	do
	{
		printf("\n***MENU***");
		printf("\nenter 1 to to give  input ");
		printf("\nenter 2 to sort as per the avg batting score");
		printf("\nenter 3 to display number  batsman of particular country");
		printf("\nenter 4 to  diplay batsman with highest average score");
		printf("\nenter 5 to  diplay number of bowlers of paricular country");
		printf("\nenter 6 to  diplay bowler that that has taken maximum wickets");
		printf("\nenter 7 to  show particular player's entire display board information");
		printf("\nenter 8   to exit ");
		printf("\n\nenter your choice");
		scanf("%d",&choice);
		if(choice>8 || choice<1)
		{
		printf("\nwrong choice please enter correct choice");
		  continue;}
		switch(choice)
		{
			case 1:
			      input(c);
			       break;
			case  2:
				  display_all(c);
				  break;
			case 3:
				  no_batsman(c);
				  break;
			case  4:
				  high_avg_score(c);
				  break;
			case 5:
				  no_bowler(c);
				  break;
			case 6:
				  max_wicket(c);
				  break;
			case 7:
				  particular_player(c);
				  break;
			case  8:
				  printf("thank you");
				  return    0;
		}
	} while(choice!=8);

}


	 void input	(player  c[])
	 {
	 	
	 	printf("\nenter data for player");
	 	printf("\nenter name of player  ");
	 	scanf("%s",c[i].name);
	 	printf("\nenter age :");
	 	scanf("%d",&c[i].age);
	 	printf("\nenter country");
	 	scanf("%s",c[i].country);
	 	printf("\nenter category of player [batsman,bowlwer,wicket_keeper,all_rounder]");
	 	scanf("%s",c[i].category);
	 	printf("\nenter number of ODIs played");
	 	scanf("%d",&c[i].ODI);
	 	printf("\nenter number of 20-20 played");
	 	scanf("%d",&c[i].T_20);
	 	printf("enter average batting score");
	 	scanf("%f",&c[i].batting_avg);
	 	printf(" enter total numbers of wickets taken");
	 	scanf("%d",&c[i].wicket);
	 	i++;
	 }


	 void display_all(player  c[])
	 {
	 	//printf("%d",i);
	 	if(i==0)
		 {
		   printf("\nno records");
		   return ;
		   }
       int k,j;player temp;//insertion sort
       for(k=1;k<i;k++)
       {
          j=k-1;
          temp=c[k];
          while(j>-1 && c[j].batting_avg>temp.batting_avg)
          {
            c[j+1]=c[j];
            j--;
          }
          c[j+1]=temp;

       }
		printf("\n name\t age\tcountry\tcategory\tODI\tT_20\tavg_batting score\twicket");
		for(int j=0;j<i;j++)
		{
			printf("\n%s\t%d\t%s\t%s\t%d\t%d\t%f\t     %d",c[j].name,c[j].age,c[j].country,c[j].category,c[j].ODI,c[j].T_20,c[j].batting_avg,c[j].wicket);
		}
	 	
	 }


	 void no_batsman( player c[])
	 {
	 	
	 	char cntry[20];
	 	int count=0,n,m;
	 	printf("enter name of country");
	 	scanf("%s",cntry);
	 	for(int j=0;j<i;j++)
	 	{
	 	   n=	strcmp(cntry,c[j].country);
	 	   m= strcmp("batsman",c[j].category);
	 	   if(n==0 && m==0)
	 	    count++;
		 }
		 printf("\n%d batsman are there of  country %s",count,cntry);
	 }
	 


void  high_avg_score( player c[])
{
	int j;int loc=0;
	float max=c[0].batting_avg;
	for( j=1;j<i;j++)
	{
		if(max<c[j].batting_avg){
		    max=c[j].batting_avg;
        loc=j;}
	}
	//printf("\n batsman with highest average score is %s with score %f",c[loc].name ,max);
   printf("\n name\t age\tcountry\tcategory\tODI\tT_20\tavg_batting score\twicket");
	 	   	  printf("\n%s\t%d\t%s\t%s\t%d\t%d\t%f\t     %d",c[loc].name,c[loc].age,c[loc].country,c[loc].category,c[loc].ODI,c[loc].T_20,c[loc].batting_avg,c[loc].wicket);
}


void no_bowler( player c[])
	 {
	 	
	 	char cntry[20];
	 	int count=0,n,m;
	 	printf("enter name of country");
	 	scanf("%s",cntry);
	 	for(int j=0;j<i;j++)
	 	{
	 	   n=	strcmp(cntry,c[j].country);
	 	   m= strcmp("bowler",c[j].category);
	 	   if(n==0 && m==0)
	 	    count++;
		 }
		 printf("\n%d bowlers are there of  country %s",count,cntry);
	 }


void  max_wicket( player c[])
{
	int j;int loc1=0;
	float max=c[0].wicket;
	for( j=0;j<i;j++)
	{
		if(max<c[j].wicket){
		    max=c[j].wicket;
        loc1=j;}
	}
//	printf("\n bowler with maximum is %s with score %f wickets",c[loc].name ,max);
   printf("\n name\t age\tcountry\tcategory\tODI\tT_20\tavg_batting score\twicket");
	 	   	  printf("\n%s\t%d\t%s\t%s\t%d\t%d\t%f\t     %d",c[loc1].name,c[loc1].age,c[loc1].country,c[loc1].category,c[loc1].ODI,c[loc1].T_20,c[loc1].batting_avg,c[loc1].wicket);
}	 


void particular_player(player c[])
{
   	    char Name[20];
	 	int count=0,n;
	 	printf("\nenter name of player to display his full information");
	 	scanf("%s",Name);
	 	for(int j=0;j<i;j++)
	 	{
	 	   n=	strcmp(Name,c[j].name);
	 	   if(n==0)
			{
	 	   	  printf("\n name\t age\tcountry\tcategory\tODI\tT_20\tavg_batting score\twicket");
	 	   	  printf("\n%s\t%d\t%s\t%s\t%d\t%d\t%f\t     %d",c[j].name,c[j].age,c[j].country,c[j].category,c[j].ODI,c[j].T_20,c[j].batting_avg,c[j].wicket);
	 	   	  return ;
			}
	 	    
		 }
		
}
