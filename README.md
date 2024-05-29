
# Pegasus Clock README

## Deskripsi
Pegasus Clock adalah aplikasi jam alarm yang dikembangkan dengan menggunakan bahasa pemrograman Python dan modul tkinter. Aplikasi ini memungkinkan pengguna untuk mengatur waktu alarm dan memainkan suara ketika waktu yang ditentukan tercapai.

## Fitur
- Set alarm berdasarkan jam, menit, dan detik.
- Menampilkan waktu saat ini.
- Memainkan suara alarm ketika waktu yang ditentukan tercapai.

## Dibuat oleh
Letda Kes dr. Sobri, S.Kom, CEH, OSCP, OSCE

## Cara Penggunaan
1. **Clone repository ini** atau unduh file `pegasus_clock.py`.
2. **Pastikan Anda memiliki Python dan Tkinter** terinstal di sistem Anda.
3. **Jalankan aplikasi** dengan menjalankan perintah berikut di terminal:
   ```bash
   python pegasus_clock.py
   ```
4. **Atur waktu alarm** dengan memilih jam, menit, dan detik dari dropdown.
5. **Klik tombol "Set Alarm"** untuk memulai alarm.

## Instalasi
1. **Instal Python**: Jika belum terinstal, unduh dan instal Python dari [python.org](https://www.python.org/).
2. **Instal Tkinter**: Tkinter biasanya sudah termasuk dalam instalasi Python standar. Jika tidak, Anda dapat menginstalnya dengan perintah berikut:
   ```bash
   sudo apt-get install python3-tk
   ```
   atau untuk pengguna Windows, Tkinter sudah termasuk dalam instalasi Python.

3. **Instal winsound**: Modul winsound sudah termasuk dalam Python untuk Windows. Untuk pengguna lain, Anda mungkin perlu menggunakan modul audio lain.

## Kode Sumber
```python
from tkinter import *
import datetime
import time
import winsound
from threading import *

# Buat Objek
root = Tk()

# Atur ukuran
root.geometry("400x200")

# Gunakan Threading
def Threading():
    t1 = Thread(target=alarm)
    t1.start()

def alarm():
    # Loop tak terbatas
    while True:
        # Atur Waktu Alarm
        set_alarm_time = f"{hour.get()}:{minute.get()}:{second.get()}"

        # Tunggu satu detik
        time.sleep(1)

        # Dapatkan waktu saat ini
        current_time = datetime.datetime.now().strftime("%H:%M:%S")
        print(current_time, set_alarm_time)

        # Periksa apakah waktu alarm sama dengan waktu saat ini
        if current_time == set_alarm_time:
            print("Waktunya Bangun!")
            # Mainkan suara
            winsound.PlaySound("sound.wav", winsound.SND_ASYNC)

# Tambahkan Label, Frame, Button, Optionmenus
Label(root, text="Alarm Clock", font=("Helvetica 20 bold"), fg="red").pack(pady=10)
Label(root, text="Set Time", font=("Helvetica 15 bold")).pack()

frame = Frame(root)
frame.pack()

hour = StringVar(root)
hours = ('00', '01', '02', '03', '04', '05', '06', '07',
        '08', '09', '10', '11', '12', '13', '14', '15',
        '16', '17', '18', '19', '20', '21', '22', '23')
hour.set(hours[0])

hrs = OptionMenu(frame, hour, *hours)
hrs.pack(side=LEFT)

minute = StringVar(root)
minutes = ('00', '01', '02', '03', '04', '05', '06', '07',
        '08', '09', '10', '11', '12', '13', '14', '15',
        '16', '17', '18', '19', '20', '21', '22', '23',
        '24', '25', '26', '27', '28', '29', '30', '31',
        '32', '33', '34', '35', '36', '37', '38', '39',
        '40', '41', '42', '43', '44', '45', '46', '47',
        '48', '49', '50', '51', '52', '53', '54', '55',
        '56', '57', '58', '59')
minute.set(minutes[0])

mins = OptionMenu(frame, minute, *minutes)
mins.pack(side=LEFT)

second = StringVar(root)
seconds = ('00', '01', '02', '03', '04', '05', '06', '07',
        '08', '09', '10', '11', '12', '13', '14', '15',
        '16', '17', '18', '19', '20', '21', '22', '23',
        '24', '25', '26', '27', '28', '29', '30', '31',
        '32', '33', '34', '35', '36', '37', '38', '39',
        '40', '41', '42', '43', '44', '45', '46', '47',
        '48', '49', '50', '51', '52', '53', '54', '55',
        '56', '57', '58', '59')
second.set(seconds[0])

secs = OptionMenu(frame, second, *seconds)
secs.pack(side=LEFT)

Button(root, text="Set Alarm", font=("Helvetica 15"), command=Threading).pack(pady=20)

# Jalankan Tkinter
root.mainloop()
```

## Lisensi
Proyek ini dilisensikan di bawah lisensi MIT. Silakan lihat file `LICENSE` untuk informasi lebih lanjut.
