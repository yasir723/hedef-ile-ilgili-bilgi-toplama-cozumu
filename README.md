# Hedef ile İlgili Bilgi Toplama Saldırısının Çözümü

Bu saldırıyı anlatım sayfasında bahsettiğimiz HTML ve JavaScript kodlarındaki yorum satırlarının potansiyel zararlarından söz ettik. Ancak bu yorum satırlarının, Hacker olarak değil de geliştirici olarak düşünerek, sistemde bulunmaması daha uygun olacaktır. İçinde hassas bilgileri içeren önemli yorum satırlarının istemci tarafında görünmemesi için, tehlikeli yorumları server tarafında yazmamız gerekmektedir.

HTML yorum satırların sunucu tarafında oluşturmak için kodu aşağıdaki gibi güncelleyebiliriz

Eski kod:
```html
<!--
    Test data:</br>
    userName: admin</br>
    password: admin</br>
-->
```

Güncel kod:
```php
<?php
    // Test data:</br>
    // userName: admin</br>
    // password: admin</br>
?>
```

Ayrıca, JavaScript yorum satırlarını sunucu tarafında da yazma imkanımız var. Saldırıyı anlatım sayfasında bahsettiğimiz JavaScript Önemli yorum satırı, bir hacker tarafından geliştirdiğimiz sistemi hakkında bilgi toplamak için kullanılabilir. Bu tür riskleri önlemek için JavaScript içinde hassas bilgileri içeren önemli yorum satırlarını sunucu tarafında yazmak daha güvenli bir yaklaşım olabilir.

Eski kod:
```JavaScript
<script>
    // Show error message in $_GET["error"] that send from different pages
    var urlParams = new URLSearchParams(window.location.search);
    var error = urlParams.get('error');
    
    if (error != "") {
        alert(error);
    }
</script>
```

Güncel kod:

```JavaScript
<script>
    <?php
      // Show error message in $_GET["error"] that send from different pages
    ?>
    var urlParams = new URLSearchParams(window.location.search);
    var error = urlParams.get('error');

    if (error != "") {
        alert(error);
    }
</script>
```

Önemli bir noktaya değinmek gerekirse, yazdığımız tüm kodları sunucu tarafında yazmak zorunda değiliz. Ancak, sistem hakkında bilgi edinme olasılığı olan, potansiyel risk taşıyan ve `içinde hassas bilgileri içeren önemli yorumları sunucu tarafında yazmalıyız`. Diğer yandan, `normal yorum satırlarımızın istemci tarafında` olması gerekmektedir.


