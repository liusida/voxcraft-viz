# Install voxcraft-viz On Mac

```bash
brew install cmake
brew install boost
brew install qt5
brew install glfw3
brew cask install xquartz
brew install freeglut
brew install glm
brew install mesa
```

this will take a while...

```bash
git clone https://github.com/liusida/voxcraft-viz.git
cd voxcraft-viz/
mkdir build
cd build/
cmake -DCMAKE_BUILD_TYPE=Release ..
```
Wait a minute, you need to make a little bit of hacking in the source files:

The first one is `src/QTUtils/QOpenGL.cpp`

```bash
Change line 11 from
    #include "GL/glu.h"
To
    #include "OpenGL/glu.h"
```

The second one is `CMakeFiles.txt`

```bash
Change line 70 from
    find_package(glm CONFIG REQUIRED) # glm
to
    # find_package(glm CONFIG REQUIRED) # glm

Change line 44 from
    target_link_libraries(VoxCAD PRIVATE ${OpenGL_LIBRARIES} GL)
to
    target_link_libraries(VoxCAD PRIVATE ${OpenGL_LIBRARIES})
```

OK, let’s continue.

```
make -j 10
```

Done!

Thank Arlo Cohen at University of Vermont for providing the instruction on Mac.


