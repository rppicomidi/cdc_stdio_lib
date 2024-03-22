# cdc_stdio_lib
Library allows a pico-sdk application that uses TinyUSB to add USB serial stdio support

Normally, the pico-sdk will emit an error at compile time if you attempt to enable
USB stdio on the USB device port in an application that is using TinyUSB for any
reason, including using Pico PIO USB as a USB host. This library copies the
essential bits from the pico-sdk's own source code to glue the TinyUSB CDC
device driver to the pico-sdk's stdio library.

# Requirements
To use this library,
1. In tusb_config.h implement a USB Device interface, enable CFG_TUD_ENABLED and CFG_TUD_CDC
2. Add a CDC interface in the application's device descriptor.
3. The application must first call tud_init() or tusb_init(), then call the function cdc_stdio_lib_init() from this library.
4. Make sure the application periodically calls tud_task().

# License and Copyright
As this code is pretty much a copy from the pico-sdk's own source code, the
Copyright and License belong to Raspberry Pi (Trading) Ltd. All I did was
hack out the parts that prevent it from working with a regular TinyUSB-based
application and wrap it in library form. Please obey the terms of the pico-sdk
license in LICENSE.TXT when using this code, and note the all caps "AS IS"
disclaimer.

None of this implies that Raspberry Pi (Trading) Ltd. is endorsing
this library.
