cmake_minimum_required(VERSION 3.0)

set(CMAKE_CXX_COMPILER icc) #must come before any language definition (or project definition)

project(qr_opencl)

set(CMAKE_CXX_STANDARD 14)

set (CMAKE_SHARED_LINKER_FLAGS "-Wl,--as-needed")

add_executable(qr_opencl main.cpp opencl.cpp options.cpp)

target_include_directories(qr_opencl PUBLIC /home/carlos/libOpenCLAlteraApp/common/inc/ /home/carlos/intelFPGA/16.1/hld/host/include)

target_link_libraries(qr_opencl
        /home/carlos/intelFPGA/16.1/hld/host/linux64/lib/libalteracl.so
        /home/carlos/intelFPGA/16.1/hld/host/linux64/lib/libalterahalmmd.so
        /home/carlos/intelFPGA/16.1/hld/board/s5phq/linux64/lib/libaltera_s5phq_mmd.so
        /home/carlos/intelFPGA/16.1/hld/host/linux64/lib/libelf.so
        /home/carlos/intelFPGA/16.1/hld/host/linux64/lib/libOpenCL.so
        /home/carlos/intelFPGA/16.1/hld/host/linux64/lib/libacl_emulator_kernel_rt.so
        m)