#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int tipo[3], linhas, i=0, x=1;
double pontoeq, CA[i], CT[i], VT[i], VA[i],PH[x], K;
double ML[x]={0,0.50*pontoeq[i],pontoeq[i],0.25*pontoeq[i]};//aumentar quantidade de pontos

int pontodeequivalencia ()
{
    VA[i]=(VT[i]*CT[i])/CA[i];
    pontoeq= VA[i];
}

int criarcurva ()
{
    printf("Existe uma diferença muito grande entre a concentração de acido e base? (EXEMPLO: acido fraco+base forte ou vice e versa)\n1.Sim \n2. Nao");
        scanf("%d",&tipo[3]);

    printf("O titulado eh um: \n1. Acido \n2. Base");//titulado eh quem esta no becker
        scanf("%d",&tipo[2]);//faz diferença para o calculo de PH

    switch (tipo[3])
        case 1: printf("Digite a constante de dissociação do titulado");
                scanf("%lf", &K);
}

int calcularPH ()
{
    switch (tipo[3]){

        case 1:{

            for (0<ML[x]<pontoeq)//EXCESSO DE TITULADO
                do PH[x]=-log10(K)+log10(cIONtitulado/CT[i]);

            for (ML[x]>pontoeq)// EXCESSO ANALITO
                do{
                    if (tipo[2]=2)
                        PH[x]= 14 -(-log10(excessoanalito));
                            else
                                PH[x]= -log10(excessoanalito);}

            for (ML[x]=0)
                do {
                    if (tipo[2]=1)
                        PH[x]=-log10((sqrt(CT[x]*K)));
                            else (calcular ph de base fraca)}

            for (ML[x]=pontoeq)
                do {if (tipo[2]=1))
                    PH[x]=14-(-log10(sqrt(K*cIONtitulado)))};}
        break;

        case 2:{//acido base normais

            switch (tipo[2]){

                case 1:{
                    for (ML[x]=pontoeq)
                        PH[x]==7;

                    for (0<ML[x]<pontoeq)
                        do PH[x]=14-(-log10(((VT[i]*CT[i])-(VA[i]*ML[x]))/(VT[i+ML[x])));

                    for (ML[x]>pontoeq)// EXCESSO ANALITO
                        doPH[x]=-log10(((VA[i]*ML[x])-(VT[i]*CT[i]))/(VT[i+ML[x]));

                    for (ML[x]=0)
                        do PH= 14-(-log10(CT[i]));}
                break;

                case 1:{
                    for (ML[x]=pontoeq)
                        PH[x]==7;

                    for (0<ML[x]<pontoeq)
                        do PH[x]=-log10(((VT[i]*CT[i])-(VA[i]*ML[x]))/(VT[i+ML[x]));

                    for (ML[x]>pontoeq)// EXCESSO ANALITO
                        doPH[x]=14-(-log10(((VA[i]*ML[x])-(VT[i]*CT[i]))/(VT[i+ML[x])));

                    for (ML[x]=0)
                        do PH=-log10(CT[i]);}
                break;

            }  //fim switch acido base normal

        }//fim switch inicial

}//fim função



int acidobase1 ()//já está tudo ok nessa função
{
    printf("Digite o volume do titulado em mL");
        scanf("%lf",VT[i]);
    printf("Digite o volume do analito adicionado até alteração do indicador (em mL)");
        scanf("%lf",VA[i]);//nesse caso pontoeq=VA
    printf("Digite a concentração do analito");
        scanf("%lf",CA[i]);

    CT[i]=(CA[i]*VA[i])/VT[i];
    printf("A concentração do titulado eh de %lf mol/L. \n", CT[i]);
}

int main()
{
    printf("ESCOLHA O TIPO DE TITULAÇÃO");
    printf("Voce deseja:\n1. Descobrir a concentração do titulado \n2.Criar uma curva de titualçao de uma reação em que se conhece a concentração do analito e do titulado");
        scanf("%d", tipo[1]);

        switch (tipo[1]){
            case 1:
                i=1;
                acidobase1;
            break;

            case 2:
                i=2;
                criarcurva;
            break;

            default:
                printf("DIGITE UMA OPÇÃO VALIDA");
                        }//fim switch

    return 0;
}//fim função


