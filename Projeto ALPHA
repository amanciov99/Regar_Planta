#include <LiquidCrystal.h>  //biblioteca do LCD
#include <DHT.h>            //biblioteca do DHT
#include <DHT_U.h>          //biblioteca necessária para o funcionamento correto da biblioteca do DHT
#include <Adafruit_Sensor.h>  //biblioteca necessária para o funcionamento correto da biblioteca do DHT
#define buzzer 11  //Pino conectado ao buzzer
#define ledm 13    //Pino conectado ao LED vermelho
#define ledd 12     //Pino conectado ao LED verde
#define DHTPIN A1 // pino que estamos conectando o DHT
#define DHTTYPE DHT11 // selecionamos o DHT 11 como o sensor a ser utilizados
float umidade;              //valor do pino analógico da umidade
float temperatura;          //valor do pino analógico da temperatura
DHT dht(DHTPIN, DHTTYPE);   //declaração do objeto DHT
LiquidCrystal lcd(2,3,4,5,6,7); //declaração do objeto LCD
int melodia[] = {660,660,660,510,660,770,380,510,380,320,440,480,450,430,380,660,760,860,700,760,660,520,580,480,510,380,320,440,480,450,430,380,660,760,860,700,760,660,520,580,480,500,760,720,680,620,650,380,430,500,430,500,570,500,760,720,680,620,650,1020,1020,1020,380,500,760,720,680,620,650,380,430,500,430,500,570,585,550,500,380,500,500,500,500,760,720,680,620,650,380,430,500,430,500,570,500,760,720,680,620,650,1020,1020,1020,380,500,760,720,680,620,650,380,430,500,430,500,570,585,550,500,380,500,500,500,500,500,500,500,580,660,500,430,380,500,500,500,500,580,660,870,760,500,500,500,500,580,660,500,430,380,660,660,660,510,660,770,380};
//Melodia do MARIO THEME
int duracaodasnotas[] = {100,100,100,100,100,100,100,100,100,100,100,80,100,100,100,80,50,100,80,50,80,80,80,80,100,100,100,100,80,100,100,100,80,50,100,80,50,80,80,80,80,100,100,100,100,150,150,100,100,100,100,100,100,100,100,100,100,150,200,80,80,80,100,100,100,100,100,150,150,100,100,100,100,100,100,100,100,100,100,100,100,100,100,100,100,100,150,150,100,100,100,100,100,100,100,100,100,100,150,200,80,80,80,100,100,100,100,100,150,150,100,100,100,100,100,100,100,100,100,100,100,100,100,60,80,60,80,80,80,80,80,80,60,80,60,80,80,80,80,80,60,80,60,80,80,80,80,80,80,100,100,100,100,100,100,100};
//Duração de cada nota

void setup() {
  lcd.begin(16,2);  //inicializa o LCD
  dht.begin();      //inicializa o DHT
  pinMode(buzzer, OUTPUT);  //Configura o pino como saída
  pinMode(ledm, OUTPUT);    //Configura o pino como saída
  pinMode(ledd, OUTPUT);    //Configura o pino como saída
}

void loop() {
  lcd.clear();  //limpa a tela do LCD
  umidade = dht.readHumidity(); //lê a umidade através do DHT
  temperatura = dht.readTemperature();  //lê a temperatura através do DHT
  lcd.setCursor(0,0);   //seleciona o início da escrita na coluna 0 e linha 0
  lcd.print("Umid: ");  //printa no display
  lcd.print(umidade);   //printa no display
  lcd.print("%");       //printa no display
  lcd.setCursor(0,1);   //seleciona o início da escrita na coluna 0 e linha 1
  lcd.print("Temp: ");  //printa no display
  lcd.print(temperatura); //printa no display
  lcd.print(" C");      //printa no display
  if((umidade<50.0)||(temperatura>30.0)) {  //confere se o valor da variável umidade é menor que 50 OU o valor da variável temperatura é maior que 30
    digitalWrite(ledm, HIGH);   //manda um sinal alto para o LED vermelho
    digitalWrite(ledd, LOW);    //manda um sinal baixo para o LED verde
    for(int nota = 0; nota < 156; nota++) {   //for para tocar as 156 notas começando no 0 até 15
              int duracaodanota = duracaodasnotas[nota];
              tone(buzzer, melodia[nota], duracaodanota);
              //pausa depois das notas
              int pausadepoisdasnotas[] ={150,300,300,100,300,550,575,450,400,500,300,330,150,300,200,200,150,300,150,350,300,150,150,500,450,400,500,300,330,150,300,200,200,150,300,150,350,300,150,150,500,300,100,150,150,300,300,150,150,300,150,100,220,300,100,150,150,300,300,300,150,300,300,300,100,150,150,300,300,150,150,300,150,100,420,450,420,360,300,300,150,300,300,100,150,150,300,300,150,150,300,150,100,220,300,100,150,150,300,300,300,150,300,300,300,100,150,150,300,300,150,150,300,150,100,420,450,420,360,300,300,150,300,150,300,350,150,350,150,300,150,600,150,300,350,150,150,550,325,600,150,300,350,150,350,150,300,150,600,150,300,300,100,300,550,575};
              delay(pausadepoisdasnotas[nota]);
    }
    noTone(buzzer); //silencia o buzzer
  } else {
    digitalWrite(ledm, LOW);  //manda um sinal baixo para o LED vermelho
    digitalWrite(ledd, HIGH); //manda um sinal alto para o LED verde
  }
  delay(60000); //espera 1 minuto
}
