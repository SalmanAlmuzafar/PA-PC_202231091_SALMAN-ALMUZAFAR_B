# Deteksi Tepi Pola Objek

## IMPORT LIBRARY
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
* adalah singkatan dari OpenCV, sebuah library komputer vision yang populer.
Kode ini mengimport modul OpenCV, yang memungkinkan kita untuk menggunakan fungsi-fungsi dan kelas-kelas yang tersedia dalam OpenCV untuk mengolah gambar dan video. <br>
* NumPy digunakan untuk mengolah array dan matriks, yang sangat berguna dalam pengolahan gambar dan video. <br>
* Matplotlib digunakan untuk membuat plot dan visualisasi data, termasuk gambar dan video. <br>

```python
image_path = "salman.jpg"
image = cv2.imread(image_path)
```
* Kode ini mendeklarasikan sebuah variabel image_path dan mengisi nilai string "salman.jpg" ke dalamnya. <br>
* Kode ini menggunakan fungsi imread() dari OpenCV untuk membaca file gambar yang terletak pada path yang telah ditentukan sebelumnya (image_path).
Fungsi imread() mengembalikan sebuah array 3D yang merepresentasikan gambar, dengan ukuran (height, width, channels).
Array ini disimpan dalam variabel image.<br>

## Convert the image to grayscale
```python
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```
* Kode ini mengkonversi gambar asli (image) ke dalam format grayscale menggunakan fungsi cvtColor() dari OpenCV.
Parameter cv2.COLOR_BGR2GRAY menentukan bahwa kita ingin mengkonversi gambar dari format BGR (Blue, Green, Red) ke dalam format grayscale.
Hasil konversi disimpan dalam variabel gray.

## Apply Gaussian blur to reduce noise
```python
blurred = cv2.GaussianBlur(gray, (5, 5), 0)
```
* Kode ini mengaplikasikan filter Gaussian blur pada gambar grayscale (gray) menggunakan fungsi GaussianBlur() dari OpenCV.
Parameter (5, 5) menentukan ukuran kernel (window) yang digunakan untuk menghitung blur.
Parameter 0 menentukan bahwa kita tidak ingin mengatur nilai sigma (standar deviasi) secara manual.
Hasil blur disimpan dalam variabel blurred.

## Apply Canny edge detection
```python
edges = cv2.Canny(blurred, 50, 90)
```
* Kode ini mengaplikasikan deteksi tepi Canny pada gambar blur (blurred) menggunakan fungsi Canny() dari OpenCV.
Parameter 50 dan 90 menentukan nilai threshold untuk deteksi tepi.
Hasil deteksi tepi disimpan dalam variabel edges.

## Find contours in the edge map
```python
contours, _ = cv2.findContours(edges, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
```
* Kode ini mencari kontur dalam peta tepi (edges) menggunakan fungsi findContours() dari OpenCV.
Parameter cv2.RETR_EXTERNAL menentukan bahwa kita hanya ingin mencari kontur eksternal.
Parameter cv2.CHAIN_APPROX_SIMPLE menentukan bahwa kita ingin menggunakan metode approximasi sederhana untuk mencari kontur.
Hasil kontur disimpan dalam variabel contours.

## Create a copy of the original image to draw contours
```python
contour_image = image.copy()
```
* Kode ini membuat salinan gambar asli (image) menggunakan metode copy().
  
## Draw contours on the copy
```python
cv2.drawContours(contour_image, contours, -1, (0, 255, 0), 2)
```
* Kode ini menggambar kontur pada salinan gambar (contour_image) menggunakan fungsi drawContours() dari OpenCV.
Parameter contours menentukan kontur yang ingin digambar.
Parameter -1 menentukan bahwa kita ingin menggambar semua kontur.
Parameter (0, 255, 0) menentukan warna hijau untuk kontur.
Parameter 2 menentukan ketebalan kontur.

## Display the original image, Canny edge detection, and contours detection using plt
```python
fig, axs = plt.subplots(1, 3, figsize=(15, 5))
```
* Kode ini membuat figure dan axes menggunakan fungsi subplots() dari Matplotlib.
Parameter 1, 3 menentukan bahwa kita ingin membuat 1 baris dan 3 kolom.
Parameter figsize=(15, 5) menentukan ukuran figure.

## Menampilkan Gambar Asli
```python
axs[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
axs[0].set_title('Original Image')
axs[0].axis('off')
```
* Kode ini menampilkan gambar asli (image) pada axes pertama (axs[0]).
Fungsi cvtColor() dari OpenCV digunakan untuk mengkonversi gambar dari format BGR ke format RGB, karena Matplotlib menggunakan format RGB untuk menampilkan gambar.
Judul gambar diatur menjadi "Original Image" menggunakan fungsi set_title().
Fungsi axis('off') digunakan untuk menghilangkan axis pada gambar.

## Menampilkan Hasil Deteksi Tepi Canny
```python
axs[1].imshow(edges, cmap='gray')
axs[1].set_title('Canny Edge Detection')
axs[1].axis('off')
```
* Kode ini menampilkan hasil deteksi tepi Canny (edges) pada axes kedua (axs[1]).
Fungsi imshow() digunakan untuk menampilkan gambar, dengan parameter cmap='gray' untuk menampilkan gambar dalam format grayscale.
Judul gambar diatur menjadi "Canny Edge Detection" menggunakan fungsi set_title().
Fungsi axis('off') digunakan untuk menghilangkan axis pada gambar.

## Menampilkan Hasil Deteksi Kontur
```python
axs[2].imshow(cv2.cvtColor(contour_image, cv2.COLOR_BGR2RGB))
axs[2].set_title('Contours Detection')
axs[2].axis('off')
```
* Kode ini menampilkan hasil deteksi kontur (contour_image) pada axes ketiga (axs[2]).
Fungsi cvtColor() dari OpenCV digunakan untuk mengkonversi gambar dari format BGR ke format RGB, karena Matplotlib menggunakan format RGB untuk menampilkan gambar.
Judul gambar diatur menjadi "Contours Detection" menggunakan fungsi set_title().
Fungsi axis('off') digunakan untuk menghilangkan axis pada gambar.

## Menampilkan Gambar
```python
plt.show()
```
* Kode ini digunakan untuk menampilkan semua gambar yang telah diatur sebelumnya.

## Maka Output Yang Dihasilkan Seperti Berikut 
![image](https://github.com/SalmanAlmuzafar/PA-PC_202231091_SALMAN-ALMUZAFAR_B/assets/169425467/7f248e58-4c17-458d-a281-bf8dda3dc5ca)




