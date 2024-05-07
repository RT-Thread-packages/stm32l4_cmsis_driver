from building import *
import os

# Import environment variables
Import('env')

# Get the current working directory
cwd = GetCurrentDir()

# Initialize include paths and source files list
path = [os.path.join(cwd, 'Include')]
src = [os.path.join(cwd, 'Source', 'Templates', 'system_stm32l4xx.c')]

# Map microcontroller units (MCUs) to their corresponding startup files
mcu_startup_files = {
    'STM32L412xx': 'startup_stm32l412xx.s',
    'STM32L422xx': 'startup_stm32l422xx.s',
    'STM32L431xx': 'startup_stm32l431xx.s',
    'STM32L432xx': 'startup_stm32l432xx.s',
    'STM32L433xx': 'startup_stm32l433xx.s',
    'STM32L442xx': 'startup_stm32l442xx.s',
    'STM32L443xx': 'startup_stm32l443xx.s',
    'STM32L451xx': 'startup_stm32l451xx.s',
    'STM32L452xx': 'startup_stm32l452xx.s',
    'STM32L462xx': 'startup_stm32l462xx.s',
    'STM32L471xx': 'startup_stm32l471xx.s',
    'STM32L475xx': 'startup_stm32l475xx.s',
    'STM32L476xx': 'startup_stm32l476xx.s',
    'STM32L485xx': 'startup_stm32l485xx.s',
    'STM32L486xx': 'startup_stm32l486xx.s',
    'STM32L496xx': 'startup_stm32l496xx.s',
    'STM32L4A6xx': 'startup_stm32l4a6xx.s',
    'STM32L4P5xx': 'startup_stm32l4p5xx.s',
    'STM32L4Q5xx': 'startup_stm32l4q5xx.s',
    'STM32L4R5xx': 'startup_stm32l4r5xx.s',
    'STM32L4R7xx': 'startup_stm32l4r7xx.s',
    'STM32L4R9xx': 'startup_stm32l4r9xx.s',
    'STM32L4S5xx': 'startup_stm32l4s5xx.s',
    'STM32L4S7xx': 'startup_stm32l4s7xx.s',
    'STM32L4S9xx': 'startup_stm32l4s9xx.s',
}

# Check each defined MCU, match the platform and append the appropriate startup file
for mcu, startup_file in mcu_startup_files.items():
    if mcu in env.get('CPPDEFINES', []):
        if rtconfig.PLATFORM in ['gcc', 'llvm-arm']:
            src += [os.path.join(cwd, 'Source', 'Templates', 'gcc', startup_file)]
        elif rtconfig.PLATFORM in ['armcc', 'armclang']:
            src += [os.path.join(cwd, 'Source', 'Templates', 'arm', startup_file)]
        elif rtconfig.PLATFORM in ['iccarm']:
            src += [os.path.join(cwd, 'Source', 'Templates', 'iar', startup_file)]
        break

# Define the build group
group = DefineGroup('STM32L4-CMSIS', src, depend=['PKG_USING_STM32L4_CMSIS_DRIVER'], CPPPATH=path)

# Return the build group
Return('group')
