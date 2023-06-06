# LoginUser ☺️

>Öncelikle ne oluşturmak istediğime ve nasıl görünmesini istediğime karar vermem gerekiyordu. Yaptığım araştırmalar ve hoşuma gidebilecek projelere de göz gezdirdikten sonra artık ne istediğime de karar verip başlayabilirdim böylelikle.😎

Yaptığım projenin amacı bir nevi kullanıcı girişi ancak ben bunu günümüzde düğün telaşında yapmakta zorlanılan ve belirli bir masrafı da bulunan davetiyelerle bağlantıladım. Açıkçası önemli bir sorun çünkü düğüne davet edilecek kişilere ulaşmak kolay bir eylem değil bu nedenle daha rahat bir şekilde oluşturduğumuz bu proje sayesinde gelin ve damadın zaten düğünün vermiş olduğu panik ve kaygının önemli bir adımını rahatlıkla tamamlamış oluyoruz. Tabi ki daha fazla geliştirilerek uygulama tamamlandıktan sonra bir veri havuzu oluşturarak ortaya çıkan gelecekler veya gelemeyecekler listesinden faydalanıp yapılacak olan diğer masraflardan da kurtulmuş olabiliriz böylelikle.

## Ana Özellikleri:
- Basit bir arayüze sahip olması,
- Sade ve anlaşılır bir anlatıma sahip olması,
- Arayüzün birden fazla kez kullanılabilir olması 

gibi özelliklere sahiptir.

## Uygulama Adımları:
- [ ] Visual Studio kurulumu gerçekleştirmek.
- [ ] Daha sonra **WPF Application(.NET Framework)** sayfa oluşturmak.
- [ ] Proje isim ver ve projeye geç.
- [ ] Kodları yazmaya başlaç
- [ ] NuGet paketlerinden MaterialDesignThemes paketini indir.
- [ ] Sonra kod yazmaya devam önemli ipuçları altta bulunucaktır. Sayfayı takip edin.

Oluşturduğum sayfayı **WPF platformunu kullanarak Xaml komutlarıyla** oluşturdum. 
**Visual Studio 2022** kod yazma uygulamasını kullanarak oluşturmak istediğim projeyi yapabilmek için öncellikle bir **WPF Application(.NET Framework)** sayfası oluşturarak işe başladım. 
![NewProject](https://github.com/bsrtk/LoginUser/assets/101363847/97621ae8-8e55-4bfb-8b68-93f0c9081469)

>Projeme bir isim verdim ve benim için otomatik olarak gelen en güncel sürümle devam ederek oluştur dedim ve projeyi yapma aşamasına artık geçebiliriz.👩💻 

![NewProject2](https://github.com/bsrtk/LoginUser/assets/101363847/cd2c6116-ca6c-4a27-86e5-92ea9ceda555)


>Zaten hazır şablona sahip bir sayfa önüme çıktı. Benim yapamam gereken sadece bu sayfanın görünümünü ve içeriğini oluşturmak oldu. Xaml komutlarıyla öncelikle sayfamın boyutuna karar vererek yapmaya başladım.

![NewProject3](https://github.com/bsrtk/LoginUser/assets/101363847/581a7726-9f55-4018-b40a-bbeb6133026f)


Uygulamada yapacağımız arayüzün boyutunu, genişliğini, arayüz çalıştırıldığında hangi konumda çalışacağını, kullanacağımız yazı stilini, arka plan rengi gibi ayarlamaları öncellikle yapıyoruz.

```
        Height="645"
        Width="875"
        WindowStartupLocation="CenterScreen"
        WindowStyle="None"
        AllowsTransparency="True"
        Background="Transparent"
        ResizeMode="NoResize"
        FontSize="18"
        FontFamily="{DynamicResource MaterialDesignFont}
```

Daha sonra uygulama sayfasının margin yani kenar boşlukları ve kenarlara uygulanacak efektleri yazdırıyorum.

```
<Grid Margin="20">

        <Grid.Effect>

            <DropShadowEffect BlurRadius="30"
                              ShadowDepth="1"
                              Opacity="0.4" />

        </Grid.Effect>
```

Uygulamayı iki bölmeye ayıracağız çünkü bir taraf başlık gibi yazıların bulunduğu kısım olurken diğer taraf kullanıcının girişini yapacağı bölüm olacak.

```
        <Grid.ColumnDefinitions>

            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="1.22*" />

        </Grid.ColumnDefinitions>
```

**Sol işlemler** adımıyla devam edeceğiz burda sol bölmede yer alacak ayarlamalar yapılacak. `border` kodunu kullanarak kenar kıvrımlarını **_(CornerRadius)_**, arka plan rengini **_(Background)_** ve sol bölme boyutunun değişkenliğini **_(ClipToBounds)_** kullanarak gerekli ayarlmalar yapılır.

```
        <Border Background="#FFF5B8"
                CornerRadius="10 0 0 10"
                ClipToBounds="True">

            <Border.Clip>

                <RectangleGeometry Rect="0,0,400,605"
                                   RadiusX="10"
                                   RadiusY="10" />

            </Border.Clip>
```


Şimdi de sol bölmede yer alacak başlık ayarlamalarını yapmaya geldi sıra. `StackPannel` kod bloğunu kullanarak sol bölmede yazıların nasıl hizalanacağını **_(VerticalAligmnet)_**, yazı boyutunu **_(FontSize)_**, yazı boyutu ağırlığını **_(FontWeight)_**, yazıyı **_(Text)_**, yazı rengini belirtmek için(Foreground) ve son olarak da yazının nerde bulunacağını **_(TextAligment)_** belirleyerek projemizi oluşturmaya devam ediyoruz. Bu kısımda böylelikle arayüzde bulunan yazıların bütün özellikleri hazırlanmış oldu.

```
                <StackPanel Margin="0 120 0 0 "
                        VerticalAlignment="Top">

                    <TextBlock FontSize="30"
                               FontWeight="Light"
                               Text="𝒟𝓊ℊ𝓊𝓃 𝒟𝒶𝓋ℯ𝓉𝒾𝓎ℯ𝓈𝒾"
                               Foreground="#080202"
                               TextAlignment="Center" />

                    <TextBlock FontWeight="Light"
                               FontSize="16"
                               Foreground="#080202"
                               TextAlignment="Center"
                               Text="Lütfen size gönderilen davetiyeye"
                               Margin="0 15 0 3" />

                    <TextBlock FontSize="16"
                               FontWeight="Light"
                               Text="başvurunuzu yapın."
                               Foreground="#080202"
                               TextAlignment="Center" />

                </StackPanel>
```

Ve uygulmamızı daha şık bir görünümde olmasını sağlamak için `Ellipse` kod bloğunu kullanarak daireler oluşturuyoruz. Ellipse ögesinin `Fill` özelliğini kullanarak oluşturduğumuz dairelere arka plan rengi vermiş olduk. `Margin` ile uygulamanın kenar boşluklarını ayarladık ve son olarak `Opacity` özelliği ile opaklık ayarlamalarını gerçekleştirdik. Birkaç tane bu dairelerden oluşturup kenarlık ayarlamalarını, arka plan renklerini ve opaklıklarını ayarlayarak uygulamamızın görsel anlamda daha iyi görünmesini sağlamış olduk böylelikle.

```
                <Ellipse Width="500"
                         Height="500"
                         VerticalAlignment="Bottom"
                         Fill="#5eccb4"
                         Margin="50 0 0 -200"
                         Opacity="0.6" />
```

>Uygulamada görsel anlamda daha etkin kılabilmek için renkli tike sahip bir buton oluşturdum.

Şimdi de sıra **sağ işlemler** adımıyla devam ediyoruz. Burda da hemen hemen benzer adımlarla işlem basamaklarına devam ediyoruz. Kenarlıklara tıklandığında hareket ettirebilmek **_(MouseDown)_** özelliğini kullanarak kenarlar üzerinde hareket işlemini tamamlamış oluyoruz. 

```
        <Border Grid.Column="1"
                Background="#ffffff"
                CornerRadius="0 10 10 0"
                MouseDown="Border_MouseDown">
```

**Kapama ikonlarına** gelecek olursak bu kısımda `materialDesign` paketinin yüklü olmuş olması gerekiyor. Yani:






















