// Inclui a biblioteca que permite o controle do display LCD 16x2
#include <LiquidCrystal.h>

// Define os pinos conectados ao sensor de luminosidade (LDR), buzzer e LEDs
const int sensorLDR = A0;           // Entrada analógica conectada ao LDR
const int buzzer = 12;              // Pino digital conectado ao buzzer
const int ledVerde = 8;             // LED verde (ambiente OK)
const int ledAmarelo = 9;           // LED amarelo (alerta)
const int ledVermelho = 10;         // LED vermelho (problema)

// Inicializa o objeto lcd com os pinos conectados ao display LCD
// Parâmetros: RS, E, D4, D5, D6, D7
LiquidCrystal lcd(13, 7, 6, 5, 4, 3, 2);

// Criação de um caractere personalizado (um ícone ou logo simples)
// O LCD permite até 8 caracteres customizados (índices 0 a 7)
byte customChar[] = {
  B00000,
  B10001,
  B01010,
  B01110,
  B00100,
  B00100,
  B01110,
  B01110
};

// Função de inicialização: executa apenas uma vez ao ligar o Arduino
void setup() {
  // Define o pino do buzzer como saída
  pinMode(buzzer, OUTPUT);

  // Inicializa a comunicação serial (opcional, usada para monitoramento no console)
  Serial.begin(9600);

  // Define os pinos dos LEDs como saída
  pinMode(ledVerde, OUTPUT);
  pinMode(ledAmarelo, OUTPUT);
  pinMode(ledVermelho, OUTPUT);

  // Inicializa o display LCD com 16 colunas e 2 linhas
  lcd.begin(16,2);

  // Limpa o display (opcional)
  lcd.clear();

  // Mostra a mensagem de boas-vindas na primeira e segunda linha
  lcd.setCursor(0,0);
  lcd.print("DevPrime deseja");
  lcd.setCursor(0,1);
  lcd.print("Boas Vindas :)");

  // Cria o caractere personalizado no slot 0 do LCD
  lcd.createChar(0, customChar);
}

// Função principal do programa: roda em loop continuamente
void loop() {
  // Lê o valor analógico do sensor LDR (0 a 1023)
  int leitura = analogRead(sensorLDR);

  // Converte o valor lido para uma escala de 0 a 100 (em %)
  int porcentagem = map(leitura, 0, 1023, 0, 100);

  // Mostra o valor da luminosidade no monitor serial
  Serial.print("Luminosidade: ");
  Serial.print(porcentagem);
  Serial.println("%");

  // Lógica para acender os LEDs com base no valor da luminosidade
  if (porcentagem >= 40 && porcentagem <= 60) {
    // Ambiente está OK
    digitalWrite(ledVerde, HIGH);
    digitalWrite(ledAmarelo, LOW);
    digitalWrite(ledVermelho, LOW);
  } else if ((porcentagem >= 20 && porcentagem < 40) || (porcentagem > 60 && porcentagem <= 80)) {
    // Nível de alerta
    digitalWrite(ledVerde, LOW);
    digitalWrite(ledAmarelo, HIGH);
    digitalWrite(ledVermelho, LOW);
  } else {
    // Problema detectado (muito claro ou muito escuro)
    digitalWrite(ledVerde, LOW);
    digitalWrite(ledAmarelo, LOW);
    digitalWrite(ledVermelho, HIGH);
  }

  // Se a luminosidade estiver em nível de alerta ou problema, o buzzer soa por 3 segundos
  if ((porcentagem >= 0 && porcentagem < 40) || (porcentagem > 60 && porcentagem <= 100)) {
    tone(buzzer, 1000);   // Liga o buzzer com frequência de 1000 Hz
    delay(3000);          // Espera 3 segundos
    noTone(buzzer);       // Desliga o buzzer
  }

  delay(500);             // Pequena pausa para estabilidade

  // Efeito visual no LCD: "piscar"
  delay(1000);            // Aguarda 1 segundo
  lcd.noDisplay();        // Desliga a exibição do LCD (sem apagar conteúdo)
  delay(500);             // Aguarda meio segundo
  lcd.display();          // Liga a exibição novamente

  // Mostra o logo customizado no canto inferior direito do LCD
  lcd.setCursor(15, 1);   // Última coluna da segunda linha
  lcd.write(byte(0));     // Escreve o caractere personalizado (índice 0)

  delay(0);               // Delay nulo (desnecessário, pode ser removido)
}
