# Jhoan
#include<conio.h>
#include<stdio.h>
#include<stdlib.h>
#include<iostream>
#include<string.h>
#include<windows.h>
#include<fstream>

using namespace std;
void gotoxy(short x, short y)                                                         
{
 COORD pos ={x,y};
 SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), pos);
}

FILE *archivo;
long int dir_fisica, dir_logica;

struct cita
{
	char nombre[30];
	char apellido[30];
	char ced[15];
	char cel[30];
	char pel[30];
	char fecha[30];
	char hora[30];
cita *sig;												 
};

cita *p,*ini,*fin;

struct cita registro;
char continuar='s';
int aux=0;
char auxcc [15];

void crearini()
{system ("cls");
 ini=NULL;
 fin=NULL;
 while ((continuar=='s')||(continuar=='S'))
  { 
  	 p=new cita;
  	 gotoxy(50,4);cout<<"Nombre: ";cin>>p->nombre;
  	 gotoxy(50,5);cout<<"Apellido: ";cin>>p->apellido;
	 gotoxy(50,6);cout<<"C.C: ";cin>>p->ced;  	
	 gotoxy(50,7);cout<<"Celular: ";cin>>p->cel;
	 gotoxy(50,8);cout<<"Peluquero: ";cin>>p->pel;
	 gotoxy(50,9);cout<<"Fecha: ";cin>>p->fecha;
	 gotoxy(50,10);cout<<"Hora: ";cin>>p->hora;
	 gotoxy(40,12);cout<<"Presione <s> para agregar mas datos: ";cin>>continuar;
 	 if(ini==NULL)
	 {
	  ini=p;
	  p->sig=NULL;	
	  fin=p;
	 }
	 else
	 {
	  p->sig=ini;
	  ini=p;
	 }
   system ("cls");  
  }
  aux=1;
}
void crearfin()
{system ("cls");
 ini=NULL;
 while ((continuar=='s')||(continuar=='S'))
  { 
  	 p=new cita;
  	 gotoxy(50,4);cout<<"Nombre: ";cin>>p->nombre;
  	 gotoxy(50,5);cout<<"Apellido: ";cin>>p->apellido;
	 gotoxy(50,6);cout<<"C.C: ";cin>>p->ced;  	
	 gotoxy(50,7);cout<<"Celular: ";cin>>p->cel;
	 gotoxy(50,8);cout<<"Peluquero: ";cin>>p->pel;
	 gotoxy(50,9);cout<<"Fecha: ";cin>>p->fecha;
	 gotoxy(50,10);cout<<"Hora: ";cin>>p->hora;
	 gotoxy(40,12);cout<<"Presione <s> para agregar mas datos: ";cin>>continuar;
 	 if(ini==NULL)
	 {
	  ini=p;
	  p->sig=NULL;
	  fin=p;	
	 }
	 else
	 {
	  fin->sig=p;
	  fin=p;
	  p->sig=NULL;
	 }
   system ("cls");  
  }
  aux=1;
}
void ver()
{int pos=2;
 p=ini;
 cout<<"Nombre====Apellidos====Cedula cliente====Celular cliente====Peluquero====Fecha de cita====Hora de cita"<<endl<<endl;
  	while(p!=NULL)
  	{
  	 gotoxy(1,pos);cout<<p->nombre;
  	 gotoxy(11,pos);cout<<p->apellido;
	 gotoxy(24,pos);cout<<p->ced; 	
	 gotoxy(42,pos);cout<<p->cel;
	 gotoxy(61,pos);cout<<p->pel;
	 gotoxy(74,pos);cout<<p->fecha;
	 gotoxy(91,pos);cout<<p->hora;
	 p=p->sig;
	 pos++;
	}
	 getch();
	 cout<<endl<<endl;
}
void anexarini()
{system ("cls");
 do
  { 
  	 p=new cita;
  	 gotoxy(50,4);cout<<"Nombre: ";cin>>p->nombre;
  	 gotoxy(50,5);cout<<"Apellido: ";cin>>p->apellido;
	 gotoxy(50,6);cout<<"C.C: ";cin>>p->ced;  	
	 gotoxy(50,7);cout<<"Celular: ";cin>>p->cel;
	 gotoxy(50,8);cout<<"Peluquero: ";cin>>p->pel;
	 gotoxy(50,9);cout<<"Fecha: ";cin>>p->fecha;
	 gotoxy(50,10);cout<<"Hora: ";cin>>p->hora;
	 gotoxy(40,12);cout<<"Presione <s> para agregar mas datos: ";cin>>continuar;
 	 if(ini==NULL)
	 {
	  ini=p;
	  p->sig=NULL;	
	  fin=p;
	 }
	 else
	 {
	  p->sig=ini;
	  ini=p;
	 }
   system ("cls");  
  }while ((continuar=='s')||(continuar=='S'));
}
void anexarfin()
{system ("cls");
 do
  { 
  	 p=new cita;
  	 gotoxy(50,4);cout<<"Nombre: ";cin>>p->nombre;
  	 gotoxy(50,5);cout<<"Apellido: ";cin>>p->apellido;
	 gotoxy(50,6);cout<<"C.C: ";cin>>p->ced;  	
	 gotoxy(50,7);cout<<"Celular: ";cin>>p->cel;
	 gotoxy(50,8);cout<<"Peluquero: ";cin>>p->pel;
	 gotoxy(50,9);cout<<"Fecha: ";cin>>p->fecha;
	 gotoxy(50,10);cout<<"Hora: ";cin>>p->hora;
	 gotoxy(40,12);cout<<"Presione <s> para agregar mas datos: ";cin>>continuar;
 	 if(ini==NULL)
	 {
	  ini=p;
	  p->sig=NULL;
	  fin=p;	
	 }
	 else
	 {
	  fin->sig=p;
	  fin=p;
	  p->sig=NULL;
	 }
   system ("cls");  
  }while ((continuar=='s')||(continuar=='S'));
}
void buscar()
{int pos=2;
 p=ini;
 cout<<"Ingrese el numero de cedula del cliente: ";cin>>auxcc;
 while(p!=NULL)
  { 
   if(strcmp(auxcc,p->ced)==0)
  	{cout<<"Nombre====Apellidos====Cedula cliente====Celular cliente====Peluquero====Fecha de cita====Hora de cita"<<endl<<endl;
  	 gotoxy(1,pos);cout<<p->nombre;
  	 gotoxy(11,pos);cout<<p->apellido;
	 gotoxy(24,pos);cout<<p->ced; 	
	 gotoxy(42,pos);cout<<p->cel;
	 gotoxy(61,pos);cout<<p->pel;
	 gotoxy(74,pos);cout<<p->fecha;
	 gotoxy(91,pos);cout<<p->hora;
	 pos++;
	}
	p=p->sig;
  }
}
void modificar()
{p=ini;
 cout<<"Ingrese el numero de cedula del cliente: ";cin>>auxcc; 
 while(p!=NULL)
  {
	if(strcmp(auxcc,p->ced)==0)
  	{gotoxy(50,2);cout<<"El registro encontrado es: ";
	 gotoxy(50,4);cout<<"Nombre: ";cout<<p->nombre;
  	 gotoxy(50,5);cout<<"Apellido: ";cout<<p->apellido;
	 gotoxy(50,6);cout<<"C.C: ";cout<<p->ced;  	
	 gotoxy(50,7);cout<<"Celular: ";cout<<p->cel;
	 gotoxy(50,8);cout<<"Peluquero: ";cout<<p->pel;
	 gotoxy(50,9);cout<<"Fecha: ";cout<<p->fecha;
	 gotoxy(50,10);cout<<"Hora: ";cout<<p->hora;
	 
	  gotoxy(1,10);cout<<endl<<endl<<"===================================================================================================================="<<endl<<endl;
     
     gotoxy(50,14);cout<<"Nombre: ";cin>>p->nombre;
  	 gotoxy(50,15);cout<<"Apellido: ";cin>>p->apellido;
	 gotoxy(50,16);cout<<"C.C: ";cin>>p->ced;  	
	 gotoxy(50,17);cout<<"Celular: ";cin>>p->cel;
	 gotoxy(50,18);cout<<"Peluquero: ";cin>>p->pel;
	 gotoxy(50,19);cout<<"Fecha: ";cin>>p->fecha;
	 gotoxy(50,20);cout<<"Hora: ";cin>>p->hora;
	}
 p=p->sig;
 }
}

void guardar()
{
 if(ini==NULL)
  {
  	cout<<"No tienes registros creados";
  	p=NULL;

  }
  else
  {system("cls");
   p=ini;
   archivo=fopen("CITAS.TXT","wb");	
  while(p!=NULL)
  {
   system("cls");
   strcpy(registro.nombre,p->nombre);
   strcpy(registro.apellido,p->apellido);
   strcpy(registro.ced,p->ced);
   strcpy(registro.cel,p->cel);
   strcpy(registro.pel,p->pel);
   strcpy(registro.fecha,p->fecha);
   strcpy(registro.hora,p->hora);
   fwrite(&registro,sizeof(registro),1,archivo);
   p=p->sig;
  }
  fclose(archivo);
  cout<<"Los resgitros se han guardado de forma exitosa";
  }
}
void abrir()
{
 p=ini;
 system("cls");
 archivo=fopen("CITAS.TXT","r+");
 dir_fisica=dir_logica*sizeof(registro);
 fseek(archivo,dir_fisica,SEEK_SET);
 while(!feof(archivo))
 {
  fread(&registro,sizeof(registro),1,archivo);
  p=new cita;
   strcpy(p->nombre,registro.nombre);
   strcpy(p->apellido,registro.apellido);
   strcpy(p->ced,registro.ced);
   strcpy(p->cel,registro.cel);
   strcpy(p->pel,registro.pel);
   strcpy(p->fecha,registro.fecha);
   strcpy(p->hora,registro.hora);
  
  if(ini==NULL)
  {
  	ini=p;
    p->sig=NULL;
  }
  else
  {
  	p->sig=ini;
  	ini=p;
  }
  aux=1;
 }
 fclose(archivo);
 cout<<"Abrir archivo";
}
void menu ()
{int op=1;
 while(op!=0)
  {
  	gotoxy(50,2);cout<<"==============MENU==============="<<endl<<endl;
    gotoxy(50,4);cout<<"Crear por inicio______________[1]";
    gotoxy(50,5);cout<<"Crear por fin_________________[2]";	
    gotoxy(50,6);cout<<"Ver___________________________[3]";
    gotoxy(50,7);cout<<"Anexar por inicio_____________[4]";
    gotoxy(50,8);cout<<"Anexar por fin________________[5]";
    gotoxy(50,9);cout<<"Buscar________________________[6]";
    gotoxy(50,10);cout<<"Modificar_____________________[7]";
    gotoxy(50,11);cout<<"Guardar inf HHD_______________[8]";
    gotoxy(50,12);cout<<"Abrir inf HHDD________________[9]";
    gotoxy(50,13);cout<<"Salir_________________________[0]";
    gotoxy(50,14);cout<<"Digite la opcion: ";cin>>op;
    fflush(stdin);
  
   switch(op)
    {
  	  case 1: system ("cls");
  	          if (aux==0)
  	          {
				crearini();
			  }
			  else
			  {
			   gotoxy(20,14);cout<<"El comando no se puede ejecutar por que ya tiene informacion";
			   getch();
			   system ("cls");
			  }
		      break;
	  case 2: system ("cls");
  	          if (aux==0)
  	          {
				crearfin();
			  }
			  else
			  {
			   gotoxy(20,14);cout<<"El comando no se puede ejecutar por que ya tiene informacion";
			   getch();
			   system ("cls");
			  }
		      break;	
	  case 3: system ("cls");
	          ver();
	          getch();
			  system ("cls");
			  break;
	 case 4:  system ("cls");
	          anexarini();
	          getch();
			  system ("cls");
			  break;
	 case 5: system ("cls");
	        anexarfin();
	        getch();
			system ("cls");
			break;		
	 case 6: system ("cls");
	        buscar();
	        getch();
			system ("cls");
			break;
	 case 7: system ("cls");
	        modificar();
	        getch();
			system ("cls");
			break;	
	 case 8: system ("cls");
	        guardar();
	        getch();
			system ("cls");
			break;	
	 case 9: system ("cls");
	        abrir();
	        getch();
			system ("cls");
			break;								
    }	
  } 
}

int main()
{
 system("color 04");
 menu();
 return 0;	
}
