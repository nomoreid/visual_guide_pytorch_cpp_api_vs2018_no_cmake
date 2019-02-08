# visual guide : pytorch cpp api setting on vs2018 , no CMake 
visual guide for pytorch 1.0 c++ api  on VS2018 , with no CMake (cpu only)


## step 1 : download torch api on https://pytorch.org/ 
  stable -> windows -> libtorch -> c++ -> None(cpu only) 

## step 2 : unzip to some folder (ex d:\test\libtorch )
  libtorch-win-shared-with-deps-latest.zip -> d:\test\libtorch
  ![folder preview](https://github.com/nomoreid/visual_guide_pytorch_cpp_api_vs2018_no_cmake/blob/master/screenshot/0.PNG)

## step 3 : create new c++ project on VS2017
  ![folder preview](https://github.com/nomoreid/visual_guide_pytorch_cpp_api_vs2018_no_cmake/blob/master/screenshot/1.png)

## step 4 : change project ->> win64 release <<- IMPORTANT!!!
  ![folder preview](https://github.com/nomoreid/visual_guide_pytorch_cpp_api_vs2018_no_cmake/blob/master/screenshot/_44.PNG)
  * some function (ex: torch::jit::load )  of torchlib don't work on debug mode. see ( https://github.com/pytorch/pytorch/issues/15589?fbclid=IwAR24TH_8j6ADJnsqozC-dqGVAfYbANcOw77Z8ES2TRfAhDYT-Rv8UTn-GuU ) 
  
  > For MSVC, `std::string` is not defined the same for the configurations Debug and Release. Since we built libtorch with the **Release** configuration, if you try to use the **Debug** configuration when compiling the executable, the `std::string` object could not be passed into the torch library, and hence the error.

## step 5 : change project setting
  1. add include directory : D:\test\libtorch\include   ,  D:\test\libtorch\include\torch\csrc\api\include
  2. add lib : D:\test\libtorch\lib\torch.lib , D:\test\libtorch\lib\caffe2.lib , D:\test\libtorch\lib\c10.lib
  3. on c/C++ tab ,  "SDL checks" to "No"
  4. on c/c++ -> Language tab ,  "Conformance mode" to "No"
  
  ![folder preview](https://github.com/nomoreid/visual_guide_pytorch_cpp_api_vs2018_no_cmake/blob/master/screenshot/9.png)

