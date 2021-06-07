# Lab10Web
```
Nama        : Panji Putra Pamungkas
Nim         : 311910587
Kelas       : TI. 19. B1
Mata Kuliah : Pemograman Web - Praktikum 8
```
### PHP OOP
#### 1. Buka XAMPP lalu jalakan Apache dan MySQL
![1 1](https://user-images.githubusercontent.com/81550517/121011704-1a5f4980-c7c1-11eb-9059-4ffac5484e46.png)

#### 2. Buat file lab10_php_oop pada root directory web server c:\xampp\htdocs
![2 1](https://user-images.githubusercontent.com/81550517/121012085-8c379300-c7c1-11eb-9795-c89e988d20bf.png)

#### 3. Buat file baru dengan nama mobil.php pada folder c:\xampp\htdocs\lab10_php_oop

Coding PHP OOP sederhana, membuat Class dan memanggil Class
```
<?php
/**
* Program sederhana pendefinisian class dan pemanggilan class.
**/

class Mobil
{
    private $warna;
    private $merk;
    private $harga;

    public function __construct()
    {
    $this->warna = "Biru";
    $this->merk = "BMW";
    $this->harga = "10000000";
    }

    public function gantiWarna ($warnaBaru)
    {
    $this->warna = $warnaBaru;
    }

    public function tampilWarna ()
    {
    echo "Warna mobilnya : " . $this->warna;
    }
}
// membuat objek mobil
$a = new Mobil();
$b = new Mobil();

// memanggil objek
echo "<b>Mobil pertama</b><br>";
$a->tampilWarna();
echo "<br>Mobil pertama ganti warna<br>";
$a->gantiWarna("Merah");
$a->tampilWarna();

// memanggil objek
echo "<br><b>Mobil kedua</b><br>";
$b->gantiWarna("Hijau");
$b->tampilWarna();

?>
```
Hasil Ketika di buka menggunakan link di sammping http://localhost/lab10_php_oop
![3](https://user-images.githubusercontent.com/81550517/121037781-f0fee780-c7d9-11eb-8ac3-936254d67fe0.png)

#### 4. Buat file baru dengan nama form.php pada folder c:\xampp\htdocs\lab10_php_oop

Coding form.php ini untuk Class
```
<?php
/**
* Nama Class: Form
* Deskripsi: CLass untuk membuat form inputan text sederhana
**/

class Form
{
    private $fields = array();
    private $action;
    private $submit = "Submit Form";
    private $jumField = 0;

    public function __construct($action, $submit)
    {
    $this->action = $action;
    $this->submit = $submit;
    }
    
    public function displayForm()
    {
    echo "<form action='".$this->action."' method='POST'>";
    echo '<table width="100%" border="0">';
    for ($j=0; $j<count($this->fields); $j++) {
        echo "<tr><td align='right'>".$this->fields[$j]['label']."</td>";
        echo "<td><input type='text' name='".$this->fields[$j]['name']."'></td></tr>";
        }
        echo "<tr><td colspan='2'>";
        echo "<input type='submit' value='".$this->submit."'></td></tr>";
        echo "</table>";
    }

    public function addField($name, $label)
    {
        $this->fields [$this->jumField]['name'] = $name;
        $this->fields [$this->jumField]['label'] = $label;
        $this->jumField ++;
    }
}

?>
```
#### 5. Buat file baru dengan nama form_input.php pada folder c:\xampp\htdocs\lab10_php_oop

Coding form_input.php ini untuk memanggil Class yg sudah dibuat tadi.
```
<?php
/**
* Program memanfaatkan Program 10.2 untuk membuat form inputan sederhana.
**/

include "form.php";

echo "<html><head><title>Mahasiswa</title></head><body>";
$form = new Form("","Input Form");
$form->addField("txtnim", "Nim");
$form->addField("txtnama", "Nama");
$form->addField("txtalamat", "Alamat");
echo "<h3>Silahkan isi form berikut ini :</h3>";
$form->displayForm();
echo "</body></html>";

?>
```
Hasil Ketika di buka menggunakan link di sammping http://localhost/lab10_php_oop/form_input.php
![5](https://user-images.githubusercontent.com/81550517/121040345-05dc7a80-c7dc-11eb-8580-a7fb613ef0ff.png)
