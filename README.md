# INTERFACING-MCP3424-ADC-CHIP-USING-I2C

    HOWTO cross compile for the NanoPC-T2

1. Find a device driver for the chip under the path  /drivers/iio/adc/mcp3422.ko
2. Integrate the module into the kernel as a module .

   $ make menuconfig
    
   device drivers --->Industrial IO Support -----> Microchip Technology(MCP3422/23/24/28)
   
   Recompile the kernel using make ARCH=arm
   
   
 3. $ make ARCH=arm
 
 4. Install the module using $ make module_install.
 
 5. Find the module in /lib/modules/4.4-s5p4418/drivers/iio/adc/mcp3422.ko
 
 6. Copy the module into the target device.
 
 7. Load the module using insmod command i,e insmod mcp3422.ko
 
 8. Instantiate the mcp3424 device at 0x68 using the command below.
 
  echo mcp3424 0x68 > /sys/bus/i2c/devices/i2c-0/new_device
  
  The device get Instantiated at 0x68 check using i2cdetect -y 0
  
  0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- UU -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- 51 -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- UU -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --
