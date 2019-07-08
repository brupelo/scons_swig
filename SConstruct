#!python
import distutils.sysconfig
env = Environment(SWIGFLAGS=['-python'],
                  CPPPATH=[distutils.sysconfig.get_python_inc()],
                  SHLIBPREFIX="")
env.SharedLibrary('_example.dll', ['example.c', 'example.i'])
