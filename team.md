## Ben10 Team
_A brief introduction to the team based in Malaysia's UTP, collaborating with David M and SCUTTLE engineers for 2025 outcomes._

We are excited about the opportunity to be part of an initiative that aims to make robotics more accessible and affordable. Our team consists of four members with expertise in various fields. I have decided to name my team "UTP Ben10" for this exciting collaboration. The name "Ben10" is inspired by the character from the animated series who can transform into different forms, symbolizing this project adaptability. The number "10" represents our project goal of achieving a 10 kg payload capacity for the SCUTTLE Mini.

**Our Team**
* An image processing expert (Nazeem)
* An autonomous navigation expert (Nik_Robothon participant)
* An energy consumption and generation expert (Faiz)
* An online data monitoring expert (Ibnu_Great challenge finalist)

> **Intro**
> 
> We are particularly interested in integrating our systems into the SCUTTLE Mini. We will provide your team with a detailed methodology as required. We plan to develop two systems using one chassis to demonstrate the design's ease of modification by users. Our current project is a hazardous delivery robot, and I plan to start a domestic drain cleaning system after our current project assessment for my FYP Project.
Additionally, I am one of the participants in Robothon, and one of our team members is a finalist for the Great Challenge. We believe our experience and skills can significantly contribute to the success of the SCUTTLE Mini project.
Our goals align with SCUTTLE's objective to create a 10kg load SCUTTLE Mini version. We are eager to collaborate and help achieve this target. We have attached the current system pictures and video, but we need a new chassis for this system so that the robot can carry more loads on ramp. Our project objective is to develop an autonomous delivery robot, and we aim to ensure a high weight of load per robot weight ratio.
Please let us know how we can get involved and contribute to the project's success. We are looking forward to the possibility of collaborating with the SCUTTLE community.
>
> 

**The Challenge**
![image](https://github.com/user-attachments/assets/e183ad0a-6fa4-44ac-ab6a-77fcfa4f32dc)
![image](https://github.com/user-attachments/assets/ba596044-bf2f-4df3-a9e7-f7cbcedc5b7c)


* **Straight Path (3 meters):** The robot must travel 3 meters straight, detecting and following the black line using IR sensors.
* **Ramp Ascent (30-degree):** The robot will ascend a 1-meter ramp, transitioning from a flat surface to an incline. The IR sensors will ensure the robot stays on course during the ascent.
* **Turn:** After the ramp, the robot will perform a sharp-turn, maintaining path adherence via the IR sensors.
* **Ramp Descent (30-degree):** The robot will navigate a 1-meter ramp, transitioning from a flat surface to a downward slope.
* **Obstacle Avoidance:** At the halfway point along the straight path (after the ramp), an obstacle will be placed to test the robot's ability to detect and avoid the object using the HC-SR04P ultrasonic sensors. Positioned to detect obstacles at a 15 cm threshold. The robot will autonomously change its path to avoid obstacles while ensuring the container remains upright.


## Ben10 in The Making!
> **Progress**

1. Frame (2020):
* Widht - 160mm, Lenght - 200mm, Height - 20mm\
![WhatsApp Image 2025-03-06 at 12 28 12_54d2e751](https://github.com/user-attachments/assets/8a433e03-082a-4091-a33d-c3594a6976b0)
3. Redesign of Bracket:
* SCUTTLE drivetrain system from version 3.0 robot (extrussion 3030) to fit with SCUTTLE Mini (Extrussion 2020)\
![WhatsApp Image 2025-03-07 at 02 12 17_741f409d](https://github.com/user-attachments/assets/12f1cdc7-7353-4467-a8b5-14ebdfaf27b5)
![WhatsApp Image 2025-03-07 at 02 12 17_3046bac4](https://github.com/user-attachments/assets/07e0d67a-9078-429f-88a6-bf0de6aa4962)
4. Motor Integration:
* Four DC brushed motors (32GP-31ZY) with a rated torque of 20 kg·cm each were integrated into the system.
![WhatsApp Image 2025-04-13 at 05 59 24_b0375319](https://github.com/user-attachments/assets/aef2e7f3-fd2e-44ee-a83c-d587f52a0ef3)
5. Wheel Assembly:
* Rubber wheels (65mm diameter) were initially used but proved less precise during obstacle avoidance. (Loose back right tyre when turning).
* Future upgrades include switching to inline skate wheels (80mm) for improved stability, ground clearance, and precision during navigation.
![WhatsApp Image 2025-04-13 at 06 00 37_0178f7b0](https://github.com/user-attachments/assets/3059517d-da07-4dc4-823d-0ca82a4a914e)
6. Sensor System: 
* Three IR sensors are installed for line-following navigation, ensuring accurate detection of black lines on white surfaces.
* An HC-SR04 ultrasonic sensor is mounted for obstacle detection within a 15 cm range.
* Challenges with high-mounted obstacle sensors have been noted, and adjustments are planned to improve detection of low-profile obstacles.
![WhatsApp Image 2025-04-13 at 05 59 24_bd26e732](https://github.com/user-attachments/assets/60cb1737-04c0-48bc-b574-ba9d5c650324)
7. Power System:
* A 12V 3000mAh LiPo battery powers the system, providing an estimated runtime of 20 minutes under full load .
* A PWM solar charge controller manages energy input from a 12V solar panel.
![WhatsApp Image 2025-04-13 at 06 08 19_c811c669](https://github.com/user-attachments/assets/bf3fc5cc-54e6-4adf-9909-d9cca90547a3)
8. Software and Online Monitoring:
* The ESP32 microcontroller handles sensor data processing and motor control.
* Arduino Cloud is used for real-time monitoring of parameters such as speed, battery percentage, solar charging rate, and obstacle distance.
* Raspberry Pi 5 processes live video streams and captures images at checkpoints, uploading them to Google Drive for easy access.
![image](https://github.com/user-attachments/assets/074d29a6-4065-4282-ad5d-727482638f3b)

> **Circuit Diagram for Power Distribution**
![image](https://github.com/user-attachments/assets/879e07df-063e-479a-a3b8-9cb31f8b41f8)

> **Circuit Diagram for Autonomous Navigation**
![image](https://github.com/user-attachments/assets/aef6cf74-2227-4ffb-b10f-fd6bee6ff351)

> **Sensor Logic and Action Responses for Autonomous Navigationn**
| Condition          | Sensor Logic (SL, SR, SVR) | Action               | Speed (L, R) | Notes                                |
|--------------------|----------------------------|----------------------|--------------|--------------------------------------|
| All black          | (1, 1, 1)                  | Stop                 | (0, 0)       | End                                  |
| All white          | (0, 0, 0)                  | forward              | (200, 200)   | Follows the path                     |
| Left detected      | (1, 0, 0)                  | right                | (30, 200)    | Left sensor detects black            |
| Right detected     | (0, 1, 0)                  | left                 | (200, 30)    | Right sensor detects black           |
| Junction detected  | (0, 1, 1)                  | left                 | (130, 0)     | Stops and turns left                 |
| Obstacle detected  | Distance < 10cm            | Stop, reverse, avoid | Various      | Calls avoidance function             |


