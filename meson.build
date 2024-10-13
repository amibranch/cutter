project('cutter', 'cpp',
  version : run_command('git', 'describe', '--tags', '--always', check: true).stdout().split('v')[-1].split('\n')[0],
  default_options : [
    'warning_level=3',
    'cpp_std=c++17',
    'wrap_mode=forcefallback',
    'rz-ghidra:cutter-plugin=enabled',
    ])


version_arr = meson.project_version().split('-')[0].split('.')
if version_arr.length() > 1
  cutter_version_major = version_arr[0].to_int()
  cutter_version_minor = version_arr[1].to_int()
  cutter_version_patch = version_arr[2].to_int()
else
  # Usually this only happens, if no Tags have been pulled!
  cutter_version_major = 0
  cutter_version_minor = 0
  cutter_version_patch = 0
  warning('Version tag not available! Pull tags from upstream')
endif

qt6_deps = [
  dependency('Qt6Core'),
  dependency('Qt6Widgets'),
  dependency('Qt6Core5Compat'),
  dependency('Qt6Gui'),
  dependency('Qt6SvgWidgets'),
  dependency('Qt6Network'),
  dependency('Qt6OpenGL'),
  dependency('Qt6OpenGLWidgets'),
  ]

rz_deps = [
  dependency('rz_core'),
  dependency('rz_reg'),
  dependency('rz_flag'),
  dependency('rz_hash'),
  dependency('rz_bin'),
  dependency('rz_bp'),
  dependency('rz_io'),
  dependency('rz_search'),
  dependency('rz_sign'),
  dependency('rz_cons'),
  dependency('rz_lang'),
  dependency('rz_socket'),
  dependency('rz_type'),
  dependency('rz_debug'),
  dependency('rz_il'),
  dependency('rz_demangler'),
  dependency('rz_util'),
  dependency('rz_main'),
  dependency('rz_crypto'),
  dependency('rz_config'),
  dependency('rz_egg'),
  dependency('rz_syscall'),
  dependency('rz_magic'),
  ]

graphviz_deps = [
  dependency('libgvc'),
  ]

python_dep = [
  dependency('python3-embed'),
  ]

subdir('src')

