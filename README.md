//1. Ao acionar um botão, ligar um led. O led permanece acionado enquanto o botão
estiver acionado, o led desliga quando o botão não estiver acionado.

#include "stm32g0xx.h"

main (){
	RCC->IOPENR=0x3f;
	GPIOC->MODER=0x00;
	GPIOA->MODER=0x28000400;


	while(1){
		if(GPIOC->IDR&0x2000){
			GPIOA->ODR&=~0X20;//DESLIGA

		}else{
			GPIOA->ODR|=0x20;//LIGA

		}
	}
}
