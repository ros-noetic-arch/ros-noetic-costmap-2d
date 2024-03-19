pkgdesc="ROS - This package provides an implementation of a 2D costmap."
url='https://wiki.ros.org/costmap_2d'

pkgname='ros-noetic-costmap-2d'
pkgver='1.17.3'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD')

ros_makedepends=(
  ros-noetic-catkin
  ros-noetic-cmake-modules
  ros-noetic-message-generation
  ros-noetic-tf2-geometry-msgs
  ros-noetic-tf2-sensor-msgs
)

makedepends=(
  cmake
  ros-build-tools
  ${ros_makedepends[@]}
)

ros_depends=(
  ros-noetic-dynamic-reconfigure
  ros-noetic-geometry-msgs
  ros-noetic-laser-geometry
  ros-noetic-map-msgs
  ros-noetic-message-filters
  ros-noetic-nav-msgs
  ros-noetic-pluginlib
  ros-noetic-roscpp
  ros-noetic-rostest
  ros-noetic-sensor-msgs
  ros-noetic-std-msgs
  ros-noetic-tf2
  ros-noetic-tf2-ros
  ros-noetic-visualization-msgs
  ros-noetic-voxel-grid
  ros-noetic-message-runtime
  ros-noetic-rosconsole
)

depends=(
    ${ros_depends[@]}
)

_dir="navigation-${pkgver}/costmap_2d"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-planning/navigation/archive/${pkgver}.tar.gz")
sha256sums=('6500e427f868ea63801203715f41cbec4ed1bd1f9a29ae130a74b3776a7684f6')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
