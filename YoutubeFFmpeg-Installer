sudo apt-get remove --purge libmp3lame-dev libtool libssl-dev libaacplus-* libx264 libvpx librtmp ffmpeg &&
sudo apt-get install libmp3lame-dev; sudo apt-get install autoconf; sudo apt-get install libtool; sudo apt-get install checkinstall; sudo apt-get install libssl-dev &&
cd /home/pi/ 
mkdir src 
cd src &&
sudo apt-get install libtool-bin &&
wget http://tipok.org.ua/downloads/media/aacplus/libaacplus/libaacplus-2.0.2.tar.gz &&
tar -xzf libaacplus-2.0.2.tar.gz &&
cd libaacplus-2.0.2 &&
./autogen.sh --with-parameter-expansion-string-replace-capable-shell=/bin/bash --host=arm-unknown-linux-gnueabi --enable-static &&
make &&
sudo make install &&

cd /home/pi/src && 
git clone git://git.videolan.org/x264 &&
cd x264 &&
./configure --host=arm-unknown-linux-gnueabi --enable-static --disable-opencl &&
make &&
sudo make install &&

cd /home/pi/src
git clone https://chromium.googlesource.com/webm/libvpx
cd libvpx
./configure
make
sudo checkinstall --pkgname=libvpx --pkgversion="1:$(date +%Y%m%d%H%M)-git" --backup=no     --deldoc=yes --fstrans=no --default &&

cd /home/pi/src
git clone git://git.ffmpeg.org/rtmpdump
cd rtmpdump
make SYS=posix
sudo checkinstall --pkgname=rtmpdump --pkgversion="2:$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default &&

sudo ldconfig &&

cd /home/pi/src 
git clone --depth 1 git://git.videolan.org/ffmpeg
cd ffmpeg
./configure --arch=armel --target-os=linux --enable-gpl --enable-libx264 --enable-nonfree --enable-libaacplus --enable-librtmp --enable-libmp3lame
make
sudo make install &&

sudo reboot
