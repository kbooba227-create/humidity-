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


const int capteur = A1;

void setup() {
  Serial.begin(9600);
}

void loop() {

  int valeur = analogRead(capteur);

  float tension = valeur * (5.0 / 1023.0);

  float pressionKPa = ((tension / 5.0) + 0.04) / 0.004;

  float pressionHpa = pressionKPa * 10.0;

  Serial.println("STATION METEO");

  Serial.print("Valeur brute : ");
  Serial.println(valeur);

  Serial.print("Tension : ");
  Serial.print(tension, 2);
  Serial.println(" V");

  Serial.print("Pression : ");
  Serial.print(pressionKPa, 2);
  Serial.println(" kPa");

  Serial.print("Pression : ");
  Serial.print(pressionHpa, 2);
  Serial.println(" hPa");

  Serial.println("----------------");

  delay(2000);
}




