// Define the pins for the components

const int buzzer_pin = 11;

const int led1_pin = 10;

const int led2_pin = 9;

const int led3_pin = 8;

// Define the patterns for the LEDs

const int led_off = 0;

const int led_on = 255;

const int warning_pattern[] = {led_on, led_off, led_off};

const int success_pattern[] = {led_off, led_on, led_off};

const int error_pattern[] = {led_off, led_off, led_on};

// Set up the components

void setup() {

  pinMode(buzzer_pin, OUTPUT);

  pinMode(led1_pin, OUTPUT);

  pinMode(led2_pin, OUTPUT);

  pinMode(led3_pin, OUTPUT);

}

// Set up a loop to control the components

void loop() {

  // Play a tone on the buzzer

  tone(buzzer_pin, 1000);

  // Turn on the first LED and turn off the others

  digitalWrite(led1_pin, led_on);

  digitalWrite(led2_pin, led_off);

  digitalWrite(led3_pin, led_off);

  // Wait for 1 second

  delay(1000);

  

  // Turn off the buzzer and turn on the second LED

  noTone(buzzer_pin);

  digitalWrite(led1_pin, led_off);

  digitalWrite(led2_pin, led_on);

  digitalWrite(led3_pin, led_off);

  // Wait for 1 second

  delay(1000);

  

  // Turn on the third LED and display a warning message

  digitalWrite(led1_pin, led_off);

  digitalWrite(led2_pin, led_off);

  digitalWrite(led3_pin, led_on);

  for (int i = 0; i < 3; i++) {

    analogWrite(led1_pin, warning_pattern[i]);

    analogWrite(led2_pin, warning_pattern[i]);

    analogWrite(led3_pin, warning_pattern[i]);

    delay(500);

  }

  

  // Turn off all the LEDs and display a success message

  digitalWrite(led1_pin, led_off);

  digitalWrite(led2_pin, led_off);

  digitalWrite(led3_pin, led_off);

  for (int i = 0; i < 3; i++) {

    analogWrite(led1_pin, success_pattern[i]);

    analogWrite(led2_pin, success_pattern[i]);

    analogWrite(led3_pin, success_pattern[i]);

    delay(500);

  }

  

  // Display an error message

  for (int i = 0; i < 3; i++) {

    analogWrite(led1_pin, error_pattern[0]);

    analogWrite(led2_pin, error_pattern[1]);

    analogWrite(led3_pin, error_pattern[2]);

    delay(500);

  }

}

