# skroll
USB HID scroll wheel module for custom keyboards/macropads using XIAO ESP32S3. Features Alps EC10E encoder with 24 detents for tactile scrolling feedback + button for left-click. Plug-and-play on Windows/Mac/Linux. Includes visual connection indicator. Perfect for adding physical scroll control to DIY input devices.

Features

Tactile Scrolling: Alps EC10E encoder with 24 mechanical detents provides satisfying click feedback with each scroll increment
Smooth Operation: Physical wheel mass creates momentum for rapid scrolling while detents enable precise single-line control
Plug & Play: Standard USB HID device works instantly on Windows, macOS, and Linux - no drivers required
Visual Feedback: Cursor draws a square pattern on connection to confirm device recognition
Left Click: Integrated tactile button provides mouse click functionality
Compact Design: Minimal footprint perfect for custom keyboard integration

Hardware Requirements

Seeed Studio XIAO ESP32S3
Alps EC10E1220501 Rotary Encoder (12 pulses/revolution, 24 detents)
TE Connectivity 1825910-7 Tactile Switch
3× 10kΩ resistors
1× 0.1µF ceramic capacitor
USB-C cable

Wiring Diagram
XIAO ESP32S3 (USB-C at top)
         ┌─────┐
D0 ●─────┤     ├─────● USB
D1 ●─────┤     ├─────● GND  
D2 ●─────┤     ├─────● 3V3
D3 ●─────┤     ├─────● D10
         └─────┘

Connections:
- Encoder A   → D0 (GPIO1) + 10kΩ pull-up to 3V3
- Encoder B   → D1 (GPIO2) + 10kΩ pull-up to 3V3
- Encoder COM → GND
- Button Pin1 → D2 (GPIO3) + 10kΩ pull-up to 3V3  
- Button Pin2 → GND
- 0.1µF capacitor across button pins
Software Setup

Install Arduino IDE (2.0 or later)
Add ESP32 board support:

File → Preferences → Additional Boards Manager URLs
Add: https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json


Install ESP32 board package:

Tools → Board → Boards Manager
Search "ESP32" and install latest version


Select board and settings:

Board: "XIAO_ESP32S3"
USB CDC On Boot: Disabled (important!)
USB Mode: USB-OTG (TinyUSB)



Installation

Clone this repository
Open skroll.ino in Arduino IDE
Connect XIAO ESP32S3 via USB-C
Upload the code
Wait for cursor to draw square pattern (confirms successful connection)

Usage

Scroll: Rotate the encoder wheel

Slow rotation for precise line-by-line scrolling
Fast spin for momentum-based rapid scrolling


Click: Press the button for left mouse click
Direction: Swap encoder A/B connections if scroll direction is reversed

Technical Details

Interrupt-driven quadrature decoding ensures no missed steps
Hardware debouncing for reliable operation
Adaptive scroll speed based on rotation velocity
5-second programming window on startup for easy updates

Background
SKROLL was created in response to the discontinuation of the beloved Panasonic EVQWGD001 encoder, which had become a staple in the custom keyboard community for its excellent tactile feedback and reliability. With the EVQWGD001 no longer in production and existing stock depleted, the community was left searching for alternatives that could match its performance.
This project aims to provide a modern, accessible replacement using readily available components while maintaining the tactile scrolling experience that made the EVQWGD001 so popular in custom keyboards and macropads.
License
MIT License - see LICENSE file for details.
Commercial Use
While this project is open source under the MIT License, commercial users are kindly requested to:

Provide attribution in your product documentation
Consider supporting the project through sponsorship
Contact [your-email@example.com] for commercial support options

This ensures continued development and support for the open source community.
Contributing
Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.
Acknowledgments

Built for the custom mechanical keyboard community
Inspired by the need for better scroll control in creative applications
Created as a spiritual successor to the discontinued Panasonic EVQWGD001
Thanks to the r/ErgoMechKeyboards community for discussions on encoder alternatives
