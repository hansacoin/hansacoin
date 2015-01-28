Website: http://hansacoin.com<br>
<br>
Hansa is a PoW+PoS based cryptocurrency.<br>
<br>
HANSA wallets can download from http://hansacoin.com<br>
<br>
Building HANSA from sourcecode.<br>
Debian HANSA-QT<br>
<br>
Make sure that the required packages for Qt5 development of your distribution are installed, for Debian and Ubuntu these are:
apt-get install qt5-default qt5-qmake qtbase5-dev-tools qttools5-dev-tools \
    build-essential libboost-dev libboost-system-dev \
    libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev \
    libssl-dev libdb++-dev libminiupnpc-dev git
	<br><br>
Download latest HANSA git source: GIT CLONE https://github.com/hansacoin/hansacoin.git<br>
<br>
then execute the following:<br>
qmake<br>
make<br>
<br>
Alternatively, install Qt Creator and open the hansa-qt.pro file.<br>
An executable named hansa-qt will be built.<br>
<br>
HANSA serverside daemon (hansad)<br>
<br>
Download latest HANSA git source: GIT CLONE https://github.com/hansacoin/hansacoin.git<br>
<br>
Compile daemon:<br>
cd hansa-master/src/<br>
chmod 777 leveldb/build_detect_platform<br>
make -f makefile.unix USE_UPNP=-<br>
cp hansad /usr/bin/hansad<br>
<br>
Start daemon once: <br>
hansad<br>
<br>
Make config file hansa.conf:<br>
nano /root/.hansa/hansa.conf<br>
<br>
Example conf file:<br>
server=1<br>
daemon=1<br>
rpcuser=user <br>
rpcpassword=password<br>
rpcport=12111<br>
rpcallowip=127.0.0.1<br>
txindex=1<br>
<br>
Start daemon with new config file:<br>
hansad<br>
More info's about daemon, type:<br>
hansad help<br>
<br>
Windows build instructions:<br>
Download the QT Windows SDK and install it. You don't need the Symbian stuff, just the desktop Qt.<br>
Compile openssl, boost and dbcxx.<br>
Open the .pro file in QT creator and build as normal (ctrl-B)<br>
<br>
Mac OS X<br>
Download and install the Qt Mac OS X SDK. It is recommended to also install Apple's Xcode with UNIX tools.<br>
Download and install MacPorts.<br>
Execute the following commands in a terminal to get the dependencies:<br>
sudo port selfupdate<br>
sudo port install boost db48 miniupnpc<br>
Open the .pro file in Qt Creator and build as normal (cmd-B)<br>
Build configuration options<br>
<br>
UPNnP port forwarding<br>
To use UPnP for port forwarding behind a NAT router (recommended, as more connections overall allow for a faster and more stable hansa experience), pass the following argument to qmake:<br>
qmake "USE_UPNP=1"<br>
(in Qt Creator, you can find the setting for additional qmake arguments under "Projects" -> "Build Settings" -> "Build Steps", then click "Details" next to qmake)<br>
This requires miniupnpc for UPnP port mapping. It can be downloaded from http://miniupnp.tuxfamily.org/files/. UPnP support is not compiled in by default.<br>
Set USE_UPNP to a different value to control this:<br>
USE_UPNP=-	no UPnP support, miniupnpc not required;<br>
USE_UPNP=0	(the default) built with UPnP, support turned off by default at runtime;<br>
USE_UPNP=1	build with UPnP support turned on by default at runtime.<br>
Notification support for recent (k)ubuntu versions<br>
<br>
QR codes<br>
To see desktop notifications on (k)ubuntu versions starting from 10.04, enable usage of the FreeDesktop notification interface through DBUS using the following qmake option:<br>
qmake "USE_DBUS=1"<br>
Generation of QR codes<br>
libqrencode may be used to generate QRCode images for payment requests. It can be downloaded from http://fukuchi.org/works/qrencode/index.html.en, or installed via your package manager. Pass the USE_QRCODE flag to qmake to control this:<br>
USE_QRCODE=0	(the default) No QRCode support - libarcode not required<br>
USE_QRCODE=1	QRCode support enabled<br>
<br>
Other HANSA project files<br>
- HANSA paperwallet generator<br>
- HANSA Block explorer (No database needed)<br>
- HANSA Payment acceptor (Validate payment transactions)<br>
- HANSA Shopping cart plugins<br>
<br>
HANSA aka HansaCoin developers: 1-2015<br>
Homepage: hansacoin.com<br>
Contact email: hansacoin@gmx.com<br>
