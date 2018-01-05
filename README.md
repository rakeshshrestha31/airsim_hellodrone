# Building and running
```
export AIRSIM_PATH=<airsim root directory>
mkdir build
cd build
cmake -DCMAKE_CXX_COMPILER=clang++-3.9 ..
make
./output/bin/HelloDrone
```