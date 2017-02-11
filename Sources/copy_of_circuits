// Start on github 11.02.2017
// 
#include <Servo.h> // Funktion für Servo Ansteuerung einbinden
#include <LiquidCrystal.h> // Funktion für LCD Ansteuerung einbinden
LiquidCrystal lcd(12, 11, 10, 7, 6, 5, 4); //An diesen Pins wurde das LCD Display angeschlossen

Servo meinServomotor;  // erstellt das Objekt "meinServomotor"


char* lcd_luefter[ ] ={" EIN"," AUS"}; // Die Variable für die LCD Ausgabe des Lüfter Status wird deklariert
int modus_zz =0; // Variable "modus_zz" wird deklariert (Verwendung als Zähler für die Umschaltung der Display Seiten

// Ein & Ausgänge als Konstanten deklarieren
const int buttonPin = 2;    // Der Modus Button für das Display wird auf Pin2 gelegt
const int ledPin = 13;      // Die Onboard LED wird auf Pin 13 gelegt
const int luefter = 8; 		//Lüfter auf Digital Pin8 zuweisen

// Hier werden die Variablen deklariert:
int buttonState =LOW;           // Status des Modus Schalter für die Umschaltung des Displays
int buttonread = 0;				// In diese Variable legen wir den ausgelesenen Wert der Displayumschaltung
int i;							// Die Variable "i" wird für den Zustand des Lüfters benötigt (Displayausgabe)



void setup()
{
  meinServomotor.attach(9);  // verknüpft das Objekt "meinServomotor" mit Pin 13
  lcd.begin(16,2); //LCD als 16x2 deklarieren
  lcd.setCursor(0, 0); //Setzt den Cursor auf Zeile 1 und Zeichen 1

  pinMode(luefter, OUTPUT); // Digital Pin8 (Lüfter) wird auf Ausgabe gesetzt
  pinMode(buttonPin, INPUT); // Digital Pin0 (Modus) wird auf Eingabe gesetzt
  pinMode(ledPin, OUTPUT); // tasterled auf Ausgabe setzen

}


void loop()
{

buttonread = digitalRead(buttonPin); // Der Schalter für den Displaymodus wird ausgelesen und in die Variable "buttonread" geschrieben

  if (buttonread == HIGH) { //Hier wird geprüft, ob der Schalter gedrückt worden ist
  delay(50);					// kurze Wartezeit
  if ((buttonState == LOW) && (digitalRead(buttonPin)) ) // Ist die Variable "buttonState" Low und der Eingang wird ausgelesen
  {
    if (digitalRead(buttonPin)) { 	// Wenn der Schalter ausgelesen wird
      buttonState = HIGH;			// Die Variable "buttonState" wird auf HIGH gesetzt
      modus_zz++;					// Der Zähler wird um einen Wert erhöht
      if (modus_zz >1){				// Ist der Zähler größer 1
        modus_zz=0;					// dann setzen wir den Zähler wieder auf 0
      }

    }
  }
 }

buttonread = digitalRead(buttonPin);	// Der Schalter für den Displaymodus wird ausgelesen und in die Variable "buttonread" geschrieben
if (buttonread == LOW) { 				//Hier wird geprüft, ob der Schalter losgelassen worden ist
  delay(50);								// kurze Wartezeit
  if ((buttonState == HIGH) && (digitalRead(buttonPin)) )	// Ist die Variable "buttonState" HIGH und der Eingang wird ausgelesen
  {
    if (digitalRead(buttonPin)) {		// Wenn der Schalter ausgelesen wird
        buttonState = LOW;				// Die Variable "buttonState" wird auf LOW gesetzt

    }
  }
 }

int analogpin0 = analogRead(0); //die Variable "analogpin0" wird auf einlesen gesetzt (Hier ist der Temperaturfühler angeschlossen)
float milliVolt = (analogpin0 * 5000.0) / 1024.0; //Die Variable "millivolt" als typ float deklariert. Umrechnung des Anlagog Pin0 in millivolt
float temp = milliVolt / 10; // Die Variable "temp" wird als typ float deklariert und die eingelesenen "millivolt" werden in °C umgerechnet
int temp_b=(int)(temp+.5);



//Warte
//delay(1000);         // Delay von 1 Sekunden

if (temp >=26)		// Wenn die Temperatur größer oder = 26°C ist
{
  digitalWrite(luefter, HIGH);  // Dann schalten wir den Lüfter ein
  i=0;
}
else							// Andernfalls
{
 digitalWrite(luefter, LOW);    // Lassen wir den Lüfter aus
 i=1;
}


//Ab hier wird der Servomotor in Abhängigkeit von der Temperatur angesteuert.
switch (temp_b) {
  case 24:
      meinServomotor.write(0);//do something when var equals 2
      break;
  case 23:
      meinServomotor.write(10);//do something when var equals 2
      break;
  case 22:
      meinServomotor.write(20);//do something when var equals 2
      break;
  case 21:
      meinServomotor.write(30);//do something when var equals 2
      break;
   case 20:
      meinServomotor.write(40);//do something when var equals 2
      break;
   case 19:
      meinServomotor.write(50);//do something when var equals 2
      break;
   case 18:
      meinServomotor.write(60);//do something when var equals 2
      break;
   case 17:
      meinServomotor.write(70);//do something when var equals 2
      break;
   case 16:
      meinServomotor.write(80);//do something when var equals 2
      break;
   case 15:
      meinServomotor.write(90);//do something when var equals 2
      break;


    default:
      // if nothing else matches, do the default
      // default is optional
    break;
  }

// Ab hier wird das Display beschrieben
  switch (modus_zz) {
    case 0:
    	//lcd.clear();
		lcd.setCursor(0,0); // Der Cursor wird auf die Anfangsposition gesetzt
		lcd.print("Temperatur:"); // Der Text Temperatur wird geschrieben
		lcd.setCursor(11, 0); // Der Cursor auf dem LCD wird auf das 11 Zeichen in Zeile 1 gesetzt
		lcd.print(temp);	  // Die Variable "temp" wird auf das LCD geschrieben

		lcd.setCursor(0,1);
		lcd.print("Luefter:");
		lcd.setCursor(8,1);
		lcd.print(lcd_luefter[i]);
      //do something when var equals 1
      break;
    case 1:
        //lcd.clear();
		lcd.setCursor(0,0); // Der Cursor wird auf die Anfangsposition gesetzt
		lcd.print("Luefterautomatik"); // Der Text Temperatur wird geschrieben
		lcd.setCursor(0, 1); // Der Cursor auf dem LCD wird auf das 11 Zeichen in Zeile 1 gesetzt
		lcd.print("aktiviert       ");	  // Die Variable "temp" wird auf das LCD geschrieben

      break;
    default:
      // if nothing else matches, do the default
      // default is optional
    break;
  }

//lcd.clear();
//lcd.setCursor(0,0); // Der Cursor wird auf die Anfangsposition gesetzt
//lcd.print("Temperatur:"); // Der Text Temperatur wird geschrieben
//lcd.setCursor(11, 0); // Der Cursor auf dem LCD wird auf das 11 Zeichen in Zeile 1 gesetzt
//lcd.print(temp);	  // Die Variable "temp" wird auf das LCD geschrieben

//lcd.setCursor(0,1);
//lcd.print("Luefter:");
//lcd.setCursor(9,1);
//lcd.print(lcd_luefter[i]);

}
