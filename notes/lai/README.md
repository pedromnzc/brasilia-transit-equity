# Pedido LAI – Dados de GPS e GTFS (SEMOB-DF)

Registro do pedido de acesso à informação feito à Secretaria de Estado de Transporte e Mobilidade do Distrito Federal (SEMOB-DF) para obter os dados usados neste TCC.

## Resumo

| Campo | Valor |
|---|---|
| Protocolo | LAI-025010/2026 |
| Órgão | SEMOB – Secretaria de Estado de Transporte e Mobilidade do DF |
| Plataforma | [Participa DF](https://www.participa.df.gov.br) |
| Data do pedido | 20/10/2026, 14h29 |
| Situação atual | Respondido (atendimento parcial) |
| Prazo de resposta (estimado) | 09/11/2026 (20 dias) |
| Prazo com prorrogação (estimado) | 19/11/2026 (+10 dias) |

Base legal citada: Lei nº 12.527/2011 (LAI), Lei Distrital nº 4.990/2012 e Lei Distrital nº 7.836.

## Escopo

**Período:** 17/08/2026 (segunda-feira) a 30/08/2026 (domingo), 14 dias corridos.

O período foi escolhido por não conter feriados, recesso escolar, jogos da Copa do Mundo, greves de rodoviários ou metroviários, nem datas de eleição.

**Linhas:**

| Linha | Descrição | Corredor | Papel no estudo |
|---|---|---|---|
| 2201 | Gama / Rodoviária (expressa) | BRT Sul | Duas origens que convergem no tronco do BRT |
| 2301 | Santa Maria / Rodoviária (expressa) | BRT Sul | |
| 0.385 | QNR 5 (Ceilândia) / Rodoviária via EPTG | EPTG | Duas origens que convergem em Taguatinga e seguem pela EPTG |
| 0.306 | Taguatinga Sul / Rodoviária (Eixo) | EPTG | |
| 373.2 | Samambaia Norte / Rodoviária (EPNB – Eixo) | EPNB | Duas origens que convergem na EPNB |
| 0.809 | Recanto das Emas / Rodoviária (Eixo) | EPNB | |
| 106.2 | Circular Terminal Asa Sul / L2 Sul / L2 Norte / W3 Norte / W3 Sul | Plano Piloto | Anel grande que se sobrepõe às duas circulares menores |
| 0.116 | Circular Asa Norte (W3 Norte / L2 Norte) | Plano Piloto | Comparada com o trecho norte da 106.2 |
| 0.114 | Circular Asa Sul (W3 Sul / L2 Sul) | Plano Piloto | Comparada com o trecho sul da 106.2 |

**Itens solicitados:**

1. Registros brutos de rastreamento GPS (veículo, linha, sentido, data/hora, latitude, longitude e, se disponíveis, velocidade e identificação da viagem).
2. GTFS estático do STPC/DF vigente no período.
3. Metadados: periodicidade de registro do GPS, prazo de retenção e dicionário de campos.

## Texto integral do pedido

> Prezados,
>
> Com fundamento na Lei nº 12.527/2011 (Lei de Acesso à Informação), na Lei Distrital nº 4.990/2012 e na Lei Distrital nº 7.836, solicito, para fins de pesquisa acadêmica de Trabalho de Conclusão de Curso (TCC), as informações abaixo referentes ao Sistema de Transporte Público Coletivo do Distrito Federal (STPC/DF).
>
> O pedido se destina ao Trabalho de Conclusão de Curso de Ciência de Dados, no Centro Universitário de Brasília (UniCEUB), sob orientação do Prof. Weslley Rodrigues, que analisa a dinâmica de espaçamento entre veículos em linhas que compartilham corredores, com base em modelos de sincronização de osciladores acoplados. Comprometo-me a disponibilizar o trabalho final a esta Secretaria, caso seja de interesse.
>
> Linhas: 2201, 2301, 0.385, 0.306, 373.2, 0.809, 106.2, 0.114 e 0.116.
> Período: de 17/08/2026 (segunda-feira) a 30/08/2026 (domingo), totalizando 14 dias corridos.
>
> 1. REGISTROS DE RASTREAMENTO GPS
> Registros brutos das posições dos veículos das linhas acima no período informado, contendo, para cada registro: identificação do veículo (prefixo ou placa), código da linha, sentido da viagem (quando disponível), data e hora, latitude e longitude. Caso constem do mesmo registro, solicito também a velocidade e a identificação da viagem. Esses dados são enviados pelas operadoras à SEMOB conforme a Portaria nº 89, de 25 de outubro de 2019.
>
> 2. GTFS
> Arquivo GTFS (General Transit Feed Specification) estático do STPC/DF vigente no período informado, completo e no formato em que já é gerado.
>
> 3. METADADOS
> Periodicidade de registro das posições de GPS, prazo de retenção desses dados e dicionário dos campos disponibilizados.
>
> FORMATO
> Preferencialmente CSV ou outro formato aberto, no formato em que os dados já são armazenados, sem necessidade de tratamento adicional. Os arquivos podem ser enviados compactados ou por link para download.
>
> OBSERVAÇÕES
> Os dados solicitados não contêm informações pessoais. Caso o período solicitado não esteja mais disponível, solicito o período de 14 dias corridos mais próximo, iniciando em uma segunda-feira. Caso algum dos itens não possa ser atendido, solicito o atendimento dos demais, com a justificativa do item não atendido.
>
> Atenciosamente,
> Pedro Muniz Cherulli

## Resposta

A SEMOB enviou só os registros de GPS, em CSV, por link para download. O despacho SEMOB/GAB/ASSAD (processo SEI 00090-00016476/2026-84) devolve o pedido à Ouvidoria depois das manifestações da SUOP (Despacho 217987855) e da SUTINF (Despacho 217998977). Esses dois despachos não vieram junto.

| Item pedido | Situação |
|---|---|
| 1. Registros de GPS | Entregue, sem identificação da viagem |
| 2. GTFS estático | Não enviado e sem justificativa |
| 3. Metadados | Parcial: a mensagem descreve 5 dos 16 campos; periodicidade e retenção não foram informadas |

### Conferência do CSV

Arquivo `data/raw/posicoesLai.csv` (274 MB), conferido em 04/11/2026.

| Verificação | Resultado |
|---|---|
| Registros | 1.940.615, sem `id_posicao` duplicado |
| Linhas | As 9 pedidas, nenhuma a mais |
| Período | 17/08 a 31/08/2026 (um dia a mais que o pedido) |
| Veículos | 858 |
| Intervalo entre posições | Mediana de 30 s (p25 = 21 s, p75 = 40 s) |
| Dias sem registro | 2301 em 23/08; 0.306 em 23/08 e 30/08 (domingos) |
| Campo `sentido` | Na linha 0.385 (operadora 3450) as colunas estão deslocadas: `sentido` traz o horário planejado da viagem e `imei` traz valores como `1,67` |
| Campos quase vazios | `geom_point` (99,7%), `hora_viagemplanejada` (80,1%), `gtfs_linha` e `turno` (76,8%), `imei` (23,2%) |

Colunas do CSV: `id_posicao`, `id_operadora`, `prefixo`, `datalocal`, `velocidade`, `cd_linha`, `direcao`, `latitude`, `longitude`, `dataregistro`, `geom_point`, `imei`, `sentido`, `hora_viagemplanejada`, `gtfs_linha`, `turno`.

Descrição enviada pela SEMOB: veículo, linha, posição, sentido (`1` = ida, `0` = volta) e `datalocal` (data da posição no GPS no momento da coleta).

### Alternativa ao GTFS

A SEMOB não publica GTFS no site nem no portal de dados abertos, e o DF não aparece na [Mobility Database](https://mobilitydatabase.org).

## Histórico

| Data | Evento | Observação |
|---|---|---|
| 20/10/2026 | Pedido protocolado | Situação: Recebido |
| 23/10/2026 | Despacho SEMOB/GAB/ASSAD | Assinado em 26/10/2026; devolve o pedido à Ouvidoria |
| 28/10/2026 | Download dos dados de GPS | CSV enviado por link |

## Arquivos

- `2026-10-20_pedido.pdf`: comprovante de protocolo do Participa DF (e-mail tarjado).
- `Despacho_218014831.pdf`: despacho da SEMOB com o encaminhamento da resposta.
- `Envio_Dados.txt`: mensagem da SEMOB com o link para os dados (link e e-mail tarjados).

Os dados brutos de GPS não são versionados neste repositório por causa do tamanho. Eles ficam em `data/raw/`, que está no `.gitignore`.

## Próximos passos

- [x] Acompanhar o pedido no Participa DF até o prazo.
- [x] Conferir se vieram os três itens e a periodicidade do GPS.
- [ ] Corrigir o deslocamento de colunas da linha 0.385 no tratamento dos dados.
