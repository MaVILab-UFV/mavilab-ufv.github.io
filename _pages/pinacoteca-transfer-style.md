---
title: "MaVILab - Expo Pinacoteca"
subtitle: "Expo Pinacoteca"
layout: gridlay
excerpt: "MaVILab -- Expo Pinacoteca"
sitemap: false
permalink: /pinacoteca-50-anos/transfer-style
---

# Pinacoteca UFV
## Exposição comemorativa de 50 anos
### Obra Digtial: Transferência de Estilo

Somos o laboratório de Inteligência e Visão Computacional (MaVILab) do Departamento de Informática da Universidade Federal de Viçosa. Nosso foco é em pesquisas e soluções utilizando Visão Computacional e Inteligência Artificial (IA).  

Esse texto tem o objetivo de elucidar o funcionamento desta obra digital intitulada Transferência de Estilo. Esse trabalho foi desenvolvido utilizando um tipo específico de tecnologia de inteligência artificial denominadas redes neurais artificias para imagens. Vamos chamar essa tecnologia de rede neural.

#### Como elas funcionam?

Uma rede neural é uma técnica de aprendizado de máquina inspirada no cérebro humano, ou seja, ela tem neurônios artificiais, que por meio de um processo denominado treinamento, podem aprender uma tarefa. No caso das aplicações de visão computacional, é como se o computador fosse o nosso cérebro e a câmera nossos olhos. A câmera captura a imagem e manda para o computador fazer o processamento. 

Neste trabalho, temos duas redes neurais envolvidas, que são, uma rede de detecção de pessoas e uma rede de transferência de estilo. Vamos explicar melhor o comportamento de cada uma delas.

#### Rede neural para detecção de pessoas: 

Essa rede neural é responsável por detectar uma pessoa na imagem, isto é, dado uma imagem de entrada, saber qual região desta image representa uma pessoa. Existem muitos estudos sobre esse tipo de problema, e neste projeto, utilizamos uma das boas soluções existentes. A título de curiosidade, o nome dessa rede neural é [YOLO](https://pjreddie.com/darknet/yolo/). Na imagem a seguir, podemos ver uma das formas que a rede neural pode indicar a presença de uma pessoa, que é o quadrado preto delimitando a área em que foi detectada uma pessoa. 

<img src="{{ site.url }}{{ site.baseurl }}/images/pinacoteca-50-anos/transfer/bounding.png"  height="250px" />

Existem outras formas de representar a presença de uma pessoa na imagem, como vamos ver a seguir.

- Como a rede neural sabe que há pessoa na frente da câmera?

A rede neural, como já mencionado, têm neurônios que podem ser treinados para aprender determinadas tarefas. Neste caso, a rede neural é treinada para fazer essa detecção de pessoas. O treinamento de uma rede neural se assemelha a um aluno estudando para uma prova. A rede tem uma lista de imagens e rótulos para essas imagens, dizendo se são pessoas ou não, e em que região da imagem a pessoa está, por exemplo. Na analogia com o aluno estudando podemos imaginar que ele tem uma lista de exercícios com gabarito. A rede neural responde o que tem naquelas imagens e confere nos rótulos se a resposta está correta ou incorreta. Esse processo é repetido até que ela fique boa nisso. Para saber se ela realmente aprendeu, e não apenas decorou, aplicamos novas imagens para ela, como se fosse uma prova, para verificar se ela consegue acertar. Se sim, ela está treinada. Portanto, quando você passa na frente dela, mesmo sendo uma pessoa nova, ela consegue te identificar. 


#### Rede neural para transferência de estilo: 

Empregamos também um segundo tipo de rede neural. Neste caso a tarefa em que a rede foi treinada é para ser capaz de mudar o estilo de uma imagem. Por exemplo, é comum que alguns artistas tenham o seu estilo muito claro. Muitas pessoas conseguem ver uma obra e saber que é de determinado artista. Isso acontece também em filmes de animação, desenhos ou simplesmente um estilo como esse que você viu no trabalho que remete a traços de [Xilogravuras](https://pt.wikipedia.org/wiki/Xilogravura). 

- Como ela aprende e aplica o estilo?

Essas redes neurais são capazes de separar o conteúdo e o estilo da imagem. Então se eu tenho um cachorro desenhado a lapis, o cachorro é o conteúdo e o estilo é a lapis. Depois que essa rede separou essas duas coisas ela aprende o estilo de uma imagem e o conteúdo da outra imagem. Junta as duas coisas e obtém a imagem original de conteúdo estilizada de acordo com a imagem que escolhemos para o estilo.


<img src="{{ site.url }}{{ site.baseurl }}/images/pinacoteca-50-anos/transfer/estilizada.png"  height="250px" />


#### Como juntar as duas redes?
Você pode estar pensado "Ok, eu entendi que uma rede percebe pessoas e a outra aplica um estilo a uma imagem, mas como a rede aplica o estilo apenas nas pessoas e não no fundo?"

Esse é um processo até que simples!  

Criamos uma máscara com a região que a pessoa ocupa na imagem, de acordo com a detecção da rede neural treinada para detecção de pessoas. Onde tem pessoa fica branco e onde não tem fica preto. Usando ainda a imagem original, aplicamos a segunda rede neural, que faz transferência de estilo, treinada para transformar qualquer imagem de entrada em uma imagem com o mesmo conteúdo porém no estilo que se assemelha à Xilogravuras. Depois disso, removemos da imagem estilizada tudo o que é preto na máscara. Assim, obtemos uma imagem que tem somente a pessoa com o estilo desejado. Posteriormente, invertemos a máscara criada. Isto é, onde era branco fica preto e vice-versa. Agora temos uma máscara em que o fundo é branco. Usando essa nova máscara, retiramos da imagem tudo o que não são pessoas, mantendo só o fundo. Por fim, juntamos a imagem composta pela pessoa estilizada com a imagem que tem o fundo original sem estilo e obtemos esse resultado. O processo completo pode parecer longo, mas acreditamos que a imagem a seguir irá ajudar a entender.

<img src="{{ site.url }}{{ site.baseurl }}/images/pinacoteca-50-anos/transfer/esquema_final.png"  width="100%" /> 




<div class="row"  style="margin-left:0px;">

## Equipe:

{% for types in site.data.pinacoteca-50-anos %}

{% if types.type == "transfer" %}

{% assign number_printed = 0 %}

{% for member in types.list %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" width="15%" style="float: left" />
  <h4>{{ member.name }} {% if member.homepage %}<a href="{{ member.homepage }}" title="Link to member homepage"><i class="fa fa-home fa-fw" aria-hidden="true"></i></a>{% endif %} {% if member.github %}<a href="{{ member.github }}" title="Link to member github"><i class="fa fa-github fa-fw" aria-hidden="true"></i></a>{% endif %} </h4>
  
  <i>{{ member.level }} </i>

</div>


{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}
</div>

{% endif %}

{% endfor %}