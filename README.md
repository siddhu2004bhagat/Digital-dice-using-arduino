# Digital-dice-using-arduino




//Created by Sk_ElectroTech
//By siddhu
//for any issue email (siddhu200410@gmail.com)
// Segment pins: A to G
const int segmentPins[7] = {2, 3, 4, 5, 6, 7, 8};  
const int buttonPin = 9;

// Digits 1 to 6 (only)
// Segment order: A B C D E F G
int diceDigits[6][7] = {
  {0, 1, 1, 0, 0, 0, 0}, // 1
  {1, 1, 0, 1, 1, 0, 1}, // 2
  {1, 1, 1, 1, 0, 0, 1}, // 3
  {0, 1, 1, 0, 0, 1, 1}, // 4
  {1, 0, 1, 1, 0, 1, 1}, // 5
  {1, 0, 1, 1, 1, 1, 1}  // 6
};

void setup() {
  for (int i = 0; i < 7; i++) {
    pinMode(segmentPins[i], OUTPUT);
    digitalWrite(segmentPins[i], LOW);
  }
  pinMode(buttonPin, INPUT_PULLUP);
  randomSeed(analogRead(A0));
}

void loop() {
  if (digitalRead(buttonPin) == LOW) {
    // Rolling effect
    for (int i = 0; i < 20; i++) {
      int rollingNum = random(1, 7);
      displayDigit(rollingNum);
      delay(50); // speed of roll
    }

    // Final number
    int finalNum = random(1, 7);

    // Blink effect for final number
    for (int i = 0; i < 5; i++) {
      displayDigit(finalNum);
      delay(200);
      clearDisplay();         // turn off all segments
      delay(200);
    }

    displayDigit(finalNum);   // leave final number showing
    delay(500);               // wait before next roll
  }
}

void displayDigit(int number) {
  int *segments = diceDigits[number - 1];
  for (int i = 0; i < 7; i++) {
    digitalWrite(segmentPins[i], segments[i]);
  }
}

void clearDisplay() {
  for (int i = 0; i < 7; i++) {
    digitalWrite(segmentPins[i], LOW);
  }
}
