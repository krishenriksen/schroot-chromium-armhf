# schroot-chromium-armhf
Chromium with widewine for aarch64 (64 bit)

## Building, Testing, and Installation

Run the following in a terminal to configure the environment:

	sudo apt install -y debootstrap schroot
	cat << EOF | sudo tee /etc/schroot/chroot.d/armhf
	[armhf]
	description=chromium widewine
	type=directory
	directory=/srv/armhf
	users=pi
	root-groups=root
	EOF
	sudo debootstrap --arch=armhf buster /srv/armhf
	git clone https://github.com/krishenriksen/schroot-chromium-armhf
	cd schroot-chromium-armhf
	sudo cp dependencies/chromium-* /srv/armhf/root/
    sudo schroot -c armhf -- dpkg -i /root/chromium-*
    sudo cp widevine/libwidevinecdm.so /srv/armhf/usr/lib/chromium-browser/
    sudo cp chromium.desktop $HOME/Desktop/
    sudo cp chromium.desktop /usr/share/applications/
    schroot -c armhf -- sh -c 'DISPLAY=:0 chromium-browser %U --user-agent="Mozilla/5.0 (X11; CrOS armv7l 11895.95.0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.125 Safari/537.36"'

## Support the project

<a href="https://www.paypal.me/krishenriksendk" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>
