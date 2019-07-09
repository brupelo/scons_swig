import distutils.sysconfig
import os
import os.path
import sys
import pprint
from pathlib import Path

# -------- Config --------
cfg_vars_list = [
    'CC', 'CXX', 'OPT', 'BASECFLAGS', 'CCSHARED', 'LDSHARED', 'SO', 'BINDIR'
]
cfg_vars = {
    v: distutils.sysconfig.get_config_vars(v)
    for v in cfg_vars_list
}
cfg_vars['LIBPATH'] = ["D:/software/python364_32/libs"]  # [os.path.join(cfg_vars['BINDIR'],'libs')]
cfg_vars['SHLIBSUFFIX'] = ".pyd" if os.name == "nt" else ".so"
cfg_vars['LIBS'] = "python36.lib"
cfg_vars['CPPPATH'] = [distutils.sysconfig.get_python_inc()]
# print("->:", cfg_vars)

# -------- Environment --------
env = Environment(
    CPPPATH=[distutils.sysconfig.get_python_inc()],
    LIBPATH=cfg_vars["LIBPATH"],
    LIBS=cfg_vars["LIBS"],
    SHLIBPREFIX="",
    MSVC_VERSION='14.0',
    TARGET_ARCH='x86'
)
# env.Append(SHLINKFLAGS='/verbose:lib')
env.PrependENVPath('PATH', "D:/software/swig")
env.Tool('swig')
env['SWIGFLAGS'] = ['-python']

# -------- Build --------
# env['SHLINKCOM'] = "$SHLINK $SHLINKFLAGS $_SHLINK_TARGETS $_LIBDIRFLAGS $_LIBFLAGS $_PDB $_SHLINK_SOURCES"
env.SharedLibrary(
    'foo/_example',
    ['src/example.c', 'src/example.i'],
    SHLIBSUFFIX=cfg_vars['SHLIBSUFFIX'],
    # SHLINKFLAGS='/verbose:lib'
)

# -------- Debug --------
# print(env.Dump())
