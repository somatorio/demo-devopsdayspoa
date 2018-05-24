## devopsdayspoa
Tema para [Hugo](http://gohugo.io) baseado no layout do [DevOpsDays Porto Alegre](http://poa.devopsdays.com.br).

Demonstração de uso disponível [aqui](https://github.com/somatorio/demo-devopsdayspoa)

No momento não utilizamos nada do diretório `content/` para gerar o site, porém o hugo necessita que esse diretório exista, portanto recomendamos que se crie um arquivo neste diretório :)


### Exemplos
*Todos estes exemplos estão disponíveis no repositório de demonstração*

O site é gerado por parâmetros do arquivo `config.toml` e por `data templates`:  

#### Arquivo `config.toml`:
```
[params]
description = "Evento de exemplo :)" #irá preencher o meta description
slider = "enable" #qualquer coisa que não seja "enable" irá desabilitar o slider (as imagens que ficam correndo atrás do logo/nome do evento)
slider_selector = "disable" #qualquer coisa que não seja "enable" irá desabilitar os seletores
slider_sidecontrols = "enable" #qualquer coisa que não seja "enable" irá desabilitar os controles
intro_image = "Gears.svg" #apenas o nome da imagem, deve estar em img/intro/
link_c4p = "http://somatorio.org" #endereço para o form/sistema de call4papers

email = "nao-existe@nao-existe.com" #email da organização do email
twitter = "nao-existe" #para https://www.twitter.com/nao-existe colocar apenas "não-existe"
facebook = "nao-existe" #para https://www.facebook.com/nao-existe colocar apenas "não-existe"

#Os próximos 3 parametros aceitam tags html (ex: <br>) e markdown (ex: **negrito**)
quando = "14 de Novembro<br>**Atenção: Não é um evento real! Apenas uma demonstração!**"
onde = "Silo DevOps<br>Rua CAMS, 3464<br>ICE Ville"
quanto = "Em **breve** mais *informações*"

#latitude e longitude podem ser pegos no google maps mesmo :)
#o mapa irá ficar centralizado nessas coordenadas E irá colocar o marcador exatamente sobre elas
mapa_latitude = 28.3852332
mapa_longitude = -81.5639171
mapa_zoom = 14 #nível de zoom que será apresentado o mapa
mapa_draggable = true #o mapa poderá ser arrastado?
mapa_zoomControl = true #mostrar o controle de zoom?
mapa_scrollwheel = false #a roda de rolagem do mouse deve poder alterar o zoom?
mapa_disableDoubleClickZoom = true #vou ser sincero, não entendi o que isso faz, hahaha
mapa_key = "" #chave na api do google, lembre de permitir o uso no google maps e afins!

status_ingressos = "indisponiveis" #qualquer coisa que não seja "disponiveis" irá mostrar o aviso
aviso_status_ingressos = "Esgotados!"

status_programacao = "disponivel" #qualquer coisa que não seja "disponivel" irá mostrar o aviso
aviso_status_programacao = "Em breve! ;)"
```

#### Data templates (aqui vão exemplos de 1 arquivo, mas podem ser escritos n arquivos que irão gerar conteúdo no site)

Ficam no diretório `data/` e (preferencialmente) seguem a linguagem [toml](https://github.com/toml-lang/toml) (aceita yaml também)

`data/ingressos/padrao.toml`
```
nome = "Valor Padrão ;)" #nome do tipo de ingresso
descricao = "Valor **padrão** para os participantes" #descrição para o tipo de ingresso
valor = "À partir de R$ 60,00" #valor para o tipo de ingresso
link = "http://somatorio.org" #endereço para a compra desse tipo de ingresso
```

`data/palestrantes/voce.toml`
```
nome = "Você?" #nome do palestrante
empresa = "" #empresa do palestrante
#minibio do palestrante (aceita markdown), caso seja necessário usar aspas, escapar com \ (ex: \"isto é um exemplo \")
minibio = "Que tal palestrar no DevOpsDays Unicorpolis? Você pode compartilhar suas idéias, cases, qualquer coisa! Aceitamos palestras de qualquer nível. Maiores informações em breve!"
imagem = ""  #imagem do palestrante, apenas o nome da imagem... deve estar em static/img/palestrantes
```

`data/patrocinio/beneficios/banners.toml`
```
nome = "banners" #nome do beneficio, será usado como chave nas categorias de patrocinio
#descrição do benefício
descricao = "Oportunidade de exibição do logotipo da empresa no site, cartazes e banners (tamanho relativo)"
```

`data/patrocinio/categorias/bronze.toml`
```
nome = "bronze" #nome da categoria de patrocinio
altura = "81px" #altura da imagem dos patrocinadores dessa categoria
largura = "162px" #largura da imagem dos patrocinadores dessa categoria
cota = "500" #valor da cota de patrocinio (ex: para R$ 500,00 colocar "500")

#os próximos campos são gerados dinamicamente, tendo como "chave" o nome dos beneficios
quantidade = "ilimitado"
banners = "1/2U"
```

`data/patrocinio/patrocinadores/placeholderbronze.toml`
```
nome = "placeholderbronze" #nome do patrocinador
descricao = "Sua empresa aqui!" #descricao que irá aparecer como texto alternativo da imagem
link = "" #endereço do site do patrocinador
categoria = "bronze" #categoria do patrocinador (deve ser o mesmo nome do arquivo em data/patrocinio/categorias sem a extensão)
imagem = "suaempresa.jpg" #imagem da empresa (apenas o nome do arquivo, deve estar em static/img/patrocinio)
```

`data/programacao/abertura.toml`
```
hora = "09:00 - 09:30" #hora da atividade
atividade = "Abertura" #nome da atividade
#descricao da atividade (aceita html e markdown)
#para uma descrição em multiplas linhas, abrir e fechar o campo com 3 aspas
#exemplo:
#descricao = """blablabla
#blablabla
#blablabla"""
descricao = "Momento do discurso de abertura do evento."
palestrante = "" #nome do palestrante

```

### Código de conduta
No diretório `layouts/partials/` (dentro do diretório do tema) há dois arquivos de *markdown*: `antiassedio.md` e `conduta.md` basta copiá-los para `layouts/partials/` (da "raiz" da estrutura do hugo) e alterá-los para personalizar seu código de conduta e politica anti-assédio.

Para personalizar alguma seção basta copiar o arquivo *partial* correspondente para `layouts/partials/` (da "raiz" da estrutura do hugo) e alterá-lo a vontade... Mais informações [aqui](http://gohugo.io/themes/customizing/)
