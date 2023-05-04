src_files = [
    'example.c',
    program_icon,
]

inc_dirs = include_directories('.')

pciutils_dep = dependency('pciutils', fallback : ['pciutils', 'pciutils_dep'])

deps = [
	pciutils_dep,
]

executable(meson.project_name(), src_files, include_directories: inc_dirs, dependencies: deps, win_subsystem:'console')
