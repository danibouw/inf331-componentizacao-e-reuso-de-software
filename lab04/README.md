# Lab04 - Serviços <!-- omit in toc -->

## Tarefa 1

Componentes de Negócio

Delimite partes do diagrama à esquerda que você avalia que deveriam estar dentro de um componente.

### Diagrama

![tarefa 1]()

---

## Tarefa 2

Componentes Técnicos

Separe os componentes do View daqueles definidos no Controller.

### Diagrama

![tarefa 2]()

---

## Tarefa 3

Componentes Técnicos

Separe os componentes do Model daqueles definidos no Controller.

### Diagrama

![tarefa 2]()

## Tarefa 4

### Serviço `1`

* **Título do serviço**: `Covid19 Brazl API`
* **Breve descrição**:
  > API que notifica casos de doença pelo coronavírus 2019 (COVID-19) no Brasil e mundo.  
  > Mais informações podem ser vista em seu repositório do Github: [covid19-brazil-api @ Github](https://github.com/devarthurribeiro/covid19-brazil-api)
* **Comando da execução**:
    ~~~bash
    export PAIS=brazil
    export UF=sp
    curl --request GET \
        --url "https://covid19-brazil-api.now.sh/api/report/v1/${PAIS}/uf/${UF}"
    ~~~
* **URL completa da requisição**: `https://covid19-brazil-api.now.sh/api/report/v1/brazil/uf/sp`
* **Cabeçalho HTTP da chamada**:
    ~~~http
    GET /api/report/v1/brazil/uf/sp HTTP/2
    Host: covid19-brazil-api.now.sh
    User-Agent: curl/7.64.1
    Accept: */*
    ~~~
* **Cabeçalho HTTP da resposta**:
    ~~~http
    HTTP/2 200 
    content-type: application/json; charset=utf-8
    access-control-allow-credentials: true
    date: Sat, 29 Aug 2020 00:34:29 GMT
    access-control-allow-origin: *
    cache-control: public, max-age=0, must-revalidate
    content-length: 139
    x-vercel-cache: MISS
    age: 0
    server: Vercel
    x-vercel-id: gru1::sfo1::jlt8r-1598661269304-602a06d5c8b0
    strict-transport-security: max-age=63072000; includeSubDomains; preload
    ~~~
* **Conteúdo da resposta**:
    ~~~json
    {
        "uid": 35,
        "uf": "SP",
        "state": "São Paulo",
        "cases": 796209,
        "deaths": 29694,
        "suspects": 5334,
        "refuses": 596,
        "datetime": "2020-08-28T22:34:16.793Z"
    }
    ~~~


### Serviço 2 

* **Título do serviço:**
 
 FireBrowse Beta API
 
* **Breve descrição:**
 
O serviço da acesso a dados sobre câncer, ele pede parâmetros de formato, tipo de câncer, gene, código de barra do genoma do câncer.
Para a pesquisa foram colocados os parâmetros:
Format: json;
Cohort: ACC;
Gene: Não preenchido;
TCGA_Participant_Barcode: TGCA_GF_A4EO
	
 * **URL completa da requisição:**
 
https://any-api.com:8443/http://firebrowse.org/api/v1/Analyses/CopyNumber/Genes/All?format=json&cohort=ACC&tcga_participant_barcode=TCGA-GF-A4EO&sort_by=cohort
	
 * **Cabeçalho HTTP da chamada:**
 ~~~http
GET /http://firebrowse.org/api/v1/Analyses/CopyNumber/Genes/All?format=json&cohort=ACC&tcga_participant_barcode=TCGA-GF-A4EO&sort_by=cohort HTTP/2
Host: any-api.com:8443
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:80.0) Gecko/20100101 Firefox/80.0
Accept: application/json
Accept-Language: pt-BR,pt;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate, br
Origin: https://any-api.com
Connection: keep-alive
Referer: https://any-api.com/firebrowse_org/firebrowse_org/console/Analyses/All
TE: Trailers
~~~
 * **Cabeçalho HTTP da resposta:**
~~~http
HTTP/2 200 OK
date: Fri, 28 Aug 2020 01:10:27 GMT
content-type: text/html; charset=utf-8
set-cookie: __cfduid=dc788329fc8d33e074714630181df96511598577027; expires=Sun, 27-Sep-20 01:10:27 GMT; path=/; domain=.any-api.com; HttpOnly; SameSite=Lax
x-request-url: http://firebrowse.org/api/v1/Analyses/CopyNumber/Genes/All?format=json&cohort=ACC&tcga_participant_barcode=TCGA-GF-A4EO&sort_by=cohort
access-control-allow-origin: *
access-control-allow-methods: HEAD, GET
access-control-max-age: 21600
vary: Accept-Encoding
x-final-url: http://firebrowse.org/api/v1/Analyses/CopyNumber/Genes/All?format=json&cohort=ACC&tcga_participant_barcode=TCGA-GF-A4EO&sort_by=cohort
access-control-expose-headers: date,server,access-control-allow-origin,access-control-allow-methods,access-control-max-age,vary,content-encoding,content-length,content-type,connection,x-final-url
cf-cache-status: DYNAMIC
cf-request-id: 04d436c0370000f5dbe512f200000001
expect-ct: max-age=604800, report-uri="https://report-uri.cloudflare.com/cdn-cgi/beacon/expect-ct"
server: cloudflare
cf-ray: 5c9a27138b37f5db-GRU
content-encoding: br
X-Firefox-Spdy: h2
~~~

#### * Conteúdo da resposta:
~~~json
access-control-allow-methods: HEAD, GET
access-control-allow-origin: *
access-control-max-age: 21600
content-encoding: br
content-type: text/html; charset=utf-8
date: Fri, 28 Aug 2020 01:10:27 GMT
server: cloudflare
vary: Accept-Encoding
x-final-url: http://firebrowse.org/api/v1/Analyses/CopyNumber/Genes/All?format=json&cohort=ACC&tcga_participant_barcode=TCGA-GF-A4EO&sort_by=cohort
~~~
