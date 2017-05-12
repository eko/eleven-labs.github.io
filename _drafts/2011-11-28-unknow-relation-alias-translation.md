---
layout: post
title: Unknow relation alias Translation
author: rjardinet
date: '2011-11-28 15:06:50 +0100'
date_gmt: '2011-11-28 15:06:50 +0100'
categories:
- Symfony
tags:
- symfony
---
{% raw %}
<p>Hello,</p>
<p>Un petit Bug qui subsiste dans Symfony 1.4, lorsque l'on joue avec l'admin generator avec les éléments i18n.</p>
<p><!--more--></p>
<p>Il peut arriver que lors de l’exécution d'un batch action ou autre sur l'admin G sur une table avec une liaison i18n, on tombe sur cette erreur la : "Unknow relation alias Translation" malgré que tout semble correct.</p>
<p>La solution est simple, ouvrez le fichier generator.yml sur module sur lequel vous travaillez, et regardez attentivement la 4eme ligne: model_class.</p>
<p>Essayez de mettre une majuscule au nom de la class ici sur cette ligne.</p>
<p>On aura alors</p>
<pre class="brush: xml; gutter: false">generator:
  class: sfDoctrineGenerator
  param:
    model_class:           actor</pre>
<p>Qui devient :</p>
<pre class="brush: xml; gutter: false">generator:
  class: sfDoctrineGenerator
  param:
    model_class:           Actor</pre>
<p>Vous avez une chance sur deux pour que cela corrige votre problème. Cela vient de Doctrine qui utilise sa propre config en cache avec ses noms de model contenant une majuscule comme première lettre.</p>
<p>&nbsp;</p>
<p>Bref, en espérant que cela vous aide.</p>
<p>&nbsp;</p>
{% endraw %}