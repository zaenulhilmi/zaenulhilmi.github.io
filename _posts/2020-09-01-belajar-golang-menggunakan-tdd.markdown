---
layout: post
title:  "Belajar Golang Menggunakan Test Driven Development (TDD)"
date:   2020-09-01 05:55:18 +0700
categories: Golang 
---
Pada kesempatan kali ini, kita akan belajar bahasa pemrograman Golang dengan menerapkan Test Driven Development.
Kita tidak hanya akan membuat implementasi dari suatu program, tapi juga akan membuat test terlebih dahulu.

"Lah, Ngapain ditest dulu sebelum dibuat. Bukannya kita langsung buat aja programnya dulu setelah itu baru ditest?"

Jadi, test yang akan kita buat ini akan dibuat menjadi kode yang selanjutnya bisa dieksekusi kapanpun kita inginkan. 
Kelebihannya adalah feedback bisa menjadi lebih cepat karena selanjutnya kode test kita sendiri yang akan mengecek apakah kode kita sudah benar atau belum.
Selain itu, kita juga bisa membagi kode kita menjadi bagian-bagian kecil sehingga gampang untuk dirawat, memaksa kita untuk membuat kode yang optimal dan efisien serta 
dengan adanya test maka ketika ada perubahan nanti kita tidak perlu khawatir akan mempengaruhi fitur lain. Fitur-fitur yang sudah ada
sudah memiliki test tersendiri, karena itu jika dari pembuatan fitur baru terjadi kerusakan pada test yang sudah lama maka kita bisa langsung mengetahui hanya dengan menjalankan test yang sudah ada.

Oke, untuk memulai pelajaran kita ini, kita akan membuat program yang akan menampilkan "Hello world".

```golang
package main

import "fmt"

func main() {
    fmt.Println("Hello world")
}
```

Program di atas kita buat tanpa menggunakan test. Kita bisa mengetest hasilnya secara manual dengan cara menjalankan programnya. 
Ketika dijalankan maka hasilnya adalah tulisan "Hello world" di terminal.

Kita bisa memperbaiki kode di atas dengan mengganti literal "Hello world" dengan fungsi. Contohnya seperti berikut:
 
```golang
package main

import "fmt"

func main() {
    fmt.Println(Greeting())
}
```

Sekarang, fungsi 