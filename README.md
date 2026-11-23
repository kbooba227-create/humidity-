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
