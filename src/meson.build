src_files = [
    'main.c',
	'rc_manager.c',
    program_rc,
]

inc_dirs = include_directories('.')

pciutils_dep = dependency('pciutils', required: true)

deps = [
	pciutils_dep,
]

executable(meson.project_name(), src_files, include_directories: inc_dirs, dependencies: deps, win_subsystem:'console')
