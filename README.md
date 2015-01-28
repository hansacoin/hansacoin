Website: http://hansacoin.com

Hansa is a PoW+PoS based cryptocurrency.

HANSA wallets can download from http://hansacoin.com

Building HANSA from sourcecode.
Debian HANSA-QT
================================================================
Make sure that the required packages for Qt5 development of your distribution are installed, for Debian and Ubuntu these are:
apt-get install qt5-default qt5-qmake qtbase5-dev-tools qttools5-dev-tools \
    build-essential libboost-dev libboost-system-dev \
    libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev \
    libssl-dev libdb++-dev libminiupnpc-dev git
	
Download latest HANSA git source: GIT CLONE https://github.com/hansacoin/hansacoin.git

then execute the following:
qmake
make

Alternatively, install Qt Creator and open the hansa-qt.pro file.
An executable named hansa-qt will be built.
================================================================
HANSA serverside daemon (hansad)

Download latest HANSA git source: GIT CLONE https://github.com/hansacoin/hansacoin.git

Compile daemon:
cd hansa-master/src/
chmod 777 leveldb/build_detect_platform
make -f makefile.unix USE_UPNP=-
cp hansad /usr/bin/hansad

Start daemon once: 
hansad

Make config file hansa.conf:
nano /root/.hansa/hansa.conf

Example conf file:
server=1
daemon=1
rpcuser=user 
rpcpassword=password
rpcport=121111
rpcallowip=127.0.0.1
txindex=1

Start daemon with new config file:
hansad
More info's about daemon, type:
hansad help
================================================================
Windows build instructions:
Download the QT Windows SDK and install it. You don't need the Symbian stuff, just the desktop Qt.
Compile openssl, boost and dbcxx.
Open the .pro file in QT creator and build as normal (ctrl-B)
================================================================
Mac OS X
Download and install the Qt Mac OS X SDK. It is recommended to also install Apple's Xcode with UNIX tools.
Download and install MacPorts.
Execute the following commands in a terminal to get the dependencies:
sudo port selfupdate
sudo port install boost db48 miniupnpc
Open the .pro file in Qt Creator and build as normal (cmd-B)
Build configuration options
================================================================
UPNnP port forwarding
To use UPnP for port forwarding behind a NAT router (recommended, as more connections overall allow for a faster and more stable hansa experience), pass the following argument to qmake:
qmake "USE_UPNP=1"
(in Qt Creator, you can find the setting for additional qmake arguments under "Projects" -> "Build Settings" -> "Build Steps", then click "Details" next to qmake)
This requires miniupnpc for UPnP port mapping. It can be downloaded from http://miniupnp.tuxfamily.org/files/. UPnP support is not compiled in by default.
Set USE_UPNP to a different value to control this:
USE_UPNP=-	no UPnP support, miniupnpc not required;
USE_UPNP=0	(the default) built with UPnP, support turned off by default at runtime;
USE_UPNP=1	build with UPnP support turned on by default at runtime.
Notification support for recent (k)ubuntu versions
================================================================
QR codes
To see desktop notifications on (k)ubuntu versions starting from 10.04, enable usage of the FreeDesktop notification interface through DBUS using the following qmake option:
qmake "USE_DBUS=1"
Generation of QR codes
libqrencode may be used to generate QRCode images for payment requests. It can be downloaded from http://fukuchi.org/works/qrencode/index.html.en, or installed via your package manager. Pass the USE_QRCODE flag to qmake to control this:
USE_QRCODE=0	(the default) No QRCode support - libarcode not required
USE_QRCODE=1	QRCode support enabled
================================================================
Other HANSA project files
- HANSA paperwallet generator
- HANSA Block explorer (No database needed)
- HANSA Payment acceptor (Validate payment transactions)
- HANSA Shopping cart plugins
================================================================
HANSA aka HansaCoin developers: 1-2015
Homepage: hansacoin.com
Contact email: hansacoin@gmx.com
================================================================