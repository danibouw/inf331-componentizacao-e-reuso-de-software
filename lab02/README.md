# Lab02 - Data Flow & Mensagens

## Tarefa sobre catálogo de componentes

No diretório s02catalog em santanche/component2learn está o notebook `components-01-catalog.ipynb` que apresenta o catálogo de componentes e o modo de conectá-los (visto pela perspectiva blackbox - externa) para montar uma composição. 

Ele apresenta seis tarefas que devem ser resolvidas. A entrega desse lab será formada pelo notebook `components-01-catalog.ipynb` com as seis tarefas resolvidas.

### Resolução

[Arquivo do notebook]()

## Tarefa Web Components 1

Crie quatro botões com rótulos `Mundo`, `Brasil P`, `Brasil E` e `Bahia` que, ao serem clicados, publiquem notícias nos seguintes tópicos (conteúdo a sua escolha):
* `noticia/mundo/politica`
* `noticia/brasil/politica`
* `noticia/brasil/esporte`
* `noticia/bahia/esporte`

O segundo nível do tópico indica a região da notícia e o terceiro o assunto. Associe a cada tópico o texto de uma mensagem de sua criação.

Crie três personagens (`doctor`, `nurse` e `patient`) usando o `<dcc-lively-talk>`. Cada um deles deve mostrar seletivamente (em seu balão) notícias publicadas pelos botões, conforme os seguintes critérios:
* `doctor` - mostra notícias sobre política (independentemente de região);
* `nurse` - mostra notícias cuja região é o Brasil (independentemente do assunto);
* `patient` - mostra todas as notícias.


```html
<!-- Buttons -->
<dcc-trigger label="Mundo"
             action="noticia/mundo/politica"
             value="política mundial">
</dcc-trigger>
<dcc-trigger label="Brasil P"
             action="noticia/brasil/politica"
             value="política do Brasil">
</dcc-trigger>
<dcc-trigger label="Brasil E"
             action="noticia/brasil/esporte"
             value="esporte do Brasil">
</dcc-trigger>
<dcc-trigger label="Bahia"
             action="noticia/bahia/esporte"
             value="esporte da Bahia">
</dcc-trigger>

<!-- Characters -->
<dcc-lively-talk id="doctor"
                 character="doctor"
                 speech="Notícias sobre ">
  <subscribe-dcc topic="noticia/+/politica"></subscribe-dcc>
</dcc-lively-talk>
<dcc-lively-talk id="nurse"
                 character="nurse"
                 speech="Notícias sobre ">
  <subscribe-dcc topic="noticia/brasil/#"></subscribe-dcc>
</dcc-lively-talk>
<dcc-lively-talk id="patient"
                 character="patient"
                 speech="Notícias sobre ">
  <subscribe-dcc topic="noticia/#"></subscribe-dcc>
</dcc-lively-talk>
```

## Tarefa Web Components 2

Crie dois componentes RSS usando o `<dcc-rss>` que assinem os canais:
  * canal 1 (ciência): https://www.wired.com/category/science/feed
  * canal 2 (design): https://www.wired.com/category/design/feed

Crie um agregador de mensagens usando o `<dcc-aggregator>` para notícias de ciência.

Crie três personagens (`doctor`, `nurse` e `patient`) usando o `<dcc-lively-talk>`. Cada um deles deve mostrar seletivamente (em seu balão) RSSs ou agregados, conforme os seguintes critérios:
* `doctor` - mostra notícias agregadas de ciências;
* `nurse` - mostra notícias de ciências;
* `patient` - mostra notícias de design.

```html
<dcc-trigger label="Get News" action="next/rss">
</dcc-trigger>

<!-- Science RSS -->
<dcc-rss publish="rss/science" source="https://www.wired.com/category/science/feed">
  <subscribe-dcc topic="next/rss" role="step"></subscribe-dcc>
</dcc-rss>
<!-- Design RSS -->
<dcc-rss publish="rss/design" source="https://www.wired.com/category/design/feed">
  <subscribe-dcc topic="next/rss" role="step"></subscribe-dcc>
</dcc-rss>

<!-- Science Aggregator -->
<dcc-aggregator publish="aggregate/science" quantity="3">
  <subscribe-dcc topic="rss/science"></subscribe-dcc>
</dcc-aggregator>

<!-- Characters -->
<dcc-lively-talk id="doctor"
                 duration="0s"
                 character="doctor"
                 speech="Aggregate news about Science">
  <subscribe-dcc topic="aggregate/science"></subscribe-dcc>
</dcc-lively-talk>
<dcc-lively-talk id="nurse"
                 duration="0s"
                 character="nurse"
                 speech="News about Science">
  <subscribe-dcc topic="rss/science"></subscribe-dcc>
</dcc-lively-talk>
<dcc-lively-talk id="patient"
                 duration="0s"
                 character="patient"
                 speech="News about Design">
  <subscribe-dcc topic="rss/design"></subscribe-dcc>
</dcc-lively-talk>
```
