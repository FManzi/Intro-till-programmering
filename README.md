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

