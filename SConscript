from building import *
import rtconfig

# get current directory
cwd     = GetCurrentDir()
# The set of source files associated with this SConscript file.
src     = Glob('micropython/py/*.c')
src    += Glob('micropython/shared/readline/*.c')
src    += Glob('micropython/shared/runtime/*.c')
src    += Glob('micropython/extmod/*.c')
src    += Glob('micropython/ports/rt-thread/*.c')
src    += Glob('micropython/ports/rt-thread/modules/*.c')
src    += Glob('micropython/ports/rt-thread/modules/machine/*.c')
src    += Glob('micropython/ports/rt-thread/modules/user/*.c')
src    += Glob('micropython/shared/netutils/*.c')
src    += Glob('micropython/shared/timeutils/*.c')
src    += Glob('micropython/drivers/bus/*.c')
src    += Glob('micropython/port/rt-thread/native/*.c')

path    = [cwd + '/micropython']
path   += [cwd + '/micropython/ports/rt-thread']
path   += [cwd + '/micropython/ports/rt-thread/modules']
path   += [cwd + '/micropython/ports/rt-thread/modules/machine']

LOCAL_CCFLAGS = ''

if rtconfig.CROSS_TOOL == 'gcc':
    LOCAL_CCFLAGS += ' -std=gnu99'
elif rtconfig.CROSS_TOOL == 'keil':
    LOCAL_CCFLAGS += ' --c99 --gnu'

group = DefineGroup('MicroPython', src, depend = ['PKG_USING_MICROPYTHON'], CPPPATH = path, LOCAL_CCFLAGS = LOCAL_CCFLAGS)

Return('group')
