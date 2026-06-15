# Digital-Alarm-Clock-
Digital Alarm Clock – Project Report
1. Project Overview
This project demonstrates the working of a digital alarm clock using an Arduino Nano, RS232 serial communication, AVR Assembly language, and C++ (Arduino IDE). The project integrates time-keeping, alarm setting, LED alert, and user input via push buttons.
2. Hardware Used
•	Arduino Nano
•	Breadboard
•	Push Buttons (Increment & Confirm)
•	LED (for alarm indication)
•	RS232 Serial Monitor (for output)
•	Jumper wires


4. Software Used
•	Arduino IDE (for .ino sketch)
•	AVR Assembly (for .s source file)
•	Emu8086 IDE (if used for simulation)

6. High-Level Logic (Arduino Sketch)
•	Two buttons allow the user to set the alarm:
o	Button 2: Increment hour/minute.
o	Button 3: Confirm selection and proceed.
•	The alarm time is saved using the assembly functions setAlarmHour() and setAlarmMinute().
•	Every second, the tick() function updates time using assembly code.
•	If the current time matches the alarm time (checked via checkAlarm()), the onboard LED blinks.

7. AVR Assembly Integration
The low-level logic is handled in the clock.s file using AVR Assembly:
Key Assembly Functions:
•	startClock: Initializes all time and alarm variables to 0.
•	tick: Increments minutes and rolls over to the next hour when 60 minutes are reached.
•	getHour & getMinute: Return current hour and minute respectively.
•	setAlarmHour & setAlarmMinute: Store user-defined alarm time.
•	checkAlarm: Compares current time with alarm time and returns 1 if matched.

9. Code Highlights
Arduino Sketch:
cpp
CopyEdit
if (checkAlarm()) {
  if (!alarmActive) {
    Serial.println("⏰ ALARM TRIGGERED!");
    alarmActive = true;
    digitalWrite(ledPin, HIGH); // LED turns on
  }
}

7. Flowchart and Control Logic
The alarm setting follows a finite state machine with three states:
•	SET_HOUR → SET_MINUTE → DONE
This control flow is programmed in the main loop() function of the Arduino.

8. Output Example (Serial Monitor)
sql
CopyEdit
Set alarm using buttons:
Btn2: Increment | Btn3: Confirm
Set Alarm Hour:
Alarm Hour: 6
Set Alarm Minute:
Alarm Minute: 30
Alarm set to 06:30
Alarm started!
Time: 06:30
⏰ ALARM TRIGGERED!

9. Conclusion
This project bridges high-level programming (Arduino C++) with low-level control (AVR Assembly) to build a fully functional digital alarm clock. It effectively demonstrates the use of memory-mapped registers, modular coding, and serial communication.

10. Future Enhancements
•	Add an LCD display to show real-time clock updates.
•	Integrate a buzzer for audio alarm.
•	Include EEPROM storage to retain alarm settings after reset.

