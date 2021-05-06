---
title: Membuat program menghitung Luas dan Keliling Lingkaran dengan Javascript
tags:
  - html
  - css
  - js
  - lingkaran
comments: true
category: tutorial
date: 2021-05-07 00:04:23
---


{% img /img/tutorial/program-luas-keliling-lingkaran/hero.png '"Tampilan Program" "Tampilan Program"' %}

Bismillahirrahmanirrahim

Kali ini kita akan membahas gimana membuat program sederhana tentang penghitungan luas dan keliling sebuah lingkaran. Dimana jika kita ingin mengetahui luas sebuah lingkaran berdasarkan jari-jari nya, maka kita cukup masukkan nilai ke kolom input yang telah tersedia dan nanti kita tekan tombol **Hasil** maka otomatis jawabannya akan tampil di kolom input yang sengaja di disable.

Menarik bukan? :"... mari kita coba buat program tersebut bareng-bareng ya...

<!-- more -->

## Menghitung dengan Pi 22/7

Pertama-tama kita menghitung luas dan keliling lingkaran menggunakan cara Pi 22/7 yang dimana penghitungan ini hanya bisa dilakukan menggunakan kelipatan 7, seperti: 7,14,21,28,35,dst.

Buatlah file html terlebih dahulu, lalu tuliskan kode struktur html. Atau kamu bisa salin kode dibawah ini:

{% codeblock index.html lang:html %}
<!DOCTYPE html>
<html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Menghitung Luas dan Keliling Lingkaran</title>
    <link rel="stylesheet" href="style.css">
    </head>
    <body>

        <script src="main.js"></script>
    </body>
</html>
{% endcodeblock %}

Sedikit catatan, disini saya juga menambahkan perintah untuk menghubungkan file html kita ke file css dan javascript nya yang terletak pada baris 8 dan 12, kamu bisa menyesuaikan dimana letak kamu menyimpan file css dan file javascript. 

Setelah file html telah siap, kita buat tag form sederhana untuk user menginputkan nilai nya. Atau kamu bisa salin kode dibawah ini di dalam tag **body** pada html:
{% codeblock index.html lang:html %}
<!DOCTYPE html>
<html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Menghitung Luas dan Keliling Lingkaran</title>
    <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <h1>Menghitung Luas dan Keliling Lingkaran</h1>
        <!-- Bagian Pi 22 / 7 -->
        <form class="pi1">
        <h2>Dengan Pi: 22/7</h2>
        <table border="2px solid #333" cellpadding="10">
            <tr>
            <td><label for="luasJ"> Luas lingkaran jari-jari: </label></td>
            <td><input type="number" id="luasJ" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
            <td><input type="submit" value="Hasil" id="btnLJ" /></td>
            <td>
                <label>
                <input type="number" id="hasilLJ" disabled />
                cm<sup>2</sup>
                </label>
            </td>
            </tr>

            <tr>
            <td><label for="kelilingJ"> Keliling lingkaran jari-jari: </label></td>
            <td><input type="number" id="kelilingJ" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
            <td><input type="submit" value="Hasil" id="btnKJ" /></td>
            <td>
                <label>
                <input type="number" id="hasilKJ" disabled />
                cm
                </label>
            </td>
            </tr>

            <tr>
            <td><label for="luasD"> Luas lingkaran diameter: </label></td>
            <td><input type="number" id="luasD" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
            <td><input type="submit" value="Hasil" id="btnLD" /></td>
            <td>
                <label>
                <input type="number" id="hasilLD" disabled />
                cm<sup>2</sup>
                </label>
            </td>
            </tr>

            <tr>
            <td><label for="kelilingD"> Keliling lingkaran diameter: </label></td>
            <td><input type="number" id="kelilingD" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
            <td><input type="submit" value="Hasil" id="btnKD" /></td>
            <td>
                <label>
                <input type="number" id="hasilKD" disabled />
                cm
                </label>
            </td>
            </tr>
        </table>
        </form>

        <script src="main.js"></script>
    </body>
</html>
{% endcodeblock %}

Maka hasil tampilan kode diatas akan seperti ini.
{% img /img/tutorial/program-luas-keliling-lingkaran/tampilan-html.png '"Tampilan browser dari file html" "Tampilan browser dari file html"' %}

### Keterangan

1. Terdapat attribut html yaitu **id** yang dimana di teks akhirnya terdapat **J**, **LJ** dan **KJ** Yang dimana itu merupakan singkatan, yaitu:
 - J = jari-jari
 - LJ = luas jari-jari
 - KJ = keliling jari-jari

Setelah file html kita buat, maka sekarang kita menghias sedikit website kita agar lebih menarik menggunakan css. Sebelumnya kita sudah menghubungkan file css pada html kita, buatlah file css dengan nama **style.css** sesuai yang sudah kita hubungkan. Silahkan kamu buat, lalu kamu hias sesuai selera masing-masing.

Atau kamu bisa mengikuti saya dengan menyalin kode dibawah ini:
{% codeblock style.css lang:css %}
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

/* Untuk menghilangkan tanda panah atas dan bawah pada input number */
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}

body {
  font-family: "Roboto", sans-serif;
  margin: 0;
  overflow-x: hidden;
}

h1 {
  margin-bottom: 16px;
}

h1,
h2 {
  text-align: center;
}

h2 {
  color: #fff;
}

form {
  padding: 10px;
  background-color: rgb(44, 129, 226);
  width: 100%;
}

table {
  margin: auto;
  background-color: #fff;
}

input[type="text"] {
  color: #333;
  font-weight: 700;
  padding: 6px;
}

label {
  display: flex;
}

label input[type="text"] {
  margin-right: 5px;
}

@media (max-width: 786px) {
  form {
    overflow: scroll;
  }
}
{% endcodeblock %}

Maka hasil tampilan kode diatas akan seperti ini.
{% img /img/tutorial/program-luas-keliling-lingkaran/tampilan-css.png '"Tampilan browser dari file css" "Tampilan browser dari file css"' %}

### Keterangan

1. Saya menambahkan font Roboto yang dimana diambil dari [Google font](https://fonts.google.com/specimen/Roboto?query=robo)
2. Dibaris 5-14 saya menghilangkan tandah panah keatas dan kebawah pada input type="number", dimana default nya input type="number" ini memiliki tanda panah keatas dan kebawah

Nah, sekarang sudah lumayan menarik lah ya walaupun gak bagus-bagus amet wkwkwk. Tapi ini belum bisa melakukan penghitungan luas dan keliling, disini kita perlu javascript untuk melakukan itu.

Maka siapkan terlebih dahulu file javascript nya, buat nama file javascript kita dengan nama **main.js** sesuai yang telah kita hubungkan juga pada file html kita. 

Jika kamu sudah membuatnya, silahkan coba manipulasi sendiri jika kamu mau, mungkin cara kamu lebih efektif dibandingkan cara saya. Atau kamu bisa salin kode dibawah ini: 
{% codeblock main.js lang:javascript %}
// Menghitung luas lingkaran jari-jari
// rumus: pi * r * r
function luasJariJari(a) {
  return (22 / 7) * a * a;
}

const inputLJ = document.getElementById("luasJ");
document.getElementById("btnLJ").addEventListener("click", (e) => {
  if (inputLJ.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLJ.value != 7 && inputLJ.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputLJ.value % 7 == 0) {
    document.getElementById("hasilLJ").value = luasJariJari(inputLJ.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran jari-jari
// rumus: pi * 2 * r
function kelilingJariJari(c) {
  return (22 / 7) * 2 * c;
}

const inputKJ = document.getElementById("kelilingJ");
document.getElementById("btnKJ").addEventListener("click", (e) => {
  if (inputKJ.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKJ.value != 7 && inputKJ.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputKJ.value % 7 == 0) {
    document.getElementById("hasilKJ").value = kelilingJariJari(inputKJ.value);
  }
  e.preventDefault();
});

// Menghitung luas lingkaran diameter
// rumus: pi * (r / 2) * (r/2)
function luasDiameter(b) {
  return (22 / 7) * ((b / 2) * (b / 2));
}

const inputLD = document.getElementById("luasD");
document.getElementById("btnLD").addEventListener("click", (e) => {
  if (inputLD.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLD.value != 7 && inputLD.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputLD.value % 7 == 0) {
    document.getElementById("hasilLD").value = luasDiameter(inputLD.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran diameter
// rumus: pi * d
function kelilingDiameter(d) {
  return (22 / 7) * d;
}

const inputKD = document.getElementById("kelilingD");
document.getElementById("btnKD").addEventListener("click", (e) => {
  if (inputKD.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKD.value != 7 && inputKD.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputKD.value % 7 == 0) {
    document.getElementById("hasilKD").value = kelilingDiameter(inputKD.value);
  }
  e.preventDefault();
});
{% endcodeblock %}

Maka hasil tampilan kode diatas akan seperti ini.
{% img /img/tutorial/program-luas-keliling-lingkaran/tampilan-js.gif '"Tampilan browser dari file javascript" "Tampilan browser dari file javascript"' %}

### Keterangan
1. Membuat beberapa fungsi untuk rumus nya
2. Menyeleksi beberapa tag html dengan attribut id nya
3. Melakukan pengkondisian untuk melakukan ketika user tidak memasukkan nilai, user tidak memasukkan nilai yang bukan kelipatan 7 dan ketika user memasukkan nilai kelipatan 7 baru ditampilkan hasil nya
4. **e.preventDefault()** digunakan agar menghilangkan perilaku default dari tag form, dimana jika tidak diberikan **e.preventDefault()** ketika menekan tombol hasil maka halaman akan refersh secara otomatis

Fyuhhh, panjang juga ya wkwk. Gimana hasil teman-teman? apakah sama berjalan dengan lancar?, kalau ada masalah bisa coba japri saya via Telegram ya [Rian](https://t.me/riann18). Oke kita lanjut kepembahasan kedua yak, yaitu penghitungan menggunakan Pi 3,14.

## Menghitung dengan Pi 3,14

Sebelumnya didalam tag **body** pada file html kita berisi bagian perhitungan menggunakan Pi 22/7 atau tag **form** yang menyangkut pada perhitungan dengan Pi 22/7.

Sekarang kamu bisa tambahkan dibawah setelah tag penutup form yang ada dibaris 64 (sesuai kode file html diatas sebelumnya), kamu bisa salin kode dibawah ini:
{% codeblock index.html lang:html %}
 <!-- Bagian Pi 3, 14 -->
    <form class="pi2">
      <h2>Dengan Pi: 3,14</h2>
      <table border="2px solid #333" cellpadding="10">
        <tr>
          <td><label for="luasJ2"> Luas lingkaran jari-jari: </label></td>
          <td><input type="number" id="luasJ2" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
          <td><input type="submit" value="Hasil" id="btnLJ2" /></td>
          <td>
            <label>
              <input type="number" id="hasilLJ2" disabled />
              cm<sup>2</sup>
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="kelilingJ2"> Keliling lingkaran jari-jari: </label></td>
          <td><input type="number" id="kelilingJ2" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
          <td><input type="submit" value="Hasil" id="btnKJ2" /></td>
          <td>
            <label>
              <input type="number" id="hasilKJ2" disabled />
              cm
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="luasD2"> Luas lingkaran diameter: </label></td>
          <td><input type="number" id="luasD2" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
          <td><input type="submit" value="Hasil" id="btnLD2" /></td>
          <td>
            <label>
              <input type="number" id="hasilLD2" disabled />
              cm<sup>2</sup>
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="kelilingD2"> Keliling lingkaran diameter: </label></td>
          <td><input type="number" id="kelilingD2" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
          <td><input type="submit" value="Hasil" id="btnKD2" /></td>
          <td>
            <label>
              <input type="number" id="hasilKD2" disabled />
              cm
            </label>
          </td>
        </tr>
      </table>
    </form>
{% endcodeblock %}

Sehingga jika digabungkan kode nya, akan menjadi seperti ini:
{% codeblock index.html lang:html %}
 <!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Menghitung Luas dan Keliling Lingkaran</title>
    <link rel="stylesheet" href="lingkaran.css" />
  </head>
  <body>
    <h1>Menghitung Luas dan Keliling Lingkaran</h1>
    <!-- Bagian Pi 22 / 7 -->
    <form class="pi1">
      <h2>Dengan Pi: 22/7</h2>
      <table border="2px solid #333" cellpadding="10">
        <tr>
          <td><label for="luasJ"> Luas lingkaran jari-jari: </label></td>
          <td><input type="number" id="luasJ" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
          <td><input type="submit" value="Hasil" id="btnLJ" /></td>
          <td>
            <label>
              <input type="number" id="hasilLJ" disabled />
              cm<sup>2</sup>
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="kelilingJ"> Keliling lingkaran jari-jari: </label></td>
          <td><input type="number" id="kelilingJ" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
          <td><input type="submit" value="Hasil" id="btnKJ" /></td>
          <td>
            <label>
              <input type="number" id="hasilKJ" disabled />
              cm
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="luasD"> Luas lingkaran diameter: </label></td>
          <td><input type="number" id="luasD" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
          <td><input type="submit" value="Hasil" id="btnLD" /></td>
          <td>
            <label>
              <input type="number" id="hasilLD" disabled />
              cm<sup>2</sup>
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="kelilingD"> Keliling lingkaran diameter: </label></td>
          <td><input type="number" id="kelilingD" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
          <td><input type="submit" value="Hasil" id="btnKD" /></td>
          <td>
            <label>
              <input type="number" id="hasilKD" disabled />
              cm
            </label>
          </td>
        </tr>
      </table>
    </form>

    <!-- Bagian Pi 3, 14 -->
    <form class="pi2">
      <h2>Dengan Pi: 3,14</h2>
      <table border="2px solid #333" cellpadding="10">
        <tr>
          <td><label for="luasJ2"> Luas lingkaran jari-jari: </label></td>
          <td><input type="number" id="luasJ2" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
          <td><input type="submit" value="Hasil" id="btnLJ2" /></td>
          <td>
            <label>
              <input type="number" id="hasilLJ2" disabled />
              cm<sup>2</sup>
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="kelilingJ2"> Keliling lingkaran jari-jari: </label></td>
          <td><input type="number" id="kelilingJ2" autocomplete="off" placeholder="Masukkan nilai jari-jari" /></td>
          <td><input type="submit" value="Hasil" id="btnKJ2" /></td>
          <td>
            <label>
              <input type="number" id="hasilKJ2" disabled />
              cm
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="luasD2"> Luas lingkaran diameter: </label></td>
          <td><input type="number" id="luasD2" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
          <td><input type="submit" value="Hasil" id="btnLD2" /></td>
          <td>
            <label>
              <input type="number" id="hasilLD2" disabled />
              cm<sup>2</sup>
            </label>
          </td>
        </tr>

        <tr>
          <td><label for="kelilingD2"> Keliling lingkaran diameter: </label></td>
          <td><input type="number" id="kelilingD2" autocomplete="off" placeholder="Masukkan nilai diameter" /></td>
          <td><input type="submit" value="Hasil" id="btnKD2" /></td>
          <td>
            <label>
              <input type="number" id="hasilKD2" disabled />
              cm
            </label>
          </td>
        </tr>
      </table>
    </form>
    <script src="lingkaran.js"></script>
  </body>
</html>
{% endcodeblock %}

Maka hasil tampilan kode diatas akan seperti ini.
{% img /img/tutorial/program-luas-keliling-lingkaran/tampilan-html2.png '"Tampilan browser dari file css" "Tampilan browser dari file css"' %}

### Keterangan
1. Terdapat attribut html yaitu **id** yang dimana di teks akhirnya terdapat **D**, **LD**, **KD**. Yang dimana itu merupakan singkatan, yaitu:
 - D = diameter
 - LD = luas diameter
 - KD = keliling diameter
2. Terdapat attribut **class** pada tag form yang kedua, yaitu **pi2** walaupun form kesatu juga ada, **pi2** akan digunakan pada pemanggilan di css

Baik, kita beralih ke file css nya, di css cukup tambahkan **pi2** itu dan ubah warna background nya agar membedakan dari bagian Pi 22/7, warna background bisa kamu sesuaikan. Atau kamu bisa salin kode dibawah ini dan paste ke file css kamu sebelum nya:
{% codeblock style.css lang:css %}
.pi2 {
  background-color: rgb(33, 201, 103);
}

@media (max-width: 786px) {
  form {
    overflow: scroll;
  }

  .pi2 {
    margin-top: 20px;
  }
}
{% endcodeblock %}

Sehingga jika digabung kode nya akan menjadi seperti ini:
{% codeblock style.css lang:css %}
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

/* Untuk menghilangkan tanda panah atas dan bawah pada input number */
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}

body {
  font-family: "Roboto", sans-serif;
  margin: 0;
  overflow-x: hidden;
}

h1 {
  margin-bottom: 16px;
}

h1,
h2 {
  text-align: center;
}

h2 {
  color: #fff;
}

form {
  padding: 10px;
  background-color: rgb(44, 129, 226);
  width: 100%;
}

table {
  margin: auto;
  background-color: #fff;
}

input[type="text"] {
  color: #333;
  font-weight: 700;
  padding: 6px;
}

label {
  display: flex;
}

label input[type="text"] {
  margin-right: 5px;
}

.pi2 {
  background-color: rgb(33, 201, 103);
}

@media (max-width: 786px) {
  form {
    overflow: scroll;
  }

  .pi2 {
    margin-top: 20px;
  }
}
{% endcodeblock %}

Maka hasil tampilan dari kode diatas akan seperti ini.
{% img /img/tutorial/program-luas-keliling-lingkaran/tampilan-css2.png '"Tampilan browser dari file css" "Tampilan browser dari file css"' %}

Oke, terakhir kita ke beralih ke file javascript nya. Mungkin sama aja seperti kode javascript diatas, yang membedakan adalah rumus menggunakan 3,14. Kamu bisa salin kode ini dan tambahkan di file main.js kamu sebelum nya:
{% codeblock main.js lang:javascript %}

// ------------------- Dibawah ini khusus Pi 3,14 -----------------
// Menghitung luas lingkaran jari-jari
// rumus: pi * r * r
function luasJariJari2(e) {
  return 3.14 * e * e;
}
const inputLJ2 = document.getElementById("luasJ2");
document.getElementById("btnLJ2").addEventListener("click", (e) => {
  if (inputLJ2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLJ2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilLJ2").value = luasJariJari2(inputLJ2.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran jari-jari
// rumus: pi * 2 * r
function kelilingJariJari2(f) {
  return 3.14 * 2 * f;
}

const inputKJ2 = document.getElementById("kelilingJ2");
document.getElementById("btnKJ2").addEventListener("click", (e) => {
  if (inputKJ2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKJ2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilKJ2").value = kelilingJariJari2(inputKJ2.value);
  }
  e.preventDefault();
});

// Menghitung luas lingkaran diameter
// rumus: pi * (r / 2) * (r/2)
function luasDiameter2(g) {
  return 3.14 * ((g / 2) * (g / 2));
}

const inputLD2 = document.getElementById("luasD2");
document.getElementById("btnLD2").addEventListener("click", (e) => {
  if (inputLD2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLD2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilLD2").value = luasDiameter2(inputLD2.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran diameter
// rumus: pi * d
function kelilingDiameter2(h) {
  return 3.14 * h;
}

const inputKD2 = document.getElementById("kelilingD2");
document.getElementById("btnKD2").addEventListener("click", (e) => {
  if (inputKD2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKD2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilKD2").value = kelilingDiameter2(inputKD2.value);
  }
  e.preventDefault();
});
{% endcodeblock %}

Sehingga jika digabung kode nya akan menjadi seperti ini:
{% codeblock main.js lang:javascript %}
// Menghitung luas lingkaran jari-jari
// rumus: pi * r * r
function luasJariJari(a) {
  return (22 / 7) * a * a;
}

const inputLJ = document.getElementById("luasJ");
document.getElementById("btnLJ").addEventListener("click", (e) => {
  if (inputLJ.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLJ.value != 7 && inputLJ.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputLJ.value % 7 == 0) {
    document.getElementById("hasilLJ").value = luasJariJari(inputLJ.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran jari-jari
// rumus: pi * 2 * r
function kelilingJariJari(c) {
  return (22 / 7) * 2 * c;
}

const inputKJ = document.getElementById("kelilingJ");
document.getElementById("btnKJ").addEventListener("click", (e) => {
  if (inputKJ.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKJ.value != 7 && inputKJ.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputKJ.value % 7 == 0) {
    document.getElementById("hasilKJ").value = kelilingJariJari(inputKJ.value);
  }
  e.preventDefault();
});

// Menghitung luas lingkaran diameter
// rumus: pi * (r / 2) * (r/2)
function luasDiameter(b) {
  return (22 / 7) * ((b / 2) * (b / 2));
}

const inputLD = document.getElementById("luasD");
document.getElementById("btnLD").addEventListener("click", (e) => {
  if (inputLD.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLD.value != 7 && inputLD.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputLD.value % 7 == 0) {
    document.getElementById("hasilLD").value = luasDiameter(inputLD.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran diameter
// rumus: pi * d
function kelilingDiameter(d) {
  return (22 / 7) * d;
}

const inputKD = document.getElementById("kelilingD");
document.getElementById("btnKD").addEventListener("click", (e) => {
  if (inputKD.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKD.value != 7 && inputKD.value % 7 != 0) {
    alert("Isi nilai dengan kelipatan 7!");
  } else if (inputKD.value % 7 == 0) {
    document.getElementById("hasilKD").value = kelilingDiameter(inputKD.value);
  }
  e.preventDefault();
});

// ------------------- Dibawah ini khusus Pi 3,14 -----------------
// Menghitung luas lingkaran jari-jari
// rumus: pi * r * r
function luasJariJari2(e) {
  return 3.14 * e * e;
}
const inputLJ2 = document.getElementById("luasJ2");
document.getElementById("btnLJ2").addEventListener("click", (e) => {
  if (inputLJ2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLJ2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilLJ2").value = luasJariJari2(inputLJ2.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran jari-jari
// rumus: pi * 2 * r
function kelilingJariJari2(f) {
  return 3.14 * 2 * f;
}

const inputKJ2 = document.getElementById("kelilingJ2");
document.getElementById("btnKJ2").addEventListener("click", (e) => {
  if (inputKJ2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKJ2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilKJ2").value = kelilingJariJari2(inputKJ2.value);
  }
  e.preventDefault();
});

// Menghitung luas lingkaran diameter
// rumus: pi * (r / 2) * (r/2)
function luasDiameter2(g) {
  return 3.14 * ((g / 2) * (g / 2));
}

const inputLD2 = document.getElementById("luasD2");
document.getElementById("btnLD2").addEventListener("click", (e) => {
  if (inputLD2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputLD2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilLD2").value = luasDiameter2(inputLD2.value);
  }
  e.preventDefault();
});

// Menghitung Keliling Lingkaran diameter
// rumus: pi * d
function kelilingDiameter2(h) {
  return 3.14 * h;
}

const inputKD2 = document.getElementById("kelilingD2");
document.getElementById("btnKD2").addEventListener("click", (e) => {
  if (inputKD2.value == "") {
    alert("Isi nilai terlebih dahulu!");
  } else if (inputKD2.value % 7 == 0) {
    alert("Kelipatan 7 isi dibagian Pi: 22/7 ");
  } else {
    document.getElementById("hasilKD2").value = kelilingDiameter2(inputKD2.value);
  }
  e.preventDefault();
});
{% endcodeblock %}

Maka hasil tampilan dari kode diatas akan seperti ini.
{% img /img/tutorial/program-luas-keliling-lingkaran/tampilan-js2.gif '"Tampilan browser dari file javascript" "Tampilan browser dari file javascript"' %}

Hasil akhir dari pembelajaran ini seperti ini.
{% img /img/tutorial/program-luas-keliling-lingkaran/akhir.gif '"Tampilan akhir" "Tampilan akhir"' %}

Akhirnya selesai juga :", cukup panjang ya hehe. Gimana hasil teman-teman? apa berjalan dengan baik? jika belum berhasil coba japri via Telegram ya [Rian](https://t.me/riann18) dan sebelum japri coba di cek terlebih dahulu bagian console nya, mungkin saja ada error.

Itu saja yang bisa saya bagikan, mungkin bisa diperbaiki lebih baik lagi program yang saya buat ini. Mungkin juga bisa di refactor agar kode nya lebih rapih dan juga tidak terlalu panjang. Kamu bisa lihat hasil saya [Demo](https://mfebriann.github.io/menghitung-luas-dan-keliling-lingkaran/)

Kurang lebih nya mohon dimaafkan, silahkan kirim kan komentar nya apabila ada masukkan ya. 

Terima kasih semua, semoga dapat bermanfaat :D