---
title: "MaVILab - TCC"
subtitle: "TCC"
layout: textlay
excerpt: "TCC - Final paper (form portuguese: Trabalho de Conclusão de Curso)"
sitemap: false
permalink: /tcc
---

# TCC

TCC is the final paper of undergraduate students (from portuguese *Trabalho de Conclusão de Curso*).

<!-- ## Group highlights -->

<p> &nbsp; </p>

{% for years in site.data.tcc_list %}
<h4>{{ years.year }}</h4>

{% for tcc in years.tccs %}
<p>
<strong>{{ tcc.title }}</strong> <br />
<em>Keywords:</em> {{ tcc.Keywords }} <br />
<em>Institution:</em> {{ tcc.Institution }} <br />
<em>Department:</em> {{ tcc.Department }} <br />
<em>BsC Student:</em> {{ tcc.Student }} <br />
<em>Advisor:</em> {{ tcc.Advisor }} <br />
{% if tcc.Coadvisor %}
<em>Co-advisor:</em> {{ tcc.Coadvisor }} <br />
{% endif %}
<br />
</p>

{% endfor %}
{% endfor %}

<!-- 
### 2023

**Identificação de Doenças em Sementes de Soja.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Gabriel Macedo Nunes Pontes   
*Advisor:* Michel Melo da Silva 
<br />

**Avaliação de dispositivo de captura e técnicas de reconstrução de objetos em 3D.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Lucas Teixeira Reis   
*Advisor:* Michel Melo da Silva 
<br />

**Criação de um dataset sintético de movimentos utilizando uma Engine Gráfica.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Matheus Antonio dos Santos Lima   
*Advisor:* Michel Melo da Silva 
<br />

**Construção de dataset para Libras.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Mateus de Lana Orlovski   
*Advisor:* Michel Melo da Silva 
<br />

**Aplicação mobile para contagem de soja com danos mecânicos.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Daniela Assis de Sousa   
*Advisor:* Michel Melo da Silva 
<br />

### 2022

**Classificação automática de documentos para técnica de OCR.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Sarah Carvalho Alves   
*Advisor:* Michel Melo da Silva 
<br />

**Análise de técnicas de processamento digital de imagens para aplicação de OCR.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Manoela Werneck Auad   
*Advisor:* Michel Melo da Silva 
<br />

### 2021

**Fine tuning de rede neural para classificação de ambientes em cenas de webinário.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Ricson Luiz Oliveira Vilaça   
*Advisor:* Michel Melo da Silva  
*Co-Advisor:* Daniel Louzada Fernandes  
<br />

**Análise de funções de perda em redes convolucionais para super-resolução de ilustrações.**  
*Institution:* UFV (Viçosa, Brazil)  
*Department:* Department of Informatics  
*BsC Student:* Raphael Carmo Silva Nepomuceno   
*Advisor:* Michel Melo da Silva    
<br />

-->