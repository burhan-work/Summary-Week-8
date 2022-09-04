# REACT CONTEXT
Context menyediakan cara untuk oper data melalui diagram komponen tanpa harus oper props secara manual di setiap tingkat. Konteks digunakan untuk berbagi data yang dapat dianggap “global” untuk pohon komponen React dan menggunakan data tersebut jika diperlukan, seperti pengguna terotentikasi saat ini, tema, dll. 

## React Context API
React Context API adalah struktur komponen, yang memungkinkan kita untuk berbagi data di semua level aplikasi. Tujuan utama dari API Konteks adalah untuk memecahkan masalah pengeboran prop (juga disebut “Threading”).

### `React.createContext`
Ini menciptakan objek konteks. Saat React merender komponen yang berlangganan objek konteks ini, maka React akan membaca nilai konteks saat ini dari penyedia yang cocok di pohon komponen.

Sintaksis:

    const MyContext = React.createContext (defaultValue);

Ketika sebuah komponen tidak memiliki penyedia yang cocok di pohon komponen, ia mengembalikan argumen **defaultValue**. Ini sangat membantu untuk menguji isolasi komponen (secara terpisah) tanpa membungkusnya.

### `Context.provider`
Setiap objek Context memiliki komponen Provider React yang memungkinkan konsumsi komponen untuk berlangganan perubahan konteks. Ini bertindak sebagai layanan pengiriman. Ketika komponen konsumen meminta sesuatu, ia menemukannya dalam konteks dan menyediakannya di tempat yang dibutuhkan.

Sintaksis:

    <MyContext.Provider value={/* some value */}>

Ini menerima nilai prop dan meneruskan ke komponen konsumsi yang merupakan turunan dari Penyedia ini. Kita dapat menghubungkan satu Penyedia dengan banyak konsumen. Penyedia Konteks dapat disarangkan untuk mengganti nilai lebih dalam di dalam pohon komponen. Semua konsumen yang merupakan keturunan dari Penyedia selalu merender ulang setiap kali penyangga nilai Penyedia diubah. Perubahan ditentukan dengan membandingkan nilai lama dan baru menggunakan algoritma yang sama seperti algoritma **Object.is**.

### `Context.Consumer`
Ini adalah komponen React yang mengikuti perubahan konteks. Ini memungkinkan kita untuk berlangganan konteks di dalam komponen fungsi. Ini membutuhkan fungsi sebagai komponen. Konsumen digunakan untuk meminta data melalui penyedia dan memanipulasi penyimpanan data pusat jika penyedia mengizinkannya.

Sintaksis:

    <MyContext.Consumer>
        {value => /* render something which is based on the context value */}
    </MyContext.Consumer>

Komponen fungsi menerima nilai konteks saat ini dan kemudian mengembalikan simpul React. Argumen nilai yang diteruskan ke fungsi akan sama dengan prop nilai Penyedia terdekat untuk konteks ini di pohon komponen. Jika tidak ada Penyedia untuk konteks ini, argumen nilai akan sama dengan defaultValue yang diteruskan ke `createContext()`.

### `Class.contextType`
Properti contextType pada kelas yang digunakan untuk menetapkan objek Konteks yang dibuat oleh `React.createContext()`. Ini memungkinkan kita untuk menggunakan nilai terdekat saat ini dari tipe Konteks tersebut menggunakan `this.context`. Kita bisa mereferensikan ini di salah satu metode siklus hidup komponen, termasuk fungsi render.

# REACT TESTING
React Testing Library adalah seperangkat helpers yang memungkinkan Anda mengetes komponen pada React tanpa bergantung pada detail implementasinya. Pendekatan ini membuat refactoring menjadi mudah dan juga mendorong Anda untuk menerapkan best practices untuk aksesbilitas. Mungkin tidak memberikan cara untuk me-render secara “dangkal” pada sebuah komponen tanpa anak, test runner seperti Jest yang memungkinkan Anda melakukan mocking.

Untuk penjelasan yang lebih lengkap, kunjungi alamat https://id.reactjs.org/docs/testing.html