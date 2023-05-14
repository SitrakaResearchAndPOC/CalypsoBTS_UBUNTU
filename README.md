# CalypsoBTS UBUNTU (20.O4)

INSTALLATION KARLI BTS : 
as same ase : 
* [shamrin](https://gist.github.com/shamrin/8b2d6c1493c70544c39e) 
* [security-bits.de](https://security-bits.de/research/cellular/lab_setup) 

apt update
mkdir src
mkdir Desktop/gsmkarly_backup

cd src
mkdir gsmkarly



(commande en une seul ligne)
sudo apt-get install libboost-all-dev libusb-1.0-0-dev doxygen python3-docutils python3-mako python3-numpy python3-requests python3-ruamel.yaml python3-setuptools cmake build-essential

apt-get remove texinfo

apt-get install alsa-base alsa-oss alsa-utils
apt-get install oss-compat
#modprobe snd-pcm-oss
modprobe snd-mixer-oss


(commande en un seul ligne)
#apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3B4FE6ACC0B21F32 40976EAF437D05B5 

 

apt-get install gcc-9 g++-9 gcc-10 g++-10 git -y

# adding this one 
# for raspberry : 
# deb http://ports.ubuntu.com/ubuntu-ports xenial main restricted universe multiverse

# "Architecture could be amd64, armel, arm64 ?" 

echo "deb [arch=amd64] http://fr.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse" >> /etc/apt/sources.list


apt update
apt-get install gcc-4.9 g++-4.9 gcc-7 g++-7 -y

sed -i '$ d' /etc/apt/sources.list
apt update

(commande en un seul ligne)
apt-get install -y build-essential libusb-1.0-0-dev libsqlite3-dev libsctp-dev libgmp-dev libx11-6 libx11-dev flex libncurses5 libdbd-sqlite3 libdbi-dev libncurses5-dev libncursesw5 libpcsclite-dev zlib1g-dev libmpc3 lemon aptitude libtinfo-dev libtool shtool autoconf git-core pkg-config make libmpfr-dev libmpc-dev libtalloc-dev libfftw3-dev libgnutls28-dev libtool-bin libxml2-dev sofia-sip-bin libsofia-sip-ua-dev sofia-sip-bin libncursesw5-dev bison libgmp3-dev alsa-oss

(commande en un seul ligne)
update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.9 49 --slave /usr/bin/g++ g++ /usr/bin/g++-4.9

(commande en un seul ligne)
update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 70 --slave /usr/bin/g++ g++ /usr/bin/g++-7

(commande en un seul ligne)
update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 90 --slave /usr/bin/g++ g++ /usr/bin/g++-9

(commande en un seul ligne)
update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 100 --slave /usr/bin/g++ g++ /usr/bin/g++-10

# mousepad /etc/apt/sources.list
# Ajouter à la fin : 
# adding this another one 
# deb http://ports.ubuntu.com/ubuntu-ports bionic main restricted universe multiverse

#mousepad /etc/apt/sources.list
#changer à la fin  en : 

# adding this another one 
# deb http://ports.ubuntu.com/ubuntu-ports bionic main restricted universe 

echo "deb [arch=amd64] http://fr.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse" >> /etc/apt/sources.list

tail -f /etc/apt/sources.list

apt update
apt-get install -y gcc-5 g++-5 libssl1.0-dev

(commande en un seul ligne)
update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 50 --slave /usr/bin/g++ g++ /usr/bin/g++-5

sed -i '$ d' /etc/apt/sources.list

tail -f /etc/apt/sources.list

apt  update
update-alternatives --set gcc /usr/bin/gcc-4.9

gcc --version


TOUS LES DEB SE TROUVENT DANS : /var/cache/apt/archives/


cd /root/Desktop/karli/
wget http://ftp.gnu.org/gnu/texinfo/texinfo-4.13.tar.gz 
tar xvf texinfo-4.13.tar.gz
 cd texinfo-4.13
  ./configure --build=aarch64-unknown-linux-gnu
  make -j$(nproc)
  make -j$(nproc) install
ldconfig

TELECHARGER GNU_ARM_FOR UBUNTU DANS: 
https://drive.google.com/file/d/1xV3RLZg3Lm4m3UPd1nDfO_xEjIH2F5lQ/view?usp=share_link

cd ..
# https://medium.com/@acpanjan/download-google-drive-files-using-wget-3c2c025a8b99


wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1xV3RLZg3Lm4m3UPd1nDfO_xEjIH2F5lQ' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1xV3RLZg3Lm4m3UPd1nDfO_xEjIH2F5lQ" -O gnuarm_for_ubuntu.zip  && rm -rf /tmp/cookies.txt

unzip gnuarm_for_ubuntu.zip
mv gnuarm_for_ubuntu.zip ../../Desktop/gsmkarly_backup/
cd gnuarm
chmod +x gnu-arm-build.2.sh
bash gnu-arm-build.2.sh
BOIRE QUELQUES BIERRES PARCE QUE CA VA PRENDRE ENVION 5H : 
 
make[1]: Leaving directory '/root/Desktop/karli/gnuarm/build/gcc-4.5.2'
Build complete! Add /root/Desktop/karli/gnuarm/install/bin to your PATH to make arm-elf-gcc and friends
accessible directly.
 --------------------------------------------------------------------
mv /var/lib/dpkg/lock-frontend /var/lib/dpkg/lock-frontend.old
apt update
--------------------------------------------------------------------------
apt-get install zip
update-alternatives --set gcc /usr/bin/gcc-9


/usr/include/newlib/sys/_stdint.h:48:20: error: conflicting types for 'uint32_t'
   48 | typedef __uint32_t uint32_t ;


(commande en un seul ligne)
export PATH=$PATH:/root/Desktop/karli/gnuarm/install/bin
#export PATH=$PATH:/home/gsmkarly/Downloads/gnuarm/install/bin/

mkdir /usr/local/karly/


cd src/gsmkarly



git clone https://github.com/osmocom/libosmocore
cd libosmocore
git checkout cf70aa0c40c574c32b832454f725cc37459c5d8d
cd ..
zip -r libosmocore_karly.zip libosmocore/
mv libosmocore_karly.zip ../../Desktop/gsmkarly_backup/
cd libosmocore && autoreconf -i 
#./configure --prefix=/usr/local/karly
./configure
make -j4 
make install 
ldconfig -i 
cd ..

apt-get install python2
sudo ln -s /usr/bin/python2 /usr/bin/python

git clone https://github.com/osmocom/osmocom-bb
cd osmocom-bb/
git checkout 4f677e6ba8434dab376495cd996d140548fa6e93

# /*
mousepad src/target/firmware/Makefile	
 *|					#uncomment CFLAGS += -DCONFIG_TX_ENABLE	|*
*|					#ctrl+o return ctrl+x	
# */

cd src
sed -i -e  's/#CFLAGS += -DCONFIG_TX_ENABLE/CFLAGS += -DCONFIG_TX_ENABLE/g' target/firmware/Makefile

tail -f target/firmware/Makefile

cd ../..
zip -r osmocom-bb_karly4f677.zip osmocom-bb/
mv osmocom-bb_karly4f677.zip ../../Desktop/gsmkarly_backup/

cd osmocom-bb/src 
make -j4 
 
 
 
 # /* Error : 
 fatal error: sys/_types.h: No such file or directory
 
 implies bad gnuarm path
 # */
 
 
 
cd ../..

git clone https://github.com/osmocom/libosmo-dsp
cd libosmo-dsp
git checkout 551b9752bcd5d3d21bb2df0736b1801bda3d0d10
cd ..
zip -r libosmo-dsp_karly.zip libosmo-dsp
mv libosmo-dsp_karly.zip ../../Desktop/gsmkarly_backup/
cd libosmo-dsp/
autoreconf -i
./configure 
make -j4 
make install 
ldconfig -i

cd ..

update-alternatives --set gcc /usr/bin/gcc-5

git clone https://github.com/osmocom/osmocom-bb trx
cd trx
git checkout jolly/testing
#git checkout 620fe497efa492feff4550e336cc3f8167715936

cd src

# wget https://github.com/bbaranoff/telco_install_sh/raw/main/trx.highram.bin

(commande en un seul ligne)

sed -i -e  's/#CFLAGS += -DCONFIG_TX_ENABLE/CFLAGS += -DCONFIG_TX_ENABLE/g' target/firmware/Makefile

tail -f target/firmware/Makefile
mv trx_for_ubuntu.zip ../../Desktop/gsmkarly_backup/
cd ../..
zip -r trx_for_ubuntu.zip trx/
cd trx/src
make  HOST_layer23_CONFARGS=--enable-transceiver 
find -name trx.highram.bin
cd ../..





 

apt-get install libortp-dev
apt-get install dahdi-source  
apt-get install libtool shtool automake dahdi-source libssl-dev sqlite3 libsqlite3-dev libsctp-dev libfftw3-dev libfftw3-3 autoconf libsctp-dev libgnutls28-dev libcurl4-gnutls-dev git-core pkg-config make doxygen libtalloc-dev libpcsclite-dev libusb-1.0-0-dev


# /* for debian
apt-get install gcc gcc-arm-none-eabi
git clone https://github.com/osmocom/osmocom-bb trx2
cd trx2
git checkout jolly/testing
#git checkout 620fe497efa492feff4550e336cc3f8167715936
cd src
wget https://github.com/bbaranoff/telco_install_sh/raw/main/trx.highram.bin

(commande en un seul ligne)
sed -i -e  's/#CFLAGS += -DCONFIG_TX_ENABLE/CFLAGS += -DCONFIG_TX_ENABLE/g' target/firmware/Makefile

tail -f target/firmware/Makefile
cd ../..
zip -r trx2_for_ubuntu.zip trx2/
cd trx2/src

(commande en une seul ligne)
make HOST_layer23_CONFARGS=--enable-transceiver -e CROSS_TOOL_PREFIX=arm-none-eabi-

find -name trx.highram.bin
cd ../..

# */ for debian

update-alternatives --set gcc /usr/bin/gcc-9

git clone https://gitea.osmocom.org/osmocom/libosmo-abis.git
cd libosmo-abis && git checkout 39dffb6c29a8d78ba8527aa4ccc13f34d1c3b319
cd .. && zip -r libosmo-abis_kaly.zip libosmo-abis/
mv libosmo-abis_kaly.zip ../Desktop/gsmkarly_backup/
cd libosmo-abis
autoreconf -i 
./configure 
make -j4 
make install && \
ldconfig && \
cd ..

git clone https://gitea.osmocom.org/osmocom/libosmo-netif.git
cd libosmo-netif/  && git checkout 09c71b04f5a8d82515d0d4d541b8368b585dbd31
autoreconf -i 
./configure 
make -j4
make install 
ldconfig
cd ..

git clone --depth 1 -b 1.0.0 https://gitea.osmocom.org/osmocom/libosmo-sccp
cd libosmo-sccp
autoreconf -fi
./configure
make -j4
make check
sudo make install
sudo ldconfig

cd ..


git clone --depth 1 -b 1.13.0 https://gitea.osmocom.org/cellular-infrastructure/libsmpp34
cd libsmpp34
autoreconf -fi
./configure
make -j4
make check
sudo make install
sudo ldconfig
cd ..

#

# 
git clone git://git.osmocom.org/openbsc.git
cd openbsc/openbsc/ && \
git checkout d2550da76f9974bb1957f74c5d3eb75fdae923d9
autoreconf -i && \
./configure  --enable-nat --enable-smpp && \
make -j4 && \
make install && \
ldconfig && \
\

cd ../..

git clone https://gitea.osmocom.org/cellular-infrastructure/osmo-bts.git
cd osmo-bts
git checkout 59e7773055335a12d749faf84d88a8ed9fa0f201 
autoreconf -i 

./configure --enable-trx 
make -j4  
make install 
ldconfig 




# https://www.youtube.com/watch?v=_nGVeG_76W8&pp=ygUQY2FseXBzb2J0cyBrYXJseQ%3D%3D

# find the phone
dmesg | grep tty

cd src/OTHER/trx/src  &&  host/osmocon/osmocon -m c123xor -p /dev/ttyUSB0  -c target/firmware/board/compal_e88/trx.highram.bin


cd src/OTHER/trx/src  &&  host/osmocon/osmocon -m c123xor -p /dev/ttyUSB0 -s /tmp/osmocom_l2 -c target/firmware/board/compal_e88/trx.highram.bin -r 99


cd src/OTHER/trx/src  && host/osmocon/osmocon -m c123xor -p /dev/ttyUSB1 -s /tmp/osmocom_l2.2 -c target/firmware/board/compal_e88/trx.highram.bin -r 99


cd src/OTHER/trx/src/host/layer23/src/transceiver/ && ./transceiver -a 975 -2 -r 99

config open-bsc.cfg
# https://pastebin.com/Euj2QQ66


osmo-nitb -c open-bsc.cfg -l hlr.sqlite3 -P -C --debug=DRLL:DCC:DMM:DRR:DRSL:DNM


config osmo-bts.cfg
# https://pastebin.com/YM3mS2bY


apt-get install stress

osmo-bts-trx -c osmo-bts.cfg --debug DRSL:DOML:DLAPDM 

