---
title: "MaVILab - Expo Pinacoteca"
subtitle: "Expo Pinacoteca"
layout: gridlay
excerpt: "MaVILab -- Expo Pinacoteca"
sitemap: false
permalink: /pinacoteca-50-anos/face-animation
---

# Pinacoteca UFV
## Exposição comemorativa de 50 anos
### Obra digital: Animação de Retratos

Somos o laboratório de Inteligência e Visão Computacional (MaVILab) do Departamento de Informática da Universidade Federal de Viçosa. Nosso foco é em pesquisas e soluções utilizando Visão Computacional e Inteligência Artificial (IA).  

Para criar essa obra digital, utilizamos uma tecnologia chamada rede neural artificial com o objetivo de dar vida à obra 'Francisca', fazendo com que ela se mova como se estivesse falando o texto que vocês ouviram. Originalmente, [Francisca é um retrato desenhado por Tarsila do Amaral](https://www.dac.ufv.br/sem-categoria/ufv-semana-de-arte-moderna-tarsila-do-amaral/).

Para alcançar esse objetivo, contamos com o projeto chamado [MakeItTalk](https://people.umass.edu/~yangzhou/MakeItTalk/), que tem como objetivo animar animar uma imagem em formato de retrato com base em um áudio de entrada para simular que a pessoa retratada na imagem esteja narrando o áudio de entrada. Para isso, o projeto executa as seguintes tarefas: reconhecimento de pontos faciais e animação desses pontos faciais a partir de um áudio de entrada. Para executar essas tarefas, são utilizadas duas rede neurais artificiais, uma para cada tarefa.

Adaptamos a aplicação destas redes neurais artificiais para otimizar o resultado para a nossa obra digital. O projeto original do MakeItTalk apresenta duas limitações:

1. A rede neural artificial foi treinada para detectar pontos faciais em imagens naturais, como fotos ou pinturas mais realistas.
2. A segunda rede neural artificial foi treinada para gerar animações dos pontos da face com base em áudio em inglês.

Para a criação desta obra, precisamos animar um desenho feito à mão com traços menos realistas, além de usar um áudio em português.

#### Solução para a detecção de pontos: 

Para contornar a dificuldade da rede em inferir os pontos faciais em imagens não realistas, realizamos uma primeira inferência utilizando a rede neural artificial e, em seguida, ajustamos manualmente os pontos para as posições corretas por meio de uma ferramenta específica para essa tarefa. Ou seja, após a inferência da rede neural artificial, movemos os pontos para as posições corretas.


##### Imagem com marcações feitas pela rede: 

<img src="{{ site.url }}{{ site.baseurl }}/images/pinacoteca-50-anos/face/Captura.png"  height="300px" />

#### Mesma imagem após os ajustes manuais:

<img src="{{ site.url }}{{ site.baseurl }}/images/pinacoteca-50-anos/face/Captura_filtrado.png"  height="300px" />


###### Solução para a movitação com áudio em português: 

Para solucionar relacionado com a animação dos pontos faciais para simular os movimentos de narrar o áudio de entrada, utilizamos uma ferramenta denominada [MediaPipe](https://developers.google.com/mediapipe/solutions/vision/pose_landmarker). Essa é uma outra rede neural artifical que, entre outras funcionalidades, detecta pontos, tanto faciais quanto corporais, em vídeos.

Nós gravamos um vídeo da face de uma pessoa narrando o texto que a Francisca irá narrar, e inferimos os pontos faciais para cada imagem desse vídeo utilizando o MediaPipe. Essa ferramenta detecta até mais pontos do que precisávamos, então fizemos uma filtragem para obter o número exato de pontos desejado. Isso porque precisamos que o video tenha o mesmo número de pontos por quadro que a imagem da Francisca. Isso nos forneceu as posições do nariz, olhos, boca e outros pontos da atriz em cada momento do vídeo. O resultado da rede foi um arquivo com todos os pontos e quadros capturados.

##### Pontos encontrados pelo MediaPipe:

<img src="{{ site.url }}{{ site.baseurl }}/images/pinacoteca-50-anos/face/PontosMulher.png"  height="300px" />

Agora, temos a imagem de Francisca com os pontos faciais importantes marcados e uma sequência que representa o movimento facial da atriz em cada quadro do vídeo. O próximo passo é combinar essas informações. Uma ferramenta semelhante àquela usada no MakeItTalk move os pontos de Francisca, ou seja, deforma a imagem dela da mesma forma que os pontos no vídeo da atriz foram deformados enquanto ela falava. Isso resulta em um vídeo de Francisca falando o texto desejado. Basta combinar o áudio com essa sequência de quadros para criar o efeito que vocês viram.

<video width="640" height="360" controls>
  <source src="{{ site.url }}{{ site.baseurl }}/images/pinacoteca-50-anos/face/video.mp4" type="video/mp4">
</video>



<div class="row"  style="margin-left:0px;">

## Equipe:

{% for types in site.data.pinacoteca-50-anos %}

{% if types.type == "face" %}

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
