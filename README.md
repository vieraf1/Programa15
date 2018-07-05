# Programa 15

Linguagem Utilizada: C++.

Programa com menu que faz leitura de nome, idade, sexo e salário de várias pessoas e retorna uma tabela com todas as pessoas registradas, e com um acréscimo no salário informado inicialmente.

Programa Desenvolvido no DEV C++ IDE.

Código:

#include "iostream"
#include "string"
using namespace std;

struct cliente 
{
	string nom;
	int ida;
	char sex;
	double sal;
	double novo;
};
struct cliente cad[10];

void armazenar(int novalinha, string no, int idad, double sa, char se)
{
	cad[novalinha].nom = no;
	cad[novalinha].ida = idad;
	cad[novalinha].sal = sa;
	cad[novalinha].sex = se;
}

int calcular(int novalinha) {
	float salmaior = cad[0].sal, salmenor = cad[0].sal, mediaida = 0, somaid = 0, somasal = 0, mediasal = 0;
	int contidade = 0, contsal = 0;
	system("cls");
	for (int i = 0; i <= novalinha; i++)
	{
		if (salmaior < cad[i].sal) {
			salmaior = cad[i].sal;
		}
		
		if (salmenor > cad[i].sal) {
			salmenor = cad[i].sal;
		}
		somasal = somasal + cad[i].sal;
		contsal = contsal + 1;
		somaid = somaid + cad[i].ida;
		contidade = contidade + 1;
		
		if (cad[i].sex == 'M')
		{
		    cad[i].novo = cad[i].sal * 1.10;
	    }
	    if (cad[i].sex == 'H')
		{
		    cad[i].novo = cad[i].sal * 1.125;
	    }
	}
	
	mediaida = somaid / contidade;
	mediasal = somasal / contsal;
	cout << "maior salario :" << salmaior << " | menor salario: " << salmenor << " | media idade: " << mediaida << " | media salario: " << mediasal << endl;
	system("pause");
	
return 0;}

void exibir(int novalinha) {
	for (int i = 0; i <= novalinha; i++){
		cout << "\n Nome: " << cad[i].nom << " | Salario Novo: " << cad[i].novo << " | Sexo: " << cad[i].sex << endl;
	}
	system("pause");
} 

int main() {
	int tecla = 0, linha = -1;
	string nome;
	char sexo;
	int idade;
	double salar;
	
	while (tecla != 4) {
		 system("cls");
	     cout << "\n**Tela Inicial**\n";
         cout << "\n1 - Inserir Dados";
         cout << "\n2 - Calcular";
         cout << "\n3 - Exibir";
         cout << "\n4 - Sair \n" << endl;
         cin >> tecla;
         
         switch(tecla)
		 {
		 	case 1:
		 	    {
		 	    	 system("cls");
		 	    	 cin.ignore();
		 	    	 
		 	    	 cout << "\nDigite o seu nome: ";
		 	    	 getline(cin,nome);
		 	    	 
		 	    	 cout << "\nDigite a sua idade: ";
					 cin >> idade;
					 
					 cout << "\nDigite o seu salario: ";
					 cin >> salar;
					 
					 cout << "\nDigite o seu sexo(H/M): ";
					 cin >> sexo;  
					 linha = linha + 1;
					 
					 armazenar(linha, nome, idade, salar, sexo);
			         break;
			    }
			
			case 2:
				{
					if (linha >= 0)
					{
						calcular(linha);
					}
					break;
				}
			case 3:
				{
					if (linha >= 0)
					{
					    exibir(linha);
					}
					break;
				}
	     }
	}
	
return 0; }
