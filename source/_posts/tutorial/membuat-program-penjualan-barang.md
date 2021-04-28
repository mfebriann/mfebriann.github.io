---
title: Membuat Program Penjualan Barang dengan Javascript
tags:
  - html
  - css
  - javascript
comments: true
categories: tutorial
date: 2021-04-27 09:53:14
---


![Tampilan Program](/img/tutorial/membuat-program-penjualan-barang.png)

Bismillahirrahmanirrahim

Sebelumnya ada seseorang yang nge-chat saya di Telegram mengenai tugas nya yang diberikan dosen nya. Dimana tugas nya adalah membuat program penjualan barang yang cara kerja nya adalah ketika kita meng-centang atau menge-check nama barang artinya kita menjual barang tersebut dan jika kita memasukkan nilai jumlah beli, sama saja seperti dikali sesuai yang kita masukkan di kolom input. Hemm bingung ya?, gini deh. 

<!-- more -->

Jadi disini terdapat 3 barang, yaitu Handphone, Laptop, dan Komputer. Dimana masing-masing barang terdapat nilai atau harga barang tersebut adalah.
1. Handphone = 1200000 (1,2 Juta Rupiah)
2. Laptop = 5000000 (5 Juta Rupiah)
3. Komputer = 3000000 (3 Juta Rupiah)

Dimana nanti akan dikalikan dengan input-an pada jumlah beli. Yang nanti nya ketika kita meng-klik tombol <b>Proses</b> akan tampil hasil nya input-an Total Harga yang dimana akan dilakukan penjumlahan pada masing-masing barang yang dipilih, Jadi cara kerja nya jika kita menjual Laptop dan Komputer misalnya, kita meng-centang atau memilih pada barang tersebut lalu kita masukkan jumlah beli 2 pada input-an jumlah beli laptop dan komputer, itu artinya 5000000 (Harga Laptop) * 2 = 10000000 (10 Juta Rupiah) dan 3000000 (Harga Komputer) * 2 = 6000000 (6 Juta Rupiah). 

Hasil dari perkalian barang ini akan dilakukan penjumalahan 10000000 (10 Juta Rupiah) + 6000000 (6 Juta Rupiah) = 16000000 (16 Juta Rupiah). Yang nanti 16000000 akan ditampilkan pada input-an Total Harga.

Jadi, studi kasus disini adalah
1. Apabila kita memasukkan pada jumlah beli akan tetapi tidak meng-centang atau memilih barang nya, akan menampilkan pesan pemberitahuan
2. Apabila ada ada barang yang tidak ikut tercentang maka tidak akan ikut dilakukan nya penjumlahan
3. Apabila barang yang sudah terpilih lalu dimasukkan nilai jumlah beli, maka harga barang tersebut akan dikalikan sesuai nilai yang dimasukkan
4. Apabila ada barang yang dipilih tapi belum memasukkan nilai jumlah beli, maka Total Harga akan 0
5. Apabila menekan tombol <b>Reset</b> maka semua akan kembali kekeadaan awal

Kalo teman-teman sudah paham tentang studi kasus nya, coba dibuat sendiri dan hasilnya jangan lupa kirim ke saya via Telegram [Rian](https://t.me/riann18).


Oke, let's go kita buat bareng-bareng aja ya, pertama bikin terlebih dahulu file HTML nya, disini file html saya bernama **index.html**, selanjut nya buat file CSS kita, disini saya buat nama file nya **style.css** dan file Javascript yang dimana saya kasih nama **main.js**. 
> Perhatikan Ekstensi setelah titik (.) pada penamaan file

Setelah membuat ketiga file tersebut, selanjutnya kita menuliskan kode nya, untuk kode pada HTML nya:
{% codeblock index.html lang:html %}
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>PROGRAM PENJUALAN BARANG</title>
	</head>
	<body>
		<form name="form">
			<table>
				<tr>
					<th colspan="2">PROGRAM PENJUALAN BARANG</th>
				</tr>
				<tr>
					<th>NAMA BARANG</th>
					<th>JUMLAH BELI</th>
				</tr>
				<tr>
					<td>
						<label> <input type="checkbox" class="handphone" /> </label>Handphone
					</td>
					<td><input type="text" class="jumlahBeliHp" /></td>
				</tr>
				<tr>
					<td>
						<label> <input type="checkbox" class="laptop" /> </label>Laptop
					</td>
					<td><input type="text" class="jumlahBeliLaptop" /></td>
				</tr>
				<tr>
					<td>
						<label> <input type="checkbox" class="komputer" /> </label>Komputer
					</td>
					<td><input type="text" class="jumlahBeliKomputer" /></td>
				</tr>
				<tr>
					<td>
						<label> TOTAL HARGA </label>
					</td>
					<td><input type="text" id="total" disabled /></td>
				</tr>
				<tr>
					<td><input type="button" value="Proses" /></td>
					<td><input type="reset" value="Reset" /></td>
				</tr>
			</table>
		</form>

		<p>
			Catatan: <br />
			Harga 1 Handphone = 1200000, <br />
			Harga 1 Laptop = 5000000, <br />
			Harga 1 Komputer = 3000000
		</p>
	</body>
</html>
{% endcodeblock %}

Setelah itu tuliskan kode berikut pada CSS kalian:
{% codeblock style.css lang:css %}
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap');

* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

			
body {
    font-family: 'Montserrat', sans-serif;
    background-color: #555;
}

table {
    padding: 15px;
    margin: 40px auto;
    color: #333;
    width: 550px;
    border: 4px solid rgb(50, 224, 79);
    background-color: #fff;
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.2);
}

th,
td {
    border: 2px solid #333;
}

th,
td {
    padding: 10px;
}

input[type='text'] {
    width: 100%;
    padding: 5px;
}

input[type='button'],
input[type='reset'] {
    padding: 5px 10px;
    margin: auto;
    display: block;
}

p {
    color: #fff;
    width: 550px;
    margin: auto;
    font-weight: 700;
}
{% endcodeblock %}

Dan yang terakhir adalah javascript, silahkan kalian tulis kode berikut pada file javascript kalian:
{% codeblock main.js lang:javascript %}
// Untuk HP
let hp = document.querySelector('.handphone');
const jmlHp = document.querySelector('.jumlahBeliHp');

// Untuk Laptop
let laptop = document.querySelector('.laptop');
const jmlLaptop = document.querySelector('.jumlahBeliLaptop');

// Untuk Komputer
let komputer = document.querySelector('.komputer');
const jmlKomputer = document.querySelector('.jumlahBeliKomputer');

// Hasil
const hasil = document.querySelector('#total');

// Ketika tombol proses ditekan
const proses = document.querySelector('input[type="button"]');
proses.addEventListener('click', function () {
    // Kalo barang gak ada yang di check tampilkan alert
    if (hp.checked === false && laptop.checked === false && komputer.checked === false) {
        alert('Check barang terlebih dahulu!');
    }

    // Kalo barang hp di check maka akan dikali dengan jumlah barang yang di beli
    let hargaHp = 1200000; // Harga awal HP, sudah kita tentukan
    if (hp.checked === true) {
        hargaHp *= jmlHp.value;
        hasil.value = hargaHp;
    }

    // Kalo barang laptop di check maka akan dikali dengan jumlah barang yang di beli
    let hargaLaptop = 5000000; // Harga awal Laptop, sudah kita tentukan
    if (laptop.checked === true) {
        hargaLaptop *= jmlLaptop.value;
        hasil.value = hargaLaptop;
    }

    // Kalo barang komputer di check maka akan dikali dengan jumlah barang yang di beli
    let hargaKomputer = 3000000; // Harga awal Komputer, sudah kita tentukan
    if (komputer.checked === true) {
        hargaKomputer *= jmlKomputer.value;
        hasil.value = hargaKomputer;
    }

    // Kalo semua barang di check maka akan dijumlahkan harga nya dan ditampilkan ke hasil value atau ke bagian input Total Harga
    if (hp.checked === true && laptop.checked === true && komputer.checked === true) {
        hasil.value = hargaHp + hargaLaptop + hargaKomputer;

        // Kalo yang di check cuman barang hp dan laptop saja, maka akan dijumlahkan harga hp dan laptop saja
    } else if (hp.checked === true && laptop.checked === true) {
        hasil.value = hargaHp + hargaLaptop;

        // Kalo yang di check cuman barang hp dan komputer saja, maka akan dijumlahkan harga hp dan komputer saja
    } else if (hp.checked === true && komputer.checked === true) {
        hasil.value = hargaHp + hargaKomputer;

        // Kalo yang di check cuman barang laptop dan komputer saja, maka akan dijumlahkan harga laptop dan komputer saja
    } else if (laptop.checked === true && komputer.checked === true) {
        hasil.value = hargaLaptop + hargaKomputer;
    }
});
{% endcodeblock %}

Coba kalian jalankan di browser, apakah sudah sesuai atau belum. Jika ada error silahkan tanya di kolom komentar atau japri via Telegram [Rian](https://t.me/riann18). Mungkin itu saja yang bisa saya bagikan, mungkin juga teman-teman bisa membuat nya lebih ringkas lagi atau di refactoring agar kode nya terlihat pendek dan bersih. 

Saya juga masih belajar tentang Javascript ini, makanya saya senang ada pertanyaan yang mengacu kepada javascript apalagi ada studi kasus nya membuat saya terus mengasah kemampuan tentang javascript ini.

Apabila ada kekurangan mohon dimaafkan :")

Untuk Melihat Demo Program nya **[Demo-Program](https://codepen.io/mfebriann/pen/rNjRZVJ)**

