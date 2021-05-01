---
title: Cara hosting website dengan Vercel dan Netlify
tags:
  - hosting
  - website
  - vercel
  - netlify
comments: true
category: tutorial
date: 2021-04-30 22:00:28
---


{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/hosting-vercel-dan-netlify.png '"Gambar Hero" "Gambar Hero"' %}

Bismillahirrahmanirrahim

Pembahasan kali ini, saya akan membagikan cara hosting website *static* kita menggunakan **Vercel** dan **Netlify** agar website yang kita buat dapat dipamerkan atau dilihat oleh orang lain. Dengan menggunakan Vercel ataupun Netlify kita dengan mudah mem-publish atau meng-hosting projek website kita hanya cukup menghubungkan repository yang ada di akun Github kita sendiri, sebenarnya selain Github ada juga seperti _Bitbucket_ dan _GitLab_, tapi disini aku jelaskan nya menggunakan Github ya. Sesuaikan aja sama yang kamu gunakan. Mari kita mulai :)

<!-- more -->

## Persyaratan
1. Mempunyai akun Github (Daftar apabila belum punya) [Daftar](https://github.com/join?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)
2. Download & Install software Git [Download Git](https://git-scm.com/downloads)
3. Mempunyai akun Vercel (Daftar apabila belum punya) [Daftar](https://vercel.com/signup)
4. Mempunyai akun Netlify (Daftar apabila belum punya) [Daftar](https://app.netlify.com/signup?_ga=2.110615685.181452518.1619753565-1767516604.1619753565) 

Setelah persyaratan nya sudah dilengkapi. Kita mulai dengan Github terlebih dahulu dimana kita membuat repository pada Github lalu di push projek lokal kita ke website nya Github menggunakan Git.

## Membuat Repository di Github
> Apabila sudah terdapat repository projek di akun Github kamu, langkah ini bisa kamu lewati.    

1. Apabila kamu sudah membuat akun Github, silahkan login dan masuk ke dalam halaman membuat repository baru [Buat repository baru](https://github.com/new)
2. Isikan form sesuai aturan, untuk bagian Public atau Private silahkan pilih public dan untuk _Initialize this repository with:_ abaikan saja dulu ya :"). Lalu tekan *Create Repository*.
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/create-repository-github.png '"Gambar repository baru buat" "Repository baru buat"'%}
3. Lalu akan ada tampilan perintah untuk push ke Github. Untuk itu kita lewati dulu, buka folder projek kamu lalu klik kanan pada mouse dan buka Git (Jika sudah menginstall nya).
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/folder-projek.jpg '"Gambar folder projek saya" "Folder projek saya"' %}
 - Di Windows jika klik kanan pada mouse buka yang bertuliskan **Git Bash Here** 
 - Di GNU/Linux bertuliskan **Open in Terminal** (Saya menggunakan Linux Mint)
 - Di MacOS saya kurang tau hehe (Mungkin sama dengan di GNU/Linux)
4. Kemudian cek versi git mu git dengan perintah:
{% codeblock %}
git --version
{% endcodeblock %}
 pada hari ini aku memakai git versi **2.31.1**. Selanjutnya saya asumsikan kamu sudah memberikan konfigurasi awal yaitu username dan email, apabila belum kamu bisa lihat di [Config Git](https://support.atlassian.com/bitbucket-cloud/docs/configure-your-dvcs-username-for-commits/) pada teks **To set your global username/email configuration:**
5. Oke, setelah configurasi git telah selesai ketikan perintah dibawah ini untuk push ke Github kita:
```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/usernameGithub/nama-repo-kamu.git
git push -u origin main
```
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/perintah-git.png '"Gambar Perintah Git" "Perintah Git saya"' %}
6. Silahkan refersh halaman browser Github nya
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/tampilan-github.png '"Gambar tampilan github setelah di push" "Tampilan setelah di push"' %}
7. Setelah itu? sudah, untuk membuat repository baru panjang juga ya :")

## Hosting dengan Vercel
1. Silahkan buka website [Vercel](https://vercel.com/dashboard) dan login, saya asumsikan kamu sudah daftar dan mempunyai akunnya
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/tampilan-awal-vercel.png '"Gambar dashboard Vercel" "Tampilan dashboard Vercel"' %}
2. Klik **New Project**
3. Lalu pilih **Continue with Github** dan akan meminta perizinan untuk menginstall vercel. Disini kamu disuruh pilih **All repositoriess** atau **Only select repositories**, disini saya All repositories. Lalu install, dan nanti akan ada repo yang telah kita buat sebelumnya di Github (repo projek kamu). Klik Import pada repo tersebut.
4. Lalu dibagian **Select Vercel Scope** disini saya memilih personal account, karena kita belum ada team dan ini hanya untuk latihan sederhana saja ya :")
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/import-projek.png '"Gambar Import Project" "Import Project"' %}
5. Lalu tekan continue
6. Berhubung website yang di deploy sederhana, kita tidak perlu ubah-ubah lagi. Langsung deploy aja. Dan tunggu.....
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/vercel-deploy.png '"Gambar website berhasil deploy" "Website berhasil deploy"' %}
7. Ini website yang telah saya buat dengan hosting Vercel di https://cara-hosting-vercel-dan-netlify.vercel.app/. Gimana website temen-temen, huff panjang juga yak hahaha. Kalo ada kendala bisa japri saya di Telegram [Rian](https://t.me/riann18) dan bisa juga pamerin website temen-temen semua.

Okee, deploy dengan vercel sudah kelar :". Selanjut nya kita deploy dengan netlify, let's go bruhhhh....

## Hosting dengan Netlify
1. Silahkan buka website [Netlify](https://www.netlify.com/) dan login, saya asumsikan kamu sudah daftar dan mempunyai akunnya
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/tampilan-awal-netlify.png '"Gambar dashboard Netlify" "Tampilan dashboard Netlify"' %}
2. Lalu tekan tombol **New site from Git**, setelah itu pilih Github (sesuaikan saja jika kamu pengguna selain Github)
3. Otomatis akan membuka popup browser baru untuk meminta **Authorized**
4. Setelah itu akan muncul repo yang tersimpan di Github kita, pilih repo projek kamu
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/netlify-deploy.png '"Gambar setting deploy Netlify" "Tampilan setting deploy Netlify"' %}
5. Karena kita hanya web static saja yang sederhana. Tekan langsung pada tombol **Deploy site** dibawah, lalu tunggu.....
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/netlify-deploy-berhasil.png '"Gambar deploy berhasil" "Tampilan deploy berhasil"' %}
6. Jika ada pesan **published** artinya website kita sudah dapat diakses oleh orang lain, namun disini nama website kita masih aneh
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/netlify-domain-acak.jpg '"Gambar domain acak Netlify" "Tampilan domain acak Netlify"' %}
7. Untuk mengatasi itu kamu klik bagian **Domain settings**, scroll sedikit kebawah klik bagian options dan **Edit site name**
{% img /img/tutorial/hosting-web-dengan-vercel-dan-netlify/edit-domain-netlify.png '"Gambar edit domain Netlify" "Tampilan edit domain Netlify"' %}
8. Edit nama domain nya sesuai keinginan kamu, lalu save
9. Dan domain akan berubah sesuai input yang kamu edit dan domain sebelumnya tidak bisa kamu akses lagi, kamu bisa cek website yang saya buat ini dengan hosting dari Netlify di https://cara-hosting-vercel-dan-netlify.netlify.app/

Hummmm.... Panjang juga ya? gapapa lah ya hehe, baca nya disesuai kebutuhan aja. Jika ingin hosting dengan Netlify bagian Vercel bisa kamu lewati begitupun sebaliknya jika kamu ingin hosting dengan Vercel. Mungkin itu saja yang dapat saya bagikan, apabila ada saran dan kritik berikan di kolom komentar atau japri saya via Telegram [Rian](https://t.me/riann18).

Terima kasih semua, semoga dapat bermanfaat :D


