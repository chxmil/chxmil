#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int deposit(int holdmoney)
{ 
    int money;
    printf("\nmoney in account : %d", holdmoney);
    printf("\ndeposit : ");
    scanf("%d", &money);
    holdmoney = money + holdmoney;
    return holdmoney;
}

int Withdraw(int holdmoney,int credit)
{ 
    int money=0;
    char yn[1];
    printf("\nyou money acount : %d", holdmoney);
    printf("\nWithdraw money:");
    scanf("%d", &money);
    if(money>holdmoney){
        printf("\nis enough money");
        printf("\ndid you want to use credit y/n : ");
        scanf("%s", yn);
        if (strcmp(yn, "y") == 0) {
            credit=credit-money;
            printf("\nyou have use credit:%d", money);
            printf("\nyour credit:%d", credit);
        }
        
    }
    else{
        printf("\ncomplete!");
        printf("\nyou money acount : %d", holdmoney-money);
    }
    return holdmoney-money;
}

void data_acount(int holdmoney,int credit,int account)
{ 
    printf("\naccount : %d", account+1);
    if(holdmoney<0)
    {
    printf("\nyou money in account : is 0");
    printf("\nyou have credit : %d", credit+holdmoney);
    }
    else
    {
    printf("\nyou money in account : %d", holdmoney);
    printf("\nyou have credit : %d", credit);
    }
}

typedef struct std st;
struct std{
    char id[10];
    char name[30];
    char last_name[30];
    int account[30];
};

typedef struct account acc;
struct account{
    int money;
    int credit;
};

int main() {
    st std[100];
    acc account[30];
    int holdmoney,money;
    int i,j,p=0,n;
    int count[10],k=0,order[10][20],arrai[10][20];
    char m[10];
    
    for(i=0;i<11;i++)
    {
    account[i].money=0;
    count[i]=0;
    }
      for(i=0;i<5;i++)
    {
    account[i].credit=50000;
    account[i+5].credit=0;
    }
    printf("\nid:");
        scanf("%s", std[i].id);
    printf("\nname:");
        scanf("%s", std[i].name);
    printf("\nlast_name:");
        scanf("%s", std[i].last_name);
        
    for(i=0;i<1000;i++)
    {
    
    printf("\naccount id:");
        scanf("%s", m);
        int p = m[8] - '0';
        
    if (p == 0000){
        break;
    }
    p = p-1;
    printf("\n HELLO %s %s", std[i].name, std[i].last_name);
    printf("\nthe account:%d", p+1);
    for(j=0;j<1000;j++)
    {
    n=0;
    printf("\nyour order ||press|| \n 1 for deposit \n 2 for Withdraw \n 3 for account check \n 4 for exit");
        printf("\nenter : ");
        scanf("%d", &n);
            if(n==1){
                holdmoney=deposit(account[p].money);
                account[p].money=holdmoney;
                printf("\nyour money in account : %d", holdmoney);
                count[p]=count[p]+1;
                order[p][k]=1;
            }
            if(n==2){
                holdmoney=Withdraw(account[p].money,account[p].credit);
                account[p].money=holdmoney;
                printf("\nyour money in account : %d", holdmoney);
                count[p]=count[p]+1;
                order[p][k]=2;
            }
            if(n==3){
                printf("\ncheck");
                data_acount(account[p].money,account[p].credit,p);
                count[p]=count[p]+1;
                order[p][k]=3;
            }
        
            if (n==4){
                order[p][k]=3;
                break;
            }
            
            if (n>4){
                printf("\nwrong order press again!!!");
            }
            arrai[p][k]=holdmoney;
            k=k+1;
        }
        printf("\npress 0000 for exis and check all order");
    }
    printf("\ncheck\n");
    for(p=0;p<10;p++)
    {
    for(i=0;i<count[p];i++)
    {
    printf("\naccount %d ordernumber: %d", p+1,i+1);
    printf("\norder:%d", order[p][i]);
    printf("\nThe balance at that time : %d", arrai[p][i]);
    }
    }
    printf("\ncheck\n");
}
