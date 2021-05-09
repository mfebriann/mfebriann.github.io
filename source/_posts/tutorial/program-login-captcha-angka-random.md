---
title: Program login dengan captcha angka random
tags:
  - html
  - css
  - js
  - program
  - captcha
comments: true
category: tutorial
date: 2021-05-09 20:56:55
---


{% img /img/tutorial/login-captcha-angka-random/hero.png '"Tampilan Program" "Tampilan Program"' %}

Bismillahirrahmanirrahim

Pembahasan kali ini kita akan membuat program login yang sederhana, dimana user yang menginputkan harus mengisi sebuah captcha angkarandom agar bisa login. Jika user memasukkan inputan captcha salah maka user tidak akan bisa login, tapi sebalik nya jika user memasukkan captcha dengan benar maka user akan login.

Penasaran bagaimana cara membuat nya? Mari kita buat bersama-sama.

<!-- more -->

Pertama, siapkan terlebih dahulu file html kalian. Lalu buat form sederhana, jika kalian ingin membuat form pilihan kalian silahkan dibuat terlebih dahulu, atau kalian bisa ikuti saya dengan menyalin kode dibawah ini:
{% codeblock index.html lang:html %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Login sederhana</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1>Login sederhana</h1>
    <form>
      <h2><span id="tampilUsername"></span>, Anda berhasil login...</h2>
      <button type="button" id="kembali">Kembali</button>
      <table>
        <tr>
          <td><label for="username"> Username:</label></td>
          <td><input type="text" id="username" placeholder="Username" autocomplete="off" /></td>
        </tr>
        <tr>
          <td><label for="password"> Password:</label></td>
          <td><input type="password" id="password" placeholder="Password" /></td>
        </tr>
        <tr>
          <td></td>
          <td><input type="number" id="captcha" placeholder="Captcha" /><span id="angkaRandom"></span></td>
        </tr>
        <tr>
          <td></td>
          <td><span id="notifCaptcha"></span></td>
        </tr>
        <tr>
          <td></td>
          <td><input type="submit" id="btn" value="Submit" /></td>
        </tr>
      </table>
    </form>
    <script src="main.js"></script>
  </body>
</html>
{% endcodeblock %}

Perlu diingat kita juga sudah menghubungkan file css dan javascript kita, nanti kita perlu buat saja file tersebut. Jika kalian menyalin kode diatas, maka hasilnya akan seperti ini.
{% img /img/tutorial/login-captcha-angka-random/tampilan-html.png '"Tampilan awal" "Tampilan awal"' %}

Sekarang kita hias sedikit dengan css, kamu bisa menghias sendiri form nya. Atau kamu bisa ikuti saya dengan menyalin kode dibawah ini:
{% codeblock style.css lang:css %}
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}

body {
  margin: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

form {
  border: 2px solid rgb(25, 56, 190);
  padding: 40px 20px 20px;
  box-sizing: border-box;
}

h2,
#kembali {
  display: none;
  text-align: center;
}

#kembali {
  margin: auto;
}

h1 {
  text-align: center;
}

#angkaRandom {
  margin-left: 10px;
  background-color: rgb(230, 192, 123);
  border: 2px solid rgb(51, 51, 51);
  padding: 1px 8px;
  user-select: none;
  cursor: not-allowed;
}

#password {
  margin: 10px 0;
}

#btn {
  margin-top: 10px;
  padding: 2px 10px;
}

input:not(input[type="submit"]) {
  width: 100px;
}

#notifCaptcha {
  font-size: 0.8em;
}
{% endcodeblock %}

Maka hasil nya setelah ditambahkan css, jika kalian mengikuti kode diatas akan seperti ini.
{% img /img/tutorial/login-captcha-angka-random/tampilan-css.png '"Tampilan dengan CSS" "Tampilan dengan CSS"' %}

Ngomong-ngomong kalian ngeh gak ya? Ada kotak kosong warna coklat dengan border hitam, kenapa kosong? Itu nant akan diisi dengan angka random untuk captcha, kita bahas pada bagian javascript.

Baik, untuk menjawab masalah diatas tadi, sekarang kita masuk ke bagian javascript nya. Silahkan kamu buat dulu file javascript nya,lalu bisa salin kode dibawah ini:
{% codeblock main.js lang:javascript %}
// Membuat angka random untuk captcha
const angkaRandom = document.getElementById("angkaRandom");
function angkaUntukCaptcha(max, min) {
  return Math.floor(Math.random() * (max - min) + min);
}

// Membuat variable untuk menampung angka random, disini saya ingin ada 5 angka random jadi dibuat 5 variable
const angkaPertama = angkaUntukCaptcha(1, 10);
const angkaKedua = angkaUntukCaptcha(1, 10);
const angkaKetiga = angkaUntukCaptcha(1, 10);
const angkaKeempat = angkaUntukCaptcha(1, 10);
const angkaKelima = angkaUntukCaptcha(1, 10);
// Menggabungkan kelima angka random
const gabungAngkaRandom = `${angkaPertama}${angkaKedua}${angkaKetiga}${angkaKeempat}${angkaKelima}`;
angkaRandom.innerText = gabungAngkaRandom;

// Seleksi terlebih dahulu inputan html nya
const username = document.getElementById("username");
const password = document.getElementById("password");
const captcha = document.getElementById("captcha");
const submit = document.getElementById("btn");
// Lakukan event ketika tombol di klik
submit.addEventListener("click", function (e) {
  // Jika username kosong maka user wajib mengisi terlebih dahulu
  if (username.value === "") {
    alert("Isi username kamu terlebih dahulu!");
    // Jika password kosong maka user wajib mengisi terlebih dahulu
  } else if (password.value === "") {
    alert("Isi password kamu terlebih dahulu!");
    // Jika username dan password tidak kosong serta captcha berisi nilai angka yang tepat sesuai captcha yang diberikan
  } else if (username.value !== "" && password.value !== "" && captcha.value === gabungAngkaRandom) {
    document.getElementsByTagName("table")[0].style.display = "none";
    document.getElementsByTagName("h2")[0].style.display = "block";
    document.getElementById("tampilUsername").innerText = username.value;
    document.getElementById("kembali").style.display = "block";
  }
  e.preventDefault();
});

// Untuk mengecek inputan nilai yang dimasukkan user
captcha.addEventListener("input", function () {
  // Jika captcha kosong, akan menampilkan pesan
  if (captcha.value === "") {
    notifCaptcha.innerText = "Isi captcha!";
    // Jika captcha tidak sama dengan angka random yang tertera maka akan salah dan akan diberi warna merah
  } else if (captcha.value !== gabungAngkaRandom) {
    notifCaptcha.style.color = "red";
    notifCaptcha.innerText = "Captcha salah!";
    // Jika captcha sama dengan angka random yang tertera maka akan benar dan akan diberi warna hijau
  } else if (captcha.value === gabungAngkaRandom) {
    notifCaptcha.style.color = "green";
    notifCaptcha.innerText = "Captcha benar!";
  }
});

// Ketika user login, lalu ada tombol kembali. Maka akan kembali ke halam form login
kembali.addEventListener("click", function () {
  document.getElementsByTagName("table")[0].style.display = "block";
  document.getElementsByTagName("h2")[0].style.display = "none";
  document.getElementById("kembali").style.display = "none";
  document.getElementById("kembali").type = "submit";
});
{% endcodeblock %}

Maka hasil akhir dari materi ini setelah diberikan kode javascript akan seperti ini.
{% img /img/tutorial/login-captcha-angka-random/akhir.gif '"Tampilan dengan JS" "Tampilan dengan JS"' %}

Gimana? Apa hasil teman-teman sama seperti saya? Ini lebih fokus kebagian javascript aja ya atau jalannya program untuk hiasan seperti html dan css nya bisa teman-teman kreasikan sendiri. Kalo ada masalah silahkan tulis di kolom komentar ya.

Untuk mau lihat hasil saya seperti apa, teman-teman bisa lihat di [Demo-Program](https://mfebriann.github.io/login-dengan-captcha/) atau untuk yang mau lihat sumber kode nya bisa lihat di [Repo-Github](https://github.com/mfebriann/login-dengan-captcha).

Sekian yang bisa jelaskan mengenai cara membuat program login dengan captcha angka yang random, pastinya ada lebih cara yang lebih efektif lagi teman-teman bisa berikan hasil nya lewat kolom komentar. Agar dapat saya refaktor lagi program ini.

Terima kasih semua, semoga dapat bermanfaat :D
