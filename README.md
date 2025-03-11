# -eviri
.
# Kabuk

Dünya sizin istiridyenizdir ya da aslında kabuk sizin istiridyenizdir. Kabuk nedir? Kabuk temel olarak komutlarınızı klavyeden alan ve bunları gerçekleştirmesi için işletim sistemine gönderen bir programdır. Daha önce bir GUI kullandıysanız, muhtemelen “Terminal” veya “Console” gibi programlar görmüşsünüzdür, bunlar sadece sizin için bir kabuk başlatan programlardır. Tüm bu kurs boyunca kabuğun harikalarını öğreneceğiz.
Bu derste bash (Bourne Again shell) kabuk programını kullanacağız, neredeyse tüm Linux dağıtımları varsayılan olarak bash kabuğunu kullanacaktır. Ksh, zsh, tsch gibi başka kabuklar da mevcut, ancak bunların hiçbirine girmeyeceğiz.
Hadi hemen başlayalım! Dağıtıma bağlı olarak kabuk isteminiz değişebilir, ancak çoğunlukla aşağıdaki biçime uymalıdır:

    username@hostname:current_director
    pete@icebox:/home/pete $

Komut isteminin sonundaki $ işaretine dikkat ettiniz mi? Farklı kabukların farklı komut istemleri olacaktır, bizim durumumuzda $, Bash, Bourne veya Korn kabuğunu kullanan normal bir kullanıcı içindir, komutu yazarken komut istemi sembolünü eklemezsiniz, sadece orada olduğunu bilirsiniz.
Basit bir komutla başlayalım, echo. echo komutu sadece metin argümanlarını ekrana yazdırır.

    $ echo Merhaba Dünya
## pwd (Çalışma Dizinini Yazdır)

Linux'ta her şey bir dosyadır, Linux'un derinliklerine indikçe bunu anlayacaksınız, ancak şimdilik bunu aklınızda tutun. Her dosya hiyerarşik bir dizin ağacında düzenlenmiştir. Dosya sistemindeki ilk dizin uygun bir şekilde kök dizin olarak adlandırılır. Kök dizin, daha fazla klasör ve dosya vb. depolayabileceğiniz birçok klasör ve dosyaya sahiptir. İşte dizin ağacının neye benzediğine dair bir örnek:

    /
      
    |-- bin
      
    |   |-- file1
      
    |   |-- file2
      
    |-- etc
      
    |   |-- file3
      
    |   `-- directory1
      
    |       |-- file4
      
    |       `-- file5
      
    |-- home
      
    |-- var
Bu dosya ve dizinlerin konumu yol olarak adlandırılır. Eğer home adında bir klasörünüz ve içinde pete adında bir klasörünüz ve bu klasörün içinde Movies adında başka bir klasörünüz varsa, bu yol şöyle görünür: /home/pete/Movies, oldukça basit değil mi?

Dosya sisteminde gezinmek, tıpkı gerçek hayatta olduğu gibi, nerede olduğunuzu ve nereye gittiğinizi bilmeniz açısından faydalıdır. Nerede olduğunuzu görmek için pwd komutunu kullanabilirsiniz, bu komut “çalışma dizinini yazdır” anlamına gelir ve size sadece hangi dizinde olduğunuzu gösterir, yolun kök dizinden kaynaklandığına dikkat edin.

    $ pwd
Neredesin sen? Neredeyim ben? Bir dene bakalım.
## cd (Dizin Değiştir)
Artık nerede olduğunuzu bildiğinize göre, dosya sisteminde biraz dolaşıp dolaşamayacağımızı görelim. Yolları kullanarak yolumuzu bulmamız gerektiğini unutmayın. Bir yol belirtmenin mutlak ve göreceli yollar olmak üzere iki farklı yolu vardır.
Mutlak yol: Bu, kök dizinden gelen yoldur. Kök dizin baş dizindir. Kök dizin genellikle eğik çizgi olarak gösterilir. Yolunuz her / ile başladığında, kök dizinden başladığınız anlamına gelir. Örneğin, /home/pete/Masaüstü.
Göreceli yol: Bu, şu anda dosya sisteminde bulunduğunuz yerden itibaren olan yoldur. Eğer /home/pete/Documents konumundaysam ve Documents içinde taxes adlı bir dizine ulaşmak istiyorsam, /home/pete/Documents/taxes gibi kök dizinden itibaren tüm yolu belirtmek zorunda değilim, bunun yerine taxes/ dizinine gidebilirim.
Artık yolların nasıl çalıştığını bildiğinize göre, istediğimiz dizine geçmemize yardımcı olacak bir şeye ihtiyacımız var. Neyse ki bunu yapmak için cd ya da “change directory” var.

    $ cd /home/pete/Pictures
Şimdi dizin konumumu /home/pete/Pictures olarak değiştirdim.

Şimdi bu dizinin içinde Hawaii adında bir klasörüm var, bu klasöre şu şekilde gidebilirim:

    $ cd Hawaii
   

 Sadece klasörün adını nasıl kullandığımı fark ettiniz mi? Çünkü zaten `/home/pete/Pictures` içindeydim.

Her zaman mutlak ve göreceli yollarla gezin ek oldukça yorucu olabilir, neyse ki size yardımcı olacak bazı kısayollar var.

. (geçerli dizin). Bu, şu anda içinde bulunduğunuz dizindir.

  . (üst dizin). Sizi bulunduğunuz dizinin bir üstündeki dizine
   götürür.

 . (ev dizini). Bu dizin varsayılan olarak sizin “ev dizininiz ”dir.
   Örneğin /home/pete.
 . (önceki dizin). Bu sizi bulunduğunuz dizinden bir önceki dizine götürür.

## 


    $ cd .
      
    $ cd ..
      
    $ cd ~
      
    $ cd -
Onları bir deneyin!
## ls (Dizinleri Listele)
Artık sistemde nasıl hareket edeceğimizi bildiğimize göre, bize neyin açık olduğunu nasıl anlayacağız? Şu anda sanki karanlıkta hareket ediyor gibiyiz. Dizin içeriklerini listelemek için harika ls komutunu kullanabiliriz. ls komutu varsayılan olarak geçerli dizindeki dizinleri ve dosyaları listeleyecektir, ancak dizinleri listelemek istediğiniz yolu belirtebilirsiniz.

    $ ls
      
    $ ls /home/pete
ls oldukça kullanışlı bir araçtır, ayrıca baktığınız dosya ve dizinler hakkında ayrıntılı bilgi gösterir.

Ayrıca bir dizindeki tüm dosyaların görünür olmayacağını unutmayın. ile başlayan dosya adları gizlidir, ancak bunları ls komutuyla görüntüleyebilir ve -a bayrağını iletebilirsiniz (tümü için a).
 

       $ ls -a
Ayrıca kullanışlı bir ls bayrağı daha vardır, -l uzun için, bu uzun bir formatta dosyaların ayrıntılı bir listesini gösterir. Bu size soldan başlayarak ayrıntılı bilgiler gösterecektir: dosya izinleri, bağlantı sayısı, sahip adı, sahip grubu, dosya boyutu, son değişiklik zaman damgası ve dosya / dizin adı.

  

      $ ls -l
      
    pete@icebox:~$ ls -l
      
    total 80
      
    drwxr-x--- 7 pete penguingroup   4096 Nov 20 16:37 Desktop
      
    drwxr-x--- 2 pete penguingroup   4096 Oct 19 10:46  Documents
      
    drwxr-x--- 4 pete penguingroup   4096 Nov 20 09:30 Downloads
      
    drwxr-x--- 2 pete penguingroup   4096 Oct  7 13:13   Music
      
    drwxr-x--- 2 pete penguingroup   4096 Sep 21 14:02 Pictures
      
    drwxr-x--- 2 pete penguingroup   4096 Jul 27 12:41   Public
      
    drwxr-x--- 2 pete penguingroup   4096 Jul 27 12:41   Templates
      
    drwxr-x--- 2 pete penguingroup   4096 Jul 27 12:41   Videos
Komutlar, daha fazla işlevsellik eklemek için bayrak (veya argüman veya seçenek, ne derseniz deyin) adı verilen şeylere sahiptir. Nasıl -a ve -l eklediğimizi gördünüz mü, -la ile ikisini birlikte ekleyebilirsiniz. Bayrakların sırası hangi sırada gideceğini belirler, çoğu zaman bu gerçekten önemli değildir, bu yüzden ls -al da yapabilirsiniz ve yine de çalışır.

    $ ls -la
## Dokunmak
Bazı dosyaları nasıl oluşturacağımızı öğrenelim. Çok basit bir yol touch komutunu kullanmaktır. Touch yeni boş dosyalar oluşturmanızı sağlar.

    $ touch mysuperduperfile
Ve bom, yeni dosya!

Dokunma, mevcut dosya ve dizinlerdeki zaman damgalarını değiştirmek için de kullanılır. Bir deneyin, bir dosyada ls -l yapın ve zaman damgasını not edin, sonra o dosyaya dokunun ve zaman damgasını güncelleyecektir.

Dosya oluşturmanın yönlendirme ve metin editörleri gibi başka birçok yolu vardır, ancak bu konuya Metin Manipülasyonu dersinde değineceğiz.
### man
Vah, keşke bu programlardan bazıları hakkında daha fazla bilgi görebilmek için bir kullanım kılavuzuna sahip olsak. Neyse ki, sahipler! Man sayfaları olarak adlandırılan bu kılavuzlara, man komutuyla erişebilirsiniz.

    $ man ls

Man sayfaları, çoğu Linux işletim sistemine varsayılan olarak entegre edilmiş kullanım kılavuzlarıdır. Komutlar ve sistemin diğer yönleri hakkında belge sağlarlar.

Birkaç komut üzerinde deneyerek daha fazla bilgi edinin.
### whatis
Vah, şimdiye kadar epeyce komut öğrendik. Eğer bir komutun ne işe yaradığından şüpheye düşerseniz, whatis komutunu kullanabilirsiniz. Whatis komutu, komut satırı programlarının kısa bir açıklamasını sağlar.

    $ whatis cat

Açıklama, her komutun kullanım kılavuz sayfasından alınır. Eğer whatis cat komutunu çalıştırırsanız, kısa bir açıklama içeren küçük bir metin göreceksiniz.
### alias
Bazen komutları yazmak gerçekten tekrarlı hale gelebilir ya da uzun bir komutu defalarca yazmanız gerektiğinde, bunun için kullanabileceğiniz bir takma ad (alias) oluşturmak en iyisidir. Bir komut için takma ad oluşturmak için, basitçe bir takma ad adı belirleyip bunu komutla ilişkilendirirsiniz.

    $ alias foobar='ls -la'

Artık ls -la yazmak yerine, foobar yazabilirsiniz ve bu komut çalıştırılacaktır; oldukça kullanışlı bir şey. Ancak unutmayın ki, bu komut bilgisayarınızı yeniden başlattığınızda takma adınızı kaybetmez, bu yüzden kalıcı bir takma ad eklemeniz gerekecek:

    ~/.bashrc

Veya benzer dosyalar, eğer yeniden başlatma sonrasında takma adınızın kalıcı olmasını istiyorsanız.

Takma adları unalias komutuyla kaldırabilirsiniz:

    $ unalias foobar`
### exit
Gerçekten temelleri çok iyi öğrendin. Henüz yüzeyin sadece üstünü kazıdık, şimdi emeklemeyi öğrendin, bir sonraki derslerde sana yürümeyi öğretmeye başlayacağım.

Şu an için kendini tebrik edebilir ve bir mola verebilirsin. Shell'den çıkmak için exit komutunu kullanabilirsin.

    $ exit

Veya logout komutunu da kullanabilirsin.

    $ logout
Veya bir terminal GUI'si kullanıyorsanız, terminali kapatabilirsiniz. Bir sonraki derste görüşmek üzere!
## cp (Copy)

Bu dosyaların bazı kopyalarını oluşturmaya başlayalım. Diğer işletim sistemlerinde dosyaları kopyalayıp yapıştırmak gibi, kabuk bize bunu yapmanın daha da basit bir yolunu sunar.

    $ cp mycoolfile /home/pete/Documents/cooldocs
mycoolfile kopyalamak istediğiniz dosya ve /home/pete/Documents/cooldocs dosyayı kopyalayacağınız yerdir.

Birden fazla dosya ve dizini kopyalayabileceğiniz gibi joker karakterler de kullanabilirsiniz. Joker karakter, desen tabanlı bir seçimin yerine kullanılabilen ve aramalarda size daha fazla esneklik sağlayan bir karakterdir. Daha fazla esneklik için joker karakterleri her komutta kullanabilirsiniz.

 - Joker karakterlerin joker karakteri olan *, tüm tek karakterleri veya herhangi bir dizeyi temsil etmek için kullanılır.
 - ? bir karakteri temsil etmek için kullanılır
 - [] parantez içindeki herhangi bir karakteri temsil etmek için kullanılır
 - 


 



      $ cp *.jpg /home/pete/Pictures

Bu, geçerli dizininizdeki .jpg uzantılı tüm dosyaları Resimler dizinine kopyalayacaktır.

Yararlı bir komut -r bayrağını kullanmaktır, bu bir dizin içindeki dosyaları ve dizinleri özyinelemeli olarak kopyalayacaktır.

Belgeler dizininize birkaç dosya içeren bir dizinde cp yapmayı deneyin. İşe yaramadı değil mi? Çünkü -r komutu ile içindeki dosya ve dizinleri de kopyalamanız gerekecek.

    $ cp -r Pumpkin/ /home/pete/Documents
Dikkat edilmesi gereken bir husus, bir dosyayı aynı dosya adına sahip bir dizine kopyalarsanız, dosyanın üzerine kopyaladığınız şey yazılacaktır. Eğer yanlışlıkla üzerine yazılmasını istemediğiniz bir dosyanız varsa bu hiç de iyi bir şey değildir. Bir dosyanın üzerine yazmadan önce sizi uyarması için -i bayrağını (etkileşimli) kullanabilirsiniz.

    $ cp -i mycoolfile /home/pete/Pictures
## mv (Move)
Dosyaları taşımak ve yeniden adlandırmak için kullanılır. Bayraklar ve işlevsellik açısından cp komutuna oldukça benzer.
Dosyaları bu şekilde yeniden adlandırabilirsiniz:

    $ mv oldfile newfile
Ya da bir dosyayı farklı bir dizine taşıyabilirsiniz:

    $ mv file2 /home/pete/Documents
Ve birden fazla dosya taşıyın:

    $ mv file_1 file_2 /somedirectory
Dizinleri de yeniden adlandırabilirsiniz:

    $ mv directory1 directory2
cp gibi, bir dosyayı veya dizini mv yaparsanız, aynı dizindeki herhangi bir şeyin üzerine yazacaktır. Bu yüzden herhangi bir şeyin üzerine yazmadan önce sizi uyarması için -i bayrağını kullanabilirsiniz.

    mv -i directory1 directory2
Diyelim ki bir öncekinin üzerine yazmak için bir dosyayı mv yapmak istediniz. Bu dosyanın yedeğini de alabilirsiniz ve eski sürümü ~ ile yeniden adlandıracaktır.

    $ mv -b directory1 directory2
## mkdir (Make Directory)
Üzerinde çalıştığımız tüm bu dosyaları saklamak için bazı dizinlere ihtiyacımız olacak. Bunun için mkdir (Dizin Oluştur) komutu kullanışlıdır, zaten mevcut değilse bir dizin oluşturacaktır. Aynı anda birden fazla dizin bile oluşturabilirsiniz.

    $ mkdir books paintings
Aynı zamanda -p (üst bayrak) ile alt dizinler de oluşturabilirsiniz.

    $ mkdir -p books/hemmingway/favorites
## rm (Remove)
Şimdi sanırım çok fazla dosyamız var, bazı dosyaları kaldıralım. Dosyaları kaldırmak için rm komutunu kullanabilirsiniz. rm (remove) komutu dosya ve dizinleri silmek için kullanılır.

    $ rm file1
Rm kullanırken dikkatli olun, kaldırılan dosyaları bulup çıkarabileceğiniz sihirli bir çöp kutusu yoktur. Bir kez silindiklerinde sonsuza kadar silinirler, bu yüzden dikkatli olun.

Neyse ki bazı güvenlik önlemleri vardır, böylece sıradan bir kişi bir sürü önemli dosyayı kaldıramaz. Yazmaya karşı korumalı dosyalar silinmeden önce sizden onay isteyecektir. Eğer bir dizin yazmaya karşı korumalıysa, o da kolayca kaldırılamayacaktır.

Bunların hiçbiri umurunuzda değilse, bir grup dosyayı kesinlikle kaldırabilirsiniz.

    $ rm -f file1
-f ya da force seçeneği rm'ye yazma korumalı olsun ya da olmasın tüm dosyaları kullanıcıya sormadan kaldırmasını söyler (uygun izinlere sahip olduğunuz sürece).

    $ rm -i file
Diğer komutların birçoğunda olduğu gibi -i bayrağını eklediğinizde, dosyaları veya dizinleri gerçekten kaldırmak isteyip istemediğinizi soracaktır.

    $ rm -r directory
Varsayılan olarak bir dizini sadece rm yapamazsınız, tüm dosyaları ve sahip olabileceği alt dizinleri kaldırmak için -r bayrağını (özyinelemeli) eklemeniz gerekir.

Bir dizini rmdir komutu ile kaldırabilirsiniz.

    $ rmdir directory
## find
Sistemde sahip olduğumuz tüm bu dosyalarla, belirli bir dosyayı bulmaya çalışmak biraz telaşlı olabilir. Bunun için kullanabileceğimiz bir komut var, find!

    $ find /home -name puppies.jpg

find ile arama yapacağınız dizini ve ne aradığınızı belirtmeniz gerekir, bu durumda puppies.jpg adında bir dosya bulmaya çalışıyoruz.

Ne tür bir dosya bulmaya çalıştığınızı belirtebilirsiniz.

    $ find /home -type d -name MyFolder
Bulmaya çalıştığım dosya türünü dizin için (d) olarak ayarladığımı ve hala MyFolder adıyla arama yaptığımı görebilirsiniz.

Unutulmaması gereken güzel bir şey de find'un aradığınız dizinde durmadığı, o dizinin sahip olabileceği tüm alt dizinlerin içine de bakacağıdır.
## help
Linux, bir komutu nasıl kullanacağınıza veya bir komut için hangi bayrakların mevcut olduğunu kontrol etmenize yardımcı olacak bazı harika yerleşik araçlara sahiptir. Bu araçlardan biri olan help, diğer bash komutları (echo, logout, pwd, vb.) için yardım sağlayan yerleşik bir bash komutudur.

    $ `help` echo
Bu size bir açıklama ve echo'yu çalıştırmak istediğinizde kullanabileceğiniz seçenekleri verecektir. Diğer çalıştırılabilir programlar için --help ya da benzeri bir seçeneğin olması gelenekseldir.

    $ echo --help
Yürütülebilir dosyaları gönderen tüm geliştiriciler bu standarda uymayacaktır, ancak bir program hakkında yardım bulmak için muhtemelen en iyi şansınız budur.

### file
Önceki derste *touch* hakkında öğrendik, şimdi buna biraz geri dönelim. Dosya adının, muhtemelen Windows gibi diğer işletim sistemlerinde gördüğünüz standart adlandırmaya uymadığını fark ettiniz mi? Normalde *banana.jpeg* adlı bir dosya görür ve bunun bir *JPEG resim dosyası* olduğunu beklersiniz.

Linux'ta dosya adlarının dosyanın içeriğini temsil etmesi gerekmez. *funny.gif* adlı bir dosya oluşturabilirsiniz, ancak bu aslında bir *GIF dosyası olmayabilir*.

Bir dosyanın ne tür bir dosya olduğunu öğrenmek için *file* komutunu kullanabilirsiniz. Bu komut, dosyanın içeriği hakkında bir açıklama gösterir.

    $ file banana.jpg
### cat

Neredeyse dosyalar arasında gezinmeyi tamamladık, ancak önce bir dosyanın nasıl okunacağını öğrenelim. Kullanabileceğiniz basit bir komut *cat* komutudur. *Concatenate* (birleştirmek) kelimesinin kısaltması olan bu komut, sadece dosya içeriğini görüntülemekle kalmaz, aynı zamanda birden fazla dosyayı birleştirerek çıktısını da gösterebilir.

    $ cat dogfile birdfile
    
   Büyük dosyaları görüntülemek için pek uygun değildir ve yalnızca kısa içerikler için kullanılması önerilir. Daha büyük metin dosyalarını görüntülemek için kullandığımız birçok başka araç vardır ve bunları bir sonraki derste ele alacağız.
### less
Eğer basit bir çıktının ötesinde büyük metin dosyalarını görüntülüyorsanız, *less daha iyidir. (Aslında benzer bir işlevi olan **more* adlı bir komut da vardır, bu yüzden bu biraz ironiktir.)

*less* komutu, metni *sayfa sayfa görüntüleyerek* gezinmenize olanak tanır.

Şimdi bir dosyanın içeriğini *less* komutuyla görüntüleyin. *less* içinde olduğunuzda, dosyada gezinmek için farklı klavye komutlarını da kullanabilirsiniz.

    $ less /home/pete/Documents/text1
Aşağıdaki komutları kullanarak *less* içinde gezinebilirsiniz:

-   *q* - *less* komutundan çıkıp shell'e geri dönmek için kullanılır.
-   *Page Up, Page Down, Yukarı ve Aşağı Ok Tuşları* - Sayfa ve ok tuşlarını kullanarak gezinmenizi sağlar.
-   *g* - Metin dosyasının *başına* gider.
-   *G* - Metin dosyasının *sonuna* gider.
-   */arama* - Metin dosyası içinde belirli bir kelimeyi veya ifadeyi aramak için kullanılır. Aramak istediğiniz kelimenin başına */* koymalısınız.
-   *h* - *less* içinde nasıl kullanılacağını öğrenmek için yardım menüsünü açar.
### history
Shell'inizde daha önce girdiğiniz komutların bir geçmişi bulunur ve bu komutları görüntüleyebilirsiniz. Bu özellik, özellikle daha önce kullandığınız bir komutu *yeniden yazmadan* bulup çalıştırmak istediğinizde oldukça kullanışlıdır.

    $ history
Önceki komutu tekrar çalıştırmak mı istiyorsunuz? *Yukarı ok tuşuna* basmanız yeterli.

Önceki komutu yazmadan çalıştırmak için *!!* kullanabilirsiniz. Örneğin, *cat file1* komutunu çalıştırdıysanız ve tekrar çalıştırmak istiyorsanız, sadece *!!* yazıp Enter'a basabilirsiniz.

Bir başka geçmiş kısayolu ise *Ctrl + R* kombinasyonudur. Bu, *tersine arama* komutudur. *Ctrl + R* tuşlarına bastıktan sonra aramak istediğiniz komutun birkaç harfini yazarsanız, eşleşen komutları görüntüler. *Tekrar Ctrl + R* tuşuna basarak önceki eşleşmelere göz atabilirsiniz. Kullanmak istediğiniz komutu bulduğunuzda *Enter* tuşuna basarak çalıştırabilirsiniz.

Terminalimiz biraz kalabalık görünüyor, değil mi? Biraz temizlik yapalım. Görüntüyü temizlemek için *clear* komutunu kullanabilirsiniz.

    $ clear
İşte böyle, şimdi daha iyi görünüyor, değil mi?

Kullanışlı özelliklerden bahsetmişken, *komut satırındaki en faydalı özelliklerden biri* de *Tab tamamlama*dır.

Bir komut, dosya veya dizinin *başlangıcını yazıp* *Tab* tuşuna bastığınızda, eğer dizinde o harflerle başlayan başka dosya yoksa otomatik olarak tamamlanır.

Örneğin, *chrome* komutunu çalıştırmak istiyorsanız, sadece *chr* yazıp *Tab* tuşuna basabilirsiniz ve *chrome* otomatik olarak tamamlanır.

