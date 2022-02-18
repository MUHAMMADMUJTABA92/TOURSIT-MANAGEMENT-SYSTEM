#include <stdio.h>
#include<stdlib.h>
#include<string.h>
int z=1;
void adduser();
void login();
void economypackage();
void premiumpackage();
void deluxpackage();
void custompackage();
void ticketbooking();
void displayticket();
void printticket();
void cancelticket();
void brochure();
void display_economy();
void display_premium();
void display_delux();
void display_custom();
void logoutuser();

struct user{
	char n[100], p[100], u[100], s[100];
	char place[2];
	float price;
	int no_t;
} user;


	
int main(){
	printf("-----------------------------------------------------------------------------------------------------------------------");
    printf("\n\n\t\t\t\tWELCOME  TO FAST TRAVEL AND TOURS !");
    printf("\n\n-----------------------------------------------------------------------------------------------------------------------");

	int a;
	while(1){

		printf("\n1: Add user \n");
		printf("\n2: login user \n");
		printf("\n3: Brochure \n");
		printf("\n4: Exit \n");
		scanf("%d", &a);
		
		switch(a){
			case 1:
				adduser();
				break;
			case 2:
				login();
				system("pause");
				system("cls");
				break;
          case 3:
		      brochure();
			  system("pause");
			  system("cls");
			  break;
			  
		  case 4:
		  	  printf("\nExiting.......");
		  	  
		   	  exit(0);	
			  break;			
			default:
				printf("No such option..Retry!!\n");
				system("pause");
				system("cls");
		}
	}
}

//void adduser()
//{
//	printf("\n\n\t\tFOR FURTHER PROCEEDINGS PLEASE ENTER YOUR LOGIN CRETENCIALS BELOW! ");
//    printf("\n\n\t\t\t\t\tUSERNAME :");
//    fflush(stdin);
//	gets(user.n);
//    printf("\n\t\t\t\t\tPASSWORD :");
//    fflush(stdin);
//	gets(user.p);
//    system("CLS");
//    return;
//}

void login(){
	
//    printf("\n\n\t\t\t\t\tUSERNAME :");
//    fflush(stdin);
//	gets(user.u);
//    printf("\n\t\t\t\t\tPASSWORD :");
//    fflush(stdin);
//	gets(user.s);
	FILE *fp;
	int flag=0;
	char un[20], pwds[20], uname[20], pw[20];
	printf("\n\n\t\t\t\tPLEASE ENTER YOUR LOGIN CRETENCIALS BELOW!\n");
	printf ("Enter the username: ");
	scanf ("%s", uname);
	fp = fopen("uname.txt", "r");
	while (fscanf(fp,"%s", un)==1)
	{
		if (strcmp(un,uname)==0)
		{
			flag=1;
			break;
		}
		
	}
	if (flag==0)
	{
		printf ("Incorrect Username");
		getch();
		system("cls");
		return;
	}
	fclose(fp);
	
	fp = fopen("pword.txt", "r");
	printf ("Enter the password: ");
	scanf ("%s",pwds);
	
	flag = 0;
	while (fscanf(fp,"%s", pw)==1)
	{
		if (strcmp(pw,pwds)==0)
		{
			flag=1;
			break;
		}
	}
	if (flag==0)
	{
		printf ("Incorrect Password");
		getch();
		system("cls");
		return;
	}
	
    if(((strcmp(user.n,user.u))==0) && (strcmp(user.p,user.s)==0)){
        
        printf("\n\n\t\t\t\t\tSUCCESSFULLY LOGIN!\n");
        system("pause");
    	printf("\n");
    	system ("cls");
 int choice;
  	 int package_choice;
  	 while(1){
  	printf("-----------------------------------------------------------------------------------------------------------------------");
    printf("\n\n\t\t\t\tWELCOME  TO FAST TRAVEL AND TOURS !");
    printf("\n\n-----------------------------------------------------------------------------------------------------------------------");
    printf("\n\t\t PLEASE SELECT FROM THE CHOICE\n ");
    printf("\t'''''''''''''''''''''''''''''''");
    printf("\n\t\t\tBook Package - 1\n\t\t\tCheck Ticket - 2\n\t\t\tPrint Ticket - 3\n\t\t\tCancel Ticket -4\n\t\t\tLogout User - 5\n\t\t\tBrochure - 6\n\t\t\tExit - 7\n");
    scanf("%d",&choice);
    switch (choice)
    {
    	case 1:
    		printf("\t SELECT WHICH PACKAGE DO YOU WANT TO CHOOSE\n ");
    		printf("\t\t[1] ECONOMY PACKAGE\n\t\t[2] PREMIUM PACKAGE\n\t\t[3] DELUX PACKAGE\n\t\t[4] USER CUSTOM PACKAGE\n");
    		scanf("%d",&package_choice);
    		switch(package_choice)
    		{
    			case 1:
    				economypackage();
    				system("pause");
    				system("cls");
					break;
    			case 2:
    				premiumpackage();
    				system("pause");
    				system("cls");
					break;
    			case 3:
    				deluxpackage();
    				system("pause");
    				system("cls");
					break;
    			case 4:
					custompackage();
					system("pause");
					system("cls");
 					break;
 				default:
 					printf("invalid input\n");
 					system("pause");
 					system("cls");
			}
			break;
			
			case 2:
				displayticket();
				system("pause");
				system("cls");
			break;
			
			case 3:
				printticket();
				system("pause");
				system("cls");
			break;
			
			case 4:
				cancelticket();
				system("pause");
				system("cls");
				break;
			case 5:
				logoutuser();	
				return;
				break;
			case 6:
				brochure();
				system("pause");
				system("cls");
				break;
			case 7:
				printf("exiting.......");
				exit(0);
				break;
				
			default:
				printf("invalid input\n");
 					system("pause");
 					system("cls");				
	}
    	
    }

     }else{
        printf("\n\n\n\t\t\t\t\tINVALID USERNAME OR PASSWORD\n");
        printf("\n\n\t\tplease re-enter the Username or Password in login user\n\n");
        system("pause");
    	system ("cls");
	    return;
	}

}

void adduser()
{
	FILE *ptr;
	char username[20], un[20], pw[20],pwd[20];
	ptr = fopen ("uname.txt", "a+");
	printf ("Enter the Username: ");
	fflush(stdin);
	gets(username);
//	scanf ("%s", username);
	while (fscanf(ptr,"%s", un)==1)
	{
		if (strcmp(un,username)==0)
		{
			printf ("Username already exists.");
			getch();
			system("cls");
			return;
		}
	}
	fprintf (ptr,"\n%s",username);
	fclose(ptr);
	
	ptr = fopen("pword.txt", "a+");
	printf ("Enter the password: ");
	fflush(stdin);
//	scanf ("%s", pwd);
	gets(pwd);
	fprintf (ptr,"\n%s",pwd);
	fclose(ptr);
	system("cls");
}

void economypackage() {
	
  char ch;
  char choice2;
  float pricelistb[] = {30000.0,50000.0,15000.0,28000.0,120000.0,10000.0,20000.0, 22000.0,35000.0,150000.0};
  float pricelistp[] = {50000.0,70000.0,35000.0,48000.0,220000.0,20000.0,40000.0,42000.0,55000.0,350000.0};
  system("CLS");
  	display_economy();
  printf("\n enter the place code eg:( AA , BB): \n");
  fflush(stdin);
  gets(user.place);
  printf("\n WE PROVIDE YOU WITH ECONOMY SERVICES\n");
  printf("\nWould You Like to Confirm Booking?\n[1] - Yes\n[2] - No\n");
  scanf(" %c", & ch);
  if (ch != '1')
  return;
  if (strcmp(user.place, "AA") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 30000.0 \n[2] aeroplane == 50000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {
      user.price = pricelistp[0];
    } else {
      user.price = pricelistb[0];
    }ticketbooking();
    return;
  } 
  else if (strcmp(user.place, "BB") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 50000.0 \n[2] aeroplane == 70000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {

      user.price = pricelistp[1];
    }
	 else {
      user.price = pricelistb[1];
    }
	ticketbooking();
  } 
  else if (strcmp(user.place, "CC") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 15000.0 \n[2] aeroplane == 35000.0\n");
    scanf(" %c", & choice2);
  if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {
      user.price = pricelistp[2];
    } 
	else {
      user.price = pricelistb[2];
    }
	ticketbooking();
  } 
  else if (strcmp(user.place, "DD") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 28000.0 \n[2] aeroplane == 48000.0\n");
    scanf(" %c", & choice2);
  if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {

      user.price = pricelistp[3];
    }
	 else {
      user.price = pricelistb[3];
    }
	ticketbooking();
  }
   else if (strcmp(user.place, "EE") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 120000.0 \n[2] aeroplane == 220000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {
      user.price = pricelistp[4];
    } 
	else {
      user.price = pricelistb[4];
    }
	ticketbooking();
  } 
  else if (strcmp(user.place, "FF") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 10000.0 \n[2] aeroplane == 20000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {
	 user.price = pricelistp[5];
    }
	 else {
      user.price = pricelistb[5];
    }
	ticketbooking();
  } 
  else if (strcmp(user.place, "GG") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 20000.0 \n[2] aeroplane == 40000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {
      user.price = pricelistp[6];
    }
	 else {
      user.price = pricelistb[6];
    }
	ticketbooking();
  }
   else if (strcmp(user.place, "HH") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 22000.0 \n[2] aeroplane == 42000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {
    user.price = pricelistp[7];
    }
	 else {
      user.price = pricelistb[7];
    }
	ticketbooking();
  }
   	else if (strcmp(user.place, "II") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 35000.0 \n[2] aeroplane == 55000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {
      user.price = pricelistp[8];
    } else {
      user.price = pricelistb[8];
    }
	ticketbooking();
  } 
  	else if (strcmp(user.place, "JJ") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 40000.0 \n[2] aeroplane == 350000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {
		
      user.price = pricelistp[9];
    }
	 else {
      user.price = pricelistb[9];
    }
	ticketbooking();
  }
   else {
    printf("That tour code doesn't exist\n");
   return;
  }

}
void premiumpackage(){
char ch;
char choice2;
float pricelistb[]={40000.0,60000.0,25000.0,38000.0,120000.0,10000.0,30000.0,32000.0,45000.0,250000.0};
float pricelistp[]={60000.0,80000.0,45000.0,58000.0,320000.0,30000.0,50000.0,52000.0,65000.0,450000.0};
	system("CLS");
	display_premium();
printf ("\n enter the place code eg:( AA , BB): \n");
fflush(stdin);
gets(user.place);
printf("\n WE PROVIDE YOU WITH PREMIUM SERVICES\n");
    printf("\nWould You Like to Confirm Booking?\n[1] - Yes\n[2] - No\n");
    scanf(" %c",&ch);
    if(ch!='1')
     return;
    
    if(strcmp(user.place,"AA")==0){
	printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 40000.0 \n[2] aeroplane == 60000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2!='1'){
     user.price=pricelistp[0];
	}
 	else{ 
 	user.price=pricelistb[0];
    }
    ticketbooking();
    }
    
    else if(strcmp(user.place,"BB") == 0){
    printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 60000.0 \n[2] aeroplane == 80000.0\n");
   scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[1];
	}
	else{ 
 	 user.price=pricelistb[1];
    }ticketbooking();
}
   else if(strcmp(user.place,"CC") == 0){
    printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 25000.0 \n[2] aeroplane == 45000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[2];
	}
	else{ 
 	 user.price=pricelistb[2];
    }ticketbooking();
}
   else if(strcmp(user.place,"DD") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 38000.0 \n[2] aeroplane == 58000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[3];
	}
	else{ 
 	 user.price=pricelistb[3];
    }ticketbooking();
}
   else if(strcmp(user.place,"EE") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 120000.0 \n[2] aeroplane == 320000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[4];
	}
	else{ 
 	 user.price=pricelistb[4];
    }ticketbooking();
}
   else if(strcmp(user.place,"FF") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 10000.0 \n[2] aeroplane == 30000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[5];
	}
	else{ 
 	 user.price=pricelistb[5];
    }ticketbooking();
}
   else if(strcmp(user.place,"GG") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 30000.0 \n[2] aeroplane == 50000.0\n");
   scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[6];
	}
	else{ 
 	 user.price=pricelistb[6];
    }ticketbooking();
}
   else if(strcmp(user.place,"HH") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 32000.0 \n[2] aeroplane == 52000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[7];
	}
	else{ 
 	 user.price=pricelistb[7];
    }ticketbooking();
}
   else if(strcmp(user.place,"II") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 45000.0 \n[2] aeroplane == 65000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	user.price=pricelistp[8];
	}
	else{ 
 	 user.price=pricelistb[8];
    }ticketbooking();
}
   else if(strcmp(user.place,"JJ") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 50000.0 \n[2] aeroplane == 450000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2!='1'){
	
	 user.price=pricelistp[9];
	}
	else{ 
 	 user.price=pricelistb[9];
    }ticketbooking();
}
else
    {
        printf("That tour code doesn't exist\n");
        return ;
    }
}
void deluxpackage() {
  char ch;
  char choice2;
  float pricelistb[] = {50000.0,70000.0,35000.0,48000.0,220000.0,20000.0,40000.0,42000.0,55000.0,350000.0};
  float pricelistp[] = {70000.0,90000.0,55000.0,68000.0,420000.0,40000.0,60000.0,62000.0,75000.0,550000.0};
  system("CLS");
	display_delux();
  printf("\n enter the place code eg:( AA , BB): \n");
  fflush(stdin);
  gets(user.place);
  printf("\n WE PROVIDE YOU WITH DELUX SERVICES\n");

  printf("\nWould You Like to Confirm Booking?\n[1] - Yes\n[2] - No\n");
  scanf(" %c", & ch);
  if (ch != '1')
    return;

  if (strcmp(user.place, "AA") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 50000.0 \n[2] aeroplane == 70000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {
      user.price = pricelistp[0];
    } else {
      user.price = pricelistb[0];
    }ticketbooking();
  } 
  else if (strcmp(user.place, "BB") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 70000.0 \n[2] aeroplane == 90000.0\n");
    scanf(" %c", & choice2);
  if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {
      user.price = pricelistp[1];
    } else {
      user.price = pricelistb[1];
    }ticketbooking();
  } 
  else if (strcmp(user.place, "CC") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 35000.0 \n[2] aeroplane == 55000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1') {
   user.price = pricelistp[2];
    } else {
      user.price = pricelistb[2];
    }ticketbooking();
  } else if (strcmp(user.place, "DD") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 48000.0 \n[2] aeroplane == 68000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {

      user.price = pricelistp[3];
    } else {
      user.price = pricelistb[3];
    }ticketbooking();
  }
   else if (strcmp(user.place, "EE") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 220000.0 \n[2] aeroplane == 420000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {

      user.price = pricelistp[4];
    } else {
      user.price = pricelistb[4];
    }ticketbooking();
  } 
  else if (strcmp(user.place, "FF") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 20000.0 \n[2] aeroplane == 40000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {

      user.price = pricelistp[5];
    } else {
      user.price = pricelistb[5];
    }ticketbooking();
  } else if (strcmp(user.place, "GG") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 40000.0 \n[2] aeroplane == 60000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {

      user.price = pricelistp[6];
    } else {
      user.price = pricelistb[6];
    }ticketbooking();
  } else if (strcmp(user.place, "HH") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 42000.0 \n[2] aeroplane == 62000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {
      user.price = pricelistp[7];
    } else {
      user.price = pricelistb[7];
    }ticketbooking();
  } else if (strcmp(user.place, "II") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 55000.0 \n[2] aeroplane == 75000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2 != '1') {

      user.price = pricelistp[8];
    } else {
      user.price = pricelistb[8];
    }ticketbooking();
  } else if (strcmp(user.place, "JJ") == 0) {
    printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 60000.0 \n[2] aeroplane == 550000.0\n");
    scanf(" %c", & choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
	if (choice2 != '1') {

      user.price = pricelistp[9];
    } else {
      user.price = pricelistb[9];
    }ticketbooking();
  }
   
   else {
    printf("That tour code doesn't exist\n");
    return;
  }
}
void custompackage (){

char ch;
char choice2;
float pricelistb[]={30000.0,40000.0,15000.0,28000.0,90000.0,10000.0,20000.0,22000.0,35000.0,150000.0};
float pricelistp[]={50000.0,70000.0,25000.0,38000.0,210000.0,20000.0,30000.0,32000.0,55000.0,350000.0};

	system("CLS");
	display_custom();
printf ("\n enter the place code eg:( AA , BB): \n");
fflush(stdin);
gets(user.place);
printf("\n WE PROVIDE YOU WITH CUSTOM SERVICES\n");

    printf("\nWould You Like to Confirm Booking?\n[1] - Yes\n[2] - No\n");
    scanf(" %c",&ch);
    if(ch!='1')
       return;
    
    if(strcmp(user.place,"AA")==0){
	printf("\nWhat mode of  transport you prefer: \n");
    printf("[1] bus == 40000.0 \n[2] aeroplane == 60000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2!='1'){
     user.price=pricelistp[0];
	 }
 	else{ 
 	user.price=pricelistb[0];
    }ticketbooking();
    }
    
    else if(strcmp(user.place,"BB") == 0){
    printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 60000.0 \n[2] aeroplane == 80000.0\n");
   scanf (" %c",&choice2);
   if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2!='1'){
	
	 user.price=pricelistp[1];
	}
	else{ 
 	 user.price=pricelistb[1];
    }ticketbooking();
}
   else if(strcmp(user.place,"CC") == 0){
    printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 25000.0 \n[2] aeroplane == 45000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2!='1'){
	
	 user.price=pricelistp[2];
	}
	else{ 
 	 user.price=pricelistb[2];
    }ticketbooking();
}
   else if(strcmp(user.place,"DD") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 38000.0 \n[2] aeroplane == 58000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2!='1'){
	
	 user.price=pricelistp[3];
	}
	else{ 
 	 user.price=pricelistb[3];
    }ticketbooking();
}
   else if(strcmp(user.place,"EE") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 120000.0 \n[2] aeroplane == 320000.0\n");
    scanf (" %c",&choice2);
    if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}
    if (choice2!='1'){
	
	 user.price=pricelistp[4];
	}
	else{ 
 	 user.price=pricelistb[4];
    }ticketbooking();
}
   else if(strcmp(user.place,"FF") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 10000.0 \n[2] aeroplane == 30000.0\n");
    scanf (" %c",&choice2);
	if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}

    if (choice2!='1'){
	
	 user.price=pricelistp[5];
	}
	else{ 
 	 user.price=pricelistb[5];
    }ticketbooking();
}
   else if(strcmp(user.place,"GG") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 30000.0 \n[2] aeroplane == 50000.0\n");
   scanf (" %c",&choice2);
	if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}

    if (choice2!='1'){
	
	 user.price=pricelistp[6];
	}
	else{ 
 	 user.price=pricelistb[6];
    }ticketbooking();
}
   else if(strcmp(user.place,"HH") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 32000.0 \n[2] aeroplane == 52000.0\n");
    scanf (" %c",&choice2);
    	if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}

	if (choice2!='1'){
	
	 user.price=pricelistp[7];
	}
	else{ 
 	 user.price=pricelistb[7];
    }ticketbooking();
}
   else if(strcmp(user.place,"II") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 45000.0 \n[2] aeroplane == 65000.0\n");
    scanf (" %c",&choice2);
    	if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}

	if (choice2!='1'){
	
	 user.price=pricelistp[8];
	}
	else{ 
 	 user.price=pricelistb[8];
    }ticketbooking();
}
   else if(strcmp(user.place,"JJ") == 0){
	printf("\nWhat mode of  transport you prefer: \n");
	printf("[1] bus == 50000.0 \n[2] aeroplane == 450000.0\n");
    scanf (" %c",&choice2);
	if (choice2 != '1' && choice2 != '2'){
    	printf("INVALID SELECTION\n");
    	return;
	}

	if (choice2!='1'){
	
	 user.price=pricelistp[9];
	}
	else{ 
 	 user.price=pricelistb[9];
    }ticketbooking();
}
else
    {
        printf("That tour code doesn't exist\n");
        return ;
    }
}
void ticketbooking(){
	int n;
    printf("ENTER The Number Of Tickets You Want To Purchase: \n");
    scanf ("%d",&user.no_t);
    if (user.no_t==0){
    	printf("INVALID Number Of Tickets!");
    	return;
	}
	else {	
    user.price=user.price*user.no_t;
 	printf("BOOKING DONE!!!\n");
	}
	
}
void displayticket(){
printf("For User : %s \n",user.u);
printf("Number of Tickets = %d\nFor Total =%.2f\n",user.no_t,user.price);	
}
void printticket(){
	printf("\n%d number of tickets has been printed\n",user.no_t);
	return;
}
void cancelticket(){
	printf("NUMBER OF %d TICKETS HAS BEEN CANCELLED  \nTHANKS FOR VISITING !!\n",user.no_t);
	user.no_t=0;
	user.price=0;
	
}
void logoutuser(){
	printf("user %s has been sucessfully logged out\n ",user.u);
	return;
}
void display_economy()
{
		printf("\tPRICE LIST\t\t(ECONOMY PACKAGE BROCHURE)\n\n=============================\t\t\tBUS\t\tAEROPLANE\n1. AA - Antelope Canyon Tours\n\t\t\t\t\t\t30000.0\t\t50000.0\n2. BB - Grand Canyon Local Tours\n\t\t\t\t\t\t50000.0\t\t70000.0\n3. CC - San Francisco Local Tours\n\t\t\t\t\t\t15000.0\t\t35000.0\n4. DD - Miami Vacation\n\t\t\t\t\t\t28000.0\t\t48000.0\n""5. EE - Hawaii\n\t\t\t\t\t\t120000.0\t220000.0\n6. FF - Atlanta Vacation\n\t\t\t\t\t\t10000.0\t\t20000.0\n7. GG - San Francisco\n\t\t\t\t\t\t20000.0\t\t40000.0\n8. HH - Alaska Vacation\n\t\t\t\t\t\t22000.0\t\t42000.0\n9. II - Orlando Vacation\n\t\t\t\t\t\t35000.0\t\t55000.0\n10. JJ - South US Tour\n\t\t\t\t\t\t150000.0\t350000.0\n\n========================================================================\n");
}

void display_premium()
{
		printf("\tPRICE LIST\t\t(PREMIUM PACKAGE BROCHURE)\n\n=============================\t\t\tBUS\t\tAEROPLANE\n1. AA - Antelope Canyon Tours\n\t\t\t\t\t\t40000.0\t\t60000.0\n2. BB - Grand Canyon Local Tours\n\t\t\t\t\t\t60000.0\t\t80000.0\n3. CC - San Francisco Local Tours\n\t\t\t\t\t\t25000.0\t\t45000.0\n4. DD - Miami Vacation\n\t\t\t\t\t\t38000.0\t\t58000.0\n""5. EE - Hawaii\n\t\t\t\t\t\t125000.0\t320000.0\n6. FF - Atlanta Vacation\n\t\t\t\t\t\t10000.0\t\t30000.0\n7. GG - San Francisco\n\t\t\t\t\t\t30000.0\t\t50000.0\n8. HH - Alaska Vacation\n\t\t\t\t\t\t32000.0\t\t52000.0\n9. II - Orlando Vacation\n\t\t\t\t\t\t45000.0\t\t65000.0\n10. JJ - South US Tour\n\t\t\t\t\t\t250000.0\t450000.0\n\n========================================================================\n");
}
void display_delux()
{
		printf("\tPRICE LIST\t\t(DELUX PACKAGE BROCHURE)\n\n=============================\t\t\tBUS\t\tAEROPLANE\n1. AA - Antelope Canyon Tours\n\t\t\t\t\t\t40000.0\t\t60000.0\n2. BB - Grand Canyon Local Tours\n\t\t\t\t\t\t70000.0\t\t90000.0\n3. CC - San Francisco Local Tours\n\t\t\t\t\t\t35000.0\t\t55000.0\n4. DD - Miami Vacation\n\t\t\t\t\t\t48000.0\t\t68000.0\n""5. EE - Hawaii\n\t\t\t\t\t\t225000.0\t420000.0\n6. FF - Atlanta Vacation\n\t\t\t\t\t\t20000.0\t\t40000.0\n7. GG - San Francisco\n\t\t\t\t\t\t40000.0\t\t60000.0\n8. HH - Alaska Vacation\n\t\t\t\t\t\t42000.0\t\t62000.0\n9. II - Orlando Vacation\n\t\t\t\t\t\t55000.0\t\t75000.0\n10. JJ - South US Tour\n\t\t\t\t\t\t350000.0\t550000.0\n\n========================================================================\n");
}
void display_custom()
{
	printf("\tPRICE LIST\t\t(CUSTOM PACKAGE BROCHURE)\n\n=============================\t\t\tBUS\t\tAEROPLANE\n1. AA - Naltar valley\n\t\t\t\t\t\t30000.0\t\t50000.0\n2. BB - Kerthar area\n\t\t\t\t\t\t40000.0\t\t70000.0\n3. CC - Shangrila resort, Skardu\n\t\t\t\t\t\t15000.0\t\t25000.0\n4. DD - Ghanche District, Gilgit–Baltistan\n\t\t\t\t\t\t28000.0\t\t38000.0\n"
           "5. EE -  Gojal Valley\n\t\t\t\t\t\t9000.0\t\t21000.0\n6. FF - Ranikot Fort\n\t\t\t\t\t\t10000.0\t\t20000.0\n7. GG - Deosai Plains\n\t\t\t\t\t\t20000.0\t\t30000.0\n8. HH - Rama Meadow\n\t\t\t\t\t\t22000.0\t\t30000.0\n9. II - Ayun and Bamburet Valley\n\t\t\t\t\t\t35000.0\t\t55000.0\n10. JJ - White Palace Swat\n\t\t\t\t\t\t150000.0\t350000.0\n\n========================================================================\n");
}

void brochure ()
{
	int choice;
	printf("\t\t\t BROCHURE AND PACKAGES \t\t\t\n");
	printf("\t\t\t ======================\t\t\t\n\n");
	printf("\t\tEnter The Brochure Choise For Display:\n\n  ");
	printf("\t[1] Brochure For Delux Package\n\t[2] Brochure For Premium Package\n\t[3] Brochure For Economy Package\n\t[4] Brochure For Custom Package\n ");
	scanf("%d",&choice);
	switch (choice)
	{
		case 1:
			 display_delux();
			break;
		case 2:
			 display_premium();
			break;
		case 3:
			 display_economy();
			break;
		case 4:
			 display_custom();
			break;
				default:
				printf("No such option..Retry!!\n");
	}

	
}
