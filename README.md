# Commit 1 Reflection

Fungsi handle_connection menerima input "stream" yang merupakan suatu request yang dibuat browser. Lalu isi dari stream dimasukkan ke dalam sebuah buffer terlebih dahulu menggunakan class BufReader. Lalu objek BufReader dilakukan lines() yang mengiterasi baris-barisnya. 

Lalu dilakukan map(|result| result.unwrap()), dimana setiap elemen iterator (yang dianggap "result" pada method call ini) akan di unwrap (yang mengembalikan isi Some dari setiap iterasi). Method take_while(|line| !line.is_empty()) mengembalikan sebuah iterator baru dimana elemen-elemenya diambil dari iterator lama selama elemennya bukan emtpy. Lalu collect() membuat iteratornya menjadi sebuah collection. Pada line terakhir, isi collection diprint ke terminal.

Singkatnya, fungsi handle_connection disini mengeprint seluruh isi dari stream, ie request, yang dibuat browser.