#humidity-

#include "DHT.h"

#define DHTPIN 2
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  float humidite = dht.readHumidity();
  float temperature = dht.readTemperature();

  if (isnan(humidite) || isnan(temperature)) {
    Serial.println("Erreur de lecture du capteur !");
    delay(2000);
    return;
  }

  Serial.print("Humidite : ");
  Serial.print(humidite);
  Serial.println(" %");

  Serial.print("Temperature : ");
  Serial.print(temperature);
  Serial.println(" °C");

  Serial.println("----------------");

  delay(2000);
}








www

const int pinPression = A1;
const float tensionAlimentation = 5.0;

void setup() {
  Serial.begin(9600);
}

void loop() {

  int valeur = analogRead(pinPression);

  float tension = valeur * (tensionAlimentation / 1023.0);

  // Calcul de la pression
  float pression = ((tension / tensionAlimentation) + 0.04) / 0.004;

  // Conversion en hPa
  float pression_hPa = pression * 10.0;

  Serial.println("STATION METEO");

  Serial.print("Tension : ");
  Serial.print(tension);
  Serial.println(" V");

  Serial.print("Pression : ");
  Serial.print(pression, 2);
  Serial.println(" kPa");

  Serial.print("Pression : ");
  Serial.print(pression_hPa, 2);
  Serial.println(" hPa");

  Serial.println("----------------");

  delay(2000);
}



