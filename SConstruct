import os

env = Environment(ENV = os.environ)
env.Append(CPPPATH = ['include'])
env.Append(CCFLAGS = '-g -Wall -O0'.split())
env.Append(LIBS    = ['m'])
env.Append(RPATH   = '.')
#print env.Dump()
env['SHLIBSUFFIX'] = '.so'
env['SHLINKFLAGS'] = ['$LINKFLAGS', '-shared']
env.StaticLibrary('dubinscurves', ['src/DubinsCurves.cpp'])

appenv = env.Clone()
appenv.Append(LIBS    = ['dubinscurves'])
appenv.Append(LIBPATH = ['.'])
demo = appenv.Program('demo_app', ['demos/demo.cpp'])
test = appenv.Program('test_app', ['tests/test.cpp'])
testcli = appenv.Program('test_cli', ['tests/test-cli.cpp'])

Depends(demo, 'libdubinscurves.a')
Depends(test, 'libdubinscurves.a')
Depends(testcli, 'libdubinscurves.a')
