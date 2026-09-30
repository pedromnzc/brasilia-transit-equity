# Sincronização do Transporte Coletivo e Desigualdade de Acessibilidade em Brasília

Projeto de pesquisa do UniCEUB que investiga como a dinâmica dos ônibus e a forma urbana de Brasília se combinam para produzir desigualdades de acesso entre as regiões do Distrito Federal.

> **Status:** em fase inicial. A estrutura do repositório e o pitch do projeto já estão prontos; coleta de dados e análises ainda não começaram.

## O problema

Brasília é uma cidade planejada, mas dispersa: os empregos se concentram no Plano Piloto e a moradia nas regiões administrativas e no Entorno. Quem mora mais longe depende mais do ônibus, espera mais e faz mais baldeações. O tempo perdido na espera não é distribuído de forma igual.

## Pergunta de pesquisa

> Como a dinâmica de **sincronização dos ônibus** e a **forma urbana** de Brasília se combinam para produzir **desigualdades de acessibilidade** entre as regiões do DF?

## Eixos do projeto

### 1. Sincronização (modelo de Kuramoto)

Cada ônibus é tratado como um oscilador: a sua **fase** é a posição na rota e cada um tem um **ritmo natural**. Os ônibus se influenciam, pois um veículo atrasado encontra mais passageiros no ponto e fica ainda mais lento, enquanto o de trás encontra o ponto vazio e o alcança. O modelo de Kuramoto descreve esse fenômeno:

$$
\frac{d\theta_i}{dt} = \omega_i + \frac{K}{N}\sum_{j=1}^{N}\sin(\theta_j - \theta_i)
$$

O grau de sincronização de uma linha é medido pelo parâmetro de ordem $r$, que vai de 0 (ônibus espalhados pela rota) a 1 (ônibus todos juntos).

Nem toda sincronização é ruim:

- **Na mesma linha, é ruim:** ônibus andando juntos (*bus bunching*) aumentam o intervalo de espera.
- **Entre linhas diferentes, é boa:** chegadas coordenadas nos pontos de baldeação reduzem a espera de quem troca de ônibus.

O modelo clássico precisará ser adaptado, pois nos ônibus a influência é local e as linhas do DF não são circuitos fechados.

### 2. Forma urbana (Frederico de Holanda)

A obra de Frederico de Holanda, que analisa Brasília como uma cidade de **exceção** marcada pela segregação socioespacial, ajuda a explicar **por que** a desigualdade de acesso tem essa geografia. Imagens de satélite complementam a análise, mostrando onde a cidade cresceu e comparando essa expansão com a cobertura das linhas de ônibus.

### 3. Dados

**A fonte definitiva dos dados ainda está em aberto.** As fontes consideradas até agora são:

| Tema | Fontes candidatas |
|---|---|
| Posição dos ônibus | Feed em tempo real da Semob-DF (o mesmo do app DF no Ponto), com coleta contínua por script próprio; dados históricos solicitados via Lei de Acesso à Informação |
| Rede planejada | Linhas, horários, itinerários e paradas da Semob-DF |
| Satélite e uso do solo | Sentinel-2, Landsat, CBERS-4A (INPE), ortofotos do Geoportal DF, MapBiomas |
| Socioeconômicos | Censo 2022 (IBGE), PDAD (IPEDF), Projeto Acesso a Oportunidades (Ipea) |

## Resultados esperados

- Um diagnóstico da sincronização das linhas do DF ao longo do dia
- Um mapa da desigualdade de tempo de espera e de acessibilidade
- Propostas de ajuste, como o espaçamento de linhas e a coordenação de baldeações
- Um artigo científico e um repositório reprodutível

## Estrutura do repositório

```text
.
├── ABNT/                  # Estilo de citação ABNT e banco de referências (.bib)
├── data/
│   ├── raw/               # Dados brutos
│   └── processed/         # Dados tratados
├── manuscript/            # Artigo científico
├── notes/                 # Anotações de pesquisa
├── outputs/
│   ├── figures/
│   ├── tables/
│   └── render/            # Documentos renderizados pelo Quarto
├── presentations/         # Apresentações em Quarto (.qmd)
├── scripts/               # Scripts de coleta e análise
└── _quarto.yml            # Configuração do projeto Quarto
```

A apresentação do projeto está em `presentations/01_pitch.qmd`, com a versão renderizada em `outputs/render/presentations/01_pitch.html`. Para renderizar:

```bash
quarto render
```

## Equipe

- Pedro Muniz Cherulli
- Sofia de Carvalho Raimundo
- Rafael Rosa Alves
- Rodrigo Lucas Alves

## Referências

HOLANDA, Frederico de. **O espaço de exceção**. Brasília: Editora Universidade de Brasília, 2002.

HOLANDA, Frederico de. Inclusão e exclusão em Brasília. **urbe. Revista Brasileira de Gestão Urbana**, v. 12, e20190306, 2020.

KURAMOTO, Yoshiki. **Chemical Oscillations, Waves, and Turbulence**. Berlin: Springer-Verlag, 1984.
