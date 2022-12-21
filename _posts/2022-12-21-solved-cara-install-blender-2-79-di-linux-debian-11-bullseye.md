---
title: "Solved: Cara Install Blender 2.79b di Linux Debian 11 Bullseye"
date: 2022-12-21
category: [ Software ]
tags: [ system ]
image: /assets/images/solved-cara-install-blender-2-79-di-linux-debian-11-bullseye.jpg
---
Pada awal release Debian 11 Bullseye, saya masih bisa menginstall Blender 2.79b dari Software atau dari Terminal. Untuk menghidari Blender 2.79b ikut terupdate otomatis ke versi selanjutnya ketika menggunakan <i>apt update</i> dan <i>apt upgrade</i>, saya menggunakan <i>apt-mark hold blender</i> di terminal. Setelah beberapa bulan terdapat update pada Debian 11 yang membuat tidak bisa lagi install Blender 2.79b, akan tetapi sudah menjadi Blender 2.83 secara otomatis, baik itu dari Software atau dari Terminal. Hal ini saya ketahui karena setelah beberapa bulan tersebut saya coba-coba "Debian Sid" (Debian Unstable version) dan mengalami kesulitan untuk kembali ke "Debian Stable", jadi saya install ulang.<br/>
<br/>
Alasan menggunakan Blender 2.79b adalah perangkat yang saya gunakan masih OpenGL 2.1 (versi lama), sedangkan untuk menjalankan Blender 2.8x harus sudah mendukung OpenGL 3.3 ke atas (versi baru). Untuk perangkat dengan OpenGL 2.1 bisa mengikuti langkah yang sudah saya lakukan berikut ini:<br/>
<br/>
<h3>Install Snap</h3>
<br/>
Buka Terminal dan masuk mode super user/mode root dengan ketik:<br/>
<br/>
<i>su</i><br/>
<i>apt update</i><br/>
<i>apt install snapd</i><br/>
<br/>
Restart komputer dan buka Terminal kemudian ketik:<br/>
<br/>
<i>su</i><br/>
<i>snap install core</i><br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/install-snap-core.jpg"><br/>
<br/>
<br/>
Restart komputer, atau bisa ikuti petunjuk dari web resminya <a href="https://snapcraft.io/docs/installing-snap-on-debian" style="color:#007bff;">disini</a>.
<br/>
<h3>Install Blender 2.79b</h3>
<br/>
Buka Terminal dan masuk mode super user/mode root dengan ketik:<br/>
<br/>
<i>su</i><br/>
<i>snap install blender --channel=2.79/stable --classic</i><br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/snap-install-blender-2-79.jpg"><br/>
<br/>
<br/>
Sampai disini, Blender 2.79b sudah bisa dijalankan pada Debian 11 Bullseye. Tetapi icon launcher tidak muncul, sehingga terlihat tidak menarik.<br/>
<br/>
<h3>Fix icon launcher tidak muncul</h3>
<br/>
<i style="color:#999;">Catatan: Pada bagian ini saya lanjutkan di hari kedua, bisa dilihat dari screenshot tanggalnya.</i><br/>
<br/>
Buka GNOME Software dan install Blender, untuk saat ini yang tampil di perangkat saya adalah versi Blender 2.83.5 atau bisa juga install dari Terminal dengan ketik <i>apt install blender</i> pada super user/mode root. Alasan saya install ini untuk menggunakan icon launchernya saja, karena Blender 2.83.5 tidak bisa dibuka dari perangkat dengan OpenGL 2.1 (versi lama).
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/install-blender-gnome-software.jpg"><br/>
<br/>
Selanjutnya buka Terminal sebagai super user/mode root, kemudian ketik:<br/>
<br/>
<i>nautilus</i><br/>
<br/>
Jika belum ada, bisa install dulu dengan ketik <i>apt install nautilus</i>. Setelah terbuka, klik kanan pada file "blender_blender.desktop" yang berada di folder: <i>Filesystem root/var/lib/snapd/dekstop/applications/blender_blender.desktop</i> pilih "Open With TextEditor".<br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/nautilus-root-folder.jpg"><br/>
<br/>
Setelah TextEditor/gedit terbuka, scroll ke bawah sampai ketemu kode <i style="color:#999;">Exec=env</i> kemudian bawah tambahkan kode <i style="color:#999;">Icon=blender</i> dan klik "Save".
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/gedit-add-icon-blender.jpg"><br/>
<br/>
Hasilnya bisa dilihat pada menu aplikasi, bisa juga klik kanan icon dan pilih "Add to Favorites". Sebelum itu buka aplikasi dengan klik icon Blender untuk memastikan dulu mana yang versi 2.79 dan mana yang versi 2.83 (versi tidak bisa dibuka).
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/icon-launcher-add-to-favorites.jpg"><br/>
<br/>
