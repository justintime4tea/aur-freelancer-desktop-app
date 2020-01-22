# Maintainer: Justin Gross <jgross.biz@gmail.com>

pkgname=freelancer-desktop-app
pkgver=1.4.0
pkgrel=3
pkgdesc="Freelancer.com desktop client"
arch=('i686' 'x86_64')
url='https://www.freelancer.com/desktop-app'
license=('custom:freelancer' 'custom:oracle')
install="$pkgname.install"
changelog=CHANGELOG.md
source_i686=("http://desktop-production.freelancer.com/latest/installers/${pkgname}_ubuntu-i386.deb")
md5sums_i686=('454084c47a4119be46c7fbbeb565d781')
source_x86_64=("http://desktop-production.freelancer.com/latest/installers/${pkgname}_ubuntu-amd64.deb")
md5sums_x86_64=('27c0223052e39385119c8b5b0a593590')
package() {
	# Extract zipped tar files from Ubuntu deb package
       tar -xpJf control.tar.xz
       tar -xpJf data.tar.xz

	# Prepare the opt directory
	install -dm755 "$pkgdir/"{opt,usr/bin}

	# Copy the directory containing the freelancer binary and application files
	cp -R "$srcdir/opt/$pkgname" "$pkgdir/opt/$pkgname"

	# Install the freelancer icon files to the appropriate locations
	install -Dm644 "$srcdir/usr/share/applications/$pkgname.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/16x16/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/16x16/apps/$pkgname.png"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/24x24/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/24x24/apps/$pkgname.png"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/32x32/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/32x32/apps/$pkgname.png"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/48x48/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/48x48/apps/$pkgname.png"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/64x64/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/64x64/apps/$pkgname.png"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/96x96/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/96x96/apps/$pkgname.png"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/128x128/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/128x128/apps/$pkgname.png"
	install -Dm644 "$srcdir/usr/share/pixmaps/hicolor/256x256/apps/$pkgname.png" "$pkgdir/usr/share/icons/hicolor/256x256/apps/$pkgname.png"

    # Create an execution script, without --skip-update Freelancer update process crashes with SHA1 sig invalid
	echo "#!/bin/bash" >> "$pkgdir/usr/bin/$pkgname"
	echo "/opt/$pkgname/bin/$pkgname --skip-update" >> "$pkgdir/usr/bin/$pkgname"

    # Make launch script executable
	chmod 755 "$pkgdir/usr/bin/$pkgname"
}
