---
title: "Solved: Cara Install Blender 2.79b di Linux Debian 11 Bullseye"
date: 2022-12-21
category: [ Software ]
tags: [ system ]
image: /assets/images/solved-cara-install-blender-2-79-di-linux-debian-11-bullseye.jpg
---
Pada awal release Debian 11 Bullseye, saya masih bisa menginstall Blender 2.79b dari Software atau dari Terminal. Untuk menghidari Blender 2.79b ikut terupdate otomatis ke versi selanjutnya ketika menggunakan <i style="color:#999;">apt update</i> dan <i style="color:#999;">apt upgrade</i>, saya menggunakan <i>apt-mark hold blender</i> di terminal. Setelah beberapa bulan terdapat update pada Debian 11 yang membuat tidak bisa lagi install Blender 2.79b, akan tetapi sudah menjadi Blender 2.83 secara otomatis, baik itu dari Software atau dari Terminal. Hal ini saya ketahui karena setelah beberapa bulan tersebut saya coba-coba "Debian Sid" (Debian Unstable version) dan mengalami kesulitan untuk kembali ke "Debian Stable", jadi saya install ulang.<br/>
<br/>
Alasan menggunakan Blender 2.79b adalah perangkat yang saya gunakan masih OpenGL 2.1 (versi lama), sedangkan untuk menjalankan Blender 2.8x harus sudah mendukung OpenGL 3.3 ke atas (versi baru). Untuk perangkat dengan OpenGL 2.1 bisa mengikuti langkah yang sudah saya lakukan berikut ini:<br/>
<br/>
<h3>Install Snap</h3>
<br/>
Buka Terminal dan masuk mode super user/mode root dengan ketik:<br/>
<br/>
<i style="color:#999;">su</i><br/>
<i style="color:#999;">apt update</i><br/>
<i style="color:#999;">apt install snapd</i><br/>
<br/>
Restart komputer dan buka Terminal kemudian ketik:<br/>
<br/>
<i style="color:#999;">su</i><br/>
<i style="color:#999;">snap install core</i><br/>
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
<i style="color:#999;">su</i><br/>
<i style="color:#999;">snap install blender --channel=2.79/stable --classic</i><br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/snap-install-blender-2-79.jpg"><br/>
<br/>
<br/>
Sampai disini, Blender 2.79b sudah bisa dijalankan pada Debian 11 Bullseye. Tetapi icon launcher tidak muncul, sehingga terlihat tidak menarik.<br/>
<br/>
<h3>Fix icon launcher tidak muncul</h3>
<br/>
<i style="color:#999;">Catatan: Pada bagian ini saya lanjutkan di hari kedua, bisa dilihat dari screenshot tanggalnya. Dan screenshot dengan tanggal terbaru itu adalah langkah yang sudah saya perbaiki.</i><br/>
<br/>
Buka Terminal sebagai super user/mode root, kemudian ketik:<br/>
<br/>
<i style="color:#999;">nautilus</i><br/>
<br/>
Jika belum ada, bisa install dulu dengan ketik <i style="color:#999;">apt install nautilus</i>. Setelah terbuka, klik kanan pada file "blender_blender.desktop" yang berada di folder: <i style="color:#999;">Filesystem root/var/lib/snapd/dekstop/applications/blender_blender.desktop</i> pilih "Open With TextEditor".<br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/nautilus-root-folder.jpg"><br/>
<br/>
Setelah TextEditor/gedit terbuka, scroll ke bawah sampai ketemu kode:<br/>
<br/>
<i style="color:#999;">Exec=env</i><br/>
<br/>
kemudian bawah tambahkan kode:<br/>
<br/>
<i style="color:#999;">Icon=/snap/blender/20/icons/256x256/apps/blender.png</i><br/>
<br/>
dan klik "Save".<br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/gedit-add-icon-blender.jpg"><br/>
<br/>
Sekarang klik <i style="color:#999;">Activities > Show Applications > Blender</i> (scroll ke bawah untuk lihat install terbaru), kemudian klik kanan icon dan pilih "Add to Favorites". Icon tersebut juga muncul pada pop-up ketika klik kanan file dengan ekstensi <i style="color:#999;">.blend</i>, untuk saat ini hanya icon di <i style="color:#999;">Activities > Show Applications > Blender</i> saja yang belum bisa saya tampilkan.<br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/add-blender-icon-to-favorites.jpg"><br/>
<br/>
<h3>Update 25 Des 2022</h3>
<br/>
Icon di <i style="color:#999;">Activities > Show Applications > Blender</i> bisa saya munculkan secara tidak sengaja, dengan cara ubah <i style="color:#999;">/blender_blender.dekstop</i> sehingga menjadi <i style="color:#999;">/blender.dekstop</i>, klik "Save" dan keluar.<br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/remove-blender-underscore.jpg"><br/>
<br/>
Kemudian rename file <i style="color:#999;">blender_blender.dekstop</i> sehingga menjadi <i style="color:#999;">blender.dekstop</i><br/>
<br/>
<img class="img-post" src="{{site.baseurl}}/assets/images/rename-blender-desktop.jpg"><br/>
<br/>
Buka <i style="color:#999;">Activities > Show Applications > Blender</i> untuk cek icon yang sudah berubah. Selanjutnya rename kembali file <i style="color:#999;">blender.dekstop</i> tadi ke awal lagi, sehingga menjadi <i style="color:#999;">blender_blender.dekstop</i> dan buka filenya. Ubah kembali <i style="color:#999;">/blender.dekstop</i> tadi ke awal lagi, sehingga menjadi <i style="color:#999;">/blender_blender.dekstop</i> klik "Save".<br/>
