# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - This package provides a recovery behavior for the navigation stack that attempts to clear space by performing a 360 degree rotation of the robot."
url='http://wiki.ros.org/rotate_recovery'

pkgname='ros-hydro-rotate-recovery'
pkgver='1.11.11'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-base-local-planner
  ros-hydro-costmap-2d
  ros-hydro-tf
  ros-hydro-roscpp
  ros-hydro-catkin
  ros-hydro-nav-core
  ros-hydro-cmake-modules
  ros-hydro-pluginlib)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  eigen3)

ros_depends=(ros-hydro-tf
  ros-hydro-roscpp
  ros-hydro-pluginlib
  ros-hydro-nav-core
  ros-hydro-costmap-2d)
depends=(${ros_depends[@]}
  eigen3)

_tag=release/hydro/rotate_recovery/${pkgver}-${_pkgver_patch}
_dir=rotate_recovery
source=("${_dir}"::"git+https://github.com/ros-gbp/navigation-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
