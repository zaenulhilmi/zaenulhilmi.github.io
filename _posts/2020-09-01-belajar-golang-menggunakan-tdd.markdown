---
layout: post
title:  "Belajar Golang Menggunakan Test Driven Development (TDD)"
date:   2020-09-01 05:55:18 +0700
categories: Golang 
---

Halo semua, pada kali ini kita akan membuat program sederhana dengan menggunakan bahasa pemrograman Golang.
Kita akan memulai dengan membuat fungsi serta sekaligus belajar tipe data string.
Kita akan membuat program dengan dibantu oleh test yang terlebih dahulu kita buat. Cara ini disebut dengan nama 
*Test Driven Development*.

Untuk memulai, kita perlu membuat sebuah file baru dengan nama *greeting_test.go*. Nama file test yang akan kita buat,

{% highlight golang linenos %}
package main

import "testing"

func TestGreeting(t *testing.T) {
	actual := Greeting()
	expect := "Hello, world!"

	if actual != expect {
		t.Errorf("Actual %s, expect %s", actual, expect)
	}
}
{% endhighlight %}

Kita bisa menjalankan test ini dengan menggunakan ```go test``` di terminal. Hasil dari test ini akan gagal sebagai berikut:
Namun, tidak perlu khawatir. Kita memang perlu memastikan terlebih dahulu kalau test yang kita buat akan gagal.
```
# golang_with_test_test [golang_with_test.test]
./greeting_test.go:6:12: undefined: Greeting
FAIL    golang_with_test [build failed]
```

Setelah mengetahui tentang test kita yang gagal, perlu diperhatikan pesan error yang ada. Kali ini, *undefined: Greeting*
yang artinya, kita telah menggunakan fungsi greeting (baris 6 di greeting_test.go) namun fungsi tersebut belum dibuat.

Langkah selanjutnya yang akan kita lakukan adalah membuat fungsi greeting. Kita akan memulainya dengan membuat file baru 
dengan nama *greeting.go*.


{% highlight golang linenos %}
package main

func Greeting() string {
	return ""
}
{% endhighlight %}

Kita perlu menjalankan ```go test``` lagi di terminal. Hasilnya akan gagal, namun kita sudah memperbaiki error di mana 
fungsi Greeting belum dibuat. 
```
--- FAIL: TestGreeting (0.00s)
    greeting_test.go:10: Actual , expect Hello, world!
FAIL
exit status 1
FAIL    golang_with_test        0.002s
```
Sekarang, error-nya sudah sesuai dengan ekspektasi yang kita inginkan. Di ```greeting_test.go``` kita menginginkan kalau
fungsi ```Greeting``` akan menampilkan "Hello world!" namun sekarang tidak ada apa-pun. Sudah tepat, sekarang kita perlu 
memperbaiki fungsi ```Greeting``` kita kembali.

{% highlight golang linenos %}
package main

func Greeting() string {
	return "Hello, world!"
}
{% endhighlight %}

Setelah kita memperbaiki fungsi ```Greeting``` seperti di atas. Maka hasil dari eksekusi kita dengan menggunakan ```go test```
adalah sebagai berikut:
``` 
PASS
ok      golang_with_test        0.001s
```

Sudah PASS. Selamat!! kita sudah berhasil membuat test dan implementasi dari hello world.

