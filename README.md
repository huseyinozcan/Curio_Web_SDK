Turkcell Curio Web SDK
=========

>Turkcell Curio ile kullanıcılarınızın web sitenizdeki hareketlerini gözlemleyebilirsiniz.

Sitenize ekleyin
--------------
  - https://gui-curio.turkcell.com.tr adresinden uygulamanızı oluşturun.
  - Aşagıdaki kodu web sayfanıza ekleyiniz.
  - Oluşturdugunuz uygulamanın TRACKING_CODE ve API_KEY değerlerini aşagıdaki koda yerleştirin.
  

```sh
    <script type="text/javascript">
        var trackingCode = 'TRACKING_CODE';
        var apiKey = 'API_KEY';
    </script>
    <script src="//ttech.8digits.com/js/curio.min.js"></script>
```

Kullanımı
--------------
Kullanıcıların hareketlerini gözlemlemek için kaydetmek istediğiniz kullanıcı etkileşimlerini Turkcell Curio'ya göndermelisiniz.
<br />
Yukarıdaki kodu sitenize ekledikten sonra, bu kodun size sağladığı API ile Turkcell Curio'ya bilgi gönderimi yapabilirsiniz.
<br />
Bu bilgiler yeni bir sayfa açılması, web sitenizdeki bir elemente tıklanması veya bulunulan sayfanın terk edilmesi gibi hareketleri içerebilir.
<br />

API
--------------
Turkcell Curio'yu size sağlanan 5 adet fonksiyon ile kullanabilirsiniz.
  - Yeni Ziyaret (New Visit)
  - Yeni Sayfa (New Hit)
  - Yeni Etkileşim (New Event)
  - Sayfa Çıkış (End Hit)
  - Ziyareti Bitir (End Visit)

<br />
Yeni Ziyaret (New Visit)
--------------
Zorunlu Parametreler
  - Zorunlu parametre yoktur.

Opsiyonel Parametler
  - pageTitle
  - path
  - hitCode
  - sessionCode
  - userAgent

Örnek Kullanım
--------------
Curio.newVisit fonksiyonuna yolladığınız callback fonksiyonunuza response pas edilir.

Http işlemi başarısız ise response, false dönecektir.
Http işlemi başarılı ise server'dan alınan response size pas edilecektir.
Server json objesi yollamış ise response'un içeriği json object olacaktır, json objesi gelmemiş ise response'un içeriği server'ın yolladığı text olacaktır.

```sh

    /**
     * Example Usage: New Visit
     */
    var exampleNewVisit = function() {

        /**
         * Required Parameters
         * there is no required parameters
         *
         * Optional Parameters
         * pageTitle, path, hitCode, sessionCode, userAgent
         */
        var requestObject = {
            pageTitle: 'Example Page', // optional
            path: '/examplepath', // optional
            hitCode: '', // optional
            sessionCode: '', // optional
            userAgent: '' // optional
        };
        Curio.newVisit(requestObject, function(response) {
            if(!response) {
                return false;
            }
            // Response is yours
        });
    };

```

Yeni Sayfa (New Hit)
--------------
Zorunlu Parametreler
  - sessionCode
  - path
  - pageTitle

Opsiyonel Parametler
  - Opsiyonel parametre yoktur.

Örnek Kullanım
--------------
Curio.newHit fonksiyonuna yolladığınız callback fonksiyonunuza response pas edilir.

Http işlemi başarısız ise response, false dönecektir.
Http işlemi başarılı ise server'dan alınan response size pas edilecektir.
Server json objesi yollamış ise response'un içeriği json object olacaktır, json objesi gelmemiş ise response'un içeriği server'ın yolladığı text olacaktır.

```sh

    /**
     * Example Usage: New Hit
     */
    var exampleNewHit = function() {

        /**
         * Required Parameters
         * sessionCode, path, pageTitle
         *
         * Optional Parameters
         * there is no optional parameters
         */
        var requestObject = {
            sessionCode: Curio.sessionCode, // required
            path: '/examplePath', // required
            pageTitle: 'Example Page Title' // required
        };

        /**
         * Handling New Hit Response
         */
        Curio.newHit(requestObject, function(response) {
            if(!response) {
                return false;
            }
            // Response is yours
        });
    };

```

Yeni Etkileşim (New Event)
--------------
Zorunlu Parametreler
  - key

Opsiyonel Parametler
  - value
  - sessionCode
  - hitCode

Örnek Kullanım
--------------
Curio.newEvent fonksiyonuna yolladığınız callback fonksiyonunuza response pas edilir.

Http işlemi başarısız ise response, false dönecektir.
Http işlemi başarılı ise server'dan alınan response size pas edilecektir.
Server json objesi yollamış ise response'un içeriği json object olacaktır, json objesi gelmemiş ise response'un içeriği server'ın yolladığı text olacaktır.

```sh

    /**
     * Example Usage: New Event
     */
    var exampleNewEvent = function() {

        /**
         * Required Parameters
         * key
         *
         * Optional Parameters
         * value, sessionCode, hitCode
         */
        var requestObject = {
            key: 'exampleKey', // required
            value: 'exampleValue', // optional
            sessionCode: '', // optional
            hitCode: '' // optional
        };

        /**
         * Handling New Event Response
         */
        Curio.newEvent(requestObject, function(response) {
            if(!response) {
                return false;
            }
            // Response is yours
        });
    };

```

Sayfa Çıkış (End Hit)
--------------
Zorunlu Parametreler
  - hitCode

Opsiyonel Parametler
  - Opsiyonel parametre yoktur.

Örnek Kullanım
--------------
Curio.newHit fonksiyonuna yolladığınız callback fonksiyonunuza response pas edilir.

Http işlemi başarısız ise response, false dönecektir.
Http işlemi başarılı ise server'dan alınan response size pas edilecektir.
Server json objesi yollamış ise response'un içeriği json object olacaktır, json objesi gelmemiş ise response'un içeriği server'ın yolladığı text olacaktır.

```sh

    /**
     * Example Usage: End Hit
     */
    var exampleEndHit = function() {

        /**
         * Required Parameters
         * sessionCode, hitCode
         *
         * Optional Parameters
         * there is no optional parameters
         */
        var requestObject = {
            sessionCode: Curio.sessionCode, // required
            hitCode: Curio.hitCode // required
        };

        /**
         * Handling End Hit Response
         */
        Curio.endHit(requestObject, function(response) {
            if(!response) {
                return false;
            }
            // Response is yours
        });
    };

```

Ziyareti Bitir (End Visit)
--------------
Zorunlu Parametreler
  - sessionCode

Opsiyonel Parametler
  - Opsiyonel parametre yoktur.

Örnek Kullanım
--------------
Curio.endVisit fonksiyonuna yolladığınız callback fonksiyonunuza response pas edilir.

Http işlemi başarısız ise response, false dönecektir.
Http işlemi başarılı ise server'dan alınan response size pas edilecektir.
Server json objesi yollamış ise response'un içeriği json object olacaktır, json objesi gelmemiş ise response'un içeriği server'ın yolladığı text olacaktır.

```sh

    /**
     * Example Usage: End Visit
     */
    var exampleEndVisit = function() {

        /**
         * Required Parameters
         * sessionCode
         *
         * Optional Parameters
         * there is no optional parameters
         */
        var requestObject = {
            sessionCode: Curio.sessionCode // required
        };

        Curio.endVisit(requestObject, function(response) {
            if(!response) {
                return false;
            }
            // Response is yours
        });
    };

```

Dependencies
----
None

Version
----
0.1

License
----
GPL

