# **Texture Mapping - webGL**

<div align=justify>

Berikut adalah Repository untuk pengerjaan Tugas 4 mata kuliah Grafika Komputer (Texture Mapping dengan webGL) yang berisi _source code_, dokumentasi atau penjelasan, dan _screenshot output_.

# **Identitas**

| Nama                | NRP        | Kelas              |
| ------------------- | ---------- | ------------------ |
| Akmal Ariq Romadhon | 5025211188 | Grafika Komputer A |

# **Texture Mapping**

Berikut adalah dokumentasi serta _screenshot output_ dari code yang ada untuk pembuatan kubus dengan setiap sisinya berupa gambar.

## **Penjelasan**

Fungsi yang diubah dalam _file_ `tugas1-release.html` fungsi `initGL()`.

```js
let img = [];
for (let i = 0; i < 6; i++) {
  img[i] = new Image();
  img[i].onload = function () {
    textureObjects[i] = gl.createTexture();
    gl.bindTexture(gl.TEXTURE_2D, textureObjects[i]);
    gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.UNSIGNED_BYTE, img[i]);
    gl.generateMipmap(gl.TEXTURE_2D);
    if (i === 5) draw();
  };
  img[i].src = textureURLs[i];
}
```

Dalam kode di atas, terdapat array yang disebut img, dimana _array_ tersebut digunakan untuk menyimpan gambar-gambar. Gambar-gambar tersebut dirubah menjadi tekstur yang dapat digunakan dalam WebGL, dan setelah semua gambar telah dimuat, fungsi draw dijalankan untuk mulai menggambar objek 3D. Oleh karena itu, dilakukan melakukan loop sebanyak enam kali karena ada sisi gambar yang akan dimuat.

Pada setiap iterasi loop, objek gambar baru akan dibuat sekaligus mengatur _event handler_. Saat gambar selesai dimuat, bjek tekstur WebGL dibuat dan dihubungkan dengan gambar tersebut. Ketika 6 sisi telah diinisialisasi sebagai tekstur WebGL, fungsi draw dipanggil untuk memulai proses penggambaran objek 3D sesuai dengan _texture_ yang dimuat.

Fungsi yang diubah dalam _file_ `tugas1-release.html` fungsi `draw()`.

```js
drawSquare(textureObjects[0]); //Front
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
drawSquare(textureObjects[1]); //Right
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
drawSquare(textureObjects[2]); //Back
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
drawSquare(textureObjects[3]); //Left
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
mat4.rotateX(modelview, modelview, 0.5 * -Math.PI);
drawSquare(textureObjects[4]); //Top
mat4.rotateX(modelview, modelview, Math.PI);
drawSquare(textureObjects[5]); //Bottom
```

Dalam kode di atas, dilakukan perubahan dengan memanggil fungsi `drawSquare` sebanyak enam kali, sesuai dengan jumlah sisi kubus. Selain itu, dilakukan rotasi pada modelview matrix sebelum pemanggilan fungsi agar sesuai dengan sisi kubus yang akan diberikan gambar. Rotasi pada sumbuX diperlukan untuk sisi bagian atas dan bawah, sedangkan untuk sisi lain hanya memerlukan rotasi pada sumbuY.

## **_Screenshot Ouput_**

Berikut adalah _Screenshot output_ dari perubahan code tersebut:

![Img1](https://cdn.discordapp.com/attachments/1150687865420906517/1168784082826702939/Screenshot_1158.png?ex=65530600&is=65409100&hm=eaf1254d41c333735ac401c632afb16a3a2bf82ed732a2aa2655fde49bb8aade&)

![Img2](https://cdn.discordapp.com/attachments/1150687865420906517/1168784084118548480/Screenshot_1160.png?ex=65530600&is=65409100&hm=bbec28ec7c51f50c3f70e9ddf8b3b8c21d911157df105314c96727705f9523ca&)

![Img3](https://cdn.discordapp.com/attachments/1150687865420906517/1168784084546363393/Screenshot_1161.png?ex=65530600&is=65409100&hm=6bd6a66953d342fa6047891bef47f76af5d6aa88d6b8bc7995803dc32b6f1d9f&)

![Img4](https://cdn.discordapp.com/attachments/1150687865420906517/1168784367074685009/Screenshot_1162.png?ex=65530644&is=65409144&hm=a34a5177e92a18f840e0625c6aaa600cc4db36c90a6be79793538680b50992a4&)

# **_End Of The Line_**

```c
#include <stdio.h>

int main(){
    printf("thank you");
}
```