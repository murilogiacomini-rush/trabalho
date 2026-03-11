#include <stdio.h>
#include <stdlib.h>

int main()
{
    int tipoVeiculo, tipoSeguro, idade, eixos=0;
    float valorBase=0, adicionalCat=0;
    float adicionalIdade=0, custoCobertura=0;
    float valorTotal=0;

    printf("--- SISTEMA DE CALCULO DE SEGURO ---\n\n");

    // tipo de veiculo
    printf("ESCOLHA O TIPO DE VEICULO:\n");
    printf("1. Passeio\n2. Carga Pesada\n3. Caminhonete\n4. Moto <1000cc\n5. Moto >1000cc\n");
    printf("Opcao: ");
    scanf("%d",&tipoVeiculo);

    // idade
    printf("DIGITE A IDADE DO CONDUTOR: ");
    scanf("%d",&idade);

    // plano
    printf("\nTIPO DE PLANO:\n");
    printf("1. Basico\n2. Parcial\n3. Completo\n");
    printf("Opcao: ");
    scanf("%d",&tipoSeguro);

    // eixos se necessario
    if(tipoVeiculo==2 || tipoVeiculo==3){
        printf("\nNUMERO DE EIXOS: ");
        scanf("%d",&eixos);
    }

    // valor base
    if(tipoVeiculo>=4)
        valorBase=1200;
    else
        valorBase=1000;

    // adicional categoria
    if(tipoVeiculo==1) adicionalCat=valorBase*0.10;
    else if(tipoVeiculo==2) adicionalCat=valorBase*0.20;
    else if(tipoVeiculo==3) adicionalCat=valorBase*0.33;
    else if(tipoVeiculo==4) adicionalCat=valorBase*0.80;
    else if(tipoVeiculo==5) adicionalCat=valorBase*0.90;

    // adicional idade
    if(idade>=18 && idade<=25) adicionalIdade=valorBase*0.15;
    else if(idade<=29) adicionalIdade=valorBase*0.10;
    else adicionalIdade=valorBase*0.05;

    // plano cobertura
    if(tipoVeiculo==1){ // passeio
        if(tipoSeguro==1) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(-0.02);
        else if(tipoSeguro==2) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.02);
        else custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.10);
    }

    else if(tipoVeiculo==2 || tipoVeiculo==3){ // carga e caminhonete
        if(tipoSeguro==1) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*
            (0.03*eixos);
        else if(tipoSeguro==2) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.05*eixos);
        else custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.10*eixos);
    }

    else if(tipoVeiculo==4){ // moto <1000
        if(tipoSeguro==1) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(-0.05);
        else if(tipoSeguro==2) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.15);
        else custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.80);
    }

    else if(tipoVeiculo==5){ // moto >1000
        if(tipoSeguro==1) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.10);
        else if(tipoSeguro==2) custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(0.20);
        else custoCobertura=(valorBase+adicionalCat+adicionalIdade)*(1.00);
    }

    valorTotal = valorBase + adicionalCat + adicionalIdade + custoCobertura;

    printf("\n--- RELATORIO ---\n");
    printf("Valor Base: R$ %.2f\n",valorBase);
    printf("Adicional Categoria: R$ %.2f\n",adicionalCat);
    printf("Adicional Idade: R$ %.2f\n",adicionalIdade);
    printf("Valor Plano: R$ %.2f\n",custoCobertura);
    printf("Valor Total: R$ %.2f\n",valorTotal);

    return 0;
}
