#include <Wire.h> 
#include <RTClib.h> 
#include <Servo.h> 
RTC_DS3231 rtc; 
Servo medicineServo; 
const int buzzer = 8; 
const int led = 10; 
const int servoPin = 9; 
const int stopButton = 7; 
#define PIR_PIN 5 
bool alarm1On = false; 
bool alarm2On = false; 
bool stopPressed1 = false; 
bool stopPressed2 = false; 
bool motionDetected1 = false; 
bool motionDetected2 = false; 
bool servoDone1 = false; 
bool servoDone2 = false; 
const int alarmHour1 = 22; 
const int alarmMinute1 = 10; 
const int alarmHour2 = 22; 
const int alarmMinute2 = 12; 
int currentServoPosition = 0; 
void setup() { 
  pinMode(buzzer, OUTPUT); 
  pinMode(led, OUTPUT); 
  pinMode(stopButton, INPUT_PULLUP); 
  pinMode(PIR_PIN, INPUT); 
  Serial.begin(9600); 
  Serial.println("🔧 System Initialized. Waiting for alarms..."); 
  if (!rtc.begin()) { 
    Serial.println("⚠ Couldn't find RTC! Check connections."); 
    while (1); 
  } 
  if (rtc.lostPower()) { 
    Serial.println("⚠ RTC lost power! Set time again using 'setRTCTime()'."); 
  } 
 
  medicineServo.attach(servoPin); 
  medicineServo.write(currentServoPosition); 
  delay(500); 
  medicineServo.detach(); 
} 
void loop() { 
  DateTime now = rtc.now(); 
  Serial.print("⏰ Current Time: "); 
  Serial.print(now.hour()); 
  Serial.print(":"); 
  Serial.print(now.minute()); 
  Serial.print(":"); 
  Serial.println(now.second()); 
  // Alarm 1 
  if (now.hour() == alarmHour1 && now.minute() == alarmMinute1 && !stopPressed1) { 
    if (!alarm1On) { 
      alarm1On = true; 
      Serial.println("🔔 Alarm 1 Triggered!"); 
      digitalWrite(buzzer, HIGH); 
      digitalWrite(led, HIGH); 
    } 
    if (!servoDone1) { 
      rotateServoBy(90);  // Rotate 0 to 90 
      servoDone1 = true; 
    } 
    if (isHandDetected() && !motionDetected1) { 
      motionDetected1 = true; 
      Serial.println("✋ Hand Detected for Alarm 1 — MEDICINE TAKEN!"); 
    } 
  } 
  // Alarm 2 
  if (now.hour() == alarmHour2 && now.minute() == alarmMinute2 && !stopPressed2) { 
    if (!alarm2On) { 
      alarm2On = true; 
      Serial.println("🔔 Alarm 2 Triggered!"); 
      digitalWrite(buzzer, HIGH); 
      digitalWrite(led, HIGH); 
    } 
    if (!servoDone2) { 
      rotateServoBy(90);  // Rotate 90 to 180 
      servoDone2 = true; 
    } 
    if (isHandDetected() && !motionDetected2) { 
      motionDetected2 = true; 
      Serial.println("✋ Hand Detected for Alarm 2 — MEDICINE TAKEN!"); 
    } 
  } 
  // Stop button logic 
  if (digitalRead(stopButton) == LOW) { 
    delay(200);  // Debounce 
    if (digitalRead(stopButton) == LOW) { 
      if (alarm1On && motionDetected1) { 
        Serial.println("🛑 Stop pressed for Alarm 1 after hand detection."); 
        stopAlarm(1); 
      } else if (alarm2On && motionDetected2) { 
        Serial.println("🛑 Stop pressed for Alarm 2 after hand detection."); 
        stopAlarm(2); 
      } else { 
        Serial.println("⚠ Stop button pressed, but hand not detected yet."); 
      } 
    } 
  } 
 
  delay(200); 
} 
// Move servo by specific angle from current position 
void rotateServoBy(int degrees) { 
  medicineServo.attach(servoPin); 
  int targetPosition = currentServoPosition + degrees; 
  for (int pos = currentServoPosition; pos <= targetPosition; pos++) { 
    medicineServo.write(pos); 
    delay(15); 
  } 
  currentServoPosition = targetPosition;  // Update current position 
  delay(500); 
  medicineServo.detach(); 
} 
// Smart motion detection to detect quick hand movement 
bool isHandDetected() { 
  if (digitalRead(PIR_PIN) == HIGH) { 
    unsigned long startTime = millis(); 
    delay(300);  // Brief check delay 
    if (digitalRead(PIR_PIN) == LOW && millis() - startTime < 1000) { 
      return true;  // Detected quick motion (likely hand) 
    } 
  } 
  return false; 
} 
void stopAlarm(int alarmNumber) { 
  if (alarmNumber == 1) { 
    stopPressed1 = true; 
    alarm1On = false; 
    motionDetected1 = false; 
  } else if (alarmNumber == 2) { 
    stopPressed2 = true; 
    alarm2On = false; 
    motionDetected2 = false; 
  } 
  digitalWrite(buzzer, LOW); 
  digitalWrite(led, LOW); 
  medicineServo.detach(); 
} 
// Use this manually if you need to set RTC time again 
void setRTCTime() { 
  rtc.adjust(DateTime(2025, 4, 3, 16, 58, 0)); // YYYY, MM, DD, HH, MM, SS 
  Serial.println("✅ RTC time set successfully."); 
}
