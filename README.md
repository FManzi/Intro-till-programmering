# Intro till programmering
Detta projekt är gjort för att förenkla programmeringen för min klass i kursen teknologi.
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
