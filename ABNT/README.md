# Pasta ABNT - Padrões de Formatação e Referências Bibliográficas

## Visão Geral

A pasta `ABNT` funciona como o repositório central de tipografia acadêmica e padronização bibliográfica do projeto. O objetivo deste diretório é garantir que todos os relatórios técnicos e gerenciais compilados através do Quarto Markdown (`.qmd`) adotem, de forma automatizada e consistente, as normas da Associação Brasileira de Normas Técnicas (ABNT).

A centralização destes arquivos impede a redundância de código e facilita a manutenção cruzada. Quando uma nova referência ou lei é adicionada aqui, ela se torna imediatamente disponível para ser citada em qualquer documento ou pipeline do repositório.

## Estrutura de Diretórios

A arquitetura desta pasta é intencionalmente enxuta, contendo apenas os artefatos de estilização e o banco de dados bibliográfico:

```text
ABNT/
├── abnt.csl               # Motor de regras visuais e tipográficas (Citation Style Language)
└── referencias.bib        # Banco de dados centralizado de bibliografias (Formato BibTeX)
```

## Funcionalidade de Cada Componente

### 1. O Arquivo de Estilo (`abnt.csl`)

O arquivo `.csl` (*Citation Style Language*) é um documento XML estruturado que descreve exatamente como as citações e a lista de referências devem ser formatadas. Ele dita regras como:

* O uso de caixa alta para autores na lista de referências finais (ex: BRASIL. Lei nº 13.709...).
* A formatação de citações no meio do texto, determinando se devem usar parênteses, ano, e recuos.
* A ordenação alfabética automática da bibliografia gerada no final do PDF.

*Nota: Este arquivo geralmente não precisa ser editado ou alterado, a menos que ocorra uma atualização oficial nas normas da ABNT.*

### 2. O Banco de Dados (`referencias.bib`)

O arquivo `.bib` é um banco de dados em formato de texto puro (BibTeX). Ele armazena os metadados de todas as fontes (leis, livros, sites, manuais técnicos) utilizadas no projeto de anonimização. Cada entrada possui um "identificador único" que será chamado dentro dos scripts.

## Guia de Utilização (Adicionando Citações)

Para que uma nova fonte seja reconhecida pelos relatórios do Quarto, ela deve ser primeiramente cadastrada no arquivo `referencias.bib` e, em seguida, invocada no texto.

### Passo 1: Cadastrando a Referência no `.bib`

Abra o arquivo `referencias.bib` com qualquer editor de texto e adicione o bloco correspondente ao tipo de material. A primeira palavra após a abertura de chaves (ex: `lgpd2018`) é o identificador (chave) daquela citação.

**Exemplo de Legislação (LGPD):**

```bibtex
@legislation{lgpd2018,
  title         = {Lei nº 13.709, de 14 de agosto de 2018},
  shorttitle    = {Lei Geral de Proteção de Dados Pessoais (LGPD)},
  author        = {{Brasil}},
  year          = {2018},
  month         = {aug},
  day           = {14},
  journal       = {Diário Oficial da União},
  url           = {https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm}
}
```

Como chaves duplas foram utilizadas no campo `author` (author = {{Brasil}}), o Pandoc entende que "Brasil" é um autor institucional (corporativo) e não uma pessoa (evitando que ele vire "BRASIL, B.")

**Exemplo de Software/Manual Técnico:**

```bibtex
@manual{falabr_api,
  title        = {Manual de Integração da API Fala.BR},
  author       = {{Controladoria-Geral da União (CGU)}},
  year         = {2024},
  organization = {Governo Federal do Brasil},
  url          = {https://falabr.cgu.gov.br/help}
}
```

### Passo 2: Inserindo a Citação no Relatório (`.qmd`)

Nos seus scripts Quarto, você não precisa se preocupar em digitar o nome do autor ou o ano manualmente. Basta utilizar o identificador cadastrado entre colchetes, precedido de um arroba `[@identificador]`.

* **Citação Narrativa (Autor fora dos parênteses):**
Para citar o autor naturalmente no fluxo da frase, retire os colchetes externos.
* **Sintaxe no código:** `Conforme estabelecido pelo Governo Federal @lgpd2018, o projeto atende às normas.`
* **Resultado no PDF:** "Conforme estabelecido pelo Governo Federal Brasil (2018), o projeto atende às normas."

* **Citação em Final de Parágrafo:**
*  Ideal para quando você resume uma ideia e indica a fonte apenas no fim.
* **Sintaxe no código:** `O tratamento de dados deve seguir o princípio da finalidade [@lgpd2018].`
* **Resultado no PDF:** "O tratamento de dados deve seguir o princípio da finalidade (BRASIL, 2018)."

* **Citação Ocultando o Autor (Apenas o Ano):**
Para citar o autor naturalmente no fluxo da frase, utilize o sinal de menos `-` para suprimir o autor dos parênteses.
* **Sintaxe no código:** `Conforme estabelecido pelo Governo Federal [-@lgpd2018], o projeto atende às normas.`
* **Resultado no PDF:** "Conforme estabelecido pelo Governo Federal (2018), o projeto atende às normas."

* **Citação com Página, Artigo ou Detalhes:**
Para leis, é essencial citar o artigo ou inciso específico. Você pode adicionar qualquer texto complementar após a chave, separado por vírgula.
* **Sintaxe no código:** `Conforme definido no texto legal [@lgpd2018, art. 5º, II].`
* **Resultado no PDF:** "Conforme definido no texto legal (BRASIL, 2018, art. 5º, II)."

Ao final da renderização de qualquer `.qmd`, o Quarto varrerá o documento, encontrará todas as tags `@...` utilizadas e construirá automaticamente a seção **Referências** na última página do arquivo, devidamente formatada pela ABNT.

## Integração com a Arquitetura Global

O funcionamento desta pasta é garantido pela configuração mestre do projeto. No arquivo `_quarto.yml` (localizado na raiz do repositório), existem duas linhas que apontam o motor de renderização diretamente para esta pasta:

```yaml
bibliography: "ABNT/referencias.bib"
csl: "ABNT/abnt.csl"
```