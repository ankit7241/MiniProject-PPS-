#include<stdio.h>   
#include<stdlib.h> // rename() remove() 
#include<conio.h>  // getch() system("cls")
#include<string.h> // strcmpi() strcpy()
#include<direct.h> // delay()
struct Date
{ int dd,mm,yy;
};

struct Case
{ int caseno;
  char courtname[50],title[50],clientname[50],stageofcase[50];
  char casetype[20],act[50],address[100];
  struct Date doi,doj,nextdate;
}c;

void addcase()
{ FILE *fp;
  fp=fopen("cases.txt","ab+"); //ab+ denotes that file is opened in append binary mode
  if (fp==NULL)
  {printf("\n File Opening Error");
  }
  else 
  { system("CLS");
    fflush(stdin);
  printf("\n Enter Case number : ");
  scanf("%d",&c.caseno);
  fflush(stdin);
  printf("\n Enter Client Name : ");
  scanf("%s",c.clientname);
  printf("\n Enter Client's Address : ");
  scanf("%s",c.address);
  printf("\n Enter Court Name : ");
  scanf("%s",c.courtname);
  printf("\n Enter Case type : Criminal/Writ/Civil/Revenue : ");
  scanf("%s",c.casetype);
  printf("\n Title : ");
  scanf("%s",c.title);
  printf("\n Enter stage of case : ");
  scanf("%s",c.stageofcase);
  printf("\n Enter Act : ");
  scanf("%s",c.act);
  fflush(stdin);
  printf("\n Enter Date of Institution dd/mm/yy : ");
  scanf("%d %d %d",&c.doi.dd,&c.doi.mm,&c.doi.yy);
  printf("\n Enter Next Date of Hearing dd/mm/yy : ");
  scanf("%d %d %d",&c.nextdate.dd,&c.nextdate.mm,&c.nextdate.yy);
  printf("\n Enter Date of Judgement dd/mm/yy : ");
  scanf("%d %d %d",&c.doj.dd,&c.doj.mm,&c.doj.yy);
  fwrite(&c,sizeof(c),1,fp);
  printf("\n Record Added Successfully ! ");
  getch();
  fclose(fp);
  } 
}

void showcase()
{ FILE *fp;
  fp=fopen("cases.txt","rb");
  if(fp==NULL)
  printf("\n File Opening Error");
  else
  { system("CLS");
    printf("\n\t\t\t\t CASE RECORDS ");
    printf("\n\t\t\t\t ------------ ");
    while(fread(&c,sizeof(c),1,fp)==1)
    { printf("\n Case No. : %d",c.caseno);
      printf("\n Client Name : %s",c.clientname);
      printf("\n Enter Client's Address : %s",c.address);
      printf("\n Court Name : %s",c.courtname);
      printf("\n Case type : %s",c.casetype);
      printf("\n Title : %s",c.title);
      printf("\n Stage of Case : %s",c.stageofcase);
      printf("\n Act : %s",c.act);
      printf("\n Date of Institution : %d / %d / %d ",c.doi.dd,c.doi.mm,c.doi.yy);
      printf("\n Next Date of Hearing : %d / %d / %d ",c.nextdate.dd,c.nextdate.mm,c.nextdate.yy);
      printf("\n Enter Date of Judgement : %d / %d / %d ",c.doj.dd,c.doj.mm,c.doj.yy);
      printf("\n--------------------------------------------------------------------------------");
      getch();
    }
    printf("\n\n\t\t\t******************************************END OF FILE****************************************");
    getch();
    fclose(fp);
  }
}  
  
void searchcase()
{ FILE *fp;
  fp=fopen("cases.txt","rb");
  if(fp==NULL)
   printf("\n File Opening Error");
  else
  { int cno,flag=0;
    printf("\n Enter Case Number of the Record : ");
    scanf("%d",&cno);
    while(fread(&c,sizeof(c),1,fp)==1)
    { if(cno==c.caseno)
      { flag=1;
        system("cls");
        printf("\n Record Found ! Press Enter to see.");
        getch();
        system("cls");
        printf("\n Case No. : %d",c.caseno);
        printf("\n Client Name : %s",c.clientname);
        printf("\n Enter Client's Address : %s",c.address);
        printf("\n Court Name : %s",c.courtname);
        printf("\n Case type : %s",c.casetype);
        printf("\n Title : %s",c.title);
        printf("\n Stage of Case : %s",c.stageofcase);
        printf("\n Act : %s",c.act);
        printf("\n Date of Institution : %d / %d / %d ",c.doi.dd,c.doi.mm,c.doi.yy);
        printf("\n Next Date of Hearing : %d / %d / %d ",c.nextdate.dd,c.nextdate.mm,c.nextdate.yy);
        printf("\n Enter Date of Judgement : %d / %d / %d ",c.doj.dd,c.doj.mm,c.doj.yy);
        printf("\n--------------------------------------------------------------------------------");
        getch();
      }
    }
    if(flag==0)
    { printf("\n Record Not Found ! :/");
      getch();
    } 
    fclose(fp);
  }


}

void delcase()
{ FILE *fp,*fq;
  fp=fopen("cases.txt","rb");
  fq=fopen("temp.txt","ab+");
  if(fp==NULL || fq==NULL)
  {printf("Deletion Process Failed :/");
   getch();
  }
  else
  { int cno,flag=0;
    printf("\n Enter Case Number to be deleted : ");
    scanf("%d",&cno);
    while(fread(&c,sizeof(c),1,fp)==1)
    { if(cno!=c.caseno)
       fwrite(&c,sizeof(c),1,fq);
      else
       flag=1;
    }
    fclose(fp);
    fclose(fq);
    if(flag==0)
    { printf("\n Record Not Found!");
      getch();
      remove("temp.txt");
    }
    else
    { printf("\n Record Deleted Successfully");
      getch();
      remove("cases.txt");
      rename("temp.txt","cases.txt");
    }
  }

}

void modcase(FILE **fr)
{ system("CLS");
  printf("\n Enter Case number : ");
  scanf("%d",&c.caseno);
  fflush(stdin);
  char clntnm[50],add[100],crtnm[50],ctype[50],title_[50],act_[50],stage[50];
  printf("\n Update ClientName or Press R to Retain old value : ");
  scanf("%s",clntnm);
  if(strcmpi(clntnm,"R")!=0)
  strcpy(c.clientname,clntnm);
  printf("\n Update Client's Address or Press R to Retain old value : ");
  scanf("%s",add);
  if(strcmpi(add,"R")!=0)
  strcpy(c.address,add);
  printf("\n Update Court Name or Press R to Retain old value : ");
  scanf("%s",crtnm);
  if(strcmpi(crtnm,"R")!=0)
  strcpy(c.courtname,crtnm);
  printf("\n Update Case type or Press R to Retain old value : ");
  scanf("%s",ctype);
  if(strcmpi(ctype,"R")!=0)
  strcpy(c.casetype,ctype);
  printf("\n Update Title or Press R to Retain old value : ");
  scanf("%s",title_);
  if(strcmpi(title_,"R")!=0)
  strcpy(c.title,title_);
  fflush(stdin);
  printf("\n Update stage of case or Press R to Retain old value : ");
  scanf("%s",stage);
  if(strcmpi(stage,"R")!=0)
  strcpy(c.stageofcase,stage);
  printf("\n Update Act or Press R to Retain old value : ");
  fflush(stdin);
  scanf("%s",act_);
  if(strcmpi(act_,"R")!=0)
  strcpy(c.act,act_);
  fflush(stdin);
  //printf("\n Enter Date of Institution dd/mm/yy : ");
  //scanf("%d %d %d",&c.doi.dd,&c.doi.mm,&c.doi.yy);
  printf("\n Enter Next Date of Hearing dd/mm/yy : ");
  scanf("%d %d %d",&c.nextdate.dd,&c.nextdate.mm,&c.nextdate.yy);
  printf("\n Enter Date of Judgement dd/mm/yy : ");
  scanf("%d %d %d",&c.doj.dd,&c.doj.mm,&c.doj.yy);
  fseek(*fr,-(long)sizeof(c),1);
  fwrite(&c,sizeof(c),1,*fr);
  
}

void modifycase()
{ FILE *fp;
  fp=fopen("cases.txt","rb+");
  if(fp==NULL)
  printf("\n Modification Process Failed !");
  else
  { int cno,flag=0;
    printf("\n Enter Case Number to be Modified : ");
    scanf("%d",&cno);
    while(fread(&c,sizeof(c),1,fp)==1)
    { if(c.caseno==cno)
      { 
        flag=1;
        modcase(&fp);
        //fseek(fp,-(long)sizeof(c),1);
        //fwrite(&c,sizeof(c),1,fp);
        break;
      }
    }
     
    fclose(fp);
    if(flag==1)
    printf("\n File Modified Successfully !");
    else printf("\n Record Not Found :/");
    getch();
  }


}

void loading()
{ int i,j;
  for (i=1;i<=50;i++)
 { system("cls");
   printf("\n\n\n\n\t\t\t\t\t LOADING... \n\t\t") ;
   for(j=1;j<=i;j++)
    printf("_");
   printf("\n\n\t\t\t\t %d percent complete",2*i);
   if(i>1 &&i<20)
   printf("\n\n\t\t\t Creating Temporary files... ") ;
   else
   if(i>20 &&i<40)
	 printf("\n\n\t\t\t Accessing Main Memory...") ;
   else
	 if(i>40 &&i<48)
	 printf("\n\n\t\t\t Accessing Cache Memory... ") ;
	 //else
	 //printf("\n\n\t\t\t Press enter to continue.");
   //delay(150-i*3);
   
 }

}


void main()
{ int choice;
  loading();
  do
  { system("CLS");
    printf("\t\t\t\t\tCASE FILE HANDLING");
    printf("\n\t\t\t\t\t------------------");
    printf("\n 1. Add a Case\n");
    printf("\n 2. Show all Cases\n");
    printf("\n 3. Search a Case\n");    
    printf("\n 4. Delete a Case\n");
    printf("\n 5. Modify a Case\n");
    printf("\n 6. Exit\n");
    printf("\n Enter your choice : ");   
    scanf("%d",&choice); 
    switch(choice)
    { case 1 : addcase(); break;
      case 2 : showcase(); break;
      case 3 : searchcase(); break;
      case 4 : delcase(); break;
      case 5 : modifycase(); break;
    }
  } while(choice!=6);
}