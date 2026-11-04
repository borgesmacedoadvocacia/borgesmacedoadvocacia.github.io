# Dashboard — Termômetro de Relacionamento com os Clientes

Painel da **pesquisa de satisfação** da BM Advocacia, lido em tempo real da planilha de respostas
do formulário (`1aucxxPz_EZbHdK7Xt0bDgH2s8-IS9YGUWD_H24FdW5E`, aba `Respostas`). Não há coletor
nem cópia intermediária: o painel lê a planilha que o próprio Google Formulários alimenta.

**Acesso geral.** Os três perfis da Central — Administração, Lideranças e Equipe — têm cofre
neste painel. Entra-se pela [Central de Dashboards](https://borgesmacedoadvocacia.github.io/).

## A pesquisa

[Formulário](https://docs.google.com/forms/d/e/1FAIpQLSfV0GkwT8phtjDRNPtTcm0a70MiPXZeEKLfB8yAFxIQQ9HWJQ/viewform)
com 12 perguntas:

| Perguntas | Respostas possíveis |
|---|---|
| Resultado do processo · Condução do processo · Atendimento da equipe · Comunicação · Satisfação geral | 😠 Muito insatisfeito · 🙁 Insatisfeito · 😐 Neutro · 🙂 Satisfeito · 😍 Muito satisfeito |
| Indicaria a BM · Voltaria a contratar | 🟢 Sim · 🟡 Talvez · 🔴 Não |
| Pontos positivos · O que precisamos melhorar | texto livre |
| Gostaria de se identificar · Nome completo · Telefone | identificação opcional |

## O termômetro

A escala de 5 vira uma nota de **0 a 100**: muito insatisfeito = 0, insatisfeito = 25,
neutro = **50**, satisfeito = 75, muito satisfeito = 100. É a média dessa conversão que aparece
no cartão **Termômetro geral** (sobre a pergunta de satisfação geral) e em cada linha de
**Termômetro por dimensão**. Verde a partir de 75, amarelo de 50 a 74, vermelho abaixo de 50.

## O que o painel mostra

- **Resumo**: respostas, termômetro geral, satisfeitos (nota 4–5), insatisfeitos (1–2),
  quantos indicariam (com o saldo *sim − não*) e quantos voltariam a contratar.
- **Termômetro por dimensão**: as cinco perguntas, cada uma com a nota e a distribuição das
  respostas numa barra; clicar numa faixa abre quem respondeu aquilo.
- **Indicação e recontratação**: rosca de Sim/Talvez/Não, clicável.
- **Quem precisa de atenção**: quem marcou insatisfação em **qualquer** pergunta ou disse que
  não indicaria — com nome e telefone de quem se identificou. É a lista de resgate, e por isso é
  maior que o cartão *Insatisfeitos*, que olha só a nota geral.
- **O que os clientes escreveram**: os dois campos de texto, com busca.
- **Evolução**: termômetro geral e volume de respostas, mês a mês.
- **Pontos de atenção**: insatisfações, a dimensão mais fraca, quem ficou em cima do muro e
  quanto da amostra é anônima.

Todo cartão, barra e linha abre a lista das respostas por trás do número.

## Detalhes que importam

- **As colunas são achadas pelo texto da pergunta**, nunca pela posição: editar o formulário
  reordena e renomeia colunas, e ler por letra passaria a mostrar a resposta de outra pergunta
  sem avisar. Pergunta que o painel não encontrar vira aviso em *Pontos de atenção*.
- As opções são casadas **sem emoji e sem acento**, então tirar o emoji do formulário não quebra
  nada.
- O carimbo de data/hora é lido em `dd/mm/aaaa hh:mm` e em ISO.
- Resposta **anônima** entra nas notas, mas não dá para dar retorno — o painel diz quantas são.

## Estrutura

```
termometro/index.html    painel completo (cofres, leitura via Sheets API v4, gráficos Chart.js)
```

Mora **dentro do repositório da Central**, e não em repositório próprio como os outros painéis,
porque criar repositório público está vetado para o agente na sessão em que isto foi feito. A
pasta é autocontida: para virar repositório próprio um dia, é só movê-la e trocar a URL em
`index.html` da Central.

Publicação: GitHub Pages via Actions (`.github/workflows/pages.yml`), a cada push em `main`.
Atualização automática a cada 5 minutos enquanto a aba estiver aberta.
