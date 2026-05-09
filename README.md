# Arduino Alarm Clock Portfolio

## Project Overview

This portfolio documents our Arduino alarm clock project for the Digital Design & Fabrication exercise. The goal of the task was to build a functional alarm clock using an Arduino Uno, an LCD display, a buzzer, a real-time clock module, and push buttons. The system keeps the current time, allows alarm control through buttons, displays information on the LCD screen, and uses the buzzer as the alarm output.

The project was developed step by step by testing each component separately before combining them into one working circuit. We documented the process with photos and videos, including the buzzer test, LCD test, RTC connection, push button interface, and final alarm clock setup.

## Task Requirements

The exercise required us to build a programmable alarm clock circuit. According to the task, the alarm clock should:

- Keep and display the current time.
- Allow the alarm time to be set without changing the code.
- Ring or make noise when the alarm time is reached.
- Allow the alarm to be turned off using physical controls.
- Use the Arduino Uno together with external electronic components.
- Be documented using photos, observations, and videos.

We also explored an additional snooze-style function, shown on the LCD as “Snoozed 1 Min!”, to improve the basic alarm clock idea.

## Components Used

| Component | Purpose |
|---|---|
| Arduino Uno | Main microcontroller used to control the system |
| Breadboard | Used for prototyping and connecting components |
| Jumper wires | Used to connect the circuit elements |
| Buzzer module | Used as the alarm sound output |
| 16x2 I2C LCD display | Used to show time, messages, and alarm status |
| RTC module | Used to keep real-world time |
| Push buttons | Used as user controls for setting, stopping, or snoozing the alarm |
| USB cable | Used to power and program the Arduino |
| Arduino IDE | Used to write, upload, and test the code |

## Development Process

We built the system in smaller sub-circuits first. This helped us understand how each component worked before connecting everything together. Each stage was tested separately and then integrated into the final alarm clock circuit.

---

## Sub-circuit 1: Buzzer Test

![Buzzer test](assets/images/buzzer_test.jpg)

First, we tested the buzzer module with the Arduino Uno. The buzzer was connected to the Arduino through the breadboard and controlled using a digital output pin. By changing the HIGH and LOW states in the code, we were able to make the buzzer turn on and off.

This test helped us understand how the alarm sound could be generated later in the final circuit. The buzzer became the main output device for the alarm notification.

**Observation:**  
When the Arduino pin was set to HIGH, the buzzer produced sound. When the pin was set to LOW, the buzzer stopped. This confirmed that the buzzer could be controlled directly through Arduino code.

---

## Sub-circuit 2: LCD Display Test

![LCD test](assets/images/lcd_test.jpg)

The next step was testing the 16x2 LCD display. The LCD used I2C communication, which reduced the number of wires needed. Instead of using many digital pins, the display was connected using power, ground, SDA, and SCL.

We tested the LCD by displaying simple text messages. This confirmed that the display was wired correctly and that the Arduino could send data to it.

![LCD code test](assets/images/lcd_test-code_lcd.jpg)

The Arduino IDE was used to upload the LCD test code. During this step, we checked that the LCD library was included correctly and that the I2C address matched the display.

**Observation:**  
The LCD successfully displayed text, which showed that the I2C connection and code were working. This display was later used to show the current time and alarm status.

---

## Sub-circuit 3: Real Time Clock Connection

![RTC connection](assets/images/rtc_connection.jpg)

After testing the LCD, we connected the RTC module. The RTC module was important because it allowed the system to keep real time instead of relying only on Arduino timing functions.

The RTC also used I2C communication, so it shared the SDA and SCL lines with the LCD. This allowed both the display and the RTC to work together on the same communication bus.

**Observation:**  
The LCD displayed the current time from the RTC module. This confirmed that the RTC was communicating correctly with the Arduino and that the time data could be shown on the screen.

---

## Sub-circuit 4: Push Button Interface

![Button and buzzer test](assets/images/button+buzzer.JPEG)

We added push buttons to control the alarm clock. The buttons were used as input devices, allowing the user to interact with the system without editing the code.

The buttons were connected to Arduino input pins. In the code, the button states were read using digital input. The buttons were useful for functions such as stopping the buzzer, changing the alarm mode, or activating snooze.

![Buttons close-up](assets/images/breadboard side of buttons.JPEG)

This close-up shows the button layout on the breadboard. Multiple buttons were used so that different actions could be assigned to different controls.

**Observation:**  
The push buttons worked as physical controls for the circuit. When pressed, they changed the input state detected by the Arduino. This allowed us to control alarm behavior directly from the hardware.

---

## Combining the Circuit

![Work in progress](assets/images/middle of work.jpg)

After each component was tested individually, we combined them into one circuit. This stage involved connecting the Arduino, LCD, RTC, buzzer, and push buttons together.

This was one of the most important stages because all parts had to work at the same time. The LCD and RTC shared the I2C communication lines, while the buzzer and buttons used digital pins.

**Challenges:**

- Managing many jumper wires on the breadboard.
- Keeping the wiring organized.
- Making sure all components shared a common ground.
- Checking that the I2C devices were connected correctly.
- Making sure the buttons did not interfere with the buzzer or display.

**Solution:**  
We tested the circuit in smaller sections and then connected everything gradually. This made it easier to find mistakes and confirm that each part was working before adding the next one.

---

## Final Alarm Clock Circuit

![Final circuit](assets/images/final_circuit.jpg)

The final circuit combined all required elements into a working alarm clock. The LCD displayed the current time and alarm-related messages. The RTC provided accurate timekeeping. The buttons were used for user input, and the buzzer acted as the alarm output.

In the final version, the LCD showed the current time and a snooze message. This showed that the circuit was not only displaying time but also responding to alarm logic.

**Final features:**

- Real-time display using RTC.
- LCD output for time and status messages.
- Buzzer alarm output.
- Push button control.
- Snooze message displayed on the LCD.
- Fully assembled Arduino-based alarm clock prototype.

---

## Demo Videos

The project was also documented using short videos.

| Video | Description |
|---|---|
| `assets/videos/button_test video.mp4` | Demonstrates push button testing and interaction |
| `assets/videos/rtc_video.mp4` | Demonstrates RTC time display and clock functionality |

To view the videos, open the files from the `assets/videos` folder in this repository.

---

## Code Structure

The Arduino code was built around the following logic:

```cpp
// Basic structure of the alarm clock program

#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <RTClib.h>

// LCD and RTC objects
// Button pins
// Buzzer pin
// Alarm variables

void setup() {
  // Start serial communication
  // Initialize LCD
  // Initialize RTC
  // Set buzzer pin as output
  // Set button pins as input
}

void loop() {
  // Read current time from RTC
  // Display time on LCD
  // Read button states
  // Check alarm condition
  // Turn buzzer on when alarm time is reached
  // Stop or snooze alarm when button is pressed
}
```

The final code can be added to the repository as an `.ino` file, for example:

```text
arduino_alarm_clock.ino
```

---

## Problems and Fixes

| Problem | Fix |
|---|---|
| LCD did not show text at first | Checked wiring and I2C address |
| Too many jumper wires made the circuit confusing | Tested each part separately before combining |
| Buttons needed stable readings | Used proper input setup and checked button wiring |
| RTC and LCD both used I2C | Connected both devices to the same SDA and SCL lines |
| Alarm logic needed user control | Added push buttons for interaction |

---

## What We Learned

Through this project, we learned how to build a complete Arduino system using multiple input and output components. We learned how to use I2C communication with both the LCD and RTC module, how to control a buzzer, and how to read button inputs.

We also learned the importance of testing each part separately. Building the buzzer, LCD, RTC, and button circuits one at a time made the final integration easier. The project showed how hardware and software work together in an embedded system.

## Reflection

This project helped us understand how a real electronic system is developed. Instead of connecting everything at once, we worked step by step and tested every part before building the final circuit.

The most challenging part was organizing the wiring and making sure all components worked together. The most successful part was getting the LCD to show the time from the RTC and adding alarm-related control using buttons.

If we improved the project further, we would make the wiring cleaner, add a case for the circuit, improve the alarm setting interface, and add more advanced snooze options.

## Repository Structure

```text
arduino-alarm-clock-portfolio/
├── README.md
├── arduino_alarm_clock.ino
├── assets/
│   ├── images/
│   │   ├── buzzer_test.jpg
│   │   ├── button+buzzer.JPEG
│   │   ├── breadboard side of buttons.JPEG
│   │   ├── lcd_test.jpg
│   │   ├── lcd_test-code_lcd.jpg
│   │   ├── rtc_connection.jpg
│   │   ├── middle of work.jpg
│   │   └── final_circuit.jpg
│   └── videos/
│       ├── button_test video.mp4
│       └── rtc_video.mp4
└── docs/
    └── Manual_Ex2_AlarmClock.pdf
```

## Conclusion

We successfully built and documented an Arduino-based alarm clock prototype. The system uses an RTC module to keep time, an LCD screen to display information, buttons for user input, and a buzzer for the alarm sound. The final result demonstrates how several electronic components can be combined into one functional embedded system.
