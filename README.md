# Commit 1 Reflection

Fungsi handle_connection menerima input "stream" yang merupakan suatu request yang dibuat browser. Lalu isi dari stream dimasukkan ke dalam sebuah buffer terlebih dahulu menggunakan class BufReader. Lalu objek BufReader dilakukan lines() yang mengiterasi baris-barisnya. 

Lalu dilakukan map(|result| result.unwrap()), dimana setiap elemen iterator (yang dianggap "result" pada method call ini) akan di unwrap (yang mengembalikan isi Some dari setiap iterasi). Method take_while(|line| !line.is_empty()) mengembalikan sebuah iterator baru dimana elemen-elemenya diambil dari iterator lama selama elemennya bukan emtpy. Lalu collect() membuat iteratornya menjadi sebuah collection. Pada line terakhir, isi collection diprint ke terminal.

Singkatnya, fungsi handle_connection disini mengeprint seluruh isi dari stream, ie request, yang dibuat browser.

# Commit 2 Reflection

![commit_2_proof](assets/images/commit_2_proof.png)

Fungsi handle_connection disini tidak menggunakan variabel buf_reader dan http_request sehingga tidak perlu dijelaskan.

Singkatnya, fungsi handle_connection disini membuat sebuah response secara manual. Sebuah response memiliki format berikut:

```
HTTP-Version Status-Code Reason-Phrase CRLF
headers CRLF
message-body
```

Variabel status_line berisi versi http, kode status response, dan frase status kode. Lalu variabel contents membaca isi hello.html. Dan length merupakan panjang dari isi html yang sudah dibaca. Dan yang terakhir, variabel response merupakan respon yang dibuat secara manual, dimana berisi status respon, panjang isi (yang dimasukkan ke header respon), dan isi dari respon, dengan menggunakan format!().

Line terakhir mengirim kembali respon yang sudah dibuat ke client.