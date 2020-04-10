
# mraa

Eclipse Mraa (Libmraa) is a C/C++ library with bindings to Java, Python and JavaScript to interface with the IO on Galileo, Edison & other platforms, with a structured and sane API where port names/numbering matches the board that you are on. Use of libmraa does not tie you to specific hardware with board detection done at runtime you can create portable code that will work across the supported platforms.

The intent is to make it easier for developers and sensor manufacturers to map their sensors & actuators on top of supported hardware and to allow control of low level communication protocol by high level languages & constructs.

The MRAA project is joining the Eclipse Foundation as an Eclipse IoT project. You can read more about this here.

C API Modules 	C++ API Classes
gpio 	Gpio class
led 	Led class
i2c 	I2c class
aio 	Aio class
pwm 	Pwm class
spi 	Spi class
uart 	Uart class
common 	common


[github](https://github.com/eclipse/mraa)
[doc](http://iotdk.intel.com/docs/master/mraa/)


# c-periphery

A C library for peripheral I/O (GPIO, LED, PWM, SPI, I2C, MMIO, Serial) in Linux.

c-periphery is a small C library for GPIO, LED, PWM, SPI, I2C, MMIO, and Serial peripheral I/O interface access in userspace Linux. c-periphery simplifies and consolidate the native Linux APIs to these interfaces. c-periphery is useful in embedded Linux environments (including Raspberry Pi, BeagleBone, etc. platforms) for interfacing with external peripherals. c-periphery is re-entrant, has no dependencies outside the standard C library and Linux, compiles into a static library for easy integration with other projects, and is MIT licensed.

Using Python or Lua? Check out the python-periphery and lua-periphery projects.

[github](https://github.com/vsergeev/c-periphery)

# wiringX

Modular GPIO interface

wiringX is a modular approach to several GPIO interfaces.

wiringX will export all common GPIO functions also found libraries such as wiringPi, wiringHB, wiringOP, etc but when using wiringX all the appropriate GPIO functions are available for various different platforms with only one uniform library. So when using wiringX, your program will just work in regard of GPIO functionality, whatever platform your program is running on.

The wiringPi and wiringHB are almost a direct copy of their initial library. However, wiringX currently does not yet support all features of the Hummingboard and Raspberry Pi I/O. Therefore, wiringPi has been stripped so it only supports those features also supported by wiringX.

Those features currently are:

    GPIO reading, writing, and interrupts.
    IC2 reading and writing.

Please refer to the documentation at https://manual.wiringx.org or in the docs folder.

[github](https://github.com/wiringX/wiringX)
