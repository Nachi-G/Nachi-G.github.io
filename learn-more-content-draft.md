# Project “Learn More” Content Draft

This is the working copy for the expanded project sections. The headings are written for the website, while the notes at the end identify facts that still need to be confirmed.

## Rhino Rover

### Short summary

A voice-controlled ESP32-S3 rover with local speech recognition, language processing, and text-to-speech. It can also be driven manually or navigate around obstacles on its own.

### What it is

Rhino Rover is a multimodal robot built around an ESP32-S3. Its hardware includes N20 motors, a motor driver, OLED display, distance sensor, amplifier and speaker, power-management hardware, and a modular port for adding other components.

The rover has three operating modes:

- **Voice control:** responds to spoken movement commands, sensor questions, and conversational prompts.
- **Manual control:** receives movement commands through a browser interface.
- **Obstacle avoidance:** reads its distance sensor and moves without direct input.

### How the system works

The system is split between the rover and a computer companion. The computer runs the voice pipeline locally:

1. **Whisper** converts microphone input into text.
2. **Qwen** routes the request into a structured robot command or conversational response.
3. **Piper** converts a response into speech.
4. The computer sends commands or a WAV file over Wi-Fi for the rover to execute or play through its speaker.

The rover and computer communicate through TCP and WebSockets. That connection carries movement commands, live sensor data, browser-recorded audio, and length-prefixed WAV files.

### Engineering work

I developed a non-blocking CircuitPython architecture so networking, sensor readings, motor control, OLED animation, and audio playback could operate together without freezing the robot. I prototyped and tested each subsystem separately before integrating them into the full rover.

I also designed the chassis and electronics layout around practical constraints: component access, secure mounting, simple assembly, and space for future modules. The completed platform is now being adapted into a modular Python robotics curriculum.

### My role

I owned the project end to end: concept development, technical research, subsystem prototyping, electronics, CAD, embedded programming, computer-side software, system integration, testing, and production documentation.

---

## OpenCV Soccer Goalie

### Short summary

A World Cup-inspired robot that tracks a ball and moves a servo-powered goalie to block it.

### What it is

The computer-vision version uses HSV filtering and contour detection to locate the ball, estimate its direction, and actuate a servo to block the shot. I also built simpler versions that used distance sensors instead of a camera.

### Designing the physical system

Most of the iteration went into turning the idea into a goal that looked like a real net but was still practical to manufacture and use. The final design needed to:

- Print with minimal support material.
- Pack nearly flat for transportation.
- Assemble easily without falling apart during use.
- Fit the existing LearnToBot build-plate ecosystem.
- Hold the servo and sensors securely while allowing the goalie to move freely.

I iterated on the frame, netting, slide-in rails, sensor and servo mounts, and male-female joints in SolidWorks. The rails needed enough clearance to assemble smoothly while retaining enough friction to stay together. I also had to account for printer tolerances and the dimensions of the existing build plates.

### My role

I took the project from concept through working prototypes and a production-ready assembly. That included researching the sensing approaches, programming the camera- and distance-sensor-based versions, designing the electronics and CAD, testing tolerances, and creating assembly instructions and video guides.

---

## Self-Balancing Robot

### Short summary

A two-wheeled robot that uses IMU feedback and PID control to remain upright.

### What I worked on

I tuned the PID controller, added a sensor-initialization phase, and adjusted the control logic to account for the robot's center-of-mass offset. I first proved the system with a popsicle-stick chassis, then rebuilt it as a more repeatable 3D-printed assembly.

### My role

I handled the controls, electronics, chassis iteration, CAD, testing, and final assembly documentation.

---

## ShinSavers

### Short summary

A shin-splint problem became an experiment in impact attenuation, wearable prototyping, and working through inconclusive data.

### Where the idea came from

During track season, several teammates and I dealt with painful shin splints. Rest was the main recommendation, so I began looking for a way to reduce the impact felt while running.

I was inspired by tennis-racquet dampeners, which change how vibration feels at impact. I wanted to explore whether a wearable device could apply a similar idea to running.

### Prototype and experiment

I built several rough prototypes and designed a treadmill experiment to compare them. Two accelerometers were placed on opposite sides of the test area—one near the foot and one near the ankle—to measure how acceleration changed across the device. We used a constant treadmill speed and a fixed number of steps to make each trial as repeatable as possible.

### The hardest part

The sensor data was inconsistent and contained significant outliers. I tested several analysis methods, including rolling comparative-maximum filters with different window lengths, to determine whether the signal could be cleaned without hiding meaningful results.

The experiment did not produce a statistically reliable result, so I could not conclude that the prototype reduced impact. The most valuable outcome was learning how difficult it is to design a repeatable biomechanics experiment, distinguish a real effect from sensor noise, and report an inconclusive result honestly.

### My role

I developed the idea, researched the mechanics, built the prototypes, designed and ran the experiment, and analyzed the sensor data. I worked with a partner who focused primarily on the abstracts and written competition materials.

---

## RetiBox

### Short summary

A mobile-browser prototype for creating, viewing, and sharing augmented-reality models without requiring a dedicated app.

### Where the idea came from

The idea started when I passed an open house and wondered whether rooms could be staged with augmented reality instead of moving physical furniture. As I researched the idea, I found that the larger obstacle was accessibility: many AR tools were powerful, but creating and viewing models still involved slow or complicated workflows.

RetiBox explored a simpler approach. A user could upload images of an object, create an AR model, and view or share it from a phone browser.

### My role

I helped shape the original concept, researched the tools and technical approach, and led the front-end development of the prototype.

---

## Facts to confirm before publishing

- **Rhino Rover power system:** confirm whether the 5 V, 2 A step-up converter is separate from the battery-management system. A boost converter and a BMS perform different jobs, so the website should not treat the terms as interchangeable.
- **Rhino Rover curriculum:** confirm whether it is accurate to say the platform “is being adapted” into a curriculum or whether “was designed with future curriculum use in mind” is safer.
- **RoboGoalie sensing:** confirm whether “estimate its direction” is technically exact or whether the code predicts an interception position.
- **Self-balancing robot:** identify the IMU model and clarify how the center-of-mass offset was represented in the code, if those details are worth showing.
- **ShinSavers:** confirm the accelerometer locations and whether “rolling comparative-maximum filter” is the name you want to use publicly.
- **RetiBox:** add the front-end tools/frameworks you used, what parts your teammates owned, and whether image upload produced a model automatically or supported a separate modeling workflow.
