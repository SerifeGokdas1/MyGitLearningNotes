# MyGitAndGithubNotes

Bu repository, Git ve GitHub hakkında öğrendiğim ve geliştirdiğim bilgilerimi bir araya getirdiğim notlarımı içermektedir. Burada Git ve GitHub kullanımıyla ilgili temel komutlar, en iyi uygulamalar, hata çözüm önerileri, çeşitli versiyon kontrol teknikleri ve sık karşılaşılan problemler hakkında bilgiler bulabilirsiniz.

Amacım, Git ve GitHub’ı öğrenirken kaydettiğim önemli noktaları derleyerek hem kendi bilgimi pekiştirmek hem de başkalarına bu araçları daha etkili kullanma konusunda yardımcı olmaktır. Bu repository, yeni başlayanlar için bir rehber olabileceği gibi, daha ileri düzey kullanıcılar için de faydalı olabilecek bilgiler içermektedir.

## Notlar:
- Git ile versiyon kontrol yönetimi
- GitHub’da repository oluşturma ve yönetme
- Commit, push, pull, branch gibi temel komutlar
- Git kullanırken sık yapılan hatalar ve çözüm önerileri


# GIT, Source Control System (Versiyon Kontrol Sistemi)

Git, 2005 yılında Linux çekirdeğinin geliştirilmesi için yapılmıştır. GitHub ise, Git için bir hosting sistemidir. Git sayesinde proje içerisindeki dokümantasyonları izleyebilir ve geriye dönüş yapabiliriz. Ayrıca, nelerin versiyonlanmaması, takip edilmemesi gerektiğini de belirtebiliyoruz.

## En Çok Kullanılan Komutlar:

- `git init`: Projeyi oluştururken, initialize etme komutudur.
- `git add`: Oluşturduklarımızı ekler.
- `git commit`: Değişiklikleri kaydeder ve mesajla açıklanabilir.
- `git status`: Değişiklikleri görmemizi sağlar.
- `git push`: Uzak bilgisayara gönderir.
- `git pull`: Uzak bilgisayardan çeker.
- `git clone`: Projenin kopyasını alır.
- `git checkout`: Branch’ler arası geçiş yapılır.
- `git rm`: Silmek için kullanılır.

## Source Control System

![Versiyon Komut Sistemi](https://github.com/user-attachments/assets/13c3f26c-a871-4df5-921d-8b56835b68e9)

Buradaki temel komutların sırası ve mantığı için çok açıklayıcı bir görsel.
## Önemli Git Terimleri:

- **Untracked**: GIT tarafından takip edilmeyen, yeni oluşturulmuş dosyalar.
- **Unstaged**: Güncellenmiş ama commitlenmek için hazırlanmamış dosyalar.
- **Staged**: Commit etmeye hazır dosyalar.
- **Deleted**: Projeden silinmesine rağmen Git üzerinden kaldırılmamış dosyalar.

Bir proje açıldığında, ilk defa versiyon kontrol sistemi kullanılacaksa, `git init` komutunu kullanmalıyız. `git init` komutuyla aslında Git ile birlikte initialize et yani Git’le başlat demiş oluyoruz. `git init` komutu, projede `.git` adında gizli bir klasör oluşturur ve bu klasörle birlikte versiyon kontrol sistemini proje içerisinde kullanabiliyoruz.

## Git Konfigürasyonu:

Projede yaptıklarımızı uzak bilgisayara ilk defa göndermek istiyorsak, git konfigürasyon ayarlarında e-mail ve kullanıcı adımızı belirtmemiz gerekiyor. Burada şu komutları yazmamız gerekiyor:

`git config --global user.mail "mailadresi"`
`git config --global user.name "İsim Soyisim"`

## Branch ile İlgili Komutlar:
Branch, bir projedeki ana yapıyı bozmadan yeni değişiklikler denemek için kullanılan bir yapıdır. Örneğin, elinizde bir hamur var ve pizza yapmak istiyorsunuz. Bir parça hamuru alıp farklı malzemeler ekliyorsunuz. Eğer beğenirseniz, bu değişikliği ana pizzaya ekleyebilirsiniz. Git’te branch kullanmak, ana yapıyı bozmadan yeni özellikleri test etmek gibidir.

![image](https://github.com/user-attachments/assets/873f798e-2119-40eb-999e-4295a08aefb3)

- Projenize yerel veya uzak repository’de branch eklemek için `git branch branchismi` komutunu kullanabilirsiniz.
- Var olan tüm branch’leri görmek için, `git branch -a` komutunu kullanabilirsiniz.
- Eğer branch silmek isterseniz, `git branch -d branchadi` komutunu kullanabilirsiniz.
- Bir branch’teyken farklı bir branch’e geçmek istiyorsanız, `git checkout geçilecekbranchadi` komutunu kullanabilirsiniz.
- Yeni bir branch açıp direkt o branch’e geçiş yapmak için, `git checkout -b yenibranchadi` komutunu kullanmalısınız.
- Başka bir branch’te yaptığınız değişiklikleri kendi branch’inizle birleştirmek isterseniz, `git merge diğerbranchadi` komutunu kullanabilirsiniz.

## Git Status Komutu:
`git status` komutu ile proje içerisinde yapılan değişiklikleri görebiliyoruz. Eğer tüm değişiklikleri göndermek istiyorsak `git add .`, `git add *` veya `git add -A` komutlarını kullanabiliriz. Fakat sadece belirli bir dosyayı göndermek istiyorsak `git add index.html` gibi dosya adını belirterek komutu kullanmamız gerekiyor. `git add` komutuyla aslında değişiklik yapılan dosyayı **staged** (hazırlanmış) dosyalar ortamına göndermiş oluyoruz.

## Git RM Komutu:
`git add` komutunu kullanarak staged hale getirdiğimiz dosyayı takip edilmemesini sağlamak yani untracked hale getirebilmek için `git rm --cached dosyaadi` komutunu kullanabiliriz. Eğer dosyayı direkt olarak silmek istiyorsak, `git rm dosyaadi` komutunu kullanabiliriz. Yaptığımız bu eklemeyi local repository’ye göndermek için `git commit -m “Değişiklik açıklaması”` komutunu kullanıyoruz. Commit komutu aslında staged dosyalarını, yani commit edilmeye hazır olan dosyaları local repository’e gönderir.

## Eski Commit'lere Geri Dönmek:
Versiyon kontrol sisteminin bize sunduğu önemli özelliklerden biri, eski commit’lerimize geri dönebilmemizdir. Her commit, ayrı bir unique ID’ye sahiptir. Eski commit’lere geri dönerek hata veya kayıpları önleyebiliriz. Başka bir commit’e geçmek için `git checkout commitId` komutunu kullanabilirsiniz.

## Git Log Komutu:
`git commit -m “Açıklama”` komutunu yazdıktan sonra projede değişiklik yaptıysanız ve bunları görmek istiyorsanız, `git diff` komutunu kullanabilirsiniz. Geçmişte yaptığınız commit’leri ve bilgilerini görmek için `git log` komutunu kullanabiliriz. `git log` ile birlikte commit ID’si, commit’i yapan kişinin isim-soyisim bilgisi, commit tarihi ve mesajını görebiliyoruz.

## Git Push Komutu:
Bu eklediğimiz ve yorumunu yazdığımız değişikliği uzak bilgisayara asıl gönderecek komut ise `git push origin branchadi` komutudur. Eğer uzak repository’de bulunan dosyayı kendi bilgisayarımıza almak istiyorsak, `git clone repositoryUrl` komutunu kullanabiliriz.

## .gitignore Dosyası:
İçerisinde kod yazmadığınız veya hazır paket aldığınız dosyaları versiyon kontrol sistemi içerisinde tutmak istemezsiniz. Görselleri, videoları, logoları veya paket yöneticiyle gelen dosyaları da tutmak istemeyebiliriz. Proje içerisinde var olan bu öğeleri versiyon kontrol sistemi içerisinde tutmamak için `.gitignore` dosyasını kullanabiliriz. `.gitignore` dosyasına, görmezden gelmesini, önemsememesini istediğimiz öğeleri ekliyoruz.

Örneğin:

```gitignore
# .NET Core (Yazılım geliştirdiğiniz alanda kullanmamanız gereken yapıları ekleyebilirsiniz.)
project.lock.json
project.fragment.lock.json
artifacts/

# img (İstediğiniz resim türünü belirterek ekleyebilirsiniz.)
*.jpg
*.png
img/ (Buradaki gibi dosya şeklinde de belirtebilirsiniz.)

# videos (Video türlerini de ekleyebilirsiniz.)
*.mp4

# packages (Eklenmesini istemediğin paketleri belirtebilirsin.)
# log (Log dosyalarının yüklenmemesini belirtebilirsin.)
*.log

Password.txt (Proje içerisinde yazmış olduğun ama paylaşmak istemediğin herhangi bir dosyayı da burada belirtebilirsin.)```
```
## .gitignore Dosyası İçin Bilmemiz Gereken Önemli Noktalar:

- Derleme sırasında oluşturulan `bin/`, `obj/` gibi klasörlerin repository’de yer almaması gerekiyor.
- IDE ayarlarını içeren `.vs/`, `vscode/`, `.idea/` gibi dizinlerin gereksiz yere paylaşılmaması için `.gitignore` dosyasına dahil edilmesi gerekiyor.
- `node_modules/` veya `packages/` gibi dosyalar, NuGet gibi paket yöneticileri tarafından tekrar indirilebileceği için `.gitignore` dosyasına dahil edilmelidir.
- Önbellek dosyaları, kilit dosyalar, log dosyaları yani `.log`, `.lock`, `.cache` gibi geçici dosyalar da `.gitignore` dosyasına dahil edilmelidir.

# Commitledikten sonra yaptığınız değişiklikleri bu commite dahil etme:
Yaptığınız değişikliği commit ettiğiniz ve push etmeden önce başka değişiklikler de eklediniz. Burada önceden yaptığın commit içerisine bu değişiklikleri dahil etmek için `git add .` komutunu ve sonra `git commit --amend` komutunu yazman gerekiyor. Burada aynı zamanda commit'in mesajını da değiştirebiliriz. Mesajı da değiştirmek istiyorsan, `git commit --amend -m "Commit mesajını değiştirdim."` komutunu kullanmalısın. Yani `git commit --amend` komutuyla son yapılan commit'i tekrar düzenleyerek yeni bir commit oluşturabilirsin. Burada çok önemli bir nokta var, amend komutunu sadece push edilmemiş commitler için kullanman gerekiyor çünkü uzaktaki repo ile çakışma yaratabilir.

# Commit'i silmek:
Öncelikle commit'inin ID'sini bilmen gerekiyor. Commit ID'sini `git log` komutunu kullanarak öğrenebilirsin. Burada da birinci son commit bilgilerini görmek için `git log -n 1` komutunu da kullanabilirsin. Commit ID'sini en az 7 karakter olacak şekilde kopyalamalısın. (Logları listelediğin kısımdan `:q` yazarak geri çıkabilirsin.) Daha sonra `git revert CommitID` komutunu kullanarak yaptığın commit'i geri alabilirsin. Tabii bu şekilde verdiğin ID'li commit'i geri aldığına dair bir commit eklenmiş oluyor. Bu arada commit'i revert ettikten sonra pişman olup eski haline çevirmek istersen yine aynı mantıkla revert edilen commit'in ID'sini en az 7 karakter olacak şekilde kopyalayıp, `git revert CommitID` ile işlemini yapabilirsin. Eğer revert edip eski haline getirdiğini commit geçmişinde görünmesini istemiyorsan, yani herhangi bir commit daha eklemeden eski haline getirmek istiyorsan bunun için reset komutunu kullanabilirsin. Tabii bu çok doğru bir yöntem olmayabilir çünkü aradan commitler gidebilir ve geriye dönemeyeceğin için yazdığın kodları gözden kaybedebilirsin. Bunun yöntemi ise, `git reset --hard ensondönmekistediğinCommitID` komutudur. Bu komutun kullanımı çok dikkat gerektirir çünkü tüm geçici değişiklikler kaybolur. Bu yüzden önemli dosyalarınızı kaybetmemek için önceden commit veya stash yapmanızda fayda var.

# İki commit arasında yapılan değişiklikleri görmek:
Commitledikten sonra değişiklikler yapıp tekrar commit'ler oluşturdun. O eski commit ile yaptığın diğer commit arasındaki yani iki commit arasındaki değişiklikleri görmek isteyebilirsin. Bunun için tabii ki de eski commit ID'si ve diğer commit ID'sini `git log` ile bulup bir kopyalaman gerekiyor. Bunun için `git diff eskiCommitID..diğerCommitID` komutunu kullanman gerekiyor. Burada sadece bir dosya üzerinde bu iki commit arasında yapılan değişiklikleri de o dosyayı belirterek görebiliriz; `git diff eskiCommitID..diğerCommitID dosyaAdi`.

# Branch:
`git branch` komutuyla projedeki branch'leri listeleyebilirsiniz. `git branch yeniBranchAdi` komutuyla yeni branch oluşturabilirsiniz ama bu komutla oluşturduğun branch'e direkt gitmezsin, kendi olduğun branch'de kalırsın ve ekstra bir branch oluşturursun. Yeni oluşturduğun branch'e gidebilmek için `git checkout yeniBranchAdi` komutunu kullanmalısın. Hem branch oluşturup hem de o branch'e geçiş yapmak için, `git checkout -b yeniBranchAdi` komutunu kullanmalısın. Bu arada bulunduğun branch'teyken farklı branch oluşturursan, bulunduğun branch'teki tüm dosyalar yeni yaptığın branch'e eklenerek oluşturulur. Oluşturduğun bir branch'i silmek için `git branch -D silmekİstediğinBranchAdi` komutunu kullanmalısın.

# Son commit'inizden bu yana yaptığınız değişiklikleri saklamak ve istediğimiz zaman geri getirmek:
Commit yaptınız ve bu değişiklikler production ortamında kullanılıyor ama sonradan fark ettiniz ki yaptığınız değişikliklerden birinde bir problem var. Bu problemi bilmediğiniz için sonradan birçok değişiklik eklediniz. Bu senaryoda ilk olarak yaptığın değişikleri bir yere kaydetmen ve daha sonra o problemi çözmen lazım. Burada da imdadımıza stash komutu yetişiyor. Stash, yaptığın değişiklikleri geçici olarak saklar ve çalışma alanını temiz tutar. Son commit'ten itibaren yaptığın tüm değişiklikleri stash'de geçici olarak saklayabilirsin. Stash'dekileri görmek için `git stash list` komutunu, bu listeyi silmek için `git stash clear` komutunu kullanabilirsin. Stash komutuyla yaptığın değişiklikleri sakladın ve sonradan o problemi çözdün diyelim. Sakladığın değişiklikleri geri getirmek için `git stash pop` ya da `git stash apply stashID` komutunu kullanabilirsin. Stash ID'sini bulmak için `git stash list` komutunu kullanabilirsin. Burada `git stash pop` ve `git stash apply stashID` komutları arasındaki farkı anlatmak istiyorum. `git stash pop` komutu en son stash'i getirir ve o en son stash'i listeden siler. `git stash apply stashID` komutu ise, belirttiğin ID'li stash'i geri getirir ve stash listeden silinmeden saklanmaya devam eder.

# Branch'lerde yapılan değişiklikleri birleştirmek:
Birkaç branch açtın ve burada kodlarını yazdın. Günün sonunda bu yaptığın değişiklikleri master branch'ine aktarman gerekiyor. Örneğin master branch'indeyken otherBranch adındaki branch'teki değişiklikleri buraya almak istiyorsun. Bunun için `git merge otherBranch` komutunu kullanarak otherBranch'de yaptıklarını master branch'ine eklenmesini sağlayabilirsin. Ama sen bu yaptığın merge işlemini de bir commit yapmak istersen o zaman, `git merge --squash otherBranch` komutunu ve daha sonra `git commit -m "otherBranch'te yapılan değişiklikler master branch'i ile merge edildi"` komutunu yazarak bu merge işlemini de commit'leyebilirsin. Burada `--squash` kullandıysan commitkomutunu da kullanman gerektiğini söylemeliyim. Bu sayede eğer merge işlemini geri almak istersen yukarıda belirttiğim şekilde commit'i geri alarak rahatlıkla yapabilirsin. Bu arada eğer merge komutunda `--squash` kullanırsan otherBranch'daki yaptığın tüm commit'leri tek tek master'da göstermez, sadece o yaptığın merge commit'i gelir ama `--squash` eklemezsen otherBranch'daki commit'ler master'a gelir ve geriye dönmek istersen hata oranını arttırabilir. İki branch'i birleştirmenin farklı bir yöntemi ise, rebase komutudur. `git rebase otherBranch` komutuyla iki branch'i birleştirebilirsin. Merge ve rebase arasındaki en önemli fark commit'leri işleme şeklidir. Merge, iki branch'in geçmişini birleştirerek, iki branch'in geçmişini olduğu gibi koruyarak mevcut branch'e dahil eder ve dalgalı bir görünüm alır. Burada her iki branch'in geçmişi ayrı ayrı görünebilir ve geriye dönük inceleme yapılmasını kolaylaştırır. Rebase ise, eklediğin branch'in commit'lerini mevcut branch'inin commit'lerinin üzerine lineer-düz bir yapıda sıralar ve geçmişi yeniden yazar. OtherBranch'daki commit'ler sanki mevcut branch'daki commit'lerden sonra yapılmış gibi sona eklenir. Merge komutunun daha güvenilir olduğunu ve rebase komutunun da temiz bir geçmiş oluşturduğunu söyleyebiliriz. Rebase komutunu kullanırken dikkatli olmak gerekir çünkü bu komut commit'leri yeniden yazdığından, paylaşılan branch'lerde çatışmalar veya problemler yaratabilir.

# Branch'ler birleştirilirken çıkan çakışmaları düzeltmek:
Merge işleminden sonra conflict çıkarsa kodlara bakıp bu conflicte sebep olan noktaları düzenledikten sonra `git add .` ve `git commit -m "Merge tamamlandı"` komutlarıyla sorunu çözebilirsin. Eğer conflict aldıktan sonra merge işlemini geri çekmek istersen `git merge --abort` komutunu kullanabilirsin.


Daha ayrıntılı bilgi için: [Git Documentation](https://git-scm.com/doc)
