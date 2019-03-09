# Git

![img3](img/git-logo.png)

## Mengenal Git dan Github
* **Git** adalah salah satu ***Version Control System*** (VCS) atau ***Source Control Manager*** (SCM) yang diciptakan oleh Linus Torvalds, pembuat Linux
* Fungsi utamanya adalah:
  * Mengatur versi dari source code
  * Mencatat setiap perubahan pada kode/file dengan menambahkan tanda/checkpoint ketika terjadi perubahan pada kode 
  * Mempermudah user untuk tetap mengetahui apa saja yang berubah dari source codenya
* Contoh pencatatan perubahan:
  ```
  01-04-2019 Soal shift 1 sementara
  02-04-2019 Mengubah fungsi baca file supaya lebih efektif
  03-04-2019 Menambah fitur back up file
  04-04-2019 Menambah fitur hapus file, soal shift 1 selesai
  ```
* Perhatikan ilustrasi di bawah ini:
  * Tanpa Git
  ![img1](img/revisi-tanpa-git.png)

  * Dengan Git
  ![img2](img/database-git.png)

* Kelebihan Git lainnya adalah sebagai pengatur proyek yang dikerjakan oleh beberapa orang, dimana orang-orang tersebut mengerjakan sebuah kode secara bersamaan
* **Github** adalah sebuah situs sharing code yang menggunakan **Git** sebagai SCM-nya. 

## Instalasi
Jika kamu menggunakan Linux berbasis Debian/Ubuntu, lakukan ini:
```bash
sudo apt-get update
sudo apt-get install git
```
Kemudian cek
```bash
git --version
```

## Bermain dengan Git dan Github
1. Buat akun di https://github.com/
2. Buat repository baru di akun Github kamu
   
   ![img4](img/ss2.png)

3. Sekarang buka terminal di PCmu, kita akan bermain Git menggunakan CLI
4. Setting Git terlebih dahulu
    ```bash
    git config --global user.name "<username>"
    git config --global user.email "<email@example.com>"
    ```
    p.s. Ubah <username> dan <email> sesuai akun Github yang sudah dibuat
5. Buka repository yang telah kamu buat tadi di Github, kemudian copy link untuk melakukan clone
   
   ![img5](img/ss1.png)

6. **Clone** repository tersebut
    ```bash
    git clone https://github.com/mocatfrio/basic-git.git
    ```

    ![img6](img/ss3.png)

7. Pindah ke folder yang telah terbuat otomatis dari hasil cloning
    ```bash
    cd basic-git
    ```
8. Lakukan modifikasi sesukamu pada source code/file. Kemudian coba cek status Git 
    ```bash
    git status
    ```
    Maka, akan keluar tampilan seperti ini:
    ```bash
    On branch master
    Your branch is up-to-date with 'origin/master'.
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)

      modified:   README.md

    Untracked files:
      (use "git add <file>..." to include in what will be committed)

      img/

    no changes added to commit (use "git add" and/or "git commit -a")
    ```
    p.s.
    * **modified** artinya file yang sudah ada dan sedang dimodifikasi
    * **Untracked files** artinya file yang baru ditambahkan (sebelumnya tidak ada)
9.  Tambahkan semua perubahan di atas (baik file yang baru maupun yang dimodifikasi) dengan melakukan **Add**
    ```bash
    git add -A
    ```
    p.s. `-A` artinya tambahkan semua file yang berubah, sehingga file yang tidak berubah, tidak akan ditambahkan

    Setelah melakukan add, coba cek kembali status git. Maka akan keluar seperti ini:
    ```bash
    $ git status
    On branch master
    Your branch is up-to-date with 'origin/master'.
    Changes to be committed:
      (use "git reset HEAD <file>..." to unstage)

      modified:   README.md
      new file:   img/1.png
      new file:   img/database-git.png
      new file:   img/git-logo.png
      new file:   img/gitkraken.gif
      new file:   img/revisi-tanpa-git.png
      new file:   img/ss1.png
      new file:   img/ss2.png
      new file:   img/ss3.png
      new file:   img/ss4.png
    ```
10. Selanjutnya, lakukan **Commit** pada file yang telah ditambahkan
    ```bash
    git commit -m "<masukkan pesan yang berfaedah yha>"
    ```
    p.s.
    * `-m` digunakan untuk memasukkan pesan commit. Usahakan pesannya jelas dan mudah dipahami, supaya bisa digunakan untuk mencari suatu perubahan
    * Contoh pesan yang baik
        ```bash
        git commit -m "mengubah fungsi baca file"
        git commit -m "menghapus fitur md5"
        git commit -m "menambah fitur hapus file setelah 5 detik"
        ```
    * Contoh pesan yang buruk
        ```bash
        git commit -m "duh capeq sekali yha"
        git commit -m "uhuy selesai tugasku"
        git commit -m "revisi"
        git commit -m "revisi terakhir bgt"
        ```
    
    Setelah di commit, maka akan keluar pesan seperti ini:
    ```bash
    [master b0b9dc8] uhuy
    10 files changed, 144 insertions(+), 2 deletions(-)
    rewrite README.md (100%)
    create mode 100644 img/1.png
    create mode 100644 img/database-git.png
    create mode 100644 img/git-logo.png
    create mode 100644 img/gitkraken.gif
    create mode 100644 img/revisi-tanpa-git.png
    create mode 100644 img/ss1.png
    create mode 100644 img/ss2.png
    create mode 100644 img/ss3.png
    create mode 100644 img/ss4.png
    ```
11. Terakhir, melakukan **Push**. Mudahnya, push ini untuk mengunggah file yang telah dimodifikasi di repository lokal (PC)
    ```bash
    git push
    ```
    Kamu akan diminta memasukkan username dan password akun Github. Jika berhasil, maka akan mengeluarkan output seperti ini:
    ```bash
    Counting objects: 13, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (13/13), done.
    Writing objects: 100% (13/13), 2.55 MiB | 34.00 KiB/s, done.
    Total 13 (delta 0), reused 0 (delta 0)
    To https://github.com/mocatfrio/basic-git.git
      862a012..b0b9dc8  master -> master
    ```
12. Suatu ketika, temanmu mengedit source code yang juga sedang kamu kerjakan. Maka kamu harus melakukan **Pull** untuk menyamakan source code yang sudah diedit temanmu dengan source code di PCmu. Mudahnya, pull ini untuk mengunduh file.
    ```bash
    git pull
    ```
    Jika proses pull berhasil, maka akan keluar output seperti ini:
    ```bash
    remote: Enumerating objects: 4, done.
    remote: Counting objects: 100% (4/4), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (3/3), done.
    From https://github.com/mocatfrio/basic-git
      04c0831..7cdc6af  master     -> origin/master
    Updating 04c0831..7cdc6af
    Fast-forward
    tes | 1 +
    1 file changed, 1 insertion(+)
    create mode 100644 tes
    ```

![img9](img/pushpull.jpg)

Ada suatu ketika, kita sudah memiliki proyek lama di PC. Kemudian, kita ingin meletakkan proyek tersebut ke Github. Maka, kita tinggal melakukan **Init** dan **Remote**. 
Caranya:
1. Pindah ke folder tempatmu meletakkan proyekmu di PC
    ```bash
    cd proyek-besar
    ```
2. Lakukan inisialisasi Git menggunakan **Init**. Init dilakukan untuk membuat repository Git lokal.
    ```bash
    git init
    ```
    ```bash
    Initialized empty Git repository in /home/mocatfrio/Documents/proyek-besar/.git/
    ```
3. Buatlah repository baru pada Github. Disarankan jangan mencentang **Initialize this repository with a README**.
4. Kembali ke terminal, lakukan **Remote** pada folder untuk menghubungkan repo lokal dan repo Githubmu
    ```bash
    git remote add origin https://github.com/mocatfrio/basic-git.git
    ```
5. Setelah mengkoneksikan repo lokal dan repo Github, kamu tinggal melakukan langkah-langkah yang sama seperti di atas, yaitu:
   ```bash
   git add -A
   git commit -m "<pesan berfaedah>"
   git push 
   #atau 
   git push -u origin master
   ```

Beberapa command di atas adalah command dasar Git yang wajib kamu ketahui. Namun, di dunia kerja nanti akan ada banyak command-command yang lebih dibutuhkan seperti **Branch**, **Merge**, **Checkout** dll.

![img10](img/ss5.png)

Ilustrasi dari gambar di atas: Ada 2 developer yang sedang membuat sebuah web, bernama Daus dan Hafara. Masing-masing membuat **Branch** sebagai tempat bekerja untuk membuat fitur masing-masing. Kenapa membuat branch? Supaya mereka berdua tidak bertabrakan ketika push dan pull source code. Setelah Hafara selesai bekerja, Daus melakukan **Merge** untuk menggabungkan pekerjaan Hafara dengan pekerjaannya. 

Jika kamu ingin belajar Git dengan cara menyenangkan, bisa mengunjungi https://git-school.github.io/visualizing-git/

## Tips
1. Untuk kamu yang tidak terbiasa dengan terminal, ada banyak sekali aplikasi Git Client yang tersedia, fitur yang ditawarkan pun beragam. Berikut ini salah satu contoh aplikasi Git Client berbasis GUI yang paling sering digunakan:

   * [GitKraken](https://www.gitkraken.com/)
     
      ![img8](img/gitkraken.gif)

   * [SourceTree](http://www.sourcetreeapp.com/)
   * [SmartGit](http://www.syntevo.com/smartgithg/)

2. Untuk menulis **Markdown (.md)** supaya lebih rapi dan menyenangkan, kamu bisa menggunakan tools **Visual Studio Code** dan menginstal beberapa Ekstensi (Ctrl+Shift+X), salah satunya adalah **Markdown Preview Enhanced**. Ekstensi ini berguna untuk memberikan preview dari markdown yang sedang ditulis.
   
    ![img7](img/ss4.png)

    Markdown cheatsheet: https://www.markdownguide.org/cheat-sheet/


## Referensi
* https://git-scm.com/book/id/v1/Dasar-dasar-Git
* https://git-school.github.io/visualizing-git/