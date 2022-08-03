#include <iostream>
#include <stdlib.h>
#include <time.h>
#include <fstream>

using namespace std;

class high_score
{
public:
    int score;
    high_score()
    {
        score=0;
    }
    void display()
    {
        cout<<"score is "<<score;
    }
    int getscore();
};
int high_score::getscore()
{
    return score;
}
void gridsystem(char* A[50],int Size)
{
    for(int i=0;i<(Size*3)+1;i++)
        cout<<'_';
    cout<<endl;
    for(int i=0;i<Size;i++)
    {
        cout<<'|';
        for(int j=0;j<Size;j++)
        {
            cout<<' '<<A[i][j]<<'|';
        }
        cout<<endl;
        for(int i=0;i<(Size*3)+1;i++)
        cout<<'_';
        cout<<endl;
    }
}
class grid
{
    char* A[50];
    char* B[50];
    int Size;
public:
    grid(int b)
    {
        Size=b;
        settraps();
    }
    void settraps();
    int traverse(int i,int j);
    void showgrid();
    void showgrid2();
    int checkwin();
};
int grid::checkwin()
{
    for(int i=0;i<Size;i++)
        for(int j=0;j<Size;j++)
            if(A[i][j]==' ')
                return 0;
    return 1;
}
void grid::settraps()
{
    int p;int z;int maxi;
    for(int i=0;i<Size;i++)
    {
        A[i]=new char[50];
        B[i]=new char[50];
        maxi=Size/2;
        z=0;
        ppt:{}
        for(int j=0;j<Size;j++)
        {
            p=rand()%2;
            B[i][j]=' ';
            if(z>=maxi)
            {
                p=0;
            }
            if(p==0)
            {
                A[i][j]=' ';
            }
            else
            {
                A[i][j]='*';z++;
            }
        }
        if(z==0)
           {
               goto ppt;
           }
    }
}
int grid::traverse(int i,int j)
{
    if(A[i][j]=='*')
        return -1;
    else if(A[i][j]=='+')
        return 0;
    else
    {
        A[i][j]='+';B[i][j]='+';
        if(checkwin())
            return 1;
        else
            return 2;
    }
}
void grid::showgrid()
{
    gridsystem(A,Size);
}
void grid::showgrid2()
{
    gridsystem(B,Size);
}

class Player
{
    char name[20];
    static char gameplayed[20];
    char winorlose;
    public:
    void getinfo()
    {
        cout<<"Enter name: ";
        cin>>name;
    }
    void winorlosestatus(char i)
    {
        winorlose=i;
        ofstream f;
        f.open("Gamelist.txt",ios::app);
        f<<name<<"     "<<winorlose<<endl;
        f.close();
    }
};
char Player::gameplayed[20]="Minesweeper";
int main()
{
    int chk;
    cout<<"GAMES-"<<endl;
    cout<<"1. MINESWEEPER        2. ODD AND EVEN"<<endl;
    cout<<"ENTER CHOICE"<<endl;
    cin>>chk;
    if (chk==1)
{
    cout<<"WELCOME TO MINESWEEPER"<<endl;
    cout<<"* denotes a mine, + denotes flag. Enjoy!"<<endl;
    Player p;
    p.getinfo();
    int b;
    givesize:
    {
        cout<<"Enter the size of grid: ";
        cin>>b;
        if(b<4)
        {
            cout<<"The size should atleast be 4,enter again: ";
            goto givesize;
        }
    }
    grid a(b);
    a.showgrid2();
    int c,r;
    do{
        cout<<"Enter the row to place flag: ";cin>>r;
        cout<<"Enter the column to place flag: ";cin>>c;
        b=a.traverse(r-1,c-1);
        if(b==0)
            cout<<"The flag is already present at this position"<<endl;
        else if(b==2)
        {
            cout<<"The flag is placed"<<endl;
            a.showgrid2();
        }
    }while(b!=-1 && b!=1);
    a.showgrid();
    if(b==-1)
    {
        cout<<"YOU LOSE, better luck next time";
        p.winorlosestatus('L');
    }
    else
    {
        cout<<"Congratulations, YOU WIN";
        p.winorlosestatus('W');
    }
}
else if (chk==2)
{
    char ch;
    int c=1,s=0,x,y,a=0,b,e,f=0,g=0,arr[5];
    cout<<"LETS PLAY ODD EVE"<<endl;
    cout<<"Enter 1 or 2 for toss"<<endl;
    ppp:
    cin>>b;
    srand(time(0));
    e=(rand()%2)+1;
    if (b==1 || b==2)
    {
         if (b!=e)
    {
         cout<<"You lose the toss"<<endl;
         srand(time(0));
         f=(rand()%2)+1;
         if (f==1)
         {
             cout<<"you bat first"<<endl;
             goto batting;
         }
         else
         {
             cout<<"you ball first"<<endl;
             goto bowling;
         }
    }
    else
        {
           cout<<"You won the toss"<<endl<<"What do you want, batting (enter 1) or bowling (enter 2) ?"<<endl;
           check:
           cin>>g;
           if(g==1)
           {
               cout<<"you bat first"<<endl;
               goto batting;
           }
           else if(g==2)
           {
               cout<<"you ball first"<<endl;
               goto bowling;
           }
           else
           {
               cout<<"please enter 1 or 2 "<<endl;
               goto check;
           }
        }
    }
   else
   {
       cout<<"Please enter 1 OR 2"<<endl;
       goto ppp;
   }
    batting:
        {
    while(c==1)
    {
        cout<<"Your number? "<<endl;
        cin>>x;
        if (x>10 || x<1)
        {
            cout<<"Enter no. from 1 TO 10"<<endl;
            continue;
        }
        y=(rand()%10)+1;
        cout<<"My number: "<<y<<endl;
        if(y==x)
        {
            if(f==1 || g==1)
            {
            cout<<"Out!"<<endl;
            cout<<"Your score: "<<s<<endl;
            cout<<"Your turn to bowl"<<endl;
            goto bowling;
            }
            else
             {
            cout<<"Out!"<<endl;
            cout<<"Your score: "<<s<<endl;
            cout<<"Game over"<<endl;
            goto endd;
             }
        }
        s+=x;
        cout<<"Your current score: "<<s<<endl;
         if (f==2 || g==2)
        {
            if (s>a)
            {
                goto endd;
            }
        }
    }
        }
    bowling:
{
        while (c==1)
        {
            cout<<"Your number?"<<endl;
        cin>>x;
         if (x>10 || x<1)
        {
            cout<<"Enter no. from 1 TO 10"<<endl;
            continue;
        }
        y=(rand()%10)+1;
        cout<<"My number: "<<y<<endl;
        if(y==x)
        {
            if (f==1 || g==1)
            {
            cout<<"Out!"<<endl;
            cout<<"My score: "<<a<<endl;
            goto endd;
            }
            else
             {
                 cout<<"Out!"<<endl;
                 cout<<"Your turn to bat"<<endl;
                 cout<<"My score: "<<a<<endl;
                 goto batting;
             }
        }
        a+=y;
        cout<<"My current score: "<<a<<endl;
        if (f==1 || g==1)
        {
             if (a>s)
        {
            goto endd;
        }
        }
        }
}
        endd:
            {
            if(a>s)
                cout<<"You lost"<<endl;
            else
                cout<<"You won"<<endl;
            }
    cout<<"Your total score: "<<s<<endl;
    cout<<"My total score: "<<a<<endl;
    fstream f1;
    f1.open("highscores.dat",ios::binary | ios::in);
    for(int i=0;i<5;i++)
    {
        high_score A;
        f1.read((char*)(&A),sizeof(A));
        arr[i]=A.score;
    }
    f1.close();
    if(s>arr[0] && s<arr[1])
    {
        arr[0]=s;
    }
    else if (s>arr[1] && s<arr[2])
    {
        arr[0]=arr[1];
        arr[1]=s;
    }
   else if (s>arr[2] && s<arr[3])
    {
        arr[0]=arr[1];
        arr[1]=arr[2];
        arr[2]=s;
    }
     else if (s>arr[3] && s<arr[4])
    {
        arr[0]=arr[1];
        arr[1]=arr[2];
        arr[2]=arr[3];
        arr[3]=s;
    }
     else if (s>arr[4])
    {
        arr[0]=arr[1];
        arr[1]=arr[2];
        arr[2]=arr[3];
        arr[3]=arr[4];
        arr[4]=s;
    }
    f1.open("highscores.dat",ios::binary | ios::out);
    for(int i=0;i<5;i++)
    {
        high_score A;
        A.score=arr[i];
        f1.write((char*)(&A),sizeof(A));
    }
    f1.close();
    cout<<"Show high score list? (Y/N)"<<endl;
    cin>>ch;
    if(ch=='Y')
    {
         for(int i=0;i<5;i++)
    {
        cout<<"High score "<<i+1<<endl;
        cout<<arr[4-i]<<endl;
    }
}
}
    return 0;



}
