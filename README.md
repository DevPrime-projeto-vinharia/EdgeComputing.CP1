Projeto: Sistema de Alarme de Luminosidade com Arduino


 Descrição do Projeto

Este projeto consiste na implementação de um sistema de monitoramento e alarme baseado em Arduino, que faz a leitura da luminosidade ambiente utilizando um sensor LDR. A leitura é feita por meio do conversor analógico-digital (ADC) do Arduino, e os dados são convertidos para uma escala de 0 a 100% utilizando a função map().

Com base na intensidade da luz, o sistema aciona LEDs indicadores e um buzzer:

LED Verde: Indica que a luminosidade está em nível adequado (ambiente OK).
LED Amarelo: Indica nível de alerta (acende e o buzzer soa por 3 segundos).
LED Vermelho: Indica problema grave (luminosidade muito alta ou muito baixa).

O sistema também pode ser estendido para exibir informações em um LCD 16x2, incluindo ícones personalizados.

 Dependências do projeto
 - Placa Arduino UNO
 - Sensor de luminosidade LDR 
 - LED Verde
 - LED Amarelo
 - LED Vermelho
 - Buzzer 
 - Display LCD 16x2 
 - Protoboard
 - Jumpers
 - Resistores
   

Biblioteca LiquidCrystal.h (Incluímos no Wokwi)


Montando o circuito:

Inicializamos o site Wokwi para fazer todo o circuito e código.
Começamos adicionando os itens básicos como Protoboard,Jumpers, buzzer, leds, LDR e a placa arduíno.
Primeiramente integramos os resistores e leds na protoboard e colocamos no arduino. 
Adicionamos o sensor de iluminosidade(LDR) com jumpers e um resistor de 10 KΩ.
Colocamos o buzzer integrado com jumpers na protoboard e no arduino.
Para conectar o LCD conectamos cada jumper na respectiva entrada do Display e no arduino de acordo com o nosso código.



