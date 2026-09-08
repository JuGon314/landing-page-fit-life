# FitLife - Landing Page

Landing page para um aplicativo fitness, criada com HTML e CSS puros. O projeto apresenta o FitLife, destaca a tela principal do aplicativo e explica seus principais recursos de forma simples e responsiva.

## Objetivo

Construir uma pagina clean e sofisticada para um aplicativo fitness, usando uma paleta baseada em tons de verde, bastante espaco em branco e uma hierarquia visual clara.

A pagina foi organizada em quatro partes principais:

- Header com a marca, seletor de idioma e botao de download
- Hero com a mensagem principal, o print de destaque e os pontos-chave do app
- Secao de funcionalidades com tres recursos explicados
- CTA e rodape

## Estrutura de arquivos

```text
landing_page/
|-- index.html
|-- style.css
|-- README.md
|-- docs/
|   `-- plan.md
`-- images/
    |-- print_1.png
    |-- print_2.png
    |-- print_3.png
    `-- print_4.png
```

## HTML aplicado

### Estrutura semantica

O documento usa elementos semanticos para separar as areas da pagina:

- `header`: apresenta a marca FitLife e a acao principal
- `main`: agrupa o conteudo principal
- `section`: organiza hero, funcionalidades e CTA
- `article`: representa cada funcionalidade individual
- `footer`: apresenta a informacao de direitos reservados

Essa organizacao facilita a leitura do codigo, melhora a acessibilidade e deixa mais claro o papel de cada bloco.

### Header e idioma

O cabecalho apresenta a marca FitLife e, ao lado, um controle simples para alternar entre PT-BR e EN. Esse seletor foi desenhado como uma pequena switcher com botoes visuais, mantendo a navegacao rapida e sem adicionar muita complexidade ao codigo.

Os textos da pagina foram organizados em um objeto de traducoes para facilitar a manutencao. Ao clicar no idioma desejado, os elementos com atributo `data-i18n-key` recebem o conteudo correspondente, incluindo textos visuais e atributos como `alt` e `aria-label`.

### Hero

A hero possui tres areas:

1. Mensagem principal sobre o aplicativo
2. Imagem central com `print_1.png`
3. Lista com os pontos-chave: saude, exercicio e amigos

O link da marca usa a ancora `#hero` para retornar ao inicio da pagina.

### Funcionalidades

A secao usa tres elementos `article`, cada um com:

- Uma imagem do aplicativo
- Um numero de identificacao
- Um titulo
- Uma descricao curta

Os textos foram escritos de acordo com o conteudo visual de cada print:

- `print_2.png`: acompanhamento de calorias
- `print_3.png`: escolha de exercicios
- `print_4.png`: compartilhamento da evolucao com amigos

As imagens possuem textos alternativos descritivos por meio do atributo `alt`.

### CTA

A chamada para acao fica em uma secao propria, com:

- Um pequeno texto de contexto
- Um titulo de incentivo
- Um botao maior de download
- A informacao de que o aplicativo e totalmente gratuito

Os botoes estao preparados com links internos. Para disponibilizar um download real, basta substituir o valor de `href` pela URL da loja ou do arquivo do aplicativo.

## CSS aplicado

### Variaveis de cor

As cores principais foram centralizadas em `:root`, o que facilita a manutencao e garante consistencia visual:

- Verde escuro para a marca e estados de maior contraste
- Verde principal para botoes e destaques
- Verde claro para fundos de apoio
- Tons de texto e borda para informacoes secundarias

### Reset basico e box model

O seletor universal aplica `box-sizing: border-box`, fazendo com que padding e borda sejam incluidos no tamanho total dos elementos. Isso torna o dimensionamento mais previsivel.

As margens padrao do `body` sao removidas e os links herdam a cor do contexto, evitando estilos inesperados do navegador.

### Tipografia

A fonte principal e Roboto, carregada pelo Google Fonts. Os titulos usam peso moderado, altura de linha compacta e leve ajuste de espaco entre letras para preservar o estilo clean da proposta.

A classe `.eyebrow` identifica pequenos textos de apoio em caixa alta, com cor verde e espacamento entre letras.

### Layout responsivo

A implementacao das novas secoes segue uma abordagem mobile-first:

- No mobile, cada funcionalidade aparece em uma coluna
- As imagens ficam centralizadas e limitadas pela largura disponivel
- O CTA ocupa toda a largura visual da tela
- No desktop, a secao de funcionalidades passa a usar CSS Grid com duas colunas
- A segunda funcionalidade inverte a ordem para formar o padrao imagem/texto, texto/imagem, imagem/texto
- O header ajusta seu comportamento em telas estreitas para evitar overflow do seletor de idioma e do botao de download
- O grupo de controles do topo pode quebrar em duas linhas em resolucoes muito pequenas, sem comprometer legibilidade

A media query `@media (min-width: 761px)` aplica apenas os ajustes necessarios para telas maiores. O layout existente da hero continua usando sua media query para adaptar a apresentacao em telas pequenas, com ajustes extras em pontos muito pequenos como 320px.

### Espacamento e hierarquia

As secoes usam `max-width` para evitar linhas de texto muito longas. Bordas superiores discretas separam as funcionalidades sem transformar cada item em um card, mantendo o visual leve.

O CTA usa o tom verde claro como faixa de destaque, criando separacao visual sem fugir da identidade da pagina.

### Interacoes

O botao de download possui estados `hover` e `focus-visible`:

- O fundo muda para o verde escuro
- O botao sobe levemente com `transform`
- O estado de foco permanece visivel para navegacao por teclado

O seletor de idioma tambem recebe destaque visual ao estar ativo, mostrando ao usuario qual linguagem esta selecionada.

A propriedade `scroll-behavior: smooth` deixa a navegacao entre ancoras mais fluida.

## JavaScript aplicado

A pagina foi atualizada com um script simples para gerenciar a internacionalizacao sem depender de bibliotecas ou frameworks.

### Estrutura da traducao

Os textos sao armazenados em um objeto JavaScript com chaves por idioma:

- `pt-BR`: textos em portugues
- `en`: textos em ingles

Cada elemento da pagina que deve mudar de idioma possui o atributo `data-i18n-key`, e o codigo identifica a chave correspondente para trocar o conteudo do texto visual ou de atributos como `aria-label` e `alt`.

### Alternancia entre idiomas

Os botoes de idioma possuem os atributos `data-lang`, e o codigo observa o clique para:

- atualizar o texto visivel dos elementos traduziveis
- ajustar `aria-label` e `alt` quando necessario
- alterar o estado ativo do botao escolhido
- definir o idioma do documento em `document.documentElement.lang`

Essa abordagem e simples, leve e muito facil de manter, especialmente para uma landing page com poucas secoes e um conjunto limitado de textos.

## Acessibilidade

Foram aplicados alguns cuidados basicos:

- `lang="pt-br"` identifica o idioma principal do documento
- Cada imagem possui um `alt` descritivo
- As secoes usam `aria-labelledby` quando possuem um titulo associado
- A lista de pontos-chave possui `aria-label`
- O foco do teclado e preservado com `:focus-visible`
- O logo possui um `aria-label` explicando sua funcao
- O seletor de idioma expande a acessibilidade ao indicar o idioma ativo e manter labels claras para leitores de tela
- Os botoes e links permanecem com foco visivel em navegacao por teclado

## Como visualizar

Como o projeto usa apenas HTML, CSS e imagens locais, nao e necessario instalar dependencias.

Basta abrir o arquivo `index.html` no navegador ou usar a extensao Live Server no VS Code para acompanhar as alteracoes em tempo real.

## Conceitos praticados

- HTML semantico
- Acessibilidade basica na web
- CSS custom properties
- CSS Flexbox
- CSS Grid
- Design responsivo
- Abordagem mobile-first
- Media queries
- Hierarquia tipografica
- Estados de interacao
- Uso de textos alternativos em imagens
- Organizacao de layout por secoes
- Internacionalizacao simples com JavaScript
- Alternancia de idioma em tempo real
- Ajustes de responsividade para telas pequenas
