//# FP-2021
//Código do programa para calculo de titulações ácido-base
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int tipo[3], l, c;
double pontoeq, CA, CT, VT, VA, K;
double matriz[5][2];

int pontodeequivalencia (void)
{
    VA=(VT*CT)/CA;
    pontoeq= VA;
    printf("\n O ponto de equivalencia acontece com a adição de %lf mL de titulante. \n");
    return (pontoeq);
}

int calcularPH ()
{
int i=1;
double PH[5], ML[5]={0,0.25*pontoeq,0.50*pontoeq,pontoeq,1.25*pontoeq,1.50*pontoeq};//aumentar quantidade de pontos

    pontodeequivalencia;

    switch (tipo[3]){

        case 1:{

        //para 0 ml adicionados
            do {
                if (tipo[2]=1){
                    PH[i]=-log10((sqrt(CT*K)));
                        }else{ (calcular ph de base fraca);}
                matriz[i][0]=ML[i];
                matriz[i][1]=PH[i];
                i++;
                }
                while (ML[i]=0);

        //antes do ponto de eq
            for (ML[i]>0;ML[i]<pontoeq;i++){
                    PH[i]=-log10(K)+log10(((CA*ML[i])/VT)/CT);
                    matriz[i][0]=ML[i];
                    matriz[i][1]=PH[i];}

        //no ponto eq
            do {
                if (tipo[2]=1){
                   PH[i]=14-(-log10(sqrt(K*cIONtitulado)));
                        matriz[i][0]=ML[i];
                        matriz[i][1]=PH[i];
                i++;}
                while (ML[i]=pontoeq);

        //depois do ponto eq
            do{
                if (tipo[2]=2){// EXCESSO ANALITO
                    PH[i]= 14 -(-log10((ML[i]*CA)-(VT*CT)/(VT+ML[i])));
                        matriz[i][0]=ML[i];
                        matriz[i][1]=PH[i];
                    i++;
                        }else{
                            PH[i]= -log10((ML[i]*CA)-(VT*CT)/(VT+ML[i]));
                                matriz[i][0]=ML[i];
                                matriz[i][1]=PH[i];
                            i++;}}
                while (ML[i]>pontoeq);

        case 2:{//acido base normais

            switch (tipo[2]){

                case 2:{//titulado eh base

                //para 0 ml adicionados
                    do {
                        PH= 14-(-log10(CT));
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];
                        i++;}//fim case 1
                        while (ML[i]=0);

                //antes ponto eq
                    for (ML[i]>0;ML[i]<pontoeq;i++){
                        PH[i]= 14-(-log10(((VT*CT)-(VA*ML[i]))/(VT+ML[i])));
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];}

                //no ponto eq
                    do{
                        PH[i]==7;
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];
                         i++;}
                        while (ML[i]=pontoeq);

                //depois do ponto eq
                    do{
                        PH[i]=-log10(((VA*ML[i])-(VT*CT))/(VT[i]+ML[i]));
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];
                        i++;}
                        while (ML[i]>pontoeq);


                break;

                case 1:{//titulado eh acido

                //para 0 ml de titulante adicionado
                    do{
                        PH=-log10(CT);
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];
                        i++;}
                        while(ML[i]=0);

                //antes do ponto eq
                    for (ML[i]>0;ML[i]<pontoeq;i++){
                        PH[i]=-log10(((VT*CT)-(VA*ML[i]))/(VT+ML[i]));
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];}

                //no ponto eq
                    do{
                        PH[i]==7;
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];
                        i++;}
                        while(ML[i]=pontoeq);

                // depois ponto eq
                    do{
                        PH[i]=14-(-log10(((VA*ML[i])-(VT*CT))/(VT+ML[i])));
                        printf("(%lf , %lf)", ML[i], PH[i]);
                            matriz[i][0]=ML[i];
                            matriz[i][1]=PH[i];
                        i++;}
                    while (ML[i]>pontoeq);

                break;
                            }//fim case 1-acido


            }//fim switch acido base normal

        }//fim switch inicial
    return matriz[i][1]=PH[i];
    return matriz[i][0]=ML[i];

}//fim função


int criarcurva (void)
{
    calcularPH;
    for (i>0; i=0; i--)
        printf("(%lf , %lf)", matriz[i][0], matriz[i][1]);
        i++;
//return ();
}


int acidobase1 (void)
{
    printf("Digite o volume do titulado em mL");
        scanf("%lf",&VT);
    printf("Digite o volume do analito adicionado até alteração do indicador (em mL)");
        scanf("%lf",&VA);
    printf("Digite a concentração do analito");
        scanf("%lf",&CA);

    CT=(CA*VA)/VT;
    printf("A concentração do titulado eh de %lf mol/L. \n", CT);
    return (CT);
}

int main()
{
    printf("ESCOLHA O TIPO DE TITULAÇÃO");
    printf("Voce deseja:\n1. Descobrir a concentração do titulado \n2.Criar uma curva de titualçao de uma reação em que se conhece a concentração do analito e do titulado");
        scanf("%d", tipo[1]);

        switch (tipo[1]){
            case 1:
                acidobase1;
            break;

            case 2:
                printf("Existe uma diferença muito grande entre a concentração de acido e base? (EXEMPLO: acido fraco+base forte ou vice e versa)\n1.Sim \n2. Nao");
                    scanf("%d",&tipo[3]);

                printf("O titulado eh um: \n1. Acido \n2. Base");
                    scanf("%d",&tipo[2]);

                switch (tipo[3]){
                    case 1:
                        printf("Digite a constante de dissociação do titulado");
                        scanf("%lf", &K);
                    break;}

                criarcurva;
            break;

            default:
                printf("DIGITE UMA OPÇÃO VALIDA");
                        }//fim switch

    return 0;
}//fim função

