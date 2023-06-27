<h3>A. manual Mounting-Hardisk di Linux - STB B860H</h3>
<h4>1. Instalasi Format File Sistem NTFS ke Linux  </h4>
&nbsp;&nbsp;&nbsp;&nbsp; apt install ntfs-3g fuse
<h4>2. Buat direktori di linux </h4>
&nbsp;&nbsp;&nbsp;&nbsp; mkdir -p usb/data
<h4>3. Cek Perankgat di linux </h4>
&nbsp;&nbsp;&nbsp;&nbsp; blkid    ### (/dev/sda2)
<h4>4. Proses Mounting USB-Hardisk di linux </h4>
&nbsp;&nbsp;&nbsp;&nbsp; mount /dev/sda2 /usb/data   <i>## seusiakan dengan yang terlihat dilangkah sebelumnya</i>
<h4>5. Pembacaan direktori</h4>
&nbsp;&nbsp;&nbsp;&nbsp; cd /usb/data<br/> 
&nbsp;&nbsp;&nbsp;&nbsp; ls

<h2>B. Auto Mounting-Hardisk di Linux - STB B860H</h2>
<h4>1. Buat Auto start  </h4>
&nbsp;&nbsp;&nbsp;&nbsp; nano /etc/fstab <br/>
&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;  UUID="lihat_sesuai_ID_nya_yg_terlihat"  /usb/data   ntfs-3g  defaults,nofail  0 0  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <i>### Tambahkan di akhir baris + simpan file</i> [ Ctrl+X | Y ]  <br/>
<h4>2. Cek direktori  </h4>
&nbsp;&nbsp;&nbsp;&nbsp; ls

<h2>C. Deteksi Otomatis Mounting-Hardisk di Linux - STB B860H dengan Skrip</h2>
Gunakan opsi ketiga ini agar konfigurasi di atas dapat mengotomatisasi dengan cepat perangkat langsung dapat terbaca/terhubung sesekali dilepas perangkatnya dari Linux,cukup mempermudah user tanpa harus melakukan mounting command ketika terlepas / terpasang
s dilengkapi dengan skrip ya
<h4>1. Duplikasi Direktori dari Github ke Host  </h4>
&nbsp;&nbsp;&nbsp;&nbsp; git clone https://github.com/masihgurutkj/Mounting-Hardisk.git && cd Mounting-Hardisk
<h4>2. Duplikasi file ke direktori <u>/root</u> </h4>
&nbsp;&nbsp;&nbsp;&nbsp; cp usb-mount.sh /root
<h4>3. Duplikasi file ke direktori <u>/etc/systemd/system/</u></h4>
&nbsp;&nbsp;&nbsp;&nbsp; cp usb-mount@.service /etc/systemd/system/
<h4>4. Duplikasi file ke direktori <u>/etc/udev/rules.d/</u></h4>
&nbsp;&nbsp;&nbsp;&nbsp; cp 99-local.rules /etc/udev/rules.d/
<h4>5. Restart Service tersebut</h4>
&nbsp;&nbsp;&nbsp;&nbsp; udevadm control --reload-rules<br/>
&nbsp;&nbsp;&nbsp;&nbsp; systemctl daemon-reload
<h4>6. Coba mount ke Direktori /media</h4>
&nbsp;&nbsp;&nbsp;&nbsp; cd /media<br/><br/>

<h6>Sumber: <br/>
https://unix.stackexchange.com/questions/681379/usb-flash-drives-automatically-mounted-headless-computer<br/>
https://www.youtube.com/watch?v=AGlzCyARGcQ</h6>
