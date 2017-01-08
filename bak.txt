#include<reg51.h>
#define LED P2 
sbit   BUT=P3^7	;
sbit   L1=P3^0;
sbit   L2=P3^1; 
unsigned char num[]={0x3f,0x06,0x5b,0x4f,0x66,0x6d,0x7d,0x07,0x7f,0x6f};
unsigned char chen[2]={0};
void display();
void main( )
{
	int a=0,b=0,i;
	while(1)
	  { 
	  	  display();
	  	BUT=1;
		if(BUT==0)
		{
			i=1000;
			while(i--);
			if(BUT==0)
			{

			a++;
			if(a==9)
			{	 b++;
				chen[1]=num[b];
				a=0;
				if(b==10)  b=0;
			}
			chen[0]=num[a];
			while(BUT==0);	   //À… ÷ºÏ≤‚



			}		

		 }
	   }



}
void display()
{
	int i,b;
	for(i=0;i<2;i++)
	{
		switch(i)
				{
					case(0): L1=1;L2=0;break;
					case(1): L1=0;L2=1;break;
				}
			
				LED=chen[i];
				b=1000;
				while(b--);
				LED=0x00;		   //œ˚“˛
			}

}