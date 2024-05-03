# UTS-PRAK.PBO-OnixaShafaP.W-Kelas-E
Mata Kuliah 	: Praktikum PBO
<br>Nama		      : Onixa Shafa Putri Wibowo
<br>NIM		        : 1227050107
<br>Jurusan		    : [Teknik Informatika](http://if.uinsgd.ac.id/) [UIN Sunan Gunung Djati Bandung](https://uinsgd.ac.id/) 

## Deskripsi Umum
Program ini adalah program sederhana tentang hewan-hewan untuk mengimplementasikan encapsulation, inheritance, polymorphism, dan interface. 

## Deskripsi
Program ini adalah program sederhana tentang hewan-hewan untuk mengimplementasikan encapsulation, inheritance, polymorphism, dan interface. Program ini juga menggunakan konsep abstraksi dengan membuat class hewan sebagai abstract class, dimana method suara() dideklarasikan sebagai abstract method yang harus diimplementasikan oleh subclassnya. Outputnya berupa jenis hewan, suara jenis hewan tersebut, dan proses makan masing-masing hewan.
1. Encapsulation
Variabel ‘jenis’ dalam class hewan dienkapsulasi dengan akses modifier protected, dan diakses melalui metode setter dan getter, yaitu getJenis dan setJenis.
2. Inheritance
Class kucing dan anjing merupakan subclass dari class hewan sehinggga mewarisi sifat dan perilaku dari class hewan.
3. Polymorphism
Bagian ini terjadi pada saat objek dari class kucing dan anjing dimasukkan ke dalam array ‘hewanArr’ yang bertipe hewan. Dalam loop for, method suara() dipanggil pada setiap objek tanpa perlu mengetahui tipe sebenarnya (kucing atau anjing).
4. Interface
Terdapat interface makanan yang mendefinisikan metode prosesMakan(). Class kucing dan anjing mengimplementasikan interface ini. Hal ini memungkinkan objek-obejk dari kedua class ini untuk memiliki akses ke metode prosesMakan().

## Source Code

interface makanan {
    void prosesMakan();
}

abstract class hewan {
    protected String jenis;

    public hewan(String jenis) {
        this.jenis = jenis;
    }

    abstract void suara();

    public String getJenis() {
        return jenis;
    }

    public void setjenis(String jenis) {
        this.jenis = jenis;
    }
}

class kucing extends hewan implements makanan {
    public kucing(String jenis) {
        super(jenis);
    }

    @Override
    void suara() {
        System.out.println("Meow!");
    }

    @Override
    public void prosesMakan() {
        System.out.println(getJenis() + " sedang makan dry food.");
    }
}

class anjing extends hewan implements makanan {
    public anjing(String jenis) {
        super(jenis);
    }

    @Override
    void suara() {
        System.out.println("Woof woof!");
    }

    @Override
    public void prosesMakan() {
        System.out.println(getJenis() + " sedang makan ayam.");
    }
}

public class binatang {
    public static void main(String[] args) {
        kucing Kucing = new kucing("Kucing");
        anjing Anjing = new anjing("Anjing");

        hewan[] hewanArr = { Kucing, Anjing };

        for (hewan Hewan : hewanArr) {
            System.out.println("Jenis Hewan: " + Hewan.getJenis());
            Hewan.suara();

            if (Hewan instanceof makanan) {
                ((makanan) Hewan).prosesMakan();
            }
            System.out.println();
        }
    }
}

## Output
Berikut adalah output kedua program tersebut
<br>![Screenshot 2024-05-03 172232](https://github.com/onixasf/UTS-PRAK.PBO-OnixaShafaP.W-Kelas-E/assets/119369695/5b3f644c-abf4-4a84-97ff-e91e867460cd)

