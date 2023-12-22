FROM ubuntu:22.04

# Get all the necessary dependencies from the package manager
RUN apt update -y &&\
    apt install -y build-essential libsdl2-dev libspirv-cross-c-shared-dev git python3 libvulkan-dev pkg-config cmake wget unzip &&\
#    apt install -y build-essential libassimp-dev librenderdoc-dev libfreetype-dev libbullet-dev libsdl2-dev libspirv-cross-c-shared-dev git python3 libvulkan-dev pkg-config cmake wget unzip &&\
    mkdir -p /deps/installed

# Download, build and install the compressonator library 
RUN cd /deps &&\
    git clone --recursive --depth=1 https://github.com/GPUOpen-Tools/Compressonator.git; cd Compressonator &&\
    cd scripts/; python3 fetch_dependencies.py; cd .. &&\
    cmake -DOPTION_ENABLE_ALL_APPS=OFF -DOPTION_BUILD_CMP_SDK=ON -DOPTION_CMP_OPENGL=OFF -DOPTION_CMP_QT=OFF -DOPTION_CMP_OPENCV=OFF &&\
    make -j12; \
    mkdir -p /deps/installed/lib/Compressonator; cp lib/*.a /deps/installed/lib \
    mkdir -p /deps/installed/include; cp cmp_compressonatorlib/compressonator.h /deps/installed/include/compressonator.h

