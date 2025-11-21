[[!meta title="LoRa APRS iGate on TTGO LoRa32"]]

# LoRa APRS iGate

The official documentation of
[https://github.com/lora-aprs/LoRa_APRS_iGate](https://github.com/lora-aprs/LoRa_APRS_iGate)
uses the PlatformIO plugin of MS Visual Studio Code. Here are the commands to
get it running without the GUI:

```
git clone https://github.com/lora-aprs/LoRa_APRS_iGate.git
cd LoRa_APRS_iGate
```

* Edit data/is-cfg.json with your station info
* Edit platformio.ini: `board = ttgo-lora32-v21`

```
pip3 install platformio

pio run
...
Building .pio/build/lora_board/firmware.bin
...

pio run --target upload
...
Uploading .pio/build/lora_board/firmware.bin
...

pio run --target uploadfs
...
Building SPIFFS image from 'data' directory to .pio/build/lora_board/spiffs.bin
/is-cfg.json
...
Uploading .pio/build/lora_board/spiffs.bin
...
```

# LoRa APRS Tracker

The procedure for the tracker is the same, but the GPS module might need a
reset first:

```
git clone https://github.com/lora-aprs/TTGO-T-Beam_GPS-reset.git
cd TTGO-T-Beam_GPS-reset
pio run -e ttgo-t-beam-v1
pio run --target upload -e ttgo-t-beam-v1
# screen /dev/ttyACM0 115200
```

... and then upload https://github.com/lora-aprs/LoRa_APRS_Tracker.git

[[!tag afu]]
