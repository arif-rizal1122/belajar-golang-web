### PENGENALAN WEB 

1. Saat ini web digunakan oleh jutaan, bahkan mungkin milyaran orang setiap hari
2. Dengan web, kita bisa melakukan belajar online, mendengarkan musik online, nonton video online, belanja online, sampai memesan makanan secara online
3. Namun perlu diperhatikan, Web bukanlah Internet

 == INTERNET

1. Internet adalah mekanisme komunikasi antar komputer
2. Awal internet ada, untuk komunikasi antar komputer, kita membutuhkan jaringan kabel telepon
Namun sekarang, semenjak berjamurnya jaringan wifi dan sejenisnya, komunikasi antar komputer menjadi lebih cepat dan mudah

 == WEB

1. Web merupakan kumpulan informasi yang tersedia dalam sebuah komputer yang terkoneksi secara terus menerus melalui internet
2. Web bisa berisi informasi dalam bentuk apapun, seperti teks, gambar, audio, video dan lain-lain
3. Web berjalan di aplikasi yang bernama Web Server, yaitu aplikasi yang digunakan untuk menyimpan dan menyampaikan isi informasi Web

 == WEB HOST

1. Pemilik Web, biasanya tidak menjalankan aplikasi Web Server di komputer pribadi nya
2. Biasanya mereka akan menyewa komputer di tempat penyedia data center (kumpulan komputer) yang terjamin keandalan dan kecepatan koneksi internetnya
3. Pihak penyedia komputer untuk Web Server biasa disebut Web Host

 == DOMAIN

1. Saat komputer Web terhubung ke internet, biasanya dia memiliki alamat
2. Alamat ini bernama ip address, formatnya misal nya 172.217.194.94
3. Karena alamat ip address sangat menyulitkan untuk diingat
4. Untung saja ada yang namanya nama domain
5. Nama domain adalah alamat yang bisa digunakan sebagai alias ke ip address
6. Misal seperti google.co.id, blibli.com, dan lain-lain
7. Dengan nama domain, sebagai manusia kita akan mudah mengingat dibandingkan ip address
8. Namun, saat kita menggunakan nama domain, sebenarnya komputer tetap akan mengakses web menggunakan alamat ip address

 == WEB BROWSER

1. Jika Web Server adalah aplikasi yang digunakan untuk menyimpan informasi Web
2. Web Browser adalah aplikasi yang digunakan untuk mengakses Web melalui internet
3. Kita bisa saja mengakses Web secara langsung tanpa bantuan Web Browser, namun Web Server hanya akan memberikan informasi bahasa mesin seperti HTML, JavaScript, CSS, Gambar, Video dan lain-lain
4. Dengan menggunakan Web Browser, semua bahasa mesin tersebut bisa ditampilkan secara visual sehingga kita bisa menyerap informasinya dengan lebih mudah



### CLIENT AND SERVER


1. Web adalah aplikasi berbasis Client dan Server, sekarang pertanyaannya, apa itu Client dan Server?
2. Sederhananya client server merupakan konsep arsitektur aplikasi yang menghubungkan dua pihak, sistem client dan sistem server
3. Sistem client dan sistem server yang saling berkomunikasi melalui jaringan komputer, internet, atau juga bisa di komputer yang sama


 == TUGAS CLIENT DAN SERVER

1. Aplikasi Client bertugas mengirim request ke Server, dan menerima response dari Server
2. Sedangkan, aplikasi Server bertugas menerima request dari Client, memproses data, dan mengembalikan hasil proses data ke Client

 == KEUNTUNGAN CLIENT DAN SERVER

1. Perubahan aplikasi bisa dilakukan dengan mudah di server, tanpa harus membuat perubahan di client, apalagi jika client nya di lokasi yang sulit dijangkau
2. Bisa digunakan oleh banyak client pada saat yang bersamaan, walaupun server tidak banyak
3. Bisa diakses dari mana saja, asal terhubung satu jaringan dengan server



 == CONTOH CLIENT DAN SERVER

1. Web adalah salah satu contoh arsitektur client server
2. Aplikasi yang bertugas sebagai Client adalah Web Browser (Chrome, Firefox, Opera, Edge dan lain-lain)
3. Aplikasi yang bertugas sebagai Server adalah Web Server, dimana di dalam web server terdapat kode program Web kita




_____________ GOLANG WEB _______________

1. Go-Lang saat ini populer dijadikan salah satu pilihan bahasa pemrograman untuk membuat Web, terutama Web API (Backend)
2. Selain itu, di Go-Lang juga sudah disediakan package untuk membuat Web, bahkan di sertakan pula package untuk implementasi unit testing untuk Web
3. Hal ini menjadikan pembuatan Web menggunakan Go-Lang lebih mudah, karena tidak butuh menggunakan library atau framework


== CARA KERJA go-LANG WEB

1. Web Browser akan melakukan HTTP Request ke Web Server
2. Golang menerima HTTP Request, lalu mengeksekusi request tersebut sesuai dengan yang diminta.
3. Setelah melakukan eksekusi request, Golang akan mengembalikan data dan di render sesuai dengan kebutuhannya, misal HTML, CSS, JavaScript dan lain-lain
4. Golang akan mengembalikan content hasil render tersebut tersebut sebagai HTTP Response ke Web Browser
Web Browser menerima content dari Web Server, lalu me-render content tersebut sesuai dengan tipe content nya 


 == PACKAGE net/http

1. Pada beberapa bahasa pemrograman lain, seperti Java misalnya, untuk membuat web biasanya dibutuhkan tambahan library atau framework
2. Sedangkan di Go-Lang sudah disediakan package untuk membuat web bernama package net/http
3. Sehingga untuk membuat web menggunakan Go-Lang, kita tidak butuh lagi library tambahan, kita bisa menggunakan package yang sudah tersedia
Walaupun memang saat kita akan membuat web dalam skala besar, direkomendasikan menggunakan framework karena beberapa hal sudah dipermudah oleh web framework
4. Namun pada course ini, kita akan fokus menggunakan package net/http untuk membuat web nya, karena semua framework web Go-Lang akan menggunakan net/http sebagai basis dasar framework nya

 

    ~~ server

1. Server adalah struct yang terdapat di package net/http yang digunakan sebagai representasi Web Server di Go-Lang
Untuk membuat web, kita wajib membuat Server
2. Saat membuat data Server, ada beberapa hal yang perlu kita tentukan, seperti host dan juga port tempat dimana Web kita berjalan
3. Setelah membuat Server, kita bisa menjalankan Server tersebut menggunakan function ListenAndServe()

   ~~ hendler

1. Server hanya bertugas sebagai Web Server, sedangkan untuk menerima HTTP Request yang masuk ke Server, kita butuh yang namanya Handler
2. Handler di Go-Lang di representasikan dalam interface, dimana dalam kontraknya terdapat sebuah function bernama ServeHTTP() yang digunakan 
3. sebagai function yang akan di eksekusi ketika menerima HTTP Request

     = hendler func

1. Salah satu implementasi dari interface Handler adalah HandlerFunc
2. Kita bisa menggunakan HandlerFunc untuk membuat function handler HTTP



### SERVEMUX

1. Saat membuat web, kita biasanya ingin membuat banyak sekali endpoint URL
HandlerFunc sayangnya tidak mendukung itu
Alternative implementasi dari Handler adalah ServeMux
ServeMux adalah implementasi Handler yang bisa mendukung multiple endpoint


    ~~ url pattern dlm servemux

1. URL Pattern dalam ServeMux sederhana, kita tinggal menambahkan string yang ingin kita gunakan sebagai  endpoint, tanpa perlu memasukkan domain web kita
2. Jika URL Pattern dalam ServeMux kita tambahkan di akhirnya dengan garis miring, artinya semua url tersebut akan menerima path dengan awalan tersebut, misal /images/ artinya akan dieksekusi jika endpoint nya /images/, /images/contoh, /images/contoh/lagi
Namun jika terdapat URL Pattern yang lebih panjang, maka akan diprioritaskan yang lebih panjang, misal jika terdapat URL /images/ dan /images/thumbnails/, maka jika mengakses /images/thumbnails/ akan mengakses /images/thumbnails/, bukan /images



### REQUEST 


1. Request adalah struct yang merepresentasikan HTTP Request yang dikirim oleh Web Browser
2. Semua informasi request yang dikirim bisa kita dapatkan di Request
3. Seperti, URL, http method, http header, http body, dan lain-lain


### HTTP TEST

1. Go-Lang sudah menyediakan package khusus untuk membuat unit test terhadap fitur Web yang kita buat
2. Semuanya ada di dalam package net/http/httptest https://golang.org/pkg/net/http/httptest/ 
3. Dengan menggunakan package ini, kita bisa melakukan testing handler web di Go-Lang tanpa harus menjalankan aplikasi web nya
5. Kita bisa langsung fokus terhadap handler function yang ingin kita test


    == http.NewRequest()

1. NewRequest(method, url, body) merupakan function yang digunakan untuk membuat http.Request
2. Kita bisa menentukan method, url dan body yang akan kita kirim sebagai simulasi unit test
3. Selain itu, kita juga bisa menambahkan informasi tambahan lainnya pada request yang ingin kita kirim, seperti header, cookie, dan lain-lain

   == http.NewRecorder()

1. httptest.NewRecorder() merupakan function yang digunakan untuk membuat ResponseRecorder
2. ResponseRecorder merupakan struct bantuan untuk merekam HTTP response dari hasil testing yang kita lakukan


### QUERY PARAMETER

    Query parameter adalah salah satu fitur yang biasa kita gunakan ketika membuat web
    Query parameter biasanya digunakan untuk mengirim data dari client ke server
    Query parameter ditempatkan pada URL
    Untuk menambahkan query parameter, kita bisa menggunakan ?nama=value pada URL nya

    == url.URL

    Dalam parameter Request, terdapat attribute URL yang berisi data url.URL
    Dari data URL ini, kita bisa mengambil data query parameter yang dikirim dari client dengan menggunakan method Query() yang akan mengembalikan map

    == multiple query parameter

    1. Dalam spesifikasi URL, kita bisa menambahkan lebih dari satu query parameter
    2. Ini cocok sekali jika kita memang ingin mengirim banyak data ke server, cukup tambahkan query parameter lainnya
    3. Untuk menambahkan query parameter, kita bisa gunakan tanda & lalu diikuti dengan query parameter berikutnya

    == multiple value query parameter

    1. Sebenarnya URL melakukan parsing query parameter dan menyimpannya dalam map[string][]string
    2. Artinya, dalam satu key query parameter, kita bisa memasukkan beberapa value
    3. Caranya kita bisa menambahkan query parameter dengan nama yang sama, namun value berbeda, misal :
    name=Eko&name=Kurniawan


### HEADER


1. Selain Query Parameter, dalam HTTP, ada juga yang bernama Header
2. Header adalah informasi tambahan yang biasa dikirim dari client ke server atau sebaliknya
3. Jadi dalam Header, tidak hanya ada pada HTTP Request, pada HTTP Response pun kita bisa menambahkan informasi header
4. Saat kita menggunakan browser, biasanya secara otomatis header akan ditambahkan oleh browser, seperti informasi browser, jenis tipe content yang dikirim dan diterima oleh browser, dan lain-lain


    == request header

1. Untuk menangkap request header yang dikirim oleh client, kita bisa mengambilnya di Request.Header
2. Header mirip seperti Query Parameter, isinya adalah map[string][]string
3. Berbeda dengan Query Parameter yang case sensitive, secara spesifikasi, Header key tidaklah case sensitive

  == response header

1. Sedangkan jika kita ingin menambahkan header pada response, kita bisa menggunakan function ResponseWriter.Header()  



### FORM POST

1. Saat kita belajar HTML, kita tahu bahwa saat kita membuat form, kita bisa submit datanya dengan method GET atau POST
2. Jika menggunakan method GET, maka hasilnya semua data di form akan menjadi query parameter
3. Sedangkan jika menggunakan POST, maka semua data di form akan dikirim via body HTTP request
4. Di Go-Lang, untuk mengambil data Form Post sangatlah mudah
  
   == request form post

1. Semua data form post yang dikirim dari client, secara otomatis akan disimpan dalam attribute Request.PostForm
2. Namun sebelum kita bisa mengambil data di attribute PostForm, kita wajib memanggil method Request.ParseForm() terlebih dahulu, method ini digunakan untuk melakukan parsing data body apakah bisa di parsing menjadi form data atau tidak, jika tidak bisa di parsing, maka akan menyebabkan error

### RESPONSE CODE


2. Dalam HTTP, terdapat yang namanya response code
2. Response code merupakan representasi kode response
3. Dari response code ini kita bisa melihat apakah sebuah request yang kita kirim itu sukses diproses oleh server atau gagal
4. Ada banyak sekali response code yang bisa kita gunakan saat membuat web
https://developer.mozilla.org/en-US/docs/Web/HTTP/Status


### MENGUBAH RESPONSE CODE 

1. Secara default, jika kita tidak menyebutkan response code, maka response code nya adalah 200 OK
2. Jika kita ingin mengubahnya, kita bisa menggunakan function ResponseWriter.WriteHeader(int)
3. Semua data status code juga sudah disediakan di Go-Lang, jadi kita ingin, kita bisa gunakan variable yang sudah disediakan : https://github.com/golang/go/blob/master/src/net/http/status.go 


### COOKIE 


1. HTTP merupakan stateless antara client dan server, artinya server tidak akan menyimpan data apapun untuk mengingat setiap request dari client
Hal ini bertujuan agar mudah melakukan scalability di sisi server
2. Lantas bagaimana caranya agar server bisa mengingat sebuah client? Misal ketika kita sudah login di website, server otomatis harus tahu jika client tersebut sudah login, sehingga request selanjutnya, tidak perlu diminta untuk login lagi
Untuk melakukan hal ini, kita bisa memanfaatkan Cookie
  
   -- cookie

1. Cookie adalah fitur di HTTP dimana server bisa memberi response cookie (key-value) dan client akan menyimpan cookie tersebut di web browser
2. Request selanjutnya, client akan selalu membawa cookie tersebut secara otomatis
3. Dan server secara otomatis akan selalu menerima data cookie yang dibawa oleh client setiap kalo client mengirimkan request
 
   -- membuat cookie

1. Cookie merupakan data yang dibuat di server dan sengaja agar disimpan di web browser
2. Untuk membuat cookie di server, kita bisa menggunakan function http.SetCookie()


### FILE SERVER

1. Go-Lang memiliki sebuah fitur yang bernama FileServer
2. Dengan ini, kita bisa membuat Handler di Go-Lang web yang digunakan sebagai static file server
3. Dengan menggunakan FileServer, kita tidak perlu manual me-load file lagi
4. FileServer adalah Handler, jadi bisa kita tambahka ke dalam http.Server atau http.ServeMux


  -- 404 Not Found


1. Jika kita coba jalankan, saat kita membuka misal /static/index.js, maka akan dapat error 404 Not Found
Kenapa ini terjadi?
2. Hal ini dikarenakan FileServer akan membaca url, lalu mencari file berdasarkan url nya, jadi jika kita membuat /static/index.js, maka FileServer akan mencari ke file /resources/static/index.js
3. Hal ini menyebabkan 404 Not Found karena memang file nya tidak bisa ditemukan
4. Oleh karena itu, kita bisa menggunakan function http.StripPrefix() untuk menghapus prefix di url


### GO LANG EMBED


1. Di Go-Lang 1.16 terdapat fitur baru yang bernama Go-Lang embed
2. Dalam Go-Lang embed kita bisa embed file ke dalam binary distribution file, hal ini mempermudah sehingga kita tidak perlu meng-copy static file lagi
3. Go-Lang Embed juga memiliki fitur yang bernama embed.FS, fitur ini bisa diintegrasikan dengan FileServer


   -- 404 Not Found


1. Jika kita coba jalankan, dan coba buka /static/index.js, maka kita akan mendapatkan error 404 Not Found
2. Kenapa ini terjadi? Hal ini karena di Go-Lang embed, nama folder ikut menjadi nama resource nya, misal resources/index.js, jadi untuk mengaksesnya kita perlu gunakan URL /static/resources/index.js
3. Jika kita ingin langsung mengakses file index.js tanpa menggunakan resources, kita bisa menggunakan function fs.Sub() untuk mendapatkan sub directory



### SERVEFILE

1. Kadang ada kasus misal kita hanya ingin menggunakan static file sesuai dengan yang kita inginkan
2. Hal ini bisa dilakukan menggunakan function http.ServeFile()
3. Dengan menggunakan function ini, kita bisa menentukan file mana yang ingin kita tulis ke http response


    -- golang embed

1. Parameter function http.ServeFile hanya berisi string file name, sehingga tidak bisa menggunakan Go-Lang Embed
2. Namun bukan berarti kita tidak bisa menggunakan Go-Lang embed, karena jika untuk melakukan load file, kita hanya butuh menggunakan package fmt dan ResponseWriter saja



### TEMPLATE HTML

   -- web dinamis

1. Sampai saat ini kita hanya membahas tentang membuat response menggunakan String dan juga static file
2. Pada kenyataannya, saat kita membuat web, kita pasti akan membuat halaman yang dinamis, bisa berubah-ubah sesuai dengan data yang diakses oleh user
3. Di Go-Lang terdapat fitur HTML Template, yaitu fitur template yang bisa kita gunakan untuk membuat HTML yang dinamis


   -- html template

1. Fitur HTML template terdapat di package html/template
2. Sebelum menggunakan HTML template, kita perlu terlebih dahulu membuat template nya
3. Template bisa berubah file atau string
4. Bagian dinamis pada HTML Template, adalah bagian yang menggunakan tanda {{  }}

   -- membuat template

1. Saat membuat template dengan string, kira perlu memberi tahu nama template nya
2. Dan untuk membuat text template, cukup buat text html, dan untuk konten yang dinamis, kita bisa gunakan tanda {{.}}, contoh :
3. <html><body>{{.}}</body></html>

   -- template dari file

1. Selain membuat template dari string, kita juga bisa membuat template langsung dari file
2. Hal ini mempermudah kita, karena bisa langsung membuat file html
3. Saat membuat template menggunakan file, secara otomatis nama file akan menjadi nama template nya, misal jika kita punya file simple.html, maka nama template nya adalah simple.html


   -- template directory

1. Kadang biasanya kita jarang sekali menyebutkan file template satu persatu
2. Alangkah baiknya untuk template kita simpan di satu directory
3. Go-Lang template mendukung proses load template dari directory
4. Hal ini memudahkan kita, sehingga tidak perlu menyebutkan nama file nya satu per satu


   -- template dari golang embed

1. Sejak Go-Lang 1.16, karena sudah ada Go-Lang Embed, jadi direkomendasikan menggunakan Go-Lang embed untuk menyimpan data template
2. Menggunakan Go-Lang embed menjadi kita tidak perlu ikut meng-copy template file lagi, karena sudah otomatis di embed di dalam distribution file



### TEMPLATE DATA


1. Saat kita membuat template, kadang kita ingin menambahkan banyak data dinamis
2. Hal ini bisa kita lakukan dengan cara menggunakan data struct atau map
3. Namun perlu dilakukan perubahan di dalam text template nya, kita perlu memberi tahu Field atau Key mana yang akan kita gunakan untuk mengisi data dinamis di template
4. Kita bisa menyebutkan dengan cara seperti ini {{.NamaField}}



### TEMPLATE ACTION

1. Go-Lang template mendukung perintah action, seperti percabangan, perulangan dan lain-lain

   # if else

1. {{if .Value}} T1 {{end}}, jika Value tidak kosong, maka T1 akan dieksekusi, jika kosong, tidak ada yang dieksekusi
2. {{if .Value}} T1 {{else}} T2 {{end}}, jika value tidak kosong, maka T1 akan dieksekusi, jika kosong, T2 yang akan dieksekusi
3. {{if .Value1}} T1 {{else if .Value2}} T2 {{else}} T3 {{end}}, jika Value1 tidak kosong, maka T1 akan dieksekusi, jika Value2 tidak kosong,   maka T2 akan dieksekusi, jika tidak semuanya, maka T3 akan dieksekusi


   # operator perbandingan

Go-Lang template juga mendukung operator perbandingan, ini cocok ketika butuh melakukan perbandingan number di if statement, berikut adalah 
operator nya :

1. eq	artinya arg1 == arg2 [sama dengan] 
2. ne	artinya arg1 != arg2 [tidak sama dengan]
3. lt	artinya arg1 < arg2  [kurang dari]
4. le	artinya arg1 <= arg2 [kurang dari sama dengan]
5. t	artinya arg1 > arg2  [lebih dari]
6. ge	artinya arg1 >= arg2 [lebih dari sama dengan]  


  -- kenapa operator nya didepan
1. Hal ini dikarenakan, sebenarnya operator perbandingan tersebut adalah sebuah function
2. Jadi saat kita menggunakan {{eq First Second}}, sebenarnya dia akan memanggil function eq dengan parameter First dan Second : eq(First, Second)


   # Range

1. Range digunakan untuk melakukan iterasi data template
2. Tidak ada perulangan biasa seperti menggunakan for di Go-Lang template
3. Yang kita bisa lakukan adalah menggunakan range untuk mengiterasi tiap data array, slice, map atau channel
4. {{range $index, $element := .Value}} T1 {{end}}, jika value memiliki data, maka T1 akan dieksekusi sebanyak element value, dan kita bisa menggunakan $index untuk mengakses index dan $element untuk mengakses element
5. {{range $index, $element := .Value}} T1 {{else}} T2 {{end}}, sama seperti sebelumnya, namun jika value tidak memiliki element apapun, maka T2 yang akan dieksekusi


   # with

1. Kadang kita sering membuat nested struct 
2. Jika menggunakan template, kita bisa mengaksesnya menggunakan .Value.NestedValue
3. Di template terdapat action with, yang bisa digunakan mengubah scope dot menjadi object yang kita mau
4. {{with .Value}} T1 {{end}}, jika value tidak kosong, di T1 semua dot akan merefer ke value
5. {{with .Value}} T1 {{else}} T2 {{end}}, sama seperti sebelumnya, namun jika value kosong, maka T2 yang akan dieksekusi


   -- comment

1. Template juga mendukung komentar
2. Komentar secara otomatis akan hilang ketika template text di parsing
3. Untuk membuat komentar sangat sederhana, kita bisa gunakan {{/* Contoh Komentar */}}



### TEMPLATE LAYOUT


1. Saat kita membuat halaman website, kadang ada beberapa bagian yang selalu sama, misal header dan footer
2. Best practice nya jika terdapat bagian yang selalu sama, disarankan untuk disimpan pada template yang terpisah, agar bisa digunakan di template lain
3. Go-Lang template mendukung import dari template lain

   # import template

1. Untuk melakukan import, kita bisa menggunakan perintah berikut :
2. {{template “nama”}}, artinya kita akan meng-import template “nama” tanpa memberikan data apapun
3. {{template “nama” .Value}}, artinya kita akan meng-import template “nama” dengan memberikann data value

   # template name

1. Saat kita membuat template dari file, secara otomatis nama file nya akan menjadi nama template
2. Namun jika kita ingin mengubah nama template nya, kita juga bisa melakukan mengguakan perintah {{define “nama”}} TEMPLATE {{end}}, artinya kita membuat template dengan nama “nama”


### TEMPLATE FUNCTION


1. Selain mengakses field, dalam template, function juga bisa diakses
2. Cara mengakses function sama seperti mengakses field, namun jika function tersebut memiliki parameter, kita bisa gunakan tambahkan parameter ketika memanggil function di template nya
3. {{.FunctionName}}, memanggil field FunctionName atau function FunctionName()
4. {{.FunctionName “eko”, “kurniawan”}}, memanggil function FunctionName(“eko”, “kurniawan”)


   # global function

1. Go-Lang template memiliki beberapa global function
2. Global function adalah function yang bisa digunakan secara langsung, tanpa menggunakan template data
3. Berikut adalah beberapa global function di Go-Lang template 
https://github.com/golang/go/blob/master/src/text/template/funcs.go 


   # menambah global function

1. Kita juga bisa menambah global function
2. Untuk menambah global function, kita bisa menggunakan method Funcs pada template
3. Perlu diingat, bahwa menambahkan global function harus dilakukan sebelum melakukan parsing template

   # function pipelines

1. Go-Lang template mendukung function pipelines, artinya hasil dari function bisa dikirim ke function berikutnya
2. Untuk menggunakan function pipelines, kita bisa menggunakan tanda | , misal :
{{ sayHello .Name | upper }}, artinya akan memanggil global function sayHello(Name) hasil dari sayHello(Name) akan dikirim ke function upper(hasil)
3. Kita bisa menambahkan function pipelines lebih dari satu



### TEMPLATE CACHING

1. Kode-kode diatas yang sudah kita praktekan sebenarnya tidak efisien
2. Hal ini dikarenakan, setiap Handler dipanggil, kita selalu melakukan parsing ulang template nya
3. Idealnya template hanya melakukan parsing satu kali diawal ketika aplikasinya berjalan
4. Selanjutnya data template akan di caching (disimpan di memory), sehingga kita tidak perlu melakukan parsing lagi
5. Hal ini akan membuat web kita semakin cepat


### XSS SCRIPTING

1. XSS adalah salah satu security issue yang biasa terjadi ketika membuat web
2. XSS adalah celah keamanan, dimana orang bisa secara sengaja memasukkan parameter yang mengandung JavaScript agar dirender oleh halaman website kita
3. Biasanya tujuan dari XSS adalah mencuri cookie browser pengguna yang sedang mengakses website kita
3. XSS bisa menyebabkan account pengguna kita diambil alih jika tidak ditangani dengan baik

   # auto escape

1. Berbeda dengan bahasa pemrograman lain seperti PHP, pada Go-Lang template, masalah XSS sudah diatasi secara otomatis
2. Go-Lang template memiliki fitur Auto Escape, dimana dia bisa mendeteksi data yang perlu ditampilkan di template, jika mengandung tag-tag html atau script, secara otomatis akan di escape
3. Semua function escape bisa diliat disini :
https://github.com/golang/go/blob/master/src/html/template/escape.go 
https://golang.org/pkg/html/template/#hdr-Contexts    