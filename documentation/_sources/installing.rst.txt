TeArch Linux Kurulumu
==========

TeArch Linux'u kurmak oldukça kolay ve zahmetsizdir. Aşağıdaki adımları takip ederek TeArch Linux'u çok kısa bir sürede kolayca kurabilirsiniz.

En Güncel Kurulum Medyasını İndirin
----------
TeArch Linux'a ait en yeni kurulum medyasını `indirme sayfamızdan <https://tearch-linux.github.io/download>`_ indirebilirsiniz. 
  .. figure:: _static/images/download_menu.png
      :alt: TeArch Linux'un indirme sayfası.


Kurulum Medyasını USB Belleğe veya DVD'ye Yazdırın
----------
**Windows'ta Canlı USB veya DVD Oluşturmak**
Windows'ta usb veya dvd medyası oluşturmak için `Etcher <https://www.balena.io/etcher/>`_ veya `Rufus <https://rufus.ie/>`_ programlarını tercih edebilirsiniz. 

.. figure:: _static/images/etcher.gif
      :alt: Etcher'a ait bir gif.
      
      
Bilgisayarı USB veya DVD'den başlatın
----------
Kuruluma başlamak için bilgisayarınızı yeniden başlatın ve boot menüsüne girin. Boot menüsü anakarttan anakarta farklılık gösterse de genel olarak **F12**, **Del**, **Esc** ve **F2** tuşlarıdır. Daha fazla bilgi için `bu linke <https://www.technopat.net/sosyal/konu/boot-menuesue-kisayol-tuslari-veritabani.10898/>`_ bakabilirsiniz. 


Her şeye rağmen yine de USB veya DVD'den başlatamıyorsanız şu yolları deneyebilirsiniz:

**-** Bios'tan "Secure Boot"u devre dışı bırakmak.
**-** Boot menüsü yerine boot sırasını BIOS'tan değiştirmek. BIOS tuşunuzu öğrenmek için de `bu linke <https://www.technopat.net/sosyal/konu/boot-menuesue-kisayol-tuslari-veritabani.10898/>`_ bakabilirsiniz. 

.. figure:: _static/images/boot_menu.png
      :alt: Boot menüsüne ait bir fotoğraf.
      
      
Kuruluma Başlayın
-------------------
Bilgisayarımızı önyüklediğimiz aygıttan başlattık ve artık her şey hazır. İsterseniz TeArch Linux'u deneyebilirsiniz veya bilgisayarınıza kurabilirsiniz. Kurmak istiyorsanız ağaşıdaki adımları takip etmenizi öneriyoruz...

Kurulum Aracı Kullanımı
-------------------
TeArch Linux başlatıldıktan sonra kurulum aracı otomatik olarak açılmakta. Fakat kurulum aracını kapattıysanız veya kurulum aracı otomatik olarak açılmadıysa, kurulum aracını uygulamalar menüsünden açınız.

.. figure:: _static/images/tearch_gnome_appmenu.jpg
      :alt: TeArch Linux'a ait uygulama menüsü.


Genel Ayarları Yapmak
^^^^^^^^^
Kurulum aracı açıldıktan sonra sırayla; dil, zaman dilimi, klavye ve kullanıcı hesabı ayarlarını yapmanız istenecektir. Bu ayarları nasıl istiyorsanız öyle yapabilirsiniz. Ayrıca kullanıcı hesabı kısmında yaptığınız ayarlamaları bir yere not etmenizi öneriyoruz.

.. figure:: _static/images/tearch_user_account_settings.png
      :alt: Kullanıcı ayarları kısmı.


Disk Bölümlemesi
^^^^^^^^^
Kurulumun en önemli kısmı disk bölümlemesidir. Burada yapacağınız en ufak bir hata verilerinizin silinmesine veya kurulumun düzgün gerçekleştirilememesine sebep olabilir. Bu sebepten ötürü bu aşamada dikkatlı olmanızı tavsiye ediyoruz.

Disk bölüm ekranına geldiğinizde karşınıza 2 seçenek çıkmaktadır. Bunlardan **"Automated Installation"**, diskinizdeki her şeyi silerek yeni bölümler oluşturmaktadır. Eğer başka bölümleriniz varsa **"Manual Partitioning"** seçeneğini seçerek devam edebiliriz.

.. figure:: _static/images/tearch_disk_partitining.png
      :alt: Disk bölümleme seçeceği kısmı.
      
      
Manual Disk Bölümlemek
^^^^^^^^^
Manual disk bölümlemeye geçmeden önce sistemimiz **efi** destekliyor mu onu öğrenmeliyiz. Konsola **"efibootmgr"** yazdığımızda çıktı, **"EFI variables are not supported on this system"** şeklinde oluyorsa sistemimiz efi desteklemiyor demektir. Kurulumu yaparken buna dikkat etmemiz gerekecek.


EFI Destekleyen Bilgisayarlarda Kurulum Yapmak:
"""""""""
**"Manual Partitioning"** kısmına geldikten sonra bizi bölümlerimiz ve altta 2 buton karşılayacak. Biz yeni bölüm(ler) oluşturmak için alttaki **"Edit Partitions"** butonuna tıklayacağız.


Eğer bilgisayarımızda FAT32 ile formatlandırılmış bir disk bölümü yoksa elle kendimiz **"EFI Sistem Bölümü" (ESP)** oluşturmak zorundayız. Bunun için GParted'ı açtıktan sonra üstteki **+** simgesine tıklamalıyız. Oluşturacağınız ESP bölümünün özellikleri ise şunlar olmalıdır:

**-** Minimum 512 MiB alan.
**-** FAT32 dosya sisteminde oluşturmak.
**-** ESP bayrağı vermek. (Bunu diski oluşturduktan sonra diske sağ tıklayarak **"Manage flags"** menüsüne girerek vereceğiz.


ESP bölümünü oluşturduktan sonra sıra dosyalarımızın olacağı **ext4** dosya sistemine sahip disk bölümünü olşturmakta. Bu bölüme vereceğiniz alan size bağlı fakat minimum 15G alan vermenizi önermekteyiz.


Diskleri oluşturup üstteki **tik** işaretine tıkladıktan sonra GParted'a kapatıp kurulum aracımızdaki **"Refresh"** tuşuna basabiliriz. Bu sayede yeni oluşturduğumuz bölümler de kurulum aracına eklenecektir.


Burada ise yeni oluşturduğumuz 512MiB'lik boot alanını veya daha önce başka işletim sistemleri tarafından oluşturulan EFI alanına sağ tıklayıp **"Assign to /boot/efi"** tuşuna tıklamalıyız. Daha sonra da kendimiz oluşturduğumuz **"ext4"** formatındaki alana sağ tıklayıp **"Assign to /"** tuşuna tıklamalıyız. Artık her şeyimiz hazır, gönül rahatlığıyla **Next** diyebilirsiniz :)

.. figure:: _static/images/uefi_disk_partitining.png
      :alt: EFI disk bölümlendirme.
      

EFI Desteklemeyen (Eski BIOS) Bilgisayarlarda Kurulum Yapmak:
"""""""""
**"Manual Partitioning"** kısmına geldikten sonra bizi bölümlerimiz ve altta 2 buton karşılayacak. Biz yeni bölüm(ler) oluşturmak için alttaki **"Edit Partitions"** butonuna tıklayacağız.


İlk yapacağımız şey **ext4** dosya sistemine sahip disk bölümünü olşturmakta. Bu bölüme vereceğiniz alan size bağlı fakat minimum 15G alan vermenizi önermekteyiz.


Diski oluşturup üstteki **tik** işaretine tıkladıktan sonra GParted'a kapatıp kurulum aracımızdaki **"Refresh"** tuşuna basabiliriz. Bu sayede yeni oluşturduğumuz bölüm(ler) de kurulum aracına eklenecektir.


Buradaysa kendimiz oluşturduğumuz **"ext4"** formatındaki alana sağ tıklayıp **"Assign to /"** tuşuna tıklamalıyız. Artık her şeyimiz hazır, gönül rahatlığıyla **Next** diyebilirsiniz :)

.. figure:: _static/images/bios_disk_partitining.png
      :alt: BIOS disk bölümlendirme.
      

.. note:: Swap bölümünü oluşturmak zorunlu değil, 
	  bu yüzden anlatmadık. Eğer sistem belleğiniz 2G'dan azsa aynı yöntemleri izleyip "linux-swap" 	  dosyasistemine sahip bir swap alanı oluşturabilirsiniz. Daha sonra da bu bölümü aktifleştirmek 		  için "Assign to swap" tuşuna basabilirsiniz.
	  
.. warning:: Next dedikten sonra sisteminizin düzgün bir şekilde açılması için 
	  **"Install the GRUB boot menu on: /dev/sdx"** seçeneğindeki tiki kaldırmayınız lütfen.
	  
	  
Beklemek
^^^^^^^^^
Geriye kalan tek şey beklemek... TeArch Linux, sisteminize yaklaşık 15 dakika gibi kısa bir sürede kurulacaktır. Kurulum bittikten sonra bilgisayarınızı yeniden başlatın ve TeArch'ı kullanmaya hemen başlayın :)

.. figure:: _static/images/pic02.jpg
      :alt: Kurulumun bitmesini beklemek...
