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

```bash
git config --global user.mail "mailadresi"
git config --global user.name "İsim Soyisim"```

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

## .gitignore Dosyası İçin Bilmemiz Gereken Önemli Noktalar:

- Derleme sırasında oluşturulan `bin/`, `obj/` gibi klasörlerin repository’de yer almaması gerekiyor.
- IDE ayarlarını içeren `.vs/`, `vscode/`, `.idea/` gibi dizinlerin gereksiz yere paylaşılmaması için `.gitignore` dosyasına dahil edilmesi gerekiyor.
- `node_modules/` veya `packages/` gibi dosyalar, NuGet gibi paket yöneticileri tarafından tekrar indirilebileceği için `.gitignore` dosyasına dahil edilmelidir.
- Önbellek dosyaları, kilit dosyalar, log dosyaları yani `.log`, `.lock`, `.cache` gibi geçici dosyalar da `.gitignore` dosyasına dahil edilmelidir.

Daha ayrıntılı bilgi için: [Git Documentation](https://git-scm.com/doc)
