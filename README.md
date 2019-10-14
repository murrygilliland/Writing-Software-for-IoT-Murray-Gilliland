# Writing-Software-for-IoT-Murray-Gilliland
Prototype Stock adjustment device code
Stock Adjustment is read into deviced - Stock Adjustment is saved and written to a Libre Office Calc. - Adjustment is displayed on a computer monitor via wireless access
#*********************************************************#
#   Author  : Murray Gilliland
#   email   : murray.gilliland.fresca@outlook.com
#*********************************************************#


#import
import RPi.GPIO as GPIO
import time
from pad4pi import rpi_gpio

#******************************************#
KEYPAD = [
    ["1", "2", "3", "A"],
    ["4", "5", "6", "B"],
    ["7", "8", "9", "C"],
    ["*", "0", "#", "D"]
]

COL_PINS = [17, 15, 14, 4] # BCM numbering
ROW_PINS = [24,22,27,18] # BCM numbering

factory = rpi_gpio.KeypadFactory()
keypad = factory.create_keypad(keypad=KEYPAD, row_pins=ROW_PINS, col_pins=COL_PINS)

#******************************************#

def printKey(key):
    lcd_byte(ord(key),LCD_CHR)

#******************************************#

# printKey will be called each time a keypad button is pressed
keypad.registerKeyPressHandler(printKey)
