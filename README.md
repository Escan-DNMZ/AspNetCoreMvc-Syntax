# AspNetCoreMvc-Syntax
All Notes belong to me
## Proje oluşturma

Öncelikle konsolumuza dotnet verisonumuzu öğrenmek için (dotnet —version) yazıyoruz

ardından masaüstümüzüe yeni klasör oluşturuyoruz adı çok da önemli değil ardından o klasörün içine siteadi.webui adında bir klasör daha oluşturuyoruz ardından tekrar terminale dönüp cd diyip dosya adını yazdıkdan sonra terminale şunları yazıyoruz (dotnet new globaljson —-sdk-version 3.1.401(sizin versiyon neyse)) bunu yazdıkdan sonrada (dotnet new web yazıyoruz) tebrikler çalışma dosyası oluşturuldu

## Proje çalıştırma

<img width="699" alt="Screen Shot 2021-09-03 at 13 06 26" src="https://user-images.githubusercontent.com/84273839/158033573-c0fc898d-11c9-4096-825c-5b904c33aa99.png">


```csharp
//Öncelikle yazdığınız kodları görüntülemek için girmeniz gereken local host var
//Buna girmek için vscode daki terminal alanına dotnet run yazabilirsiniz
//örnek: https://localhost:5001
```

---

## Mvc Patters
<img width="699" alt="1" src="https://user-images.githubusercontent.com/84273839/158033622-74f64811-e0fd-4946-9796-4ce5ec04bc88.png">
<img width="615" alt="2" src="https://user-images.githubusercontent.com/84273839/158033625-7a2f6631-e9ad-47b6-a6d1-0c0411f7db22.png">
<img width="153" alt="3" src="https://user-images.githubusercontent.com/84273839/158033627-1f5ce4f3-6c0e-4023-9152-d9259f7d2c20.png">

**Controllers Models ve Views dosyalarını ekliyoru**
<img width="550" alt="4" src="https://user-images.githubusercontent.com/84273839/158033631-64cded46-c1b8-4617-85bf-ae704a6a67b3.png">

<img width="947" alt="5" src="https://user-images.githubusercontent.com/84273839/158033633-02bf8d88-c918-4ca4-bb1b-0ff12ae99bc9.png">


---

---

## **Default Routing**

kullanıcı direk bağlandığında ona direk index sayfasını göstermeli veya kişi [localhost:5000/product](http://localhost:5000/product) yazdığında ona direkt product/list i vermeli bunun için ise bir action kodu yazacağız

<img width="1045" alt="6" src="https://user-images.githubusercontent.com/84273839/158033648-c0223880-536a-4937-8ac0-0e15394ff33c.png">


controller=home diyerek sayfayı otomatik home da çalıştırıcaz aynı şekilde / sonrası ikinci alanda product yazdık diyelim ve sonrasını yazmadık bizi otomatik product ın index sayfasına atacak

---

## Views

Öncelikle önceden About gibi alanlarda hep bir string değer yazdırdık şimdi ise dinamik bir html 

aktarmak istiyoruz bunun için ise IActionResult değerini kullanmalıyız ve return alanına View(); girmeliyiz Not: bunu ProductController da da yapın

<img width="432" alt="7" src="https://user-images.githubusercontent.com/84273839/158033702-dd967736-4621-4088-a2f4-f1237df37c91.png">
<img width="170" alt="8" src="https://user-images.githubusercontent.com/84273839/158033706-656b80cf-58b5-42c2-8a19-b73c1fb227b6.png">


Views klasörüne Home ve Product klasörlerini oluşturun Home klasörüne Index ve About için html klasörü oluşturun aynısını Product için de yapın ve dotnet run diyerek sonucu görün

---

## ViewBag

Verilerimizi Controller dan View kısmına aktarmak için kullanırız

Mesela atıyorum biz index.cshtml sayfamızda kullanıcıya  Günaydın ...., nasılsınız yazdırmak istiyorum bunu nasıl yapacağım  öncelikle Index sayfamızı dinamik yapmak için HomeController 

sayfamızdan ViewBag leri eklemeliyiz saate göre bize iyi günler veya günaydın yazdıracak

<img width="597" alt="9" src="https://user-images.githubusercontent.com/84273839/158033722-91744c36-455c-4c90-933c-2cd606de7f3f.png">

Index html alanında ise bunları tanımlıyoruz @ViewBag.greeting şeklinde

<img width="597" alt="10" src="https://user-images.githubusercontent.com/84273839/158033734-80ca3b29-74e6-4df2-9b4d-3839160da869.png">

---

## Models

Projenin iş mantığının tasarlandığı bölümdür, veritabanı modelleri başta olmak üzere görüntü verebilecek ve işlem yapılabilinecek modelleri burada tanımlarsınız. Bu modelleri projenizde size fazlasıyla yardımı olurlar. Doğrulama (Validation) işlemleri bu bölümde yapılabilinir.

Öncelikle model ile daha basit ve düzenli dinamik veri yapabiliyoruz öncelikle oluşturduğumuz models dosyasında Product.cs adında bir class oluşturuyoruz ardından

<img width="196" alt="11" src="https://user-images.githubusercontent.com/84273839/158033765-94903db9-42f8-414e-ad5e-a76261984463.png">

Name,Price,Description gibi bilgileri giriyoruz

<img width="501" alt="12" src="https://user-images.githubusercontent.com/84273839/158033772-ccde81ba-3091-4be8-b0ae-149ae1053c8b.png">

Ardından Controllers dan ProductController a dönüyoruz ve...

<img width="205" alt="13" src="https://user-images.githubusercontent.com/84273839/158033777-c6101aa0-6659-431d-a1b4-a053739b3330.png">


Details alanında p değişkenine Product class ını tanımlıyorun (Not: namespace ini eklemeyi unutmayın cmd+. ile) ardından ve ardından değerlerini giriyoruz View() de ise p değişkenini döndürtüyoruz

<img width="410" alt="14" src="https://user-images.githubusercontent.com/84273839/158033782-8dd41148-390e-4aad-a9e6-cacf21fea15f.png">

Ardından Product kalasöründeki Details.cshtml dosyasına gelerek html kodlarında ufak bir değişiklik yapıyoruz

<img width="190" alt="15" src="https://user-images.githubusercontent.com/84273839/158033789-3fde4ef4-b4bd-4334-ba36-cce8c2222bea.png">

Html kodunun en başına bu tanımlamayı yapmalıyız yoksa kodumuz geçersiz olur details.cshtml başına bu kodu yaz

### **@model List<shopapp.webui.Models.Product>  //Kodu bu şekilde düzeltin**

Ardından Body alanına kodlarını yazıyoruz. Tebrikler artık Dinamik bir içerik oluşturduk tekrardan

<img width="474" alt="16" src="https://user-images.githubusercontent.com/84273839/158033795-7a3b4047-8fcc-4a0f-8e7e-87925e9db793.png">

---

## ViewData

Verilerimizi Controller dan View kısmına aktarmak için kullanırız.

Öncelikle bu işlemi ProductController da yapıyoruz

<img width="867" alt="17" src="https://user-images.githubusercontent.com/84273839/158033833-f18daeab-ebc8-4e2c-92ad-36dd59a19748.png">

Bu şekilde bodysini de ekliyeceğiz

<img width="867" alt="18" src="https://user-images.githubusercontent.com/84273839/158033837-9bb170ce-d178-431d-856c-b0c232141420.png">

---

## ViewModels Çoklu üyeleri alma


<img width="875" alt="19" src="https://user-images.githubusercontent.com/84273839/158033871-7e6bd851-d765-45a5-9663-e473a7118cbf.png">

ProductController geliyoruz ve aşağıdaki kodu yazıyoruz not List<Product> kodunu yazdıkdan sonra cmd+. ile using ekleyin


<img width="820" alt="20" src="https://user-images.githubusercontent.com/84273839/158033876-2f9045cb-adc8-4c73-8845-f0d0fc7aefc9.png">

List cshtml e model imizi tanıtıyoruz ama eğer bunu bu şekilde yazmak istemez isek şu adımları izleyebiliriz


<img width="874" alt="21" src="https://user-images.githubusercontent.com/84273839/158033877-022b1b26-0d86-44fc-b210-13dc7b804301.png">

ViewModels adında bir klasör oluşturup içine ProductViewModel.cs adında bir dosya yaratabiliriz ardından içerisine

<img width="186" alt="22" src="https://user-images.githubusercontent.com/84273839/158033881-537b48b3-4c36-4e53-8ac7-d4c940ef9156.png">

List<Product> ı Product değişkenine dönüştürüp bunu da ProductViewModel e koyabilirz


<img width="534" alt="23" src="https://user-images.githubusercontent.com/84273839/158033885-ddc34c72-ec28-4263-91e3-57614b454528.png">

Ardından List.cshtml e bu kodu yazabiliriz ve tamamdır iş tamam


<img width="534" alt="25" src="https://user-images.githubusercontent.com/84273839/158033916-662069bf-cfcf-4b9e-9186-35d7bb95df77.png">

Bu şekilde istediğimiz alandaki telefonu alabiliriz yani çoklu veri alabiliriz
<img width="874" alt="24" src="https://user-images.githubusercontent.com/84273839/158033900-183414b5-e1b4-40e7-9fb2-fa82f38b0357.png">


---

## Razor

Razor dediğimiz yapı html üzerinde c# kodları kullanmamıza yarar mesela aşağıdaki gibi bir şey. yapmamız mümkün

<img width="406" alt="26" src="https://user-images.githubusercontent.com/84273839/158033977-b55064e2-6adb-4287-a27c-17a29a3d6cab.png">

Razor da istediğiniz döngü ve benzeri şeyleri kullanabilirsiniz.

### Örnek kullanım

Eğer hiç products bulunmuyorsa ürün bulunmamakta yazdır eğer var ise değerleri yazdır tarzında bir kod yazdık

<img width="553" alt="27" src="https://user-images.githubusercontent.com/84273839/158033985-65406bb5-6123-42cf-a922-e6e3055c24fa.png">

<img width="191" alt="28" src="https://user-images.githubusercontent.com/84273839/158033999-c5885e2a-5745-4293-bcdc-27f8cbabad8d.png">

Views/Share/_navbar.cshtml adında bir dosya oluşturuyoruz


<img width="691" alt="29" src="https://user-images.githubusercontent.com/84273839/158034008-0f4f136a-6d82-47ee-b677-f7b79a33b41a.png">

_navbar.cshtml dosyamıza navbar kodunun tamamını atıyoruz


<img width="378" alt="30" src="https://user-images.githubusercontent.com/84273839/158034010-c99fc51b-b4f6-483c-8026-00e297343ae0.png">

Şimdi list.cshtml gibi yerlerdeki navbar alanını siliyoruz ve. oraya. bu kodu yazıyoruz  artık navbardaki neyi değiştirirsek değiştirelim otomatik gelicek


<img width="691" alt="31" src="https://user-images.githubusercontent.com/84273839/158034016-e37b4478-1c02-4156-8fb9-0a531e333b3d.png">

Mesela List.cshtml e Header da ekleyelim ve bu sefer partial kullanalım ilk önce _navbar.cshtml deki gibi bir text oluşturun _header.cshtml diye ardından aşığıdaki kodları girin tabiki ilk önce partial etkin hale getirmeliyiz bunun için


<img width="177" alt="32" src="https://user-images.githubusercontent.com/84273839/158034020-5bac4993-767d-41ea-b74d-c3cb4e2b9b21.png">

adında bir klasör oluşturup içine bu kodları yazon


<img width="738" alt="33" src="https://user-images.githubusercontent.com/84273839/158034024-d92b64ea-af48-4776-b45a-580227af6bb7.png">

Bu kodları yazdığınız zaman partial kullanılabilir olucak


<img width="738" alt="34" src="https://user-images.githubusercontent.com/84273839/158034030-cf37b78c-cb76-491f-9b93-105c746d6814.png">

ufak bir örnek olsun list.cshtml de ürün yok yazısı yazdırmışdık hatırlıyorsanız onu kesip

<img width="524" alt="35" src="https://user-images.githubusercontent.com/84273839/158034032-35fee60b-872e-4e87-84b4-382ef1243247.png">

Shared klasörüne bir dizin daha oluşturalım _noproduct.cshtml ve bu dizine kesdiğimiz kodları yapıştıralım ardından list.cshtml dönüş tekrar aşığdaki kodu yazalım artık daha az kod ile bunu yaptık


# Partial View

Partial view bir tasarımı her sayafada kullanmak yerine spesifik yerlerde kullanmanıza yarar

> Not: Partial çok bağımlıdır genelde bağımlı olması nedeniyle tercih edilmez daha çok View Component tercih edilir
> 

Öncelikle PartialController adında bir controller oluşturalım ve içerisine menu ActionResultını girelim

```csharp
public class PartialController : Controller
{
    public ActionResult Menu()
    {
        return PartialView();
    }
}
```

Ardından Menu View imizi kuralım ve içerisine eklemek istediğimiz tasarımı ekleyelim

```html
<div class="masthead">
    <h1 class="display-4">Teknolog Web</h1>
    <nav class="navbar navbar-expand-md navbar-light bg-light rounded mb-3">
        ...
    </nav>
</div>
```

Ve tamamdır şimdi ise tasarımımızı eklemek istediğimiz sayfaya yazmak

```csharp
@{Html.RenderAction("Menu", "Partial");}
```

# View Componet

View Componet nedir asıl amacı partial view gibi her sayfada kullanmak istemediğiniz menu,category gibi tasarımları burda taşımanızı sağlar 

Partial View yerine View Componet  kullanabilirsiniz

> Partial View direk **URL** üzerinden giderken View Component **URL** üzerinden gitmez
> 

ViewComponets adında bir klasör oluşturalım

<img width="232" alt="36" src="https://user-images.githubusercontent.com/84273839/158034060-37c00409-2721-4cb4-944d-97faf72f4f06.png">


Ardından CategoryGetList.cs adında bir dizin oluşturuyoruz


<img width="379" alt="37" src="https://user-images.githubusercontent.com/84273839/158034099-9059ba39-f2b7-4cce-afcd-f6d1dfdbfb20.png">

Ardından İçeriğini bu şekilde dolduruyoruz burda aslında bizim repository olarak eklediğimiz TList nesnemizi catgoryList ile Viewe aktarıyoruz ki verilerimizi View de kullanabilelim

<img width="719" alt="38" src="https://user-images.githubusercontent.com/84273839/158034106-81d3f864-4484-4571-875c-1dbac7761159.png">


Ardından View deki Default klasörümüze bu klasörümüzün içinde e-ticaret sitemizin tam hali var Index de  Component klasörü açıyoruz onun içinede CategoryGetList klasörü açıyor ve içine Default.cshtml klasörümüzü koyuyoruz


<img width="272" alt="39" src="https://user-images.githubusercontent.com/84273839/158034109-2564aae3-f9df-48bb-91d8-05cb397e2482.png">

Ardından Default.cs dizinimizin içine eklemek istediğimiz Category html kodunu yazıyoruz


<img width="179" alt="40" src="https://user-images.githubusercontent.com/84273839/158034115-486c4f46-3f73-4c0b-b999-7cdd40570eca.png">

Sonrada Layout umuzdaki Temel site html inin olduğu yerdeki Category alanını silip onun yerine Component kodunu yazıyoruz


<img width="467" alt="41" src="https://user-images.githubusercontent.com/84273839/158034119-352d5871-d95c-4a9f-badb-6d9a5390603c.png">

Ve tebrikler peki sizin dinamik bir web siteniz var ve siz Category ekledikce bunların otomatik olarak gelmesini istiyorsunuz ne yapıcaksınız.

### Dinamik bir Web sitesinde category leri otomatik getirme

Burda yaptığımız şey model deki category imizi istedik ve foreach ile model deki verilerimizi item a aktardık sonra da html kodumuz ilede her. yeni category de bunu ekliyeceğimizi belirttik


<img width="831" alt="42" src="https://user-images.githubusercontent.com/84273839/158034122-89f728cd-66da-47ca-a046-341c82353557.png">

---

# wwroot içerisine bootstrap kurmak (Client Side Library)

> Bunun için wwroot’a gelip sağ tıklayıp Add Client Side Library tıklıyoruz ve aşağıdaki gibi dolduruyor Not: Library yerine bootstrap yazdığınız an aşağıda library’si otomatik gelir
> 



## Layout

Layout aslında binevi partial view ile aynı mantıkda tek fark burda kodları tekrardan yazmak. yerine otomatik düzltiyoruz diyelim ki home.cshtml de bir content iniz var aynı content list.cshtml de de var home.cshtml de değiştirdiğiniz bir kod list.cshtml de de değişmesini istiyorsanız bu alan önemli

Öncelikle Shared da _Layout.cshtml adında bir dizin oluşturalım ardından html iskeletiyle dolduralım içini ve eğer isterseniz bootstrap linkinizi bu layout içine atın yani artık main html iniz burası tüm ayarları siteniz burdan alıcak mesela bootstrap veya javascript gibi

<img width="209" alt="44" src="https://user-images.githubusercontent.com/84273839/158034203-638f3c16-f7ce-495f-adb3-f816aa30dce4.png">

Mesela navbar ve header alalım bu dizinimizin içine.

<img width="444" alt="45" src="https://user-images.githubusercontent.com/84273839/158034209-95b0a206-5037-4797-82ec-989f9c3be1c7.png">

Ardından bir main alanı oluşturalım ve ordaki container alanına yani sitemizin değişecek her alanında kullanılacak olan yere @RenderBody() yazıyoruz Not: genelde Render body içerik sayfası için kullanılır ki veri tabanından bir haber eklendiğinde otomatik olarak sayfalara düşsün 


<img width="444" alt="46" src="https://user-images.githubusercontent.com/84273839/158034213-a636c9c7-4ce9-4275-a9e9-e051c52c5e45.png">

Ardından index.cshtml gibi alanlarımızda bu kodu yazıyoruzki nerden tasarımı almaları gerektiğini bilsin. ve tebrikler 

<img width="349" alt="47" src="https://user-images.githubusercontent.com/84273839/158034219-4c14fc28-04a8-4cc3-a1c3-81508bea5b95.png">

Eğer siz heryere layout="_Layout" yazıp kendinizi yormak istemiyorsunuz yapacağını şey /Views/_ViewStart.cshtml diye bir dizi oluşturuyoruz ve kodu onun içine atıyoruz artık hepsiyle uğraşmamıza gerek kalmıyor tüm sayfalar otomatik olarak layout alıyor 

<img width="349" alt="48" src="https://user-images.githubusercontent.com/84273839/158034229-56a6f53e-a531-494e-88a7-514186a59b5a.png">

Eğer siz bazılarında olsun bazılarında olmasın diyorsanız Atıyorum login sayfanızda layout olmasın istiyorsunuz yapacağınız şey şu

<img width="144" alt="49" src="https://user-images.githubusercontent.com/84273839/158034234-663a29f2-1854-4253-952a-7328792d7e57.png">

## Section

Mesela atıyorum. bizim bir mesajımız olsun  ve biz bu mesajı sadece belirli sayfalarda fakat birden çok sayfada olmasını istiyoruz bunu _Layout.cshtml taşıdığımızda ne yapmalıyız

<img width="464" alt="50" src="https://user-images.githubusercontent.com/84273839/158034262-e7c55294-7885-43f5-8e9a-ab766d1feba4.png">


Öncelikle _Layout.cshtml dizinimize şu kodu yazıyoruz ve üstte yazdığımız kodu kesiyoruz Not: false yazmamızın sebebi değeri zorunlu olmamasını sağlamak ki tanımlama yapmadığımız siteler için bize hata vermesin

<img width="313" alt="51" src="https://user-images.githubusercontent.com/84273839/158034268-fdf5dd3e-0e45-49d2-b1ad-461747e968bb.png">

Ardından sayfamızda gelmesini istediğimiz rastgele bir sayfaya şu kodu yazıyoruz mesela Index.cshtml

<img width="536" alt="52" src="https://user-images.githubusercontent.com/84273839/158034273-ddb13bbb-5d3e-4e92-a0e2-d3f890c70393.png">

 

Eğer bazı sayfalarda bootsrap veya script kullanmak istiyor bazılarında istemiyor iseniz şu adımları izleyin

_Layout.cshtml de en alta bu kodu yazın ardından istediğiniz sayfaya gelin mesela index.cshtml

<img width="313" alt="53" src="https://user-images.githubusercontent.com/84273839/158034282-0b0b6bd9-8a5f-4cc2-a080-215d69f979ea.png">

Oraya bu kodları yazın ve işiniz bitti artık o sayfada script kullanıyorsunuz

<img width="822" alt="54" src="https://user-images.githubusercontent.com/84273839/158034285-36499761-1431-4099-9a61-ef02047e6d90.png">

## Static files

Diyelim ki sayfamızda bir fotoğraf ve javascript dosyaları var onları bir başlık altında sayfamızda sakalamak istiyoruz bunun için shopapp.webui klasörümüze wwwroot adında bir klasör yapıyoruz altınada css image ve javascript diye klasörler oluşturuyoruz ardından startup.cs e geliyoruz
Startup.cs de app.UseStaticFiles kodunu yazıyoruz 

<img width="654" alt="56" src="https://user-images.githubusercontent.com/84273839/158034297-017cd83c-a068-4369-953c-907f9cfded2a.png">

Ve İmage klasörümüze atmak istediğimiz fotoları atıyoruz ardından fotoğrafı koymak istediğimiz yerdeki linki siliyoruz ki bizim dosya altındaki resmimizi koyalım onun kinkini buraya yazıyoruz ve evet tebrikler oldu bunu css gibi yerlerden de kullanabilirsiniz


<img width="183" alt="55" src="https://user-images.githubusercontent.com/84273839/158034292-045222ee-dda5-4412-8142-78c2a9a34a00.png">

# Entity Core

Öncelikle birkaç paket indirmeliyiz indirmemiz gereken paketleri aşağıya sıralıyorum

1- Microsoft.EntityFrameworkCore

2- Microsoft.EntityFrameworkCore.Design

3- Microsoft.EntityFrameworkCore.SqlServer

3- Microsoft.EntityFrameworkCore.Tools

---

### Entity Core kullanım alanlar

 Model First (tamamen entity model üzerinden veritabanı oluşturmak için kullanılan yaklaşımdır.)
 Database First (Var Olan Veritabanını Kullanma)
 Code First(Yeni Veritabanı Kod Yazarak oluştururuz ve yönetimi bunun üzerinden yaparız)

---

# Linq Sorguları

> OrderBy(x⇒x.Name) //ismi Alfabeye göre sırala
> 

> Where(x⇒x.yas == 20) //Yaş 20 ise
> 

> Max() //maksimum değeri alır
> 

> Min() //Minumum değeri alır
> 

> Sum() //Sayı kumesindeki elemanların toplamını bulan extension methodtur.
> 

## **First**

Collectiondaki ilk elemanı bulan extension methodtur. Eğer collectionda aranan değer bulunamadıysa *InvalidOperationException* fırlatır.

## **FirstOrDefault**

Collectiondaki ilk elemanı bulur, eğer eleman yoksa type’in default value’sini döndürür.

## **Last**

Collectiondaki son elemanı bulan extension methodtur. Eğer collectionda aranan değer bulunamadıysa *InvalidOperationException* fırlatır.

## **LastOrDefault**

Collectiondaki son elemanı bulur, eğer eleman yoksa type’in default value’sini döndürür.

## **Single**

Collectionda yer alan tek bir uniqe elemanı bulan extension methodtur. Eğer collectionda aranan eleman bulunamadıysa veya birden daha fazla sayıda varsa *InvalidOperationException* fırlatır.

## **SingleOrDefault**

Collectionda yer alan tek bir uniqe elemanı bulan extension methodtur. Eğer eleman bulunamdıysa diğer *OrDefault’lar gibi* default valueyi döner. Aranan eleman collectionda yoksa *InvalidOperationException* fırlatır.

# Code First

Code first dediğimiz yapı kodlar ile database tasarlamaya denir günümüzde çok aktif kullanılmasada bilinmesi işinize yarayacakdır

Öncelikle Models üzerinden table larımızı oluşturuyoruz

<img width="654" alt="56" src="https://user-images.githubusercontent.com/84273839/158034350-81ccccac-eacc-4b06-9d7c-a045d3b3b924.png">


### Personel

<img width="182" alt="57" src="https://user-images.githubusercontent.com/84273839/158034361-8217db6e-d984-4bac-a118-1f5b3ef217ac.png">


### Departmanlar

<img width="495" alt="58" src="https://user-images.githubusercontent.com/84273839/158034373-5a906fc3-66db-44f0-90a5-e0760b3b9132.png">

### Ardından Context yapımızı ekliyoruz


<img width="495" alt="59" src="https://user-images.githubusercontent.com/84273839/158034377-2707eb52-fc2e-476c-bf2d-0c4389d4a3cb.png">

Kullancağınız database e göre şekillendirebilirsiniz ben mysql kullanıcam Not:local kullandığım için şifrenin görünmesi herhangi bir sorun teşkil etmiyor ayriyetden hata yapmamanız için veritabanı bağlama kodunu aşağıya yazılı bırakıyorum

```csharp
protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder){
optionsBuilder.UseMySql(@"server=localhost;port=3306;database=corepersonel;user=root;password=er266914");

}
```

<img width="171" alt="60" src="https://user-images.githubusercontent.com/84273839/158034388-e85ed7a2-edf4-471a-9b83-bb1e3644e94e.png">
<img width="932" alt="61" src="https://user-images.githubusercontent.com/84273839/158034397-d509e5e0-0438-4091-a592-8f9f64ffa0b8.png">


### Sonrası Migration alanından takip ederek bir Migration oluşturun

## Migration oluşturma

### **dotnet ef migrations add InitialCreate**

### dotnet ef database update

---

## Scaffolding

Bütün ekleme çıkarma ve güncelleme gibi işlemleri Scaffolding ile çok kısa bir şekilde yapabilirsiniz, biz genede bunu elle yazmak isterseniz nasıl yapıcağınızı aşağıda yazdık

(Bütün ekleme çıkarma güncelleme işlemlerini yapabilirsiniz)

**İlk 2 dakikada kurulumu gösteriyor**

[https://www.youtube.com/watch?v=WNuAVyD6Cv4](https://www.youtube.com/watch?v=WNuAVyD6Cv4)

## Departman a bilgi ekleme

Öncelikle mysql üzerinden karakterlerimizi giriyoruz.

<img width="163" alt="62" src="https://user-images.githubusercontent.com/84273839/158034443-5aa138cf-2e24-4434-b5a6-edfe705c0680.png">

ardından departController.cs den models i kullanıyoruz.


<img width="277" alt="63" src="https://user-images.githubusercontent.com/84273839/158034463-1f96049f-40a2-443e-97bb-24205920aec7.png">

Sonrasında Context Modelimizi kullanarak departmanlars daki elemanları bize ToList olarak çıkartıyoruz


<img width="459" alt="64" src="https://user-images.githubusercontent.com/84273839/158034469-a41eda97-44f3-4259-a1be-32572684dc75.png">

Index imizde hemen tasarımımızı yapalım ve şimdi statik sitemizi dinamik hale getiriyoruz

<img width="459" alt="65" src="https://user-images.githubusercontent.com/84273839/158034476-6d77d4d0-d707-4180-8c2d-daabf7a70620.png">


Öncelikle index sayfamızda CoreDepartman.models kullanmasını istiyor ve altında bir List oluşturarak bize tüm departmanlar ı vermesini istiyoruz bu departmanları Context.cs de tanımlamışdık biliyorsunuz ki bu bizim database deki kolon adımız

<img width="459" alt="66" src="https://user-images.githubusercontent.com/84273839/158034482-4bdc2416-ff2a-46ee-968d-d0bccff4f1e5.png">

Ardından bir foreach döngüsüyle bütün id ve departmanad larını yazdırıyoruz ve ardından altına sonradan yapacağımız sil,güncelle ve detaylar butonlarını ekliyorum

<img width="885" alt="67" src="https://user-images.githubusercontent.com/84273839/158034485-48f4aa01-8ef6-45be-bbdb-a86b7f424546.png">

## Yeni Departman ekleme

**Get: Güvenlik açısından URL’lerin ekranda görüntüleniyor olması ve URL’in hedefine ulaşıncaya kadar ve hedef sunucu üzerinde iz kayıtlarında görülebilmesi gönderilen parametrelerin gizlilik ihtiyacı varsa sıkıntı yaratabilir. Bu nedenlerle hassas isteklerin GET ile gönderilmemelidir.**

**POST: Bu metod ile sunucuya veri yazdırabilirsiniz. Bu metodla istek parametreleri hem URL içinde hem de mesaj gövdesinde gönderilebilir. Sadece mesaj gövdesinin kullanımı yukarıda sayılan riskleri engelleyecektir. Tarayıcılar geri butonuna basıldığında POST isteğinin mesaj gövdesinde yer alan parametreleri tekrar göndermek isteyip istemedimizi sorarlar. Bunun temel nedeni bir işlemi yanlışlıkla birden fazla yapmayı engellemektir. Bu özellik ve de güvenlik gerekçeleriyle bir işlem gerçekleştirileceğinde POST metodunun kullanılması önerilir.**

### Öncelikle Get ve Post için iki ayrı Controller ekliyoruz

HttpGet de sayfa yüklendiğinde açılsın HttpPost da ise butona tıklandığında çalışsın anlamına geliyor

<img width="704" alt="68" src="https://user-images.githubusercontent.com/84273839/158034542-2b6ad8f1-fac1-456d-91c1-eef65de18563.png">


Ardından bir View ekliyoruz YeniDepartman adında sonrasında Model imizi ekliyoruz

<img width="704" alt="69" src="https://user-images.githubusercontent.com/84273839/158034575-59455256-d849-49ab-abf7-2ac26e4a4028.png">

Ve bir form tasarımı yapıyoruz form tasarlarken şunu yapmayı unutmayın method="post" burda post edildiğinde göster gibi bir yazı yazdık sonrasında yaptığımız html.LabelFor ise bize departmanad olarak yazdırır isterseniz bunu <p> olarak da kullanabilirsiniz html.TextBoxFor da ise form a girilen biligileri ad ile eşleştir anlamına geliyor

<img width="416" alt="70" src="https://user-images.githubusercontent.com/84273839/158034581-2bf5426f-04c1-4e1f-b7f1-28b3fb3171d0.png">

Eğer class ekleyip daha güzel bir tasarım istersek şu şekilde class da ekleyebilirsiniz

<img width="639" alt="71" src="https://user-images.githubusercontent.com/84273839/158034585-b6157e0c-8ec6-4d71-aad8-a59a4337e452.png">

**İŞTE ASIL BEKLENEN'AN YENİ DEPARTMAN EKLEME**

Burda yaptığımız şey sırasıyla şu öncelikle önceden belirlediğimiz Context değişkeni olan c ye şunu söyledik c.departmanlars.Add(d); departmanlars a yeni bir parametre yükle buda d olsun ardından c.SaveChanges(); diyerek de database in veriyi güncellemesini sağladık onun altında ise 

yani return RedirectToAction("Index"); alanında ise veriyi eklediğimiz zaman index e dön dedik

Not: Html.TextBoxFor(x=>x.departmanad, new {@class="form-control"}) bu yazdığımız kod da x.departmanad diyerek  ordan veriyi otomatikman çekdik bunu nasıl yaptık biz SaveChanges dediğimizde saten veri tabanına işlemişdi biz burda veri tabanı ile rm u sekronize ettik

<img width="639" alt="72" src="https://user-images.githubusercontent.com/84273839/158034599-e992f74c-e0bc-4949-bab5-6f4f0ae09c15.png">


## Departman Silme

Öncelikle DeparController.cs den DepartmanDelete adında bir property oluşturuyoruz ve id parametresi veriyoruz bunu veriyoruz çünkü biz bir veriye sil dediğimizde hangisi olduğunu bu veri üzerinden anlayıcak SelectedId değişkenimiz ilede id değerini buluyoruz 

<img width="639" alt="73" src="https://user-images.githubusercontent.com/84273839/158034612-525709f5-7ff8-4fff-9cb8-2ee6b91c363a.png">

Ardından Index.cshtml e gelip Sil alanımızın değerini veriyoruz burda değer verirken yaptığımız şey şu bastığımızda bize bastığımız verinin hangi değere sahip olduğunu söylüyor ve ona göre verimizi siliyor 

<img width="782" alt="74" src="https://user-images.githubusercontent.com/84273839/158034614-9fda9e64-f252-4175-8563-0437e1fd6349.png">

## Departman Güncelleme

Burada bir alanı form içerisine getirmesini istiyicez 

Öncelikle bastığımız alanı anlaması için bir find parametresi kullanıyor ve bunu View ile döndürüyoruz

<img width="521" alt="75" src="https://user-images.githubusercontent.com/84273839/158034634-b082cb0f-52e9-4b49-b54b-d0ab21b045ee.png">

Sonrasında DepartmanGetir adında bir View oluşturuyor ve tasarımımızı yapıyoruz

Fakat bu sefer farklı olan şey bunu using ile yapıyor olmamız başta BeginForm oluşturduk yani bilidğiniz form sonrasında DepartmanGuncelle diye bir parametre girdik ve sonrasında depart parametremizi kullanmasını istedik en sonda da bu işlemi post olarak yapmasını istedik


<img width="851" alt="76" src="https://user-images.githubusercontent.com/84273839/158034662-e93364e2-8f60-4d85-9adc-a806252237fe.png">

<img width="851" alt="77" src="https://user-images.githubusercontent.com/84273839/158034683-2d831a6d-7d97-4d00-b25f-25916a051e67.png">

Ardından İndex alanından Güncelleyi View imize bağladık


<img width="851" alt="78" src="https://user-images.githubusercontent.com/84273839/158034691-f1bbb343-d2e4-4457-8095-54c1222b45f0.png">

### Şimdi ise güncelleme işlemine başlıyoruz

Öncelikle burda departmanlardan d parametresini yolladık ve dedikki d parametresindeki id yi bul sonrasında altında seçtiğimiz parametre ile bulunan parametreyi eşledik ve database'i kaydettik

<img width="851" alt="79" src="https://user-images.githubusercontent.com/84273839/158034696-8be4042c-6618-471d-939a-100132e87023.png">

## Migration Update and Delete Database

Atıyorum yeni bir tablo ekliyoruz veya yeni bir kategori bunun için migration güncellemeliyiz nasıl yapıyoruz gelin beraber görelim 

Öncelikle departmanlar.cs e detay diye bir property yani detay adında bir kolon giriyoruz 


Bunu yansıtmak ve güncellemek için terminale bunları yazıyoruz

### **dotnet ef migrations add MigrationAdınız**

Sonrasında database güncelliyoruz 

### **dotnet ef database update**

**PEKİ SİLMEK İSTERSEK**

önceden yazdığımız detay prop unu siliyoruz 

```csharp
public string detay {get;set;}
```

Ardından Terminale şunları yazıyoruz

İsterseniz yeni bir migraton ekleyerek de kullanabilirsiniz

**dotnet ef migrations add MigrationAdınız**

**dotnet ef database update**

Bunları yaptıkdan sonra eski migration ı silip bu migration kullanamya devam edebilirsiniz

## İlişkilerin Kurulması (One to Many)

Öncelikle depratmanlar.cs dizinimize personels ile bağlantı kurduruyoruz

```csharp
public IList<Person> Personels {get;set;}
```

ve aynısınızı personel.cs için de yapıyıoruz

```csharp
public departmanlar depart {get;set;}
```

Sonra da bu eklediğimiz ilişkileri databse e kaydetmemiz gerek bunun içinde şu migartion kodlarını yazıyoruz

**dotnet ef migrations add Test**

**dotnet ef database update**

Şeklinde databse de kaydettik

Ve evet departid olarak personel databse ini departman ile eşledik

Artık departid ye departmanlar daki ile uyumlu id ler verebiliriz mesela 1 diyerek müdür olarak atayabiliriz gibi


## İlişkili yapılar içinde Personel departmanı gösterme

Öncelikle PersonelController.cs dosyamızı açıyoruz ve içine aşağıdaki kodları yazıyoruz

Burda ilişkili bir yapıyı kullanmak için Include metotunu kullandık bu Include metodu bize  Birim.cs deki tüm bilgileri getirdi böylece yazdıracağımız zaman direk BirimAd ı gösterebileceğiz

Not:Departman adını Birim olarak değiştirdim yani siz Birim mi diğer derslerdeki Departman olarak düşünün

```csharp
  Context c = new Context();
public IActionResult Index(){
  var degerler = c.Personels.Include(x=>x.Birim).ToList();
  
  return View(degerler);
  }
```

Gördüğünüz gibi önceliklerinden ekstra olarak Birim.BirimAd diyerek Birim deki Birim adı yazdır dedik 

<img width="754" alt="82" src="https://user-images.githubusercontent.com/84273839/158034941-ea8ac6cd-32f3-405e-856c-8e6bd0b75e12.png">

---

## DropDownListe Birimleri çekme

Öncelikle Burda işlemimizi [HttpGet] olarak yapıyoruz yani sayfa açıldığında işleme girecek olan yer, Burda şunu yaptık SelectListItem diye bir metot denedik burda yaptığımız şey Birimlerin bütün elemanlarını x e tanımladık sonrasında yeni bir SelectListItem oluşturduk ve burda text olarak BirimAdı mesela Muhasebe Value olan yerde de ıd sini tanımladık bundan sonrada .ToList diyerek database kaydettik 

ViewBag.dgr = degerler; degerler değişkenimizi front-end alanında kullanmak için yolladık, YeniPersonel.cshtml alanımıza yolladıkdan sonra 

```csharp
[HttpGet]
O references
public IActionResult YeniPersonel(){
    List<SelectListItem> degerler =(from x in c.Birims.ToList()
                                       select new SelectListItem{
                                           Text=x.BirimAd,
                                           Value=x.BirimID.ToString( )
                                       }).ToList();
   ViewBag.dgr = degerler;
    return View();
}
```
Değerimizi burda kullandık baştan anlatmam gerekirse

DropDownListFor adında yeni bir işlevimiz var bunun anlamı aşağı doğru açılan kutucuklar atıyorum 300 e yakın departmanımız var bunların ıd sini teker teker yazacağımıza direk kutucuk üzerinden işaretlememize yarar burda List<SelectListItem> diyerek listemizi kullanıyoruz ve ardından degerler değişkenimizi ViewBag ile getirtiyoruz 

Daha kısa kullanım olarak

```csharp
	ViewBag.City = new SelectList(Cities().ToList,"Id","Name");
```

Artık Birimler önümüze DropDown yani kutucuk şeklinde önümüze güncellenerek geliyor şimdi sıra personel ekleme işleminde

```csharp
	<b>Personel Birimi</b>
@Html.DropDownListFor(x=>x.Birim.BirimID,(List<SelectListItem>)ViewBag.dgr, new
{@class="from-control"})
<br>
```
yeni bir prop daha oluşturuyoruz seçmiş olduğumuz id yi dahil etmek için per diyoruz ve BirimId p.Birim.BirimId ye eşit olan ilk karakterini alıyoruz sonrasında p.Birim den aldığımız değeri per e atıyoruz sonrasında Personels yani database imize p parametresini ekliyoruz ve kaydediyoruz sonrasında ise bizi otomatik olarak Index e atıyor
```csharp
public IActionResult YeniPersonel(Personel p)
{
    var per = c.Birims.Where(x => x.BirimID
    p.Birim = per;|
    c. Personels. Add(p);
    c. SaveChanges ();
    return RedirectToAction("Index");
}
 ```

Index den gidiş yolunu da ayarladığımızda tamamen olay bitiyor

<img width="754" alt="83" src="https://user-images.githubusercontent.com/84273839/158035058-a6546b1b-f486-4df8-b5eb-1d10fbaee0ee.png">

---

# Login işlemi

Tasarımını eklediğinizi düşünerek den anlatıyorum öncellikle LoginController.cs ekliyoruz ve ardından GirisYap sayfamızı ekliyoruz siz Views ini felanda eklersiniz 

```csharp
public IActionResult GirisYap()
{
   
    return View();
}
 ```

arından model dosyamıza geliyoruz ve Admin.cs dosyamızı oluşturuyoruz içine AdminId gibi column larımızı ekliyoruz ve ardından Context.cs dosyamıza geçiyoruz

<img width="754" alt="84" src="https://user-images.githubusercontent.com/84273839/158035080-3e570ba5-d02e-459c-adc3-f6d340925486.png">

Context yapımızda personel de yaptığımız gibi database ile bir bağlantı kuruyor ve aynısını orayada kuruyoruz sonrada migration ekliyoruz

```csharp
public DbSet<Admin> Admins()
 ```

### Authorize İşlemi

İlk önce Startup.cs den cookielerimizi etkinleştiricez bunun için şu using i ekleyin

```csharp
using Microsoft.AspNetCore.Authentication.Cookies
 ```

Burda yaptığımız şey bir authentication oluşturma .AddCookie dedikden sonra şunu diyoruz kimlik doğrulama işlemi bittikden sonra bizi /Login/GirisYap a yönelendir yani cshtml dosyamıza

<img width="769" alt="85" src="https://user-images.githubusercontent.com/84273839/158035117-5a43f473-c359-4451-96b6-ce5d3fde175e.png">

bu alana bunları da ekliyoruz

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
  
 }
 ```

```csharp
app.UseAuthentication();
  app.UseAuthorization();
 ```

Ardından PersonelController ve DepartmanController alanlarımıza şu kodları girdik bunları girdiğimiz zaman sayfamıza girmeye çalıştığımızda. bizi otomatik olarak Giris yap sayfamıza atıyor
```csharp
using Microsoft.AspNetCore.Authorization
 ```

```csharp
[Authorize]
 ```

Peki eğer bizim 200 tane View sayfamız olsaydı hepsine nasıl tek seferde Authorize işlemi yaptıracağız işte böyle

Burda Tüm sayfaları authorize etmesini istedik fakat şöyle bir sorunumuz var bizim bir sayfayı bunun dışında tutmamız lazım bu sayfamızda Login sayfamız olucak


<img width="590" alt="86" src="https://user-images.githubusercontent.com/84273839/158035189-3c76327f-0fc0-4137-9101-6fdbb0da80fe.png">

Sayfamızı bunun dışarısında bırakmak için LoginController.cs den şu kodu yazıyoruz

[AllowAnonymous] Bu kod sayesinde bu sayfamızı dışarıda bıraktık artık bizi Index e girerken bizi Login sayfamıza atıyor

<img width="379" alt="87" src="https://user-images.githubusercontent.com/84273839/158035196-785732c0-26fe-49fb-baba-80fc22c0c218.png">

Öncelikle sizden indirmenizi istediğim birşey var Package manage console dan ceya command palete den şunu peojenize ekleyin

Install -Package Microsoft.AspNetCore.Authentication.Cookies

Ardından birtane daha GirisYap ekliyoruz ve birkaç değişiklik ekliyoruz burda yeni bir şey denedik

Burda yaptığımız şey şu bilgiler adında bir sorgu oluşturuyoruz burda kullanici ile sifre birbirine uyuyormu onu test ediyor onun altıda ise bilgiler boş değil ise yani bir değer var ise claims değişkeni oluşturuyor (Claims dokümantasyonlardan araştıraiblirsiniz bu bir yöntemdir) 

Bundan sonrasını siz yorumlaya bilirsiniz diye düşünyüorum burda sadece claim mantığını bilmeniz yeter
  
  <img width="793" alt="88" src="https://user-images.githubusercontent.com/84273839/158035212-4c96c49f-2463-4d37-b9e4-f40eb3580070.png">
 cshtml imizde name lerimizi yazıyoruz ve başarılı bir şekilde tamamlamış oluyoruz.

<img width="793" alt="89" src="https://user-images.githubusercontent.com/84273839/158035221-1f7ff0a3-aefb-465e-a6f8-9467a8d725e4.png">



---

# Repository

Controller üzerimnden yapacağımız işlemleri çok daha az kod satırıyla repository ile yapabiliyoruz ve bu bize daha düzenli bir yapı sağlıyor

(Dosyaların oluşturulması)

Öncelikle Data/Model alanımızı oluşturuyoruz ve içine bu üç dizinimizi ekliyoruz

<img width="264" alt="90" src="https://user-images.githubusercontent.com/84273839/158035235-cf547868-d6fe-457b-9ff9-d71c198bb59b.png">

Ardından Category.cs den başlayarak içlerini dolduruyoruz bunlar bizim database modellerimiz

Not: Computers One to Many yapısı oluşturuyoruz
  ```csharp
  namespace ComputerShop.Data.Models
{
    2 references
    public class Category
    {
         O references
        public int CategoryID { get; set; }
        O references
        public string CategoryName { get; set; }
         O references
        public string CategoryDescription { get; set; }
        O references
        public List<Computer> Computers { get; set; }
    }
}

 ```

Computer alanımız da bu şekilde dediğim gibi Category ile One to Many şeklinde işaretliyoruz
<img width="573" alt="92" src="https://user-images.githubusercontent.com/84273839/158035306-89a467a0-7efc-46c1-81d0-d2218ecc6dfc.png">

Context yapımızda bu şekilde


<img width="937" alt="93" src="https://user-images.githubusercontent.com/84273839/158035313-dd6552c3-fc87-4b9a-afee-633faa2ad7c4.png">

## Generic Repository

Şimdi Repository leri tek bir çatı altında toplıyacağız yani Generic de öncelikle dizinimizi oluşturuyoruz

<img width="471" alt="94" src="https://user-images.githubusercontent.com/84273839/158035323-1c3eb130-43d2-4cc6-9567-481724ecd2bf.png">
.48.png)

Ve içerisine önceden departman projesinde yaptığımız gibi add delete işlemlerini ekliyoruz

burda farklı olan şey Table yani T oluşturuyoruz ve bunu tüm Cattegory ve Computer gelicek yerlere koyuyoruz artık bunlar tek çatı altında toplandı yani ikisinede teker teker yapmamıza gerek kalmadı bize daha pratik bir yapı sağladı


<img width="862" alt="95" src="https://user-images.githubusercontent.com/84273839/158035326-a562726d-b852-4843-9df4-92a267cd4453.png">

Repositories klasörü oluşturup içerisine table larımızın repository lerine giriyoruz

![Screen Shot 2021-10-21 at 18.23.32.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b3ffab60-7215-48d4-bad7-d64bc1677ca8/Screen_Shot_2021-10-21_at_18.23.32.png)

Category den başlayarak dolduruyoruz 

ComputerRepository ve CategoryRepository ye bunları kalıtım ile ekliyoruz ki bu şablon üzerinden bazı metotlarımızı kullanabilelim


<img width="274" alt="96" src="https://user-images.githubusercontent.com/84273839/158035373-407d1a42-3dc7-4335-8ff1-fd80f9e05294.png">

### Controller larımızı tanımlayalım

CategoryController ve ComputerController adındaki controllerlarımızı tanımladıkdan sonra içlerini dolduruyoruz

<img width="862" alt="97" src="https://user-images.githubusercontent.com/84273839/158035379-171aa50e-f3c8-420b-8d2b-a4e382aa95e3.png">

CategoryRepository sınıfımızı çekiyoruz ve categoryRepository adında değişkenimizi oluşturuyoruz ardından View alanında TList diyerek bunu yazdırıyoruz hatırlarsanız bu çekme işlemini generic repository de tanımlamışdık

<img width="272" alt="98" src="https://user-images.githubusercontent.com/84273839/158035387-6d633d5e-b8e1-44ce-913b-b3f49c6deafe.png">

ComputerController için


<img width="644" alt="99" src="https://user-images.githubusercontent.com/84273839/158035411-72f6739b-55a6-4140-9429-607477190be3.png">

Category indexini yaratalım ve tasarımlarımızı girelim 

Not: Layout ile tasarımı ekledim ben 

<img width="644" alt="100" src="https://user-images.githubusercontent.com/84273839/158035412-f9f5d09d-9a5d-44ab-bbe1-d877ac128b4b.png">

Computer için ise kod bu şeklilde

<img width="566" alt="101" src="https://user-images.githubusercontent.com/84273839/158035418-069b5303-ae78-4f3d-b7ed-e63305fb80f8.png">

### Include ile Computer içinde CategoryName nesnesini yazdırma

Bunun için GenericRepository.cs imize gelip şu kodu yazmamız yeterli bu kodda yaptığımız şey aslında departamn projesiyle yaptığımızla  aynı burada sadece bu işlemi generic de yaptık 


<img width="591" alt="102" src="https://user-images.githubusercontent.com/84273839/158035456-74c7eece-98ec-4e5c-bb6b-be1ef231361c.png">

Sonrasında ComputerController gelip şu kodu yazıyoruz burda yaptığımız şey şu  TList alanında modelimizdeki Category sınıfımızı alıyoruz ve bunu gönderiyoruz ki html den CategoryName i çekebilelim


<img width="591" alt="103" src="https://user-images.githubusercontent.com/84273839/158035462-56a9f3be-071b-4d21-a8fd-9a11a510d308.png">

Index.cshtml den de bu şekilde yazdırıyoruz


<img width="591" alt="104" src="https://user-images.githubusercontent.com/84273839/158035465-66a0e396-60b2-4eab-8a6c-9d3ecc3d236a.png">

## Repository de Delete işlemi

aslında yaptığımız herşey add deki gibi fakat burda Computer dan parametre istiyeceğimize int ile bir id istiyoruz ve bu int ın ComputerID deki id olduğunu belirtiyoruz

<img width="591" alt="105" src="https://user-images.githubusercontent.com/84273839/158035468-bb5bbecf-0444-4a18-bf53-4cbf50c5879f.png">

## Repository de Update, Get işlemi

Burda yaptığımız şey şu TGet ile sayfa açıdlığında bastığımız an bastığımız category nin id sini bize verir ct değişkeninde Model deki CategoryName ile bizim seçtiğimiz CategoryName lerini yer değiştirdik sonrasında return View diyerek bu veriyi View imize aktardık CategoryUpdate de ise seçtiğimiz ile Category deki sınıflarımızı değiştirdik.

<img width="665" alt="106" src="https://user-images.githubusercontent.com/84273839/158035472-1d0ee03b-fc20-42d6-a483-1fd7752cf981.png">

TUpdate ile TGet içeriği

<img width="441" alt="107" src="https://user-images.githubusercontent.com/84273839/158035488-1053de43-875c-4197-b487-79900a67634a.png">

Bu şekilde de yazdırıyoruz

<img width="494" alt="108" src="https://user-images.githubusercontent.com/84273839/158035494-54c566fc-d78c-4436-a26f-12d9433422eb.png">


---

## Validation (Değer boş geçilemez)

Category de bir ekleme yapmak istiyoruz diyelim fakat eklediğimizde değer boş girildiğinde bize hata versin istiyoruz bunun için ne yapmalıyız

Burda eğer Name boş geçilirse Category name not empty diye uyar şeklinde bir değer girdik 

[Required(ErrorMessage "Category Name Not Empty")] 
public string CategoryName { get; set; }

Burda ise eğer değerimiz boş ise bizi CategoryAdd gönder yani [HttpGet] deki 

<img width="591" alt="109" src="https://user-images.githubusercontent.com/84273839/158035564-5f306624-0c30-4da6-9c94-8ce4affa362d.png">

Sonrasında html alanında Validation message olarak bunu yollatıyoruz ortadaki parametreyi boş girdik çünkü biz ordaki veriyi modelimizde vermişdik saten

<img width="665" alt="110" src="https://user-images.githubusercontent.com/84273839/158035619-327381d6-ed65-42ca-a599-8db0102561e4.png">

---

## Paging (Sayfalma)

Öncelikle aşağıdaki nuget paketimizi ekliyoruz

X.PagedList.Mvc.Core
  
Ardından Index sayfamızda şu metodu giriyoruz burda iki adet parametre giriyoruz birincisinde 1. sayfadan başlat ikincisinde ise sayfada kaç parametre bulnacağını istiyor biz buna 3 diyoruz

<img width="633" alt="111" src="https://user-images.githubusercontent.com/84273839/158035646-7dd5e4c5-47f2-4c2c-b4b8-23f1da81a993.png">

Sonrasında Index sayfamıza geliyoruz ve şunu farkediyoruz modelimize hata veriyor bunun nedeni şu biz sayfayı paged ile kullanmaya karar verdik sen bunu list ile veremezsin diyor bize bunu düzeltmek için ise

@model List<ComputerShop.Data.Models.Computer>

Aşağıdaki kodu girmeliyiz

@using X.PagedList
@using X.PagedList.Mvc.Core
  
 @model IPagedList<ComputerShop.Data.Models.Computer

Index sayfamızın en aşağısına ise bu kodu girmeliyiz burda ise her 3 parametrede bir yeni bir page oluşturmamızı sağladı

<img width="669" alt="112" src="https://user-images.githubusercontent.com/84273839/158035688-4c5dfb66-3cbc-4b7c-a24e-5abbfbc69ac8.png">

Artık 1 2 3 4 5 gibi sayfa sayfa atlaya biliyoruz 

---

## Column Chart

Öncelikle ChartController adında bir Controller oluşturuyoruz

Class1 adında bir model oluşturuyorum

Modelimin içine aşağıdaki prop ları atıyorum

<img width="444" alt="113" src="https://user-images.githubusercontent.com/84273839/158035704-01dca810-d73c-4b3b-81aa-b4a12d4d3e50.png">


Ardından controller ımıza aşağıdaki kodu giriyoruz 

<img width="444" alt="114" src="https://user-images.githubusercontent.com/84273839/158035714-775cd86c-5756-4acc-894a-632491004851.png">

Ardından indeximizi oluşturup alttaki linkteki kodumuzu giriyoruz 

[https://github.com/Escan-DNMZ/Pie-Chart](https://github.com/Escan-DNMZ/Pie-Chart)

### Eğer Column Chart istiyorsak

bu şekilde yeni bir view oluşturuyoruz ChartController dan

<img width="430" alt="115" src="https://user-images.githubusercontent.com/84273839/158035727-70387884-d7b8-43ee-a9a0-a65bfdf0a3dd.png">

ve Index2 Viewimize bu kodu yazıyoruz

[https://github.com/Escan-DNMZ/Column-Chart](https://github.com/Escan-DNMZ/Column-Chart)

---

## Arama İşlemi

Arama işlemi yaparken aslında kullandığımız şey bir parametre gönderme

<img width="681" alt="116" src="https://user-images.githubusercontent.com/84273839/158035735-416113dc-611c-40aa-893c-d1803f952f76.png">

üst fotoğrafdaa if in içerisindeki List de linq Express işlemlerini kullandık bu filtreleme sayesinde seçtiğimiz Category nin. hangisi olduğunu anlayaibliyoruz üst fotoğrafda List den aldığımız X parametresindeki CategoryName ile kendi oluşturduğumuz p parametresini dğeiştiriyoruz yani List deki X i p ye aktarıyoruz sonrada TList ile Tüm Categorylerimizi aktarıyoruz 

<img width="681" alt="117" src="https://user-images.githubusercontent.com/84273839/158035746-a48fa636-e445-451a-b963-007133273e8b.png">

Html alanımızda ise p parametremizi yollayarak filtreleme işlemini yazıyoruz text alanına yazıcağımız ismi bizim için filtreleyerek buluyor ve biz Find dediğimizde önümüze o içeriği sunuyor


<img width="681" alt="118" src="https://user-images.githubusercontent.com/84273839/158035753-8107562b-ff04-4bf9-b256-c691996f2c6a.png">

