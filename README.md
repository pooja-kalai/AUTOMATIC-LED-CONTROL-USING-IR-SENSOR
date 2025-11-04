# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1920" height="1200" alt="Screenshot 2025-11-04 223700" src="https://github.com/user-attachments/assets/557b5f28-adde-48f5-8c5d-f9c397dc8f4b" />


2. Click **File → New STM32 Project**.
  <img width="1920" height="1200" alt="Screenshot 2025-11-04 223926" src="https://github.com/user-attachments/assets/2785dedd-12f9-4246-b114-13806fab1a67" />
<img width="1920" height="1200" alt="Screenshot 2025-11-04 224051" src="https://github.com/user-attachments/assets/09a8cccd-1546-490b-af89-3d6f2d659a86" />


3. Select the **target microcontroller** or board and click **Next**.
 <img width="1920" height="1200" alt="Screenshot 2025-11-04 224916" src="https://github.com/user-attachments/assets/7a276993-32c0-4122-a306-61190d00ba64" />

4. Name the project.
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/9b6437e7-6975-4fa9-b790-a84bb544dd14" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/c29ae203-ba7c-4e93-85f3-1231e5900baa" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/0ac86cb5-68ac-4cf7-812c-e08a36c351bc" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 
8. Edit the generated main program as required.
   <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/05b39060-35d6-420d-9f4d-8721439bd82f" />
<img width="1104" height="621" alt="image" src="https://github.com/user-attachments/assets/2ec55709-a45f-4e6e-8738-6aa94138eab1" />

9. Click **Project → Build All**.
    <img width="1920" height="1200" alt="Screenshot 2025-10-28 094003" src="https://github.com/user-attachments/assets/b4f20227-4bf1-4e80-bfd9-f5647c3b5007" />


10. Link the **HEX file** using the post-build process.
<img width="1920" height="1200" alt="Screenshot 2025-10-28 094003" src="https://github.com/user-attachments/assets/4ed9913e-59e2-46e9-b443-6c513698c830" />


11. Click **Debug** and connect the **STM Nucleo Board**.  
<img width="335" height="194" alt="Screenshot 2025-10-28 094040" src="https://github.com/user-attachments/assets/191174ba-6483-4b92-b016-3078d981bbc7" />


12. Click **Run** to execute the program.
    
---

### 💻 **Program**

```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON
![WhatsApp Image 2025-11-04 at 22 56 25_071c6126](https://github.com/user-attachments/assets/f9789ab6-7d99-419d-8935-df18f6f0e920)



CASE 2: LED OFF
![WhatsApp Image 2025-11-04 at 22 56 25_cceb35d6](https://github.com/user-attachments/assets/90cbb20e-9347-4a9e-b9f8-4120bcda28f4)

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




