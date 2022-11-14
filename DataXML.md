# Android: Como utilizar um ficheiro XML para guardar dados?

# Introdução:

Este documento visa mostrar um pequeno tutorial rápido e simples como utilizar um ficheiro XML para armazenar dados. Não irei entrar em partes muito teóricas e tecnicas do tópico.

# Tutorial:

### Criação do ficheiro xml:

1º → Abrir o Android Studio e na parte de gestão de projeto, clicar com o botão do lado direito do rato e adicionar a pasta ************assets************.

![floder.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd50e19a-c48c-4b53-9ba0-1f46cc1506ae/floder.jpg)

Essa será a pasta onde iremos armazenar os nosso ficheiros ******XML******.

2º → Após ter a pasta criada, clique com o botão do lado direito e vá em adicionar um ficheiro.

![data3.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ba4d37e1-b8a5-4b0b-9f4b-5ceb57e65a8d/data3.jpg)

O nome do ficheiro adicionada vai ter de ser do tipo ********************FILENAME.xml********************.

3º → Após temos o ficheiro criado esta a hora de começar a escrever nele os nosso dados. No entanto temos de respeitar alguns parâmetros. O cabeçalho do ficheiro têm de ser deste tipo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<recouse>
</recouse>
```

O nosso dados vão ser armazenados dentro da tag ****************recouse****************.

4º → Esta na hora de adicionar dados ao ficheiro. Imagina que quero adicionar uma pessoa por exemplo. E esse pessoa terá nome, idade e sexo. Para o fazer é bastante simples baste criar as tags necessárias e escrever dentro deles os dados que pretendo. O ficheiro xml resultante ficará algum do tipo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<recouse>
    <Pessoa>
        <Nome>Luis</Nome>
        <Idade>21</Idade>
        <Sexo>M</Sexo>
    </Pessoa>
    <Pessoa>
        <Nome>Ana</Nome>
        <Idade>43</Idade>
        <Sexo>F</Sexo>
    </Pessoa>
</recouse>
```

### Leitura do ficheiro xml:

Agora iremos definir as funções para fazer a leitura do ficheiro xml. Irei utilizar duas funções para esse fim uma que irei chamar de **GetNodeList** que irá retornar uma NodeList. Cada elemento da NodeList irá representar uma tag do ficheiro XML. Também irei definir a função **getValue**, que irá retornar uma String que será o conteúdo presente naquele node.

Função **GetNodeList:**

Ela recebe como argumentos:

- String FileName → Nome do ficheiro XML onde será realizada a obtenção de valores;
- String TAG → Que é o nome da TAG que queremos guardar na NodeList. No exemplo de cima a nossa **TAG = Pessoa**.

```java
private NodeList GetNodeList(String FileName, String TAG){
        NodeList nList = new NodeList() {
            @Override
            public Node item(int i) {
                return null;
            }

            @Override
            public int getLength() {
                return 0;
            }
        };
				//Abertura do ficheiro XML:
        try {
            InputStream is = getAssets().open(FileName);

            DocumentBuilderFactory dbFatory = DocumentBuilderFactory.newInstance();
            DocumentBuilder dBuilder = dbFatory.newDocumentBuilder();
            Document doc = dBuilder.parse(is);

            Element element = doc.getDocumentElement();
            element.normalize();

            nList = doc.getElementsByTagName(TAG);
        }   catch (Exception e) { e.printStackTrace(); }
        return nList;
    }
```

Função **getValue**:

Ela recebe como argumentos:

- String tag → Subtag onde queremos pegar o valor;
- Element element → O elemento onde iremos pegar o valor da tag. No caso é uma posição da nossa NodeList.

```java
private static String getValue(String tag, Element element) {
        NodeList nodeList = element.getElementsByTagName(tag).item(0).getChildNodes();
        Node node = (Node) nodeList.item(0);
        return node.getNodeValue();
    }
```

### Testagem na main:

Agora iremos fazer os teste na main. Primeiro começamos por definir a nossa NodeList.

Depois iremos imprimir no formato de uma Toast o número de pessoas que estão definidas no nosso ficheiro XML. Para essa finalidade podemos utilizar o seguinte código.

```java
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        NodeList node = GetNodeList("Data.xml", "Pessoa");
        Toast.makeText(this, String.valueOf(node.getLength()), Toast.LENGTH_SHORT).show();
    }
```

O output será 2 que representa o número de pessoas definida no ficheiro xml.

Agora para obter o conteúdo da 1º pessoa por exemplo, iremos definir um Element que será igual a posição 0 da nossa NodeList. De seguida iremos utilizar a função **getValue** para nos devolver o conteúdo presente na **tag Nome** dessa mesma pessoa. O código irá ficar o seguinte:
