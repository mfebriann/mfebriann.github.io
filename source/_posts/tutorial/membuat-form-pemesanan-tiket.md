---
title: Membuat Form Pemesanan Tiket
tags:
  - html
  - css
  - js
  - tiket
  - form
  - program
comments: true
categories: tutorial
date: 2021-06-01 22:42:53
---


{% img /img/tutorial/program-pemesanan-tiket/hero.png '"Tampilan Program" "Tampilan Program"' %}

Bismillahirrahmanirrahim

Bagaimana kabarnya teman-teman semua?, semoga dalam keadaan sehat selalu ya. Sudah lama saya tidak menulis di blog karena ada beberapa urusan, sekarang ini saya akan membagikan cara membuat form pemesanan tiket destinasi yang sederhana, dimana ide ini saya dapat dari seseorang yang bertanya di grup Telegram mengenai tugas yang diberikan oleh dosen nya dan saya meminta tentang tugas itu untuk membuat nya sendiri sekaligus melatih pembelajaran saya tentang Javascript. Baiklah, tak perlu panjang lebar mari kita buat program tersebut.

<!-- more -->

Pertama yang kita siapkan file html nya terlebih dahulu dan kita isikan struktur membuat form, jangan lupa juga untuk menghubungkan file html kita dengan file css dan file javascript nya. Jika kamu ingin membuat sendiri struktur form kamu, silahkan dibuat terlebih dahulu yang paling terpenting adalah memberikan id pada tiap input, karena sangat berguna saat kita sudah masuk ke file javascript nanti. Jika kamu ingin mengikuti struktur saya, kamu bisa salin kode dibawah ini:
{% codeblock index.html lang:html %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Ticket Payment</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="container">
      <form>
        <label for="nama">Nama:</label>
        <input type="text" id="nama" autofocus autocomplete="off" />
        <label for="destinasi">Destinasi:</label>
        <input type="text" id="destinasi" list="pilihanDestinasi" autocomplete="off" />
        <datalist id="pilihanDestinasi">
          <option value="Bandung">Bandung</option>
          <option value="Jakarta">Jakarta</option>
          <option value="Surabaya">Surabaya</option>
        </datalist>
        <label for="status">Status:</label>
        <input type="text" id="status" list="pilihanStatus" autocomplete="off" />
        <datalist id="pilihanStatus">
          <option value="Dewasa">Dewasa</option>
          <option value="Anak-anak">Anak-anak</option>
        </datalist>
        <label for="jumlah">Jumlah Tiket:</label>
        <input type="number" id="jumlah" />
        <label for="subtotal">Subtotal:</label>
        <input type="number" id="subtotal" disabled />
        <label for="diskon">Diskon:</label>
        <input type="number" id="diskon" disabled />
        <label for="total">Total:</label>
        <input type="number" id="total" disabled />

        <div class="tombol">
          <input type="submit" value="Pesan" id="pesan" />
          <input type="button" value="Hapus" id="hapus" />
        </div>
      </form>

      <!-- Jika berhasil pesan akan menampilkan berkas output nya -->
      <div class="output">
        <h2>TICKET PAYMENT</h2>
        <p>Nama: <span id="namaOutput"></span></p>
        <p>Destinasi: <span id="destinasiOutput"></span></p>
        <p>Status: <span id="statusOutput"></span></p>
        <p>Jumlah Tiket: <span id="jumlahOutput"></span></p>
        <p>Subtotal: <span id="subtotalOutput"></span></p>
        <p>Diskon: <span id="diskonOutput"></span></p>
        <p>Total: <span id="totalOutput"></span></p>
        <p><sup>*</sup>Harga 1 tiket: <span id="hargaTiket"></span></p>
      </div>
    </div>

    <div class="informasi">
      <span>Catatan:</span>
      <span><sup>*</sup>Destinasi hanya terdapat 3 kota: Bandung, Jakarta dan Surabaya <span class="">(Perhatikan huruf kecil dan besar nya)</span></span>
      <span><sup>*</sup>Status hanya terdapat 2: Dewasa dan Anak-anak <span>(Perhatikan huruf kecil dan besar nya)</span></span>
      <span><sup>*</sup>Jika membeli Jumlah Tiket lebih dari 5 bisa mendapat diskon 15% <span>(Tidak lebih dari 5 maka tidak dapat diskon)</span></span>
    </div>
    <script src="script.js"></script>
  </body>
</html>
{% endcodeblock %}

Maka jika kita buka di browser, tampilan jika kamu menyalin kode diatas hasilnya akan seperti ini:
{% img /img/tutorial/program-pemesanan-tiket/tampilan-html.png ' "Tampilan dengan HTML" "Tampilan dengan HTML" ' %}
<br>

Terlihat aneh bukan?, maka dari itu saatnya kita membuat file css dan kita mencoba mempercantiknya. Jika kamu ingin mempercantik tampilan dengan cara sendiri silahkan atau jika ingin mengikuti tampilan saya, silahkan salin kode dibawah ini:
{% codeblock style.css lang:css %}
/* Men-disabled spinners pada input number */
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
  padding: 10px;
}

.container {
  margin: 20px auto;
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 30px;
}

form {
  background-color: rgb(236, 236, 236);
  border-radius: 4px;
  padding: 15px 25px;
  width: 400px;
  border: 1px solid #333;
  box-sizing: border-box;
}

label {
  display: block;
}

input:not(#pesan, #hapus) {
  margin-bottom: 8px;
  width: 100%;
  border: 1px solid #333;
  padding: 3px 5px;
  outline: none;
}

input[disabled] {
  cursor: not-allowed;
  background-color: rgb(218, 218, 218);
}

.tombol {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 10px;
}

.tombol :is(#pesan, #hapus) {
  cursor: pointer;
}

.output {
  display: none;
  padding: 15px 25px;
  box-sizing: border-box;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
  width: 400px;
}

.output h2 {
  text-align: center;
}

.output.tampil {
  display: block;
  animation: fade 300ms;
}

.output p:last-child {
  color: rgb(32, 204, 55);
  font-weight: bold;
  margin-top: 30px;
}

@keyframes fade {
  0% {
    opacity: 0;
    transform: scale(0);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

.informasi {
  margin-top: 20px;
  color: red;
  display: flex;
  flex-direction: column;
}

.informasi span:first-child {
  margin-bottom: 10px;
  font-size: inherit;
}

.informasi span {
  font-size: 0.95em;
}

.informasi span > span {
  color: rgb(13, 182, 36);
  font-weight: bold;
}
{% endcodeblock %}

Maka tampilan sekarang akan jadi seperti ini:
{% img /img/tutorial/program-pemesanan-tiket/tampilan-css.png ' "Tampilan dengan CSS" "Tampilan dengan CSS" ' %}
<br>

Sekarang sudah mendingan untuk dilihat bukan tampilannya hahaha, sekarang lanjut ke bagian terpenting nya yaitu bagian javascript. Silahkan buat file javascript nya terlebih dahulu. Lalu kalian bisa salin kode dibawah ini, dengan catatan perhatikan **id** yang pada pada html kalian.
{% codeblock script.js lang:javascript %}
// Menyeleksi beberapa inputan textfield
const nama = document.getElementById("nama");
const destinasi = document.getElementById("destinasi");
const status = document.getElementById("status");
const jumlah = document.getElementById("jumlah");
const subtotal = document.getElementById("subtotal");
const diskon = document.getElementById("diskon");
const total = document.getElementById("total");
const cetakPesanan = document.querySelector(".output");

// Menyeleksi bagian tombol dan menjalnkan apabila tombol pesan di klik
const tombolPesan = document.getElementById("pesan");
tombolPesan.addEventListener("click", function (e) {
  e.preventDefault();

  // Pengecekan jika inputan-nya kosong atau tidak diisi
  if (nama.value == "" || destinasi.value == "" || status.value == "" || jumlah.value == "") {
    alert("Inputan nilai harus diisi terlebih dahulu!");
  } else {
    // Mengecek jika inputan nama nya sudah tidak kosong
    if (nama.value != "") {
      document.getElementById("namaOutput").innerText = nama.value;
    }

    // Mengecek inputan destinasi sesuai 3 Pilihan: Bandung, Jakarta dan Surabaya
    if (destinasi.value == "Bandung") {
      document.getElementById("destinasiOutput").innerText = destinasi.value;
    } else if (destinasi.value == "Jakarta") {
      document.getElementById("destinasiOutput").innerText = destinasi.value;
    } else if (destinasi.value == "Surabaya") {
      document.getElementById("destinasiOutput").innerText = destinasi.value;
    } else {
      alert("Pilihan Destinasi hanya Bandung, Jakarta dan Surabaya");
    }

    // Mengecek inputan status sesuai 2 pilihan: Dewasa dan Anak-anak
    if (status.value == "Dewasa") {
      document.getElementById("statusOutput").innerText = status.value;
    } else if (status.value == "Anak-anak") {
      document.getElementById("statusOutput").innerText = status.value;
    } else {
      alert("Pilihan status hanya untuk Dewasa dan Anak-anak saja!");
    }

    let harga = 0;
    let hargaPerTiket = document.getElementById("hargaTiket");

    // Mengecek antara status dan destinasi
    if (destinasi.value == "Bandung" && status.value == "Dewasa") {
      harga = 200000;
      hargaPerTiket.innerText = harga + " (Dua Ratus Ribu)";
    } else if (destinasi.value == "Bandung" && status.value == "Anak-anak") {
      harga = 100000;
      hargaPerTiket.innerText = harga + " (Seratus Ribu)";
    } else if (destinasi.value == "Jakarta" && status.value == "Dewasa") {
      harga = 300000;
      hargaPerTiket.innerText = harga + " (Tiga Ratus Ribu)";
    } else if (destinasi.value == "Jakarta" && status.value == "Anak-anak") {
      harga = 200000;
      hargaPerTiket.innerText = harga + " (Dua Ratus Ribu)";
    } else if (destinasi.value == "Surabaya" && status.value == "Dewasa") {
      harga = 400000;
      hargaPerTiket.innerText = harga + " (Empat Ratus Ribu)";
    } else if (destinasi.value == "Surabaya" && status.value == "Anak-anak") {
      harga = 300000;
      hargaPerTiket.innerText = harga + " (Tiga Ratus Ribu)";
    }

    // Mengecek inputan jumlah / tiket jika lebih dari 5 maka akan dikasih diskon, jika dibawah 5 tidak dapat diskon
    // Ubah dulu yang tipe data nya string menjadi number
    const convertToNumber = Number(jumlah.value);
    subtotal.value = harga * convertToNumber;
    document.getElementById("subtotalOutput").innerText = harga * convertToNumber;

    let discount = 0;
    if (convertToNumber >= 6) {
      discount = (subtotal.value / 100) * 15;
    } else if (convertToNumber <= 6) {
      discount = 0;
    }

    document.getElementById("jumlahOutput").innerText = convertToNumber;
    diskon.value = discount;
    document.getElementById("diskonOutput").innerText = discount;

    let totalPaid = subtotal.value - discount;
    total.value = totalPaid;
    document.getElementById("totalOutput").innerText = totalPaid;

    if (nama.value != "" || destinasi.value != "" || status.value != "" || jumlah.value != "") {
      // Mengecek jika user memasukkan nilai 0 pada inputan jumlah tiket
      if (jumlah.value == 0) {
        alert("Jumlah tiket tidak boleh 0");
        cetakPesanan.classList.remove("tampil");
      } else {
        cetakPesanan.classList.add("tampil");
      }
    }
  }
});

// Menyeleksi bagian tombol dan menjalankan apabila tombol hapus di klik
const hapus = document.getElementById("hapus");
hapus.addEventListener("click", function () {
  // Menghapus bagian output pada html
  if (nama.value == "" && destinasi.value == "" && status.value == "" && jumlah.value == "") {
    alert("Data masih kosong, apa yang mau dihapus?");
  } else if (nama.value != "" || destinasi.value != "" || status.value != "" || jumlah.value != "") {
    nama.value = "";
    destinasi.value = "";
    status.value = "";
    jumlah.value = "";
    subtotal.value = "";
    diskon.value = "";
    total.value = "";
    cetakPesanan.classList.remove("tampil");
  }
});
{% endcodeblock %}

Maka tampilan sekarang lebih menarik dimana kita bisa berinteraksi dengan pengguna
{% img /img/tutorial/program-pemesanan-tiket/tampilan-akhir.gif ' "Tampilan akhir program" "Tampilan akhir program" ' %}

Maka program form pemesanan tiket kita sudah berhasil dibuat dan berjalan dengan seharusnya, apabila ada kendala kamu bisa chat saya melalui Telegram [Rian](https://t.me/riann18).

Cukup sekian pembahasan dari saya mengenai pembuatan program pemesanan tiket yang sangat sederhana ini, saya yakin pasti ada cara yang lebih ringkas dan lebih baik lagi. Apabila ada pertanyaan silahkan ditanyakan lewat kolom komentar atau chat saya di Telegram.

Jika ingin melihat demo program kamu bisa lihat di [Demo-Program](http://form-pemesanan-tiket.surge.sh/). Terima kasih semua, semoga dapat bermanfaat :D