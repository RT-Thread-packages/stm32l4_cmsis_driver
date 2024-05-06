from building import *
import os

cwd = GetCurrentDir()
path = [os.path.join(cwd, 'Include')]
src  = [os.path.join(cwd, 'Source', 'Templates', 'system_stm32l4xx.c')]

if rtconfig.PLATFORM in ['gcc', 'llvm-arm']:
    src += [os.path.join(cwd, 'Source', 'Templates', 'gcc', 'startup_stm32l475xx.s')]
elif rtconfig.PLATFORM in ['armcc', 'armclang']:
    src += [os.path.join(cwd, 'Source', 'Templates', 'arm', 'startup_stm32l475xx.s')]
elif rtconfig.PLATFORM in ['iccarm']:
    src += [os.path.join(cwd, 'Source', 'Templates', 'iar', 'startup_stm32l475xx.s')]

group = DefineGroup('STM32L4-CMSIS', src, depend = ['PKG_USING_STM32L4_CMSIS_DRIVER'], CPPPATH = path)

Return('group')
