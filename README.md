# Intro till programmering
Detta projekt är gjort för att förenkla programmeringen för vår klass i kursen teknologi.
Språket som skrivs här är en förenklad version av `C` som används i Arduinoutveckling.
Personer som har bidragit till detta:
- `Pim Kennedy`
- `Filip Manzi`

### Kommentarer
Kommentarer är text som inte kommer att köras av programmet. Oftast använder man kommentarer för att få en struktur på sin kod. Så här ser kommentarer ut i en kodfil.
```cpp
// Detta är en enkelkommentar

/* Detta är en kommentar som
fungerar för flera kodrader. */
```

### Variabler
En variabel deklareras genom att ange variabeltypen följt av ett namn (ange relevanta namn för enkelhetens skull) sedan ett `=`-tecken och slutligen värdet som variabeln ska ha. Så här ser variabler ut i en kodfil.
```cpp
const int led = 13;
```
Notera att vi har lagt till `const` framför variabeltypen. Detta betyder att variabeln är en konstant, det vill säga att den inte kommer att ändras. En LED pin, som i exemplet ovan kommer ju inte att ändras.

I exemplet nedan kan vi se en sensors värde, detta värde kommer ju att ändras beroende på t.ex en potentiometer och vi använder därför inte `const`.
```cpp
int sensorValue = 0;
```

### Setup
Setup-metoden körs i början av programmet och är till för att configurera programmet från början. Så här ser setup-metod ut i en kodfil.
```cpp
void setup() {
  // Skriv koden som ska configureras här.
}
```

### Loop
Loop-metoden körs om och om igen i all oändlighet. Så här ser loop-metod ut i en kodfil.
```cpp
void Loop() {
  // Skriv koden som ska upprepas här.
}
```

Om du vill att koden i loop-metoden ska köras t.ex varje sekund lägger du till kommandot `delay` med värdet angivet i millisekunder.
1 sekund = 1000 millisekunder.
```cpp
void loop() {
  // Skriv koden som ska upprepas här.
  delay(1000);
}
```

Notera att kommandon alltid har sina värden inom paranteser. Antalet värden och vilka typer av värden som ska skrivas beror på vilket kommando det är. Efter parantesen berättar vi att vi är klara med ett semikolon `;`.

### Metoder
Här har ni en lista på medtoder som kan komma att provet i ett exempel.
```cpp
digitalRead(buttonPin);

digitalWrite(ledPin, HIGH / LOW);
```

### Exempel 1
I detta exempel kommer programmet alltid att lyssna efter *buttonPin* och om buttonPin trycks kommer *ledPin* antingen släckas eller tändas. 
```cpp
void loop() {
  buttonState = digitalRead(buttonPin);
  
  if(buttonState == HIGH) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }
}
```

### For-loop
For-loopen tar ett värde (*i*) och ökar det värde (*i++*) till en definierad gräns (*i < 8*). För varje gång som loopen ökar värdet *i* kommer också koden innanför klamrarna (*{ }*) att köras.
```cpp
int ledPins[] = { 2,3,4,5,6,7,8,9 };
int delayTime = 100;

void setup() {
  for(int i = 0; i < 8; i++) {
    pinMode(ledPins[i], OUTPUT);
  }
}
```

---

### Blink
```cpp
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}
```

### Buttons
```cpp
// constants won't change. They're used here to set pin numbers:
const int buttonPin = 2;     // the number of the pushbutton pin
const int ledPin =  13;      // the number of the LED pin

// variables will change:
int buttonState = 0;         // variable for reading the pushbutton status

void setup() {
  // initialize the LED pin as an output:
  pinMode(ledPin, OUTPUT);
  // initialize the pushbutton pin as an input:
  pinMode(buttonPin, INPUT);
}

void loop() {
  // read the state of the pushbutton value:
  buttonState = digitalRead(buttonPin);

  // check if the pushbutton is pressed. If it is, the buttonState is HIGH:
  if (buttonState == HIGH) {
    // turn LED on:
    digitalWrite(ledPin, HIGH);
  } else {
    // turn LED off:
    digitalWrite(ledPin, LOW);
  }
}
```

### AnalogInput
```cpp
int sensorPin = A0;    // select the input pin for the potentiometer
int ledPin = 13;      // select the pin for the LED
int sensorValue = 0;  // variable to store the value coming from the sensor

void setup() {
  // declare the ledPin as an OUTPUT:
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // read the value from the sensor:
  sensorValue = analogRead(sensorPin);
  // turn the ledPin on
  digitalWrite(ledPin, HIGH);
  // stop the program for <sensorValue> milliseconds:
  delay(sensorValue);
  // turn the ledPin off:
  digitalWrite(ledPin, LOW);
  // stop the program for for <sensorValue> milliseconds:
  delay(sensorValue);
}
```

### LED Fun
```cpp
//LED Pin Variables
int ledPins[] = {2,3,4,5,6,7,8,9}; //An array to hold the pin each LED is connected to
                                   //i.e. LED #0 is connected to pin 2, LED #1, 3 and so on
                                   //to address an array use ledPins[0] this would equal 2
                                   //and ledPins[7] would equal 9
 
/*
 * setup() - this function runs once when you turn your Arduino on
 * We the three control pins to outputs
 */
void setup()
{
  
  //Set each pin connected to an LED to output mode (pulling high (on) or low (off)
  for(int i = 0; i < 8; i++){         //this is a loop and will repeat eight times
      pinMode(ledPins[i],OUTPUT); //we use this to set each LED pin to output
  }                                   //the code this replaces is below
 
  /* (commented code will not run)
   * these are the lines replaced by the for loop above they do exactly the
   * same thing the one above just uses less typing
  pinMode(ledPins[0],OUTPUT);
  pinMode(ledPins[1],OUTPUT);
  pinMode(ledPins[2],OUTPUT);
  pinMode(ledPins[3],OUTPUT);
  pinMode(ledPins[4],OUTPUT);
  pinMode(ledPins[5],OUTPUT);
  pinMode(ledPins[6],OUTPUT);
  pinMode(ledPins[7],OUTPUT);
  (end of commented code)*/
}
 
 
/*
 * loop() - this function will start after setup finishes and then repeat
 * we call a function called oneAfterAnother(). if you would like a different behaviour
 * uncomment (delete the two slashes) one of the other lines
 */
void loop()                     // run over and over again
{
  oneAfterAnotherNoLoop();   //this will turn on each LED one by one then turn each off
  //oneAfterAnotherLoop();   //does the same as oneAfterAnotherNoLoop but with 
                             //much less typing
  //oneOnAtATime();          //this will turn one LED on then turn the next one
                             //on turning the 
                             //former off (one LED will look like it is scrolling 
                             //along the line
  //inAndOut();              //lights the two middle LEDs then moves them out then back 
                             //in again
}
 
/*
 * oneAfterAnotherNoLoop() - Will light one LED then delay for delayTime then light
 * the next LED until all LEDs are on it will then turn them off one after another
 *
 * this does it without using a loop which makes for a lot of typing. 
 * oneOnAtATimeLoop() does exactly the same thing with less typing
 */
void oneAfterAnotherNoLoop(){
  int delayTime = 100; //the time (in milliseconds) to pause between LEDs
                       //make smaller for quicker switching and larger for slower
  digitalWrite(ledPins[0], HIGH);  //Turns on LED #0 (connected to pin 2 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[1], HIGH);  //Turns on LED #1 (connected to pin 3 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[2], HIGH);  //Turns on LED #2 (connected to pin 4 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[3], HIGH);  //Turns on LED #3 (connected to pin 5 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[4], HIGH);  //Turns on LED #4 (connected to pin 6 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[5], HIGH);  //Turns on LED #5 (connected to pin 7 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[6], HIGH);  //Turns on LED #6 (connected to pin 8 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[7], HIGH);  //Turns on LED #7 (connected to pin 9 )
  delay(delayTime);                //waits delayTime milliseconds  
 
//Turns Each LED Off
  digitalWrite(ledPins[7], LOW);  //Turns on LED #0 (connected to pin 2 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[6], LOW);  //Turns on LED #1 (connected to pin 3 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[5], LOW);  //Turns on LED #2 (connected to pin 4 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[4], LOW);  //Turns on LED #3 (connected to pin 5 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[3], LOW);  //Turns on LED #4 (connected to pin 6 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[2], LOW);  //Turns on LED #5 (connected to pin 7 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[1], LOW);  //Turns on LED #6 (connected to pin 8 )
  delay(delayTime);                //waits delayTime milliseconds
  digitalWrite(ledPins[0], LOW);  //Turns on LED #7 (connected to pin 9 )
  delay(delayTime);                //waits delayTime milliseconds  
}
 
/*
 * oneAfterAnotherLoop() - Will light one LED then delay for delayTime then light
 * the next LED until all LEDs are on it will then turn them off one after another
 *
 * this does it using a loop which makes for a lot less typing. 
 * than oneOnAtATimeNoLoop() does exactly the same thing with less typing
 */
void oneAfterAnotherLoop(){
  int delayTime = 100; //the time (in milliseconds) to pause between LEDs
                       //make smaller for quicker switching and larger for slower
 
//Turn Each LED on one after another
  for(int i = 0; i <= 7; i++){
    digitalWrite(ledPins[i], HIGH);  //Turns on LED #i each time this runs i
    delay(delayTime);                //gets one added to it so this will repeat 
  }                                  //8 times the first time i will = 0 the final
                                     //time i will equal 7;
 
//Turn Each LED off one after another
  for(int i = 7; i >= 0; i--){  //same as above but rather than starting at 0 and counting up
                                //we start at seven and count down
    digitalWrite(ledPins[i], LOW);  //Turns off LED #i each time this runs i
    delay(delayTime);                //gets one subtracted from it so this will repeat 
  }                                  //8 times the first time i will = 7 the final
                                     //time it will equal 0
                                     
                                     
}
 
/*
 * oneOnAtATime() - Will light one LED then the next turning off all the others
 */
void oneOnAtATime(){
  int delayTime = 100; //the time (in milliseconds) to pause between LEDs
                       //make smaller for quicker switching and larger for slower
  
  for(int i = 0; i <= 7; i++){
    int offLED = i - 1;  //Calculate which LED was turned on last time through
    if(i == 0) {         //for i = 1 to 7 this is i minus 1 (i.e. if i = 2 we will
      offLED = 7;        //turn on LED 2 and off LED 1)
    }                    //however if i = 0 we don't want to turn of led -1 (doesn't exist)
                         //instead we turn off LED 7, (looping around)
    digitalWrite(ledPins[i], HIGH);     //turn on LED #i
    digitalWrite(ledPins[offLED], LOW); //turn off the LED we turned on last time
    delay(delayTime);
  }
}
 
/*
 * inAndOut() - This will turn on the two middle LEDs then the next two out
 * making an in and out look
 */
void inAndOut(){
  int delayTime = 100; //the time (in milliseconds) to pause between LEDs
                       //make smaller for quicker switching and larger for slower
  
  //runs the LEDs out from the middle
  for(int i = 0; i <= 3; i++){
    int offLED = i - 1;  //Calculate which LED was turned on last time through
    if(i == 0) {         //for i = 1 to 7 this is i minus 1 (i.e. if i = 2 we will
      offLED = 3;        //turn on LED 2 and off LED 1)
    }                    //however if i = 0 we don't want to turn of led -1 (doesn't exist)
                         //instead we turn off LED 7, (looping around)
    int onLED1 = 3 - i;       //this is the first LED to go on ie. LED #3 when i = 0 and LED 
                             //#0 when i = 3 
    int onLED2 = 4 + i;       //this is the first LED to go on ie. LED #4 when i = 0 and LED 
                             //#7 when i = 3 
    int offLED1 = 3 - offLED; //turns off the LED we turned on last time
    int offLED2 = 4 + offLED; //turns off the LED we turned on last time
    
    digitalWrite(ledPins[onLED1], HIGH);
    digitalWrite(ledPins[onLED2], HIGH);    
    digitalWrite(ledPins[offLED1], LOW);    
    digitalWrite(ledPins[offLED2], LOW);        
    delay(delayTime);
  }
 
  //runs the LEDs into the middle
  for(int i = 3; i >= 0; i--){
    int offLED = i + 1;  //Calculate which LED was turned on last time through
    if(i == 3) {         //for i = 1 to 7 this is i minus 1 (i.e. if i = 2 we will
      offLED = 0;        //turn on LED 2 and off LED 1)
    }                    //however if i = 0 we don't want to turn of led -1 (doesn't exist)
                         //instead we turn off LED 7, (looping around)
    int onLED1 = 3 - i;       //this is the first LED to go on ie. LED #3 when i = 0 and LED 
                             //#0 when i = 3 
    int onLED2 = 4 + i;       //this is the first LED to go on ie. LED #4 when i = 0 and LED 
                             //#7 when i = 3 
    int offLED1 = 3 - offLED; //turns off the LED we turned on last time
    int offLED2 = 4 + offLED; //turns off the LED we turned on last time
    
    digitalWrite(ledPins[onLED1], HIGH);
    digitalWrite(ledPins[onLED2], HIGH);    
    digitalWrite(ledPins[offLED1], LOW);    
    digitalWrite(ledPins[offLED2], LOW);        
    delay(delayTime);
  }
}
```
