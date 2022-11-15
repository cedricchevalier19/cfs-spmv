project('cfs-spmv', 'cpp',
  version : '0.1',
  default_options : ['warning_level=3', 'cpp_std=c++17'])

conf_data = configuration_data()
conf_data.set('version', '1.2.3')
conf_data.set('_USE_DOUBLE', true)
conf_data.set('_USE_MKL', false)

configure_file(input : 'config.h.in',
               output : 'config.h',
               configuration : conf_data)

incdirs = include_directories('include', '.')

openmp = dependency('OpenMP', language: 'cpp')
tbb = dependency('TBB', method: 'cmake', modules: ['TBB::tbb'])

executable('cfs-spmv',
           'bench/bench_spmv_mmf.cpp',
           'src/allocator.cpp',
           'src/cfs.cpp',
           'src/csr.cpp',
           'src/mmf.cpp',
           'src/runtime.cpp',
           include_directories: incdirs,
           dependencies: [openmp, tbb],
           install : true)
