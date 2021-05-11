# Rangkuman-Rekursi

Rekursif berasal dari kata rekursion yang artinya pengulangan

Fungsi rekursif -> fungsi yang bisa memanggil dirinya sendiri, jadi nanti fungsi bisa memanggil fungsi lain.

=>> Finite Recursion (Fungsi Terbatas)
    
    Jika sebuah fungsi memanggil dirinya sendiri, maka akan terjadi looping tak hingga karena jika fungsi itu benar, maka ketika direkursi akan selalu bernilai benar dan terus menerus looping. sehingga, dibutuhkan suatu fungsi rekursi terbatas agar tidak terjadi looping secara terus menerus.
    
    
contoh :

    #include<iostream>
    using namespace std;
    
    //fungsi rekursif terbatas
    int pangkatIterasi(int a, int b){
        int hasil = a;
        for (int i = 1; i < b; i++){
             hasil = hasil * a;
        }
        return hasil;
    }
    
    int main(){
        int a;
        int b;
        cout << "masukkan angka: ";
        cin >> a;
        cout << "masukkan pangkat: ";
        cin >> b;
        cout << "hasil iterasi = " << pangkatIterasi(a,b) << endl;
        
        cin.get();
        return 0;
    }
  
  
    catatan : itu jika fungsinya berbentuk pangkat. semisal 3^2=9
    
    
Bagaimana jika kita membuat fungsi yang bukan berupa pangkat?
semisal : 3^6 = 3 x 3 x 3 x 3 x 3 x 3
nah, itu kan yang berulang perkaliannya. sehingga kita bisa membuatnya dengan fungsi rekursif. wah, gimana tuh?


    Jadi, pada fungsi rekursif ini perhitungannya dihitung dari belakang. Sehingga, hasilnya merupakan perkalian terakhir yang ada pada perkalian bilangan paling depan


Penjelasannya gini,

    3 pangkat 6 = 3 x 3 x 3 x 3 x 3 x 3
    3 pangkat 5 = 3 x 3 x 3 x 3 x 3
    3 pangkat 4 = 3 x 3 x 3 x 3
    3 pangkat 3 = 3 x 3 x 3
    3 pangkat 2 = 3 x 3
    3 pangkat 1 = 3
    3 pangkat 0 = 1
    
Coba cek source code nya ya

    
    #include<iostream>
    using namespace std;
    
    //fungsi rekursif terbatas
    int pangkatIterasi(int a, int b){
        int hasil = a;
        for (int i = 1; i < b; i++){
             hasil = hasil * a;
        }
        return hasil;
    }
    int pangkatRekursif(int a, int b){
        return a * pangkatRekursif(a, (b - 1));
    }
    
    int main(){
        int a;
        int b;
        cout << "masukkan angka: ";
        cin >> a;
        cout << "masukkan pangkat: ";
        cin >> b;
        cout << "hasil iterasi = " << pangkatIterasi(a,b) << endl;
        cout << "hasil rekursif = " << pangkatRekursif(a,b) << endl;
        
        cin.get();
        return 0;
    }
    
    
Penjelasannya gini,

![gambar](https://user-images.githubusercontent.com/82517069/117557548-0a5b2980-b09e-11eb-9da7-4f1530eb35db.png)

Nah, hasil output akan ada segmentation fault. apa artinya? itu artinya looping infinite. sehingga harus mendefinisikan batasan pangkatnya berapa.

Langsung aja ini source code yang seharusnya benar.


    #include<iostream>
    using namespace std;
    
    //fungsi rekursif terbatas
    int pangkatIterasi(int a, int b){
        int hasil = a;
        for (int i = 1; i < b; i++){
             hasil = hasil * a;
        }
        return hasil;
    }
    int pangkatRekursif(int a, int b){
        if (b <= 1){
            cout << "akhir dari rekursif: " << endl;
            return a;
        }
        else {
            cout << "rekursif: " << endl;
            return a * pangkatRekursif(a, (b - 1));
        }
    }
    
    int main(){
        int a;
        int b;
        cout << "masukkan angka: ";
        cin >> a;
        cout << "masukkan pangkat: ";
        cin >> b;
        cout << "hasil iterasi = " << pangkatIterasi(a,b) << endl;
        cout << "hasil rekursif = " << pangkatRekursif(a,b) << endl;
        
        cin.get();
        return 0;
    }



===================================================Latihan Soal===================================================

1. Membuat program faktorial
2. Membuat program fibonacci

===================================================Source Code===================================================

Soal nomor 1

        #include <iostream>
        using namespace std;
        int faktorial(int n){
            if (n == 0 || n == 1)
            {
                return 1;
            }
            else {
                return n * faktorial(n-1);
            }

        }
        int main(){
            int bil, n;
            long int hasil;
            cout << "n = ";
            cin >> n;
            hasil = faktorial (n);
            cout << n << "! = " << hasil;
            return 0;
        }

input
5
output
5! = 120


Soal nomor 2

        #include <iostream>
        using namespace std;
        int fibonacci(int n){
            if (n == 0 || n == 1){
                return n;
            }
            else {
                return fibonacci(n-1) + fibonacci(n-2);
            }
        }
        int main(){
            int bil, n;
            int hasil;
            cout << "n = ";
            cin >> n;
            hasil = fibonacci(n);
            cout << "fibonacci(" << n << ") = " << hasil;
            return 0;
        }
