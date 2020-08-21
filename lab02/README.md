# Lab02 - Data Flow & Mensagens

- [Tarefa sobre catálogo de componentes]()
- [Tarefa Web Components 1]()
- [Tarefa Web Components 2]()

## Tarefa sobre catálogo de componentes

[Arquivo do notebook]()

## Tarefa Web Components 1

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
