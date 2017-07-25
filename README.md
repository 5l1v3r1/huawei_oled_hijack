Huawei OLED hijacking library
=============================

This library adds advanced menu to the OLED display of Huawei E5372 porable LTE router (and probably others).  
This is achieved by hijacking certain library calls in the "oled" executable file.

Currently this library adds 3 new menu items:

* **Network Mode**  
 (Auto, GSM Only, UMTS Only, LTE Only, LTE -> UMTS, LTE -> GSM, UMTS -> GSM)
* **TTL Mangler** (set TTL of outbound packets to 64 or 128)
* **IMEI Changer** (switch between stock, random Android and random Windows Phone IMEI)

![Screenshot 1](https://i.imgur.com/LioaPph.png) ![Screenshot 2](https://i.imgur.com/Z8UlVX4.png) ![Screenshot 3](https://i.imgur.com/mDXC7Yc.png) ![Screenshot 4](https://i.imgur.com/nR6fORk.png) ![Screenshot 5](https://i.imgur.com/hDS5V3O.png)

## How does it work
This library hijacks `sprintf()`, `osa_print_log_ex()` and `register_notify_handler()`.

`sprintf()` is hijacked to inject custom menu items, `register_notify_handler()` registers it's own proxy handler which intercepts button press events.

Custom menu is drawn in "Device Information" page, hijacking "Homepage" string. The library listens for POWER button press events on the exact page, executes page handler and redraws menu again, by leaving it and opening that same page again.

Very simple, yet effective.

## Used software

[Huaweicalc](https://github.com/forth32/huaweicalc) couresy of forth32  
**imei_generator** courtesy of Egor Grhko  
**atc** courtesy of rust3028

**Contributions are welcome**.