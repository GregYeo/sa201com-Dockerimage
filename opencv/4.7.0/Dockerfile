ARG BASE_IMAGE

FROM ${BASE_IMAGE}

RUN apt-get update && \
    apt-get install -y cmake gcc g++ unzip

RUN apt-get update && \
    apt-get install -y \
        libpng-dev \
        libjpeg-dev \
        libopenexr-dev \
        libtiff-dev \
        libwebp-dev

RUN apt-get update && \
    apt-get install -y \
        ant && \
    ant -version

ENV OPENCV_SOURCE_DIR="/tmp/opencv"
ENV OPEN_CV_VERSION="4.7.0"

RUN mkdir -p ${OPENCV_SOURCE_DIR} && \
    cd ${OPENCV_SOURCE_DIR} && \
    curl -o opencv.zip -L https://github.com/opencv/opencv/archive/refs/tags/${OPEN_CV_VERSION}.zip && \
    unzip opencv.zip && \
	cd ${OPENCV_SOURCE_DIR}/opencv-${OPEN_CV_VERSION} && \
	mkdir -p build && cd build && \
	cmake \
        -D BUILD_DOCS=OFF \
        -D BUILD_TESTS=OFF \
        -D BUILD_PERF_TESTS=OFF \
        -D BUILD_EXAMPLES=OFF \
        -D BUILD_opencv_apps=OFF \
		-D BUILD_OPENJPEG=ON \
		-D BUILD_JPEG=OpenBLAS_HOME \
		-D BUILD_TIFF=ON \
		-D BUILD_PNG=ON \
		-D BUILD_TIFF=ON \
		-D BUILD_WEBP=ON \
	    -D BUILD_ZLIB=OFF \
	    -D WITH_OPENEXR=OFF \
		-D BUILD_opencv_java=ON \
		.. && \
    make -j7 install && \
    rm -rf ${OPENCV_SOURCE_DIR}

