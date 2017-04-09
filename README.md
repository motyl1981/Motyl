/* Kod testowy do obsługi przekażnika załączanego zdalnie, lokalnie i z Domoticza
 *  Ver.1.0 by MotyL
 */
// Zaczynam od konfiguracji transmisji MySensors
// uruchamiam DEBUGOWANIE do serial portu
#define MY_DEBUG
// Uruchamiam Radio NRF24
#define MY_RADIO_NRF24
// Ustawiam numer Noda i Childa
#define CHILD_ID 1                             
#define MY_NODE_ID 2
//załączani biblioteki do obsługi komunikacji MySensors
#include <MySensors.h>
#include <MyConfig.h>
#include <SPI.h>




//zmienne dla programu
#define button 2
#define led 13
int stan = LOW;
unsigned long czas = 0;

// zmienne wystawione dla MySensors

void setup() {


pinMode(button, INPUT_PULLUP);
pinMode(led, OUTPUT);



//digitalWrite(led,LOW);
//stan = digitalRead(button);
}



void loop() {
  // put your main code here, to run repeatedly:
  if(digitalRead(button)==LOW){
    delay(10);
    if(digitalRead(button)==LOW){
      if(millis() >= czas){
      stan = !stan;
      czas=millis() + 300;
       }
      }
  }
 digitalWrite(led, stan);
}
//....................koniec peetli LOOP................
