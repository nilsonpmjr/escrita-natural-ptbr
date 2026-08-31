# escrita-natural-ptbr

Skill para agentes escreverem e revisarem texto em português do Brasil sem sotaque
de IA.

Quatro versões do mesmo artigo foram reescritas cortando "cenário", "robusto" e
"emblemático". O texto continuou soando a máquina: entre a primeira e a última versão
ele encolheu 41% e o número de séries de três subiu de oito para nove. Esse corpus é a
origem da skill e a razão da ordem em que ela trabalha. O sotaque de IA em português
está na arquitetura do texto, não no vocabulário, e trocar palavra por sinônimo mais
simples resolve pouco.

```bash
npx skills add nilsonpmjr/escrita-natural-ptbr
```

## Como ela trabalha

De fora para dentro, sempre nesta ordem:

1. **Briefing.** Antes da primeira linha, o agente levanta estilo, tema, contexto,
   tom e público, em uma rodada só de perguntas. O estilo vem primeiro, e quase sempre
   é deduzido do que você já escreveu no pedido, porque é ele que fixa o modelo de voz
   que o texto vai imitar. Texto vazio quase sempre nasce de briefing ausente, não de
   vocabulário ruim.
2. **Pesquisa.** De dois a quatro subagentes rodam em paralelo, cada um com um ângulo
   diferente: números com fonte, casos datados, histórico, contraditório. Todos recebem
   ordem de descartar conteúdo com cara de IA e de declarar o que não encontraram.
3. **Tese e linha de raciocínio.** Uma frase que o texto inteiro defende, e depois uma
   linha por parágrafo dizendo o que ele acrescenta ao anterior. Parágrafo que não
   passa nesse teste não existe ainda.
4. **Escrita**, no modelo de voz que o briefing fixou, depois de ler os exemplos
   trabalhados. Lista de proibição sem modelo de construção produz texto que não erra
   nada e não soa a ninguém.
5. **Revisão em três passadas**, nesta ordem: argumento e parágrafo, depois frase,
   depois palavra e pontuação. Inverter a ordem é o erro que fez o corpus original
   passar por quatro reescritas sem melhorar.
6. **Verificação antes de entregar**, obrigatória e contável: proporção de frases
   curtas, aberturas de parágrafo que retomam o anterior, séries de três, punchlines,
   travessões e números sem fonte.

O modo revisar roda sozinho quando você entrega um texto pronto para melhorar.

## O que tem dentro

| Arquivo | Conteúdo |
|---|---|
| `SKILL.md` | O processo: briefing, pesquisa, escrita e as três passadas de revisão |
| `references/briefing.md` | As cinco perguntas, os modelos de voz, tabela de registro com amostra de tom, padrões quando o usuário não responde |
| `references/pesquisa.md` | Protocolo dos subagentes: ângulos, prompt pronto, critério de fonte, síntese do dossiê |
| `references/estruturas.md` | Catorze tiques estruturais de IA, com evidência de corpus real |
| `references/fluencia.md` | Ritmo, coesão, argumento e voz, a partir de Othon Garcia, dos manuais de redação e da crônica |
| `references/calques.md` | Catálogo "evite, use" de calque, anglicismo, corporativês e léxico de LLM |
| `references/pontuacao.md` | Travessão, vírgula, aspas, números, títulos e listas à brasileira |
| `references/exemplos.md` | Leitura obrigatória antes de escrever: as passadas aplicadas de ponta a ponta em dois corpora reais |

## Alguns exemplos do que ela corrige

Conceito abstrato praticando verbo humano é o tique mais grave e o mais difícil de
enxergar:

> "A conformidade não enxerga essa dinâmica."

vira

> "Ninguém perguntou."

Travessão de ênfase colado, que é forma inglesa, vira vírgula, dois-pontos, parênteses
ou ponto. "Não apenas X, mas também Y" uma vez está bem; três vezes é máquina.
"Realizar a implementação de" vira "implantar". Título em caixa de sentença, nunca
Title Case. Decimal com vírgula, milhar com ponto.

E o teste que vale mais que a lista inteira, do manual do Estadão: nunca escreva o que
você não diria.

## Duas coisas que ela não faz

**Não inventa fato.** Nome, número, data, citação e fonte vêm do usuário ou da
pesquisa, com link que o agente abriu. Número que muda de valor entre rascunhos é
tratado como sinal de alucinação.

**Não muda o que o texto diz.** No modo revisar ela corta, funde, divide e reordena. A
informação permanece.

## Onde ela serve

Artigo, newsletter, post, relatório, ensaio, documentação, e-mail e copy, em qualquer
área. Os exemplos das referências saem de um artigo técnico de segurança, porque foi o
material disponível para análise forense, mas os tiques são de língua: valem igual para
pauta de saúde, relatório financeiro ou crônica.

Termo técnico consagrado da área fica, seja ele API, ebitda, anamnese ou liminar. Quem
decide o que precisa de explicação é o público definido no briefing.

## Base

Othon Garcia (*Comunicação em Prosa Moderna*), manuais de redação da imprensa
brasileira, crônica brasileira, estudos de tradução inglês para português e análise
forense de corpus real. As fontes estão citadas dentro de cada referência, com ano e
link.

## Instalação

```bash
# no projeto atual
npx skills add nilsonpmjr/escrita-natural-ptbr

# para todos os seus projetos
npx skills add nilsonpmjr/escrita-natural-ptbr -g
```

Funciona em qualquer agente suportado pela CLI `skills`, incluindo Claude Code e
Cursor. Também dá para clonar o repositório dentro de `.claude/skills/` na mão.

## In English

A skill that makes AI agents write and edit Brazilian Portuguese that reads as if a
Brazilian wrote it. The tells of machine-written Portuguese live in sentence
architecture, not in word choice, so the skill works outside in: briefing first, then
parallel research subagents, then thesis, then paragraph, then sentence, and only last
the word and the punctuation. It also covers what English-language style tools miss,
including the spaced em dash convention, English-to-Portuguese calques, Brazilian
nominalization and typography.

## Licença

MIT. Autor: Nilson Miranda.
