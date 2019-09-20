# JAVA-multithreading-


import java.util.Scanner;
import java.util.*;
import java.lang.*;
class Account 
{
public int acc_bal=600;

synchronized void work()
{

 while (acc_bal<2000)
{
    System.out.println("Enter the depositing amount\n");
    int temp;
    temp=0;
    Scanner inp=new Scanner (System.in);
    temp=inp.nextInt();
    if (temp>1 && temp<200)
    {
    acc_bal=acc_bal+temp;
    System.out.println("Current balance after depositing money is:"+acc_bal);
    }
    else
    {
        System.out.println("Enter the amount between 1 and 200");
    }
    
}
}

    
   
 
 synchronized void  work2()
{
            
        
while(acc_bal>500)
    { 
    System.out.println("Enter the withdrawing amount");
    int temp2;
    Scanner inp2=new Scanner(System.in);
    temp2=inp2.nextInt();
    if(temp2>1 && temp2<250)
        {
        
        
        acc_bal=acc_bal-temp2;
        if(acc_bal<500)
            {
                acc_bal=acc_bal+temp2;
                System.out.println("You cant withdraw money :"+temp2);
                System.out.println("You can withdraw only :"+(acc_bal-500));
            }
        System.out.println("Current balance after withdrawing  is: "+acc_bal);
        }
    }


}
}
 





class mythread extends Thread
{
    Account x;
    mythread(Account x)
    {
        this.x=x;
    }
   public void run()
   {
       
       x.work();
   }
}
class mythread2 extends Thread
{
    Account x;
    mythread2(Account x)
    {
        this.x=x;
    }
   public void run()
   {
       
       x.work2();
   }
}
public class Assignment3 {
    public static void main(String[] args){
       
        Account x =new Account();
        mythread father =new mythread(x);
        mythread2 son =new mythread2(x);
        System.out.println("*********************************DO U WANT TO DEPOSIT THE MONEY ***************************\n PRESS 1  TO continue\n ********************************DO U  WANT TO WITHDRAW MONEY*********************\n PRESS 2 TO CONTINUE \n ******************************** OR PRESS 0 TO REJECT*************************" );
        Scanner user=new Scanner(System.in);
        int input=user.nextInt();
        if(input==1)
            
            {
                
               father.start();
             son.start();
        }
        else if(input==2)
        {
        son.start();
        }
        else
           System.exit(0);
        
          /*
        System.out.println("FATHER DO U WANT TO DEPOSIT: THEN PRESS 5:ELSE PRESS  6:");
           for (int i=0;i<1;i++)
        {
            
        
        Scanner dep=new Scanner (System.in);
        int dep1=dep.nextInt();
        if(dep1==5)
        {mythread f=new mythread();
        
                f.start();
             son.start();
            i--;
        }
        
        else
            System.exit(0);
        
        }
        */
    }
    
}
