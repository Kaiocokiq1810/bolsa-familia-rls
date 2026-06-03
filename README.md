# bolsa-familia-rls
# Projeto BI II - Row Level Security (RLS)

## Autor
Kaique Duarte Guilherme

## Objetivo
Desenvolver um dashboard gerencial para acompanhamento dos repasses do Programa Bolsa Família utilizando Row Level Security (RLS) no Power BI.

## Estrutura dos Dados

Tabela Fato:
- fato_bolsa_familia

Tabelas Dimensão:
- dim_regioes
- dim_usuarios_rls

## Relacionamentos

1. fato_bolsa_familia[UF] → dim_regioes[UF]

2. dim_usuarios_rls utilizada para controle de acesso dinâmico por região.

## Medidas DAX

### Total Repasses

```DAX
Total Repasses =
SUM(fato_bolsa_familia[VALOR PARCELA])
```

### Total Beneficiarios

```DAX
Total Beneficiarios =
DISTINCTCOUNT(fato_bolsa_familia[NIS FAVORECIDO])
```

### Ticket Medio

```DAX
Ticket Medio =
AVERAGE(fato_bolsa_familia[VALOR PARCELA])
```

### Municipios Atendidos

```DAX
Municipios Atendidos =
DISTINCTCOUNT(fato_bolsa_familia[NOME MUNICÍPIO])
```

## Páginas do Relatório

### Visão Geral Nacional

- Total de Repasses
- Total de Beneficiários
- Ticket Médio
- Municípios Atendidos
- Repasses por Região
- Filtros por Ano e Mês

### Detalhe por Região/Estado

- Indicadores por UF
- Top 10 Municípios por Repasses
- Filtro por Região

## Implementação do RLS

### RLS Estático

Funções:
- Admin
- Gestor_Norte
- Gestor_Nordeste
- Gestor_CentroOeste
- Gestor_Sudeste
- Gestor_Sul

### RLS Dinâmico

Filtro aplicado:

```DAX
[email_usuario] = USERPRINCIPALNAME()
```

## Publicação

O relatório foi preparado para publicação no Power BI Service com suporte a RLS Estático e Dinâmico.
