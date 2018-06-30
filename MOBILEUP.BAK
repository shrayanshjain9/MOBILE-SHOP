#include<conio.h>
#include<stdio.h>
#include<string.h>
#include<process.h>
#include<fstream.h>
int assignmodelno();
class mobile
{
  int modelno;
  char mcompany[31];
  char mname[31];
  int price;
  int qty;
  int caminmp,ramingb,romingb;
  int battery;
  float screensize;
  public:
	  void create_mobile()
	  {
            modelno=assignmodelno();
	    cout<<"\n\n\tYour model no of the mobile is=>"<<modelno<<endl;
	    cout<<"\n\tPlease Enter the mobile company name=>";
	    gets(mcompany);
	    cout<<"\n\tPlease Enter the mobile name=>";
	    gets(mname);
	    cout<<"\n\tPlease Enter the price of the mobile=>";
	    cin>>price;
	    cout<<"\n\tPlease Enter the quantity of the mobile=>";
	    cin>>qty;
	    cout<<"\n\tPlease Enter the camera quality in MP=>";
	    cin>>caminmp;
	    cout<<"\n\tPlease Enter the RAM size in GB=>";
	    cin>>ramingb;
	    cout<<"\n\tPlease Enter the Battery size in MAh=>";
	    cin>>battery;
	    cout<<"\n\tPlease Enter the ROM size in GB=>";
	    cin>>romingb;
	    cout<<"\n\tPlease Enter the screen size in inches=>";
	    cin>>screensize;
	  }
	  void show_mobile()
	  {
	    cout<<"\n\n\tThe model no of the mobile is=>";
	    cout<<modelno;
	    cout<<"\n\tThe mobile company name is=>  ";
	    cout<<mcompany;
	    cout<<"\n\tThe mobile name is=>  ";
	    cout<<mname;
	    cout<<"\n\tThe price of the mobile is=>  ";
	    cout<<price;
	    cout<<"\n\tThe quantity of the mobile is=>  ";
	    cout<<qty;
	    cout<<"\n\tThe camera quality in MP is=>  ";
	    cout<<caminmp<<"MP";
	    cout<<"\n\tThe RAM size in GB is=>  ";
	    cout<<ramingb<<"GB";
	    cout<<"\n\tThe Battery size in MAh is=>  ";
	    cout<<battery<<"MAh";
	    cout<<"\n\tThe ROM size in GB is=>  ";
	    cout<<romingb<<"GB";
	    cout<<"\n\tThe screen size in inches is=>  ";
	    cout<<screensize<<"inches";
	  }
	  int retmodelno()
	  {
	    return modelno;
	  }
	  char* retmcompany()
	  {
	    return mcompany;
	  }
	  char* retmname()
	  {
	    return mname;
	  }
};
int nor();

void Addnewmobile()
{
   mobile M;
   fstream f("store.dat",ios::out|ios::binary|ios::app);
   M.create_mobile();
   f.write((char*)&M,sizeof(M));
   f.close();
   cout<<"\n\n\t<=The mobile has been added=>\n";
   getch();
}

void showallmobile()
{
  clrscr();
  mobile M;
  cout<<"\n\n\n\t\t<==DISPLAY ALL MOBILE==>\n\n";
  fstream f("store.dat",ios::in|ios::binary);
  while (f.read((char*)&M,sizeof(M)))
  {
    M.show_mobile();
    cout<<"\n\n===============================================================================\n";
    getch();
  }
  f.close();

}
void searchbycompany()
{ mobile M;
  char N[31];
  cout<<"\n\tEnter the company name to be searched=>";
  gets(N);
  int t=0;
  fstream f("store.dat",ios::in|ios::binary);
  while (f.read((char*)&M,sizeof(M)))
  {
   if (strcmpi(M.retmcompany(),N)==0)
   {
     M.show_mobile();
     getch();
     t=1;
   }
  }
  f.close();
  if(t==0)
  {
    cout<<"\n\n\tMobile company not found";
    getch();
  }

}

void searchbyname()
{
  char N[31];
  mobile M;
  cout<<"\n\tEnter the mobile name to be searched=>";
  gets(N);
  int t=0;
  fstream f("store.dat",ios::binary|ios::in);
  while (f.read((char*)&M,sizeof(M)))
  {
   if (strcmpi(M.retmname(),N)==0)
   {

     M.show_mobile();
     getch();
     t=1;
   }
  }
  f.close();
  if(t==0)
  {
    cout<<"\n\n\tMobile company not found";
    getch();
  }
}
void searchbymodelno()
{
  int N;
  mobile M;
  cout<<"\n\tEnter the model no of the mobile to be searched=>";
  cin>>N;
  int t=0;
  fstream f("store.dat",ios::binary|ios::in);
  while (f.read((char*)&M,sizeof(M)))
  {
   if (M.retmodelno()==N)
   {

     M.show_mobile();
     getch();
     t=1;
   }
  }
  f.close();
  if(t==0)
  {
    cout<<"\n\n\tModel no not found";
    getch();
  }
}

void modify_mobile()
{
    int no,found=0;
    clrscr();
    mobile M;
    cout<<"\n\tTo Modify ";
    cout<<"\n\tPlease Enter The model No. of The mobile=>";
    cin>>no;
    fstream f("store.dat",ios::in|ios::out|ios::binary);
    while(f.read((char*)&M,sizeof(M)) && found==0)
    {
      if(M.retmodelno()==no)
      {
	    M.show_mobile();
	    cout<<"\n\tPlease Enter The New Details of mobile=>"<<endl;
	    M.create_mobile();
	    int pos=-1*sizeof(M);
	    f.seekp(pos,ios::cur);
	    f.write((char*)&M,sizeof(M));
	    cout<<"\n\t mobile Updated";
	    found=1;
       }
     }
    f.close();
    if(found==0)
    cout<<"\n\t Mobile Not Found ";
    getch();
}

void delete_mobile()
{
  int r,t=0;
  mobile M;
  fstream f("store.dat",ios::in|ios::out|ios::binary);
  cout<<"\n\tEnter the model no to be deleted=>";
  cin>>r;
  fstream F2;
  F2.open("Temp.dat",ios::out|ios::binary);
  f.seekg(0,ios::beg);
  while (!f.eof())
  {
    f.read((char*)&M,sizeof(M));
    if (M.retmodelno()!=r)
    {
      F2.write((char*)&M,sizeof(M));
      t=1;
    }
  }
   f.close();
   F2.close();
   if (t==1)
   {
      remove("store.dat");
      rename("Temp.dat","store.dat");
      cout<<"\n\tMobile deleted";
   }
   else
   {
     cout<<"\n\tMobile not found";
   }
   getch();
}

 int nor()
 {
  ifstream f("store.dat",ios::binary);
  int r=0;                                   \
  mobile M;
  if(f.read((char*)&M,sizeof(M)))
  {
  r++;
  while(!f.eof())
  {
   f.read((char*)&M,sizeof(M));
   if(!f.eof())
   {
     r++;
   }
  }
 }
 else
 {

 f.close();
 return 0;
 }

 return r;
}


 int assignmodelno()
{

  int r=nor();
  mobile M;
  if (r==0)
  {
  return (1001);
  }
  else
  {

   ifstream f("store.dat",ios::binary);
   while(!f.eof())
   {
    f.read((char*)&M,sizeof(M));
   }
   r=M.retmodelno();
   f.close();
   return (r+1);
  }
 }

void owner()
{
  clrscr();
  char ch;
  cout<<"\n\n\n\t\t          OWNER MENU";
  cout<<"\n\n\t\t1.CREATE MOBILE";
  cout<<"\n\n\t\t2.DISPLAY ALL MOBILE";
  cout<<"\n\n\t\t3.SEARCH BY COMPANY ";
  cout<<"\n\n\t\t4.SEARCH BY NAME";
  cout<<"\n\n\t\t5.SEARCH BY MODEL NO";
  cout<<"\n\n\t\t6.MODIFY MOBILE DETAILS";
  cout<<"\n\n\t\t7.DELETE MOBILE";
  cout<<"\n\n\t\t8.EXIT";
  cout<<"\n\n\t\tPlease Enter Your Choice (1-8) ";
  ch=getche();
  switch(ch)
  {
    case '1':  clrscr(); Addnewmobile();      owner();   break;
    case '2':            showallmobile();     owner();   break;
    case '3':  clrscr(); searchbycompany();   owner();   break;
    case '4':  clrscr(); searchbyname();      owner();   break;
    case '5':  clrscr(); searchbymodelno();   owner();   break;
    case '6':  clrscr(); modify_mobile();     owner();   break;
    case '7':  clrscr(); delete_mobile();     owner();   break;
    case '8':                                            break;
    default:                        owner();
   }
}

void intro()
{
   clrscr();

   cout<<"\n\t";
   cout<<"||      || ||||||| ||      ||||||| |||||| ||||   |||| |||||||";
   cout<<"\n\t";
   cout<<"||      || ||      ||      ||      ||  || ||  |||  || ||     ";
   cout<<"\n\t";
   cout<<"||  ||  || |||||   ||      ||      ||  || ||  |||  || |||||  ";
   cout<<"\n\t";
   cout<<"||  ||  || ||      ||      ||      ||  || ||       || ||     ";
   cout<<"\n\t";
   cout<<"|||||||||| ||||||| ||||||| ||||||| |||||| ||       || |||||||";
   cout<<"\n\n\t\t\t\t      TO";
   cout<<"\n\n\t\t\t\t MOBILE SHOP";
   cout<<"\n\n\n\t\t   MADE BY=>> SHRAYANSH JAIN , PIYUSH & AJEET";
   cout<<"\n\n\n\t\t\t     KENDRIYA VIDYALAYA A.G.C.R ";
   cout<<"\n\n\n\t\t\t         CLASS:=>XII-G";
   getch();
}

void main()
{
  intro();
  clrscr();
  char pd[6];
  int i=0;
  cout<<"\n\n\n\n\n\n\t\t\tPlease Enter the password:\n";
  cout<<"\n\t\t\t";
   while(i<6)
  {
   pd[i]=getch();
   cout<<"*";
   ++i;
  }

    if(strcmp(pd,"123456")==0)
    {

     cout<<"\n\n\t\t\tYOU ARE AUTHORISED PERSON";
     cout<<"\n\t\t\tpress any key";
     getch();
     owner();
    }
    else
    {
     cout<<"\n\t\t\tWRONG PASSWORD!!!!!";
     cout<<"\n\t\t\tprogram is closing";
     getch();
   }
}














