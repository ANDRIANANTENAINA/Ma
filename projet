#include <stdio.h>
#include <stdlib.h>

struct client{
    char numClient[50];
    char nom[100];
};

struct materiel{
    char numMat[25];
    char nom[50];
    char disign[100];
    int pu;
    double StockActuel;
    double StockInit;
};


struct achat{
    char numClient[50];
    char numMat[100];
    int qte;
    char dateAchat[50];// atao struct ny date
};
void creation_Fmateriel();
int ajout_mat();
int recherch_mat(char);

int main()
{
    system("color a");
    system("cls");
    char nb[20],a,b; int choi;

    printf("--------MENU--------\n");
    printf("1---Ajout du materiel---\n");
    printf("2---Recherche du materiel---\n");
    printf("3---Quitter");
    printf("\t\t\tVotre choix svp: ");scanf("%d",&choi);

    switch(choi){
        case 1:{
             ajout_mat();
             printf("Quitter ou rester(Q\\R)");scanf("%s",&a);
             if(a == 'Q' || a == 'q') return 2;
              main();}
        break;
        case 2: {
             printf("Entrer le numero ou le nom du materiel a chercher :");scanf("%s5",nb);
             recherch_mat(*nb);
             printf("\n\tQuitter ou rester (Q\\R)");scanf("%s",&b);
                if(b == 'Q' || b == 'q') return 2;
             main();
        }break;
        case 3: return 2;
        default : printf("Mauvaise touche ..."); main();
    }
    creation_Fmateriel();
    return 0;
}


void creation_Fmateriel(){
    FILE *file = fopen("Materiel.txt","a");
    fclose(file);
}
/*
void creation_Fclient(){
    FILE *file = fopen("client.txt","w");
    fclose(file);
}
*/

int recherch_mat(char numMatrl){
    struct materiel rech;
    FILE *file = NULL;
    file = fopen("Materiel.txt","r");

        do{
            fscanf(file,"%s\t%s\t\t%s\n",rech.numMat,rech.nom,rech.disign);
            fflush(stdin);

                if(numMatrl == *rech.numMat || numMatrl == *rech.nom){
                    printf("\nNumero: %s\nNom: %s\nPrix unitaire: %s\n",rech.numMat,rech.nom,rech.disign);
                    return 1;
                }
        }while(!feof(file));

            printf("Le materiel n'existe pas \n");// si non le materiel n'existe pas

    fclose(file);
    return 0;
}


int ajout_mat(){
    struct materiel mat;
    int ajout; char chaine;
    FILE *file = NULL;

    printf("Entrer le numero du materiel: ");scanf("%s",mat.numMat);
    printf("Entrer le nom du materiel: ");scanf("%s",mat.nom);
    printf("Le taux de la materiel: ");scanf("%d",&mat.pu);

    ajout = recherch_mat(*mat.numMat);

    if(ajout == 0)
        {
            file = fopen("Materiel.txt","r");
            chaine = fgetc(file);
            fflush(stdin);

                if(chaine == 'N')
                    {
                        fclose(file);
                        file = fopen("Materiel.txt","a");
                        fprintf(file,"%s\t%s\t\t%d\n",mat.numMat,mat.nom,mat.pu);
                        fclose(file);
                        return -1;
                    }
                    else
                        {
                            fclose(file);
                            file = fopen("Materiel.txt","a");
                            fprintf(file,"Numero\tNOM\t\tTaux\n");
                            fprintf(file,"%s\t%s\t\t%d\n",mat.numMat,mat.nom,mat.pu);
                            fclose(file);
                            return -2;
                        }
    }
    else{
         printf("\nLe materiel deja saisi\n");
        }

    return 1;
}

