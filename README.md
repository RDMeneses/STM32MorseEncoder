# STM32F411 Blackpill Morse Encoder

This project demonstrates a Morse code encoder running on an STM32F411 Blackpill board that utilizes a buzzer (with PWM) to play Morse signals and an OLED display (from BitDogLab) to show each character as it is played. Instead of using UART communication, the project features three pre-defined messages that can be selected by a user through a button.

## Features

- **Hardcoded Messages:** Three pre-defined messages stored in firmware.
- **Button Selection:** Use a hardware button to cycle through the available messages.
- **Morse Code Playback:** Converts alphanumeric characters (A-Z, 0-9) to Morse code and reproduces it:
  - **Dot:** 200ms 
  - **Dash:** 600ms 
  - **Intra-character gap:** 200ms 
  - **Inter-character gap:** 600ms
  - **Inter-word gap:** 1400ms
- **OLED Display:** Displays the current character on an SSD1306-based OLED during playback.
- **Buzzer Control:** Uses PWM (via a timer) to drive the buzzer.

## Prerequisites

- **Hardware:**
  - STM32F411 (Blackpill) board with BitDogLab (includes OLED and buzzer).
  - Button connected to a GPIO pin (configured with EXTI).
  - Necessary wiring for I2C (OLED) and PWM (buzzer).
  - ST-Link for programming and debugging.

- **Software:**
  - STM32CubeIDE (includes STM32CubeMX for configuration).
  - Relevant libraries and drivers for the OLED display (e.g., SSD1306, fonts).
  
## File Structure

- `MORSE.ioc` – CubeMX configuration file.
- `Core/Src/main.c` – Main application file with project logic.
- `Core/Inc/` – Header files (including OLED driver headers).
- Other STM32CubeIDE auto-generated files and folders.

## Usage

1. **Configure and Build:**
   - Open the project in STM32CubeIDE.
   - Review the .ioc file to see the configuration:
     - I2C is set up for the OLED.
     - A timer is configured for PWM to drive the buzzer.
     - A GPIO input is configured with an EXTI interrupt for the button.
   - Build the project.

2. **Flash and Run:**
   - Connect your ST-Link programmer and flash the firmware to the STM32F411 board.
   - Run the project in debug or release mode.

3. **Operating the Device:**
   - On startup, the default message is played in Morse code.
   - Press the Button A (on BitDogLab) to cycle through the three hardcoded messages.
   - As each character is played, the corresponding character is displayed on the OLED and its Morse code is produced by the buzzer.

## Customization

- **Messages:** You can modify the array in `main.c` to add or change the pre-defined messages.
- **Timing:** Adjust the delay values in the Morse code playback function to change the tone lengths and pauses.
- **Hardware:** Adapt the pin configuration in the .ioc file as needed for your specific board or wiring.

## License

This project is provided under the MIT License. See the [LICENSE](LICENSE) file for details.
