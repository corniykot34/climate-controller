# Blender Workspace

Primary working model: `climate-controller.blend` (to be added).

## Initial modeling task

Create simplified, dimensionally correct component proxies first. Do **not** build the enclosure until the internal layout has been reviewed.

Suggested object naming:

- PCB_Main
- MCU_ESP32_WROOM_32E
- Sensor_SHT31
- Display_OLED_1_3
- Encoder_PEC11R
- Knob
- USB_C_Breakout
- Terminal_Output

Use millimeters consistently and keep transforms/axes clean enough for repeatable scripted or MCP-assisted operations.

For fit-critical geometry, verify dimensions against `docs/BOM.md` and its linked primary source before modeling.
