# Android: Como criar designs custom de botões, TextView, etc… Usando XML:

# Introdução:

Este documento visa transmitir de maneira simples e básica como  é possível criar designs interessantes para os nossos objetos utilizando apenas XML. Este tutorial irá trabalhar com as pastas **drawable** e **layout** que já vêm automaticamente quando é criado um projeto no Android Studio.

# Criação do ficheiro xml drawable:

Primeiramente vamos ao gestor de projeto do Android Studio, de seguida clicamos com o botão do lado direita em cima da pasta **drawable** e vamos em new **Drawable Resource File**.

<img src="https://user-images.githubusercontent.com/91985039/202024463-393a5768-d8b0-4ed2-a86b-b187364e0044.jpg">

No próximo menu atribuímos o nome ao nosso ficheiro e mantemos a configurações padrão.

<img src="https://user-images.githubusercontent.com/91985039/202024468-a7982f07-55ec-442d-9b80-a0737671a4f2.jpg">

Todos os ficheiro deste tipo iram ficar nesse diretoria.

# Aplicar o nosso ficheiro xml em um objeto:

O processo de aplicar o xml em um objeto é igual para todos menos o botão. Se for um botão o ficheiro pode ser aplicado mas o cor de fundo tem de ser defina utilizando a **tag backgroundTint**.

A cor de fundo num botão será aplicada da seguinte maneira:

```xml
app:backgroundTint="@color/black"
```

A aplicação do ficheiro de design por exemplo numa TextView pode ser feita da seguinte maneira:

```xml
  <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:background="@drawable/designs"/> <!-- Escolha do ficheiro de design feita nesta linha -->**
```

No caso o meu ficheiro de design chama-se: **designs**.

# Código XML para designs:

Agora que com o nosso ficheiro xml criado devemos ter algo parecido com:

```xml
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">

</selector>
```

Iremos trocar a **tag selector** pela **tag shape** e iremos escolher uma das shape que o android disponibiliza. E elas são as seguintes:

- rectangle;
- line;
- oval;
- ring.

Depois de fazer essa alteração o xml deve ficar algo parecido com o seguinte:

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">

</shape>
```

## Alterar cor de fundo:

Para fazer a alteração da cor de fundo temos duas tags:

- solid → que permite aplicar uma cor solida de fundo;
- gradient → que permite aplica uma gradiente de cor de fundo.

As duas tags utilização o código  das cores em hexadecimal.

**Utilizando a tag solid:**

A tag solid pinta o fundo de um objeto numa core solida e uniforme. No exemplo que irei mostrar ele irá pintar o fundo do objeto em vermelho.

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <solid android:color="#FF0000"></solid>
</shape>
```

<img src="https://user-images.githubusercontent.com/91985039/202024639-87b28f70-3bcd-4dc2-95a0-737abb01e162.jpg" style="height:700px">

**Utilizando a tag gradient:**

Na tag gradient posso definir, a cor de inicio, meio e fim, o angulo, a posição X e Y central, e o angulo da radiação. No entanto o exemplo que irei mostrar é bastante simples. Ele criar uma gradiente entre as cores vermelho, verde e amarelo.

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <gradient
        android:startColor="#FF0000"
        android:centerColor="#5DFF00"
        android:endColor="#FDC905"
        android:gradientRadius="0dp"
        android:angle="90"></gradient>
</shape>
```

<img src="https://user-images.githubusercontent.com/91985039/202024641-40544020-ef77-4e14-a851-7274abaddc6c.jpg" style="height:700px">

## Colocar bordas:

Para a criação de bordas podemos utilizar a tag stroke. Ela tem 4 propriedades:

- color → A cor da borda;
- width → A espessura da borda;
- dashWith → Largura dos traços, se for definida a zero a borda fica uniforme.
- daashGap → O espaçamento entre cada traço.

No exemplo a baixo irei definir uma borda tracejada em cor verde a volta de uma TextView. A espessura da borda será de 4dp.

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <stroke
        android:color="#07FF00"
        android:dashWidth="9dp"
        android:dashGap="4dp"
        android:width="4dp"></stroke>
</shape>
```

<img src="https://user-images.githubusercontent.com/91985039/202024637-4af97ecf-de8a-41f9-9bb7-7524568d12f2.jpg" style="height:700px">

No próximo exemplo irei definir uma borda uniforme de cor laranja em volta de uma TextView com espessura de 6dp.

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <stroke
        android:color="#FF6E00"
        android:dashWidth="0dp"
        android:dashGap="0dp"
        android:width="6dp"></stroke>
</shape>
```

<img src="https://user-images.githubusercontent.com/91985039/202025969-f6e7ec36-81e6-4e49-a7e2-a1606d70fdab.jpg" style="height:700px">

## Padding:

O é possível aplicar padding em objetivos utilizando a tag padding. Essa tag tem 4 propiedades:

- left → Padding do lado esquedro;
- rigth → Padding do lado direito;
- bottom → Padding na parte inferior;
- top → Padding na parte superior.

Irei utilizar o exemplo da borda anterior e irei aplicar nela uma padding de 9dp em todas as direções.

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <stroke
        android:color="#FF6E00"
        android:dashWidth="0dp"
        android:dashGap="0dp"
        android:width="6dp"></stroke>
    <padding
        android:left="9dp"
        android:right="9dp"
        android:bottom="9dp"
        android:top="9dp"></padding>
</shape>
```

<img src="https://user-images.githubusercontent.com/91985039/202024632-50170a84-af9a-4480-93ae-a08e76a4991d.jpg" style="height:700px">

No próximo exemplo irei aplicar um padding de 2dp no top e no rigth e o resto padding de 25dp.

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <stroke
        android:color="#FF6E00"
        android:dashWidth="0dp"
        android:dashGap="0dp"
        android:width="6dp"></stroke>
    <padding
        android:left="25dp"
        android:right="2dp"
        android:bottom="25dp"
        android:top="2dp"></padding>
</shape>
```

<img src="https://user-images.githubusercontent.com/91985039/202025911-97de02a8-b494-4304-b82a-69590dfee463.jpg" style="height:700px">

## Corners bordas curvas:

A tag corners permite-nos fazer curvaturas nos cantos. Ela tem 5 propriedades:

- topRigthRadius → Curvatura no campo superior direito;
- topLeftRadius → Curvatura no campo superior esquedro;
- bottomLeftRadius → Curvatura no campo inferior esquedro;
- bottomRigthRadius → Curvatura no campo inferior direito;
- radius → Coloca a mesma curvatura em todos os lados.

No exemplo a baixo, irei pintar o fundo com um verde azulado e irei aplicar uma curvatura em todos os lados de 15dp.
```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <solid android:color="#08E3D1"></solid>
    <corners
        android:topRightRadius="15dp"
        android:topLeftRadius="15dp"
        android:bottomLeftRadius="15dp"
        android:bottomRightRadius="15dp"></corners>
</shape>
```

<img src="https://user-images.githubusercontent.com/91985039/202024652-a8d5e45c-26c0-4ef4-8cbe-73e98101bd10.jpg" style="height:700px">
