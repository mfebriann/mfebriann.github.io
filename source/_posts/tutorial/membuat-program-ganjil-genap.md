---
title: Program input angka ganjil dan genap
tags:
  - html
  - css
  - javascript
  - ganjil-genap
  - program
comments: true
categories: tutorial
date: 2021-05-08 13:50:21
---


{% img /img/tutorial/membuat-program-ganjil-genap/hero.png '"Tampilan Program" "Tampilan Program"' %}

Bismillahirrahmanirrahim

Disini kita akan membuat sebuah program yang sederhana yang dimana ada opsi 2 pilihan, yaitu opsi Ganjil dan Genap. Jika kita memilih opsi Ganjil maka kita harus memasukkan nilai nya berupa angka ganjil begitupun sebaliknya untuk opsi Genap.

Nah, program ini terdapat 2 buah input, yang pertama adalah input untuk memassukan nilai awal dan input kedua adalah memasukkan nilai akhir, maksudnya gimana? 

<!-- more -->

Jadi gini, jika kamu memilih opsi Genap lalu memasukkan nilai awal di kolom input, kita ambil contoh memasukkan angka 2. Dan memasukkan nilai akhir 10 misalnya. Maka hasil yang akan keluar ketika ditekan tombol Submit adalah, teks tentang opsi yang dipilih, setelah itu angka genap yang dimulai dari angka 2 dan berakhir pada angka 10. Jadi hasil nya adalah **Bilangan Genap: 2, 4, 6, 8, 10**, masih bingung juga? Mari kita ke bahas bareng-bareng aja langsung yuk.

Pertama buatlah terlebih dahulu file html, lalu kamu bisa salin kode dibawah ini:
{% codeblock index.html lang:html %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Program menentukan bilangan ganjil atau genap dan login</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <form>
      <h2>Menampilkan bilangan ganjil atau genap</h2>
      <table>
        <tr>
          <td><label>Bilangan:</label></td>
          <td>
            <select id="pilihan">
              <option value="Ganjil">Ganjil</option>
              <option value="Genap">Genap</option>
            </select>
          </td>
        </tr>
        <tr>
          <td><label for="nilaiAwal">Nilai Awal:</label></td>
          <td><input type="number" id="nilaiAwal" placeholder="Nilai Awal" /></td>
        </tr>
        <tr>
          <td><label for="nilaiAkhir">Nilai Akhir:</label></td>
          <td><input type="number" id="nilaiAkhir" placeholder="Nilai Akhir" /></td>
        </tr>
        <tr>
          <td><input type="submit" id="btn" value="Submit" /></td>
        </tr>
      </table>
      <p id="cetakHasil"><span id="cetakBilangan"></span></p>
    </form>
    <script src="main.js"></script>
  </body>
</html>
{% endcodeblock %}

Disini saya langsung memasukkan kode untuk tag form nya dan juga menghubungkan dengan file css dan juga file javascript nya (Dibaris 8 & dibaris 37). Maka hasil dari kode diatas, ketika dibuka dibrowser akan seperti ini:
{% img /img/tutorial/membuat-program-ganjil-genap/tampilan-html.png '"Tampilan awal" "Tampilan awal"' %}

Setelah file html sudah dibuat, sekarang kita buat file css nya. Disini saya tidak mempercantik halaman nya, akan tetapi hanya mengubah letak atau posisi nya saja dan menambah sedikit saja untuk menghias halaman web nya. Silahkan kamu buat file css, pastikan nama file sama dengan nama yang telah kita hubungkan pada file html kita, yaitu nama file css nya **style.css**.

Kamu bisa salin kode css dibawah ini:
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
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

form {
  width: 400px;
}

h2,
#cetakHasil {
  text-align: center;
}

table {
  border: 2px solid #333;
  padding: 20px;
  margin: auto;
}

input[type="number"] {
  width: 65%;
}

#nilaiAwal {
  margin: 10px 0;
}

select {
  width: 69%;
}

#btn {
  padding: 5px 10px;
  margin-top: 15px;
}
{% endcodeblock %}

Jika kita buka di browser, maka hasil tampilan dari kode diatas akan seperti ini:
{% img /img/tutorial/membuat-program-ganjil-genap/tampilan-css.png '"Tampilan dengan tambahan css" "Tampilan dengan tambahan css"' %}

Sekarang masuk ketahap yang seru nya, yaitu bermain dengan javascript. Silahkan buat terlebih dahulu file javascript nya, sesuai dengan yang telah dihubungkan pada file html kita, yaitu nama file javascript nya **main.js**. Lalu kamu bisa salin kode dibawah ini atau jika ingin mencoba nya silahkan juga :D.
{% codeblock main.js lang:javascript %}
// Seleksi terlebih dahulu
const pilihan = document.getElementById("pilihan");
const nilaiAwal = document.getElementById("nilaiAwal");
const nilaiAkhir = document.getElementById("nilaiAkhir");
const kirimHasil = document.getElementById("btn");
const cetakHasil = document.getElementById("cetakHasil");

kirimHasil.addEventListener("click", function (e) {
  // Mengecek jika inputan dari nilai awal dan nilai akhir kosong, maka tampilkan alert
  if (nilaiAwal.value === "") {
    alert("Isi terlebih dahulu Nilai Awal!");
  } else if (nilaiAkhir.value === "") {
    alert("Isi terlebih dahulu Nilai Akhir!");
    // Jika user memilih pilihan Genap
  } else if (pilihan.value === "Genap") {
    // Mengecek jika user memasukkan nilai ganjil pada nilai awal
    if (nilaiAwal.value % 2 === 1) {
      alert("Nilai awal bukan angka genap!");
      // Mengecek jika user memasukkan nilai ganjil pada nilai akhir
    } else if (nilaiAkhir.value % 2 === 1) {
      alert("Nilai akhir bukan angka genap!");
      // Jika user memasukkan nilai genap
    } else {
      // Mengubah tipe data dari nilai input nilaiAwal dari string menjadi number
      let count = Number(nilaiAwal.value);
      // Membuat array kosong
      const arrGenap = [];
      for (count; count <= nilaiAkhir.value; count++) {
        // Di cek, jika pembagian yang kita inputkan nilai nya dan sisa bagi nya 0, maka dia otomatis genap
        if (count % 2 == 0) {
          // Jika benar genap, maka push nilai genap itu kedalam arrGenap
          arrGenap.push(count);
          // Memberikan method join agar koma nya ada spasi
          cetakHasil.innerText = `Bilangan Genap: ${arrGenap.join(", ")}`;
        }
      }
    }

    // Jika user memilih pilihan Ganjil
  } else if (pilihan.value === "Ganjil") {
    // Mengecek jika user memasukkan nilai genap pada nilai awal
    if (nilaiAwal.value % 2 === 0) {
      alert("Nilai awal bukan angka ganjil!");
      // Mengecek jika user memasukkan nilai genap pada nilai akhir
    } else if (nilaiAkhir.value % 2 === 0) {
      alert("Nilai akhir bukan angka ganjil!");
      // Jika user memasukkan nilai ganjil
    } else {
      // Mengubah tipe data dari nilai input nilaiAwal dari string menjadi number
      let count = Number(nilaiAwal.value);
      // Membuat array kosong
      const arrGanjil = [];
      for (count; count <= nilaiAkhir.value; count++) {
        // Di cek, jika pembagian yang kita inputkan nilai nya dan sisa bagi nya 1, maka dia otomatis ganjil
        if (count % 2 == 1) {
          // Jika benar ganjil, maka push nilai ganjil itu kedalam arrGanjil
          arrGanjil.push(count);
          // Memberikan method join agar koma nya ada spasi
          cetakHasil.innerText = `Bilangan Ganjil: ${arrGanjil.join(", ")}`;
        }
      }
    }
  }
  e.preventDefault();
});
{% endcodeblock %}

Maka kalau kita jalankan di browser, hasilnya akan seperti ini:
{% img /img/tutorial/membuat-program-ganjil-genap/akhir.gif '"Tampilan dengan tambahan js" "Tampilan dengan tambahan js"' %}

Mungkin itu saja yang saya dapat bagikan ke teman-teman semua, gimana cara membuat program sederhana menampilkan bilangan ganjil atau genap. Bukan hanya sekedar program yang menginputkan 1 nilai saja lalu akan diberitahu apakah nilai itu genap atau ganjil. Tapi lebih ke program yang menginputkan 2 nilai, yaitu nilai awal dan nilai Akhir. Mungkin teman-teman punya cara yang lebih efektif lagi mengenai kode saya ini dan jangan lupa dibagikan cara teman-teman lewat kolom komentar ya, agar saya juga nanti bisa refaktor lagi kode ini :).

Untuk hasil yang saya buat, kamu bisa lihat di [Demo-Program](https://mfebriann.github.io/menentukan-bilangan-ganjil-genap/) dan untuk melihat kode nya kamu bisa lihat di [Repo-Github](https://github.com/mfebriann/menentukan-bilangan-ganjil-genap).

Terima kasih semua, semoga dapat bermanfaat :D