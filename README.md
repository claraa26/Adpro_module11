# Nama  : Clara Sista Widhiastuti
# NPM   : 2206825782
# Kelas : ADPRO-A

### Reflection on Hello Minikube

1. Compare the application logs before and after you exposed it as a Service. What do you see in the logs? Does the number of logs increase each time you open the app?</br>
Before Exposing as a Service: Log hanya menunjukkan server yang sedang menyala, yang mengindikasikan bahwa server siap menerima koneksi.</br>
After Exposing as a Service: Setelah mengekspos aplikasi sebagai service dan mengaksesnya, log kini menyertakan entri untuk permintaan HTTP GET. Setiap kali Anda membuka aplikasi, akan membuat dua permintaan GET, seperti yang ditunjukkan oleh pasangan entri log dengan timestamp yang sama. Hal ini menunjukkan bahwa setiap kali aplikasi dibuka, aplikasi membuat dua permintaan HTTP ke server.</br>

Before</br>
![](https://imgur.com/Jol1h7F.jpg)

After</br>
![](https://imgur.com/sQdATGN.jpg)

2.  Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you
explicitly created?</br>
Opsi -n dalam kubectl get digunakan untuk menentukan namespace tempat mendaftar resources. Kluster Kubernetes secara logis dapat dibagi menjadi beberapa namespace. Jika Anda tidak menentukan namespace dengan -n, kubectl akan mendapatkan daftar resource dari namespace default, yang merupakan tempat resource dibuat.

### Reflection on Rolling Update & Kubernetes Manifest File

1. What is the difference between Rolling Update and Recreate deployment strategy?</br>
Dalam strategi rolling update, Kubernetes mengganti instance versi lama aplikasi dengan instance versi baru secara bertahap, memastikan bahwa aplikasi tetap tersedia selama proses pembaruan. Sedangkan, dalam strategi Recreate, Kubernetes menghentikan semua instans versi lama aplikasi sebelum memulai instans baru dengan versi yang diperbarui.
2. Try deploying the Spring Petclinic REST using Recreate deployment strategy and document
your attempt.
Buat deployment baru, lalu edit file deployment.yml dengan menjalankan function edit 
![](https://imgur.com/3YFLQcn.jpg)
Setelah mengedit akan langsung create container seperti berikut
![](https://imgur.com/7KkQa6S.jpg)
lalu setelah dicek bagian imagenya akan bertubah menjadi 3.2.1
![](https://imgur.com/IeLZQHT.jpg)

3.  Prepare different manifest files for executing Recreate deployment strategy</br>
Buat file deployment.yml baru dan set strategy ke Recreate
![](https://imgur.com/8pnZ1wa.jpg)

Lalu apply, setelah melakukan minicube start
![](https://imgur.com/jZ8N75e.jpg)

4.  What do you think are the benefits of using Kubernetes manifest files? Recall your experience in deploying the app manually and compare it to your experience when deploying the same app by applying the manifest files (i.e., invoking `kubectl apply -f` command) to the cluster. </br>
Jika menggunakan kubernetes file manifes kita dapat mengontrol versinya menggunakan alat bantu seperti Git, sehingga Anda dapat melacak perubahan, berkolaborasi dengan anggota tim. Selain itu, dengan perintah seperti kubectl apply -f, dapat langsung mengotomatiskan proses penerapan, sehingga lebih cepat, lebih efisien, dan lebih sedikit kesalahan. Sebaliknya, penerapan deploy secara manual melibatkan lebih banyak langkah manual, yang dapat menyebabkan kesalahan dan memakan waktu. 