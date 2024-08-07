project('gainput', 'cpp', version : '0.1')

deps = []

if host_machine.system() == 'linux'
    deps += dependency('x11')
endif

gainput_incdir = include_directories('./lib/include', is_system : true)
gainput_libsources = files(
    'lib/source/gainput/GainputInputManager.cpp',
    'lib/source/gainput/GainputInputState.cpp',
    'lib/source/gainput/GainputInputMap.cpp',
    'lib/source/gainput/recorder/GainputInputRecorder.cpp',
    'lib/source/gainput/recorder/GainputInputPlayer.cpp',
    'lib/source/gainput/recorder/GainputInputRecording.cpp',
    'lib/source/gainput/GainputMapFilters.cpp',
    'lib/source/gainput/GainputInputDevice.cpp',
    'lib/source/gainput/builtin/GainputInputDeviceBuiltIn.cpp',
    'lib/source/gainput/GainputAllocator.cpp',
    'lib/source/gainput/GainputInputDeltaState.cpp',
    'lib/source/gainput/gainput.cpp',
    'lib/source/gainput/pad/GainputInputDevicePad.cpp',
    'lib/source/gainput/pad/GainputInputDevicePadMac.cpp',
    'lib/source/gainput/mouse/GainputInputDeviceMouse.cpp',
    'lib/source/gainput/gestures/GainputButtonStickGesture.cpp',
    'lib/source/gainput/gestures/GainputSimultaneouslyDownGesture.cpp',
    'lib/source/gainput/gestures/GainputRotateGesture.cpp',
    'lib/source/gainput/gestures/GainputDoubleClickGesture.cpp',
    'lib/source/gainput/gestures/GainputHoldGesture.cpp',
    'lib/source/gainput/gestures/GainputPinchGesture.cpp',
    'lib/source/gainput/gestures/GainputTapGesture.cpp',
    'lib/source/gainput/dev/GainputMemoryStream.cpp',
    'lib/source/gainput/dev/GainputDev.cpp',
    'lib/source/gainput/dev/GainputNetAddress.cpp',
    'lib/source/gainput/dev/GainputNetConnection.cpp',
    'lib/source/gainput/dev/GainputNetListener.cpp',
    'lib/source/gainput/touch/GainputInputDeviceTouch.cpp',
    'lib/source/gainput/keyboard/GainputInputDeviceKeyboardMac.cpp',
    'lib/source/gainput/keyboard/GainputInputDeviceKeyboard.cpp',
)

link_args = []

if host_machine.system() == 'windows'
    link_args += ['-lXinput9_1_0', '-lwsock32']
endif

libtype = get_option('default_library')

cpp_args = []
if libtype != 'static'
    cpp_args += '-DGAINPUT_LIB_DYNAMIC'
endif

gainput_library = library(
  'gainput',
  gainput_libsources,
  dependencies: deps,
  include_directories: gainput_incdir,
  link_args: link_args,
  cpp_args: cpp_args
)

gainput_dep = declare_dependency(
    link_with: gainput_library,
    include_directories: gainput_incdir,
)
