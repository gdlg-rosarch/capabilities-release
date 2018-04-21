# Script generated with Bloom
pkgdesc="ROS - Package which implements capabilities, including code to parse capability interface specs, to parse capability provider specs, and implement the capability server."
url='http://wiki.ros.org/capabilities'

pkgname='ros-lunar-capabilities'
pkgver='0.2.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('python2-coverage'
'python2-mock'
'python2-pep8'
'ros-lunar-catkin'
'ros-lunar-geometry-msgs'
'ros-lunar-message-generation'
'ros-lunar-roslaunch'
'ros-lunar-rospy'
'ros-lunar-rosservice'
'ros-lunar-rostest'
'ros-lunar-std-msgs'
'ros-lunar-std-srvs'
)

depends=('python2-yaml'
'ros-lunar-bondpy'
'ros-lunar-message-runtime'
'ros-lunar-nodelet'
'ros-lunar-roslaunch'
'ros-lunar-rospy'
'ros-lunar-std-msgs'
'ros-lunar-std-srvs'
)

conflicts=()
replaces=()

_dir=capabilities
source=()
md5sums=()

prepare() {
    cp -R $startdir/capabilities $srcdir/capabilities
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

