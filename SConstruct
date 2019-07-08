import distutils.sysconfig
import os
import sys
import pprint

cfg_vars = ['CC', 'CXX', 'OPT', 'BASECFLAGS', 'CCSHARED', 'LDSHARED', 'SO']
cfg_vars = {v: distutils.sysconfig.get_config_vars(v) for v in cfg_vars}
cfg_vars['LIBPATH'] = "D:/software/python2714_32/libs"
cfg_vars['LIBS'] = "python27.lib"
cfg_vars['CPPPATH'] = [distutils.sysconfig.get_python_inc()]

env = Environment(
    SWIGFLAGS=['-python'],
    CPPPATH=[distutils.sysconfig.get_python_inc()],
    LIBPATH=cfg_vars["LIBPATH"],
    LIBS=cfg_vars["LIBS"],
    SHLIBPREFIX="",
    MSVC_VERSION='14.0',
    TARGET_ARCH='x86',
    ENV={
        'PATH': "D:/software/swig"
    }
)
env.SharedLibrary('_example', ['example.c', 'example.i'])
