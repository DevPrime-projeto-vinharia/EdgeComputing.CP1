Sistema de Monitoramento de Luminosidade com Arduino

Descrição do Projeto

Este projeto implementa um sistema de monitoramento de luminosidade usando Arduino e um sensor LDR (fotoresistor).
O sistema avalia o nível de luz ambiente e:

Acende um LED verde se a luminosidade estiver dentro da faixa ideal.
Acende um LED amarelo para indicar uma leve alteração (luz mais fraca ou mais forte).
Acende um LED vermelho e ativa um buzzer por 3 segundos se a luminosidade estiver em condição crítica (muito baixa ou muito alta).
Este sistema é útil para aplicações como:

Controle de iluminação ambiente
Monitoramento de salas, escritórios ou estufas
Alarmes automáticos baseados na intensidade de luz
Dependências

Arduino IDE (para programar o Arduino)
Biblioteca padrão Arduino.h (não é necessária nenhuma biblioteca externa)
Materiais Necessários

Quantidade	Componente
1	Arduino Uno (ou similar)
1	LDR (sensor de luminosidade)
1	Resistor 10kΩ (para o LDR)
3	LEDs (Verde, Amarelo, Vermelho)
3	Resistores 220Ω (para os LEDs)
1	Buzzer
1	Protoboard e jumpers
Esquema de Conexão

LDR:
Um terminal no 5V.
Outro terminal ao pino A0 e ligado a um resistor de 10kΩ para o GND.
LEDs:
Verde no pino 3 (com resistor de 220Ω).
Amarelo no pino 4 (com resistor de 220Ω).
Vermelho no pino 5 (com resistor de 220Ω).
Buzzer:
Pino positivo no pino 6.
Pino negativo no GND.
Código Arduino


Como Reproduzir

Monte o circuito conforme o esquema de conexão acima.
Copie o código fornecido.
Abra o Arduino IDE, cole o código e selecione a placa Arduino Uno.
Conecte o Arduino ao computador via USB.
Clique em Upload para gravar o código na placa.
Abra o Monitor Serial para observar a leitura da luminosidade em tempo real.


Observação
Você pode simular este projeto online usando plataformas como Wokwi (https://wokwi.com/).
Para simulações é possível alterar os valores da luz manualmente no ambiente virtual.
