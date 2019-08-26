FROM debian:buster-slim
MAINTAINER quentin.flayac@epitech.eu

ENV CGAL_VERSION 4.13
ENV HOME /CGAL-$CGAL_VERSION
ENV DATADIR /data
RUN mkdir -p $DATADIR/in && mkdir -p $DATADIR/out

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    automake \
    cmake \
    ca-certificates \
    build-essential \
#//CGAL DEPENDANCIES ...
    #freeglut3 \
    #freeglut3-dev \
    #binutils-gold \
    #mesa-common-dev \
    #libgmp10-dev \
    #libpcre3-dev \
    libglew-dev \
    libeigen3-dev \
    qt5-default \
    qtchooser \
    qtscript5-dev \
 #//libboost-all-dev \
    libboost-dev \
    libboost-program-options-dev \
    libboost-thread-dev \
    libboost-system-dev \
    libboost-filesystem-dev \
    libboost-program-options-dev \
    libboost-regex-dev \
    libboost-iostreams-dev \
    libmpfi-dev \
    libmpfr-dev \
    libgmp-dev  \
    libtbb-dev \
    zlib1g-dev \
    libmetis-dev \
    libsuitesparse-dev \
 #//opencv (examples/Classification)
    #libopencv-dev \
    #python3-opencv \
 #//VTK (examples/Mesh_3)
    # libvtk7-dev \
 #//OpenMesh
    clang-7 \
    graphviz \
    python3-pydot \
    doxygen \
    texlive \
#//Others
    python3-pip \
    python3.7-dev \
    swig \
    wget \
    git \
 && pip3 install pydot_ng

#//LASTOOLS
WORKDIR /opt
RUN git clone https://github.com/LAStools/LAStools.git
WORKDIR /opt/LAStools
RUN git checkout master \
  && mkdir build \
  && cd build \
  && cmake .. \
  && make -j $(grep --count ^processor /proc/cpuinfo) \
  && make install
ENV PATH /opt/LAStools/bin/:$PATH
RUN chmod 777 /opt/LAStools/data

#//CLEANUP
RUN  rm /opt/LAStools/data/* \
&& rm -rf /opt/LAStools/ArcGIS_toolbox \
&& rm -rf /opt/LAStools/IMAGINE_toolbox \
&& rm -rf /opt/LAStools/QGIS_toolbox \
&& rm -rf /opt/LAStools/example_batch_scripts

#//OPENMESH
WORKDIR /opt
RUN wget -O OpenMesh-7.1.tar.gz http://www.openmesh.org/media/Releases/7.1/OpenMesh-7.1.tar.gz \
  && tar -xf OpenMesh-7.1.tar.gz
WORKDIR /opt/OpenMesh-7.1
RUN mkdir build \
  && cd build \
  && cmake -DBUILD_APPS=OFF .. \
  && make -j $(grep --count ^processor /proc/cpuinfo) \
  && make install \
  && cd /opt && rm OpenMesh-7.1.tar.gz

WORKDIR /
#//CGAL - https://github.com/CGAL/cgal/releases/download/releases%2FCGAL-4.13/CGAL-4.13.tar.xz
RUN wget -O cgal.tar.gz https://github.com/CGAL/cgal/releases/download/releases/CGAL-$CGAL_VERSION/CGAL-$CGAL_VERSION.tar.xz \
  && tar -xf cgal.tar.gz \
  && cd CGAL-$CGAL_VERSION \
  && cmake -DCGAL_DIR=/CGAL-$CGAL_VERSION -DWITH_examples:BOOL=ON -DLASLIB_LIBRARIES:PATH=/usr/local/lib/LASlib/libLASlib.a -DLASZIP_INCLUDE_DIR:PATH=/opt/LAStools/LASzip . \
  && make -j $(grep --count ^processor /proc/cpuinfo) \
#//Unusable example are Classification, Mesh_3 & Skin_surface_pdb_reader
#//example installation make -C path/to/folder
  && make -C examples/Poisson_surface_reconstruction_3 -j $(grep --count ^processor /proc/cpuinfo) \
  && make -C examples/Point_set_processing_3 -j $(grep --count ^processor /proc/cpuinfo) \
  && make -C examples/Alpha_shapes_2 -j $(grep --count ^processor /proc/cpuinfo) \
  && make -C examples/Alpha_shapes_3 -j $(grep --count ^processor /proc/cpuinfo) \
  && make -C examples/Point_set_shape_detection_3 -j $(grep --count ^processor /proc/cpuinfo) \
  && make -C examples/Advancing_front_surface_reconstruction/ -j $(grep --count ^processor /proc/cpuinfo) \
#//continue ...
  && cd / && rm cgal.tar.gz

RUN git clone https://github.com/cgal/cgal-swig-bindings.git \
  && cd /cgal-swig-bindings/ && cmake /cgal-swig-bindings/.

RUN make cgal-swig-bindings/. -j $(grep --count ^processor /proc/cpuinfo)

# https://github.com/cgal/cgal-swig-bindings/issues/34
# PYTHONPATH should point to path PYTHON_OUTDIR_PREFIX in the file CMakeCache.txt
# python3 > sys.path.append("/cgal-swig-bindings/build-python")
# cat CMakeCache.txt | grep python
ENV PYTHONPATH="/cgal-swig-bindings/build-python"

#//CLEANUP
RUN apt-get clean && apt-get purge -y \
    autoconf automake libpcre3-dev python3-pip wget git \
  && apt-get autoremove -y \
  && rm -rf /var/lib/apt/lists/*

VOLUME ["$DATADIR", "/cgal-swig-bindings/examples/python"]
