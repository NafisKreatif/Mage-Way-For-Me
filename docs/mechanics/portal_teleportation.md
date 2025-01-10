# Portal Teleportation
Terdapat 2 set portal, setiap set terdiri dari 2 portal yang berhubungan. Portal yang berhubungan dapat menteleportasikan objek yang telah diberi component TeleportData. 
Ketika sebuah objek masuk ke dalam portal, objek tersebut:
- Diclone ke portal lain dengan memerhatikan posisi dan orientasi awal dari objek dan juga portal yang dituju.
- Disedot ke masuk ke arah portal dan clonenya disedot keluar dari portal yang lain.
- Terkena mask yang menutupi gambar dari objek untuk ilusi masuk/keluar portal
- Di-disable collisionnya dengan ground untuk sementara sampai salah satu dari clone atau objeknya berhasil masuk/keluar portal.

Saat salah satu objek keluar dari portal, clonenya akan dihapus dari kenyataan. Menyisakan satu objek.
