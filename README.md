# escrita-natural-ptbr

Skill que faz o agente escrever e revisar em português do Brasil sem o sotaque de IA,
com briefing antes de escrever, pesquisa com fonte e verificação contável antes de
entregar.

```bash
npx skills add nilsonpmjr/escrita-natural-ptbr
```

## O problema

Você pede um artigo e recebe isto:

> "No controle de acesso, onde basta alterar um identificador na requisição para expor
> dados de outro cliente. Na lógica de pagamento, que opera na camada de negócio e
> escapa aos scanners automatizados. No consentimento e no token, provando que um
> token válido não é sinônimo de acesso legítimo."

Não há erro de português aí. Há quatro fragmentos sem verbo em paralelo, um conceito
abstrato ocupando o lugar de quem age e nenhuma informação que o leitor não pudesse
adivinhar. Você responde "deixa mais natural", o agente troca "robusto" por "sólido" e
devolve o mesmo texto com outro vocabulário.

O sotaque de IA em português está na arquitetura da frase e do parágrafo. Trocar
palavra por sinônimo não alcança essa camada, e é por isso que a segunda tentativa
costuma sair igual à primeira.

## O que muda

> ❌ "A conformidade não enxerga essa dinâmica."
>
> ✅ "O checklist responde se o controle existe. Não responde se ele segura alguém
> tentando passar por cima dele."

> ❌ "Uma avaliação recente ilustra isso com precisão. Analisamos, sob escopo
> autorizado e controlado, uma plataforma de Banking as a Service que estava entre as
> mais bem estruturadas do mercado."
>
> ✅ "Testamos uma plataforma de Banking as a Service que era, honestamente, das mais
> bem-feitas que já vimos."

Os exemplos são de um texto técnico porque foi o material que existia para análise
forense. Os tiques são de língua, não de área.

## O que você ganha

**Texto que defende uma coisa.** A skill obriga a tese em uma frase e depois exige que
cada parágrafo diga o que acrescenta ao anterior. Parágrafo que só anuncia o próximo
ou ecoa o título é cortado antes de você ler.

**Fato com fonte, não afirmação genérica.** Antes de escrever, subagentes pesquisam em
paralelo com ângulos diferentes: números, casos datados, histórico, quem discorda.
Todos precisam devolver link e declarar o que não acharam. A sensação de vazio em
texto de IA vem mais da ausência de fato do que do vocabulário.

**A sua voz, não a voz média da internet.** O briefing fixa um modelo de voz, de
preferência a partir de algo que você já escreveu, e a skill imita comprimento de
frase, escolha de palavra e pontuação preferida. Gíria deliberada, regionalismo e
termo técnico da sua área ficam.

**Verificação antes da entrega.** O agente conta o que costuma denunciar máquina:
proporção de frases curtas, aberturas de parágrafo que não retomam o anterior, séries
de três, punchlines, travessões e números sem fonte. Não é impressão, é contagem.

**O que ferramenta em inglês não vê.** Travessão espaçado à portuguesa, calque do
inglês, nominalização, gerundismo, corporativês, título em caixa de sentença, decimal
com vírgula e as demais convenções tipográficas brasileiras.

## Como usar

Depois de instalar, peça em português normal. O agente escolhe o modo:

```
"revisa este artigo, ele está com cara de IA"        → modo revisar
"escreve um post sobre X para tal público"           → modo escrever
"tira o tom de LLM desse e-mail, mas não muda o que ele diz"
```

No modo escrever, espere uma rodada de perguntas antes do primeiro parágrafo: estilo,
tema, contexto, tom e público. Se você mandar escrever sem responder, ele assume um
padrão e declara a suposição em uma linha.

No modo revisar, a informação do texto permanece. A skill corta, funde, divide e
reordena, e não acrescenta fato que você não deu.

## Como ela trabalha

De fora para dentro, sempre nesta ordem:

1. **Briefing.** Estilo, tema, contexto, tom e público, em uma rodada só. O estilo vem
   primeiro porque é ele que fixa o modelo de voz que o texto vai imitar.
2. **Pesquisa.** De dois a quatro subagentes em paralelo, com ordem de descartar
   conteúdo com cara de IA e de priorizar fonte primária.
3. **Tese e linha de raciocínio**, antes de redigir qualquer parágrafo.
4. **Escrita**, no modelo de voz do briefing, depois de ler os exemplos trabalhados.
   Lista de proibição sem modelo de construção produz texto que não erra nada e não
   soa a ninguém.
5. **Revisão em três passadas:** argumento e parágrafo, depois frase, depois palavra e
   pontuação. A ordem inversa é o erro clássico.
6. **Verificação contável** antes de entregar.

## O que tem dentro

| Arquivo | Conteúdo |
|---|---|
| `SKILL.md` | O processo: briefing, pesquisa, escrita, três passadas e verificação |
| `references/briefing.md` | As cinco perguntas, os modelos de voz, tabela de registro com amostra de tom, padrões quando o usuário não responde |
| `references/pesquisa.md` | Protocolo dos subagentes: ângulos, prompt pronto, critério de fonte, síntese do dossiê |
| `references/estruturas.md` | Catorze tiques estruturais de IA, com evidência de corpus real |
| `references/fluencia.md` | Ritmo, coesão, argumento e voz, a partir de Othon Garcia, dos manuais de redação e da crônica |
| `references/calques.md` | Catálogo "evite, use" de calque, anglicismo, corporativês e léxico de LLM |
| `references/pontuacao.md` | Travessão, vírgula, aspas, números, títulos e listas à brasileira |
| `references/exemplos.md` | Leitura obrigatória antes de escrever: as passadas aplicadas de ponta a ponta em dois corpora reais |

## Onde ela serve

Artigo, newsletter, post, relatório, ensaio, documentação, e-mail e copy, em qualquer
área. Termo técnico consagrado fica, seja ele API, ebitda, anamnese ou liminar, e quem
decide o que precisa de explicação é o público que o briefing definiu.

## Duas coisas que ela não faz

**Não inventa fato.** Nome, número, data, citação e fonte vêm de você ou da pesquisa,
com link que o agente abriu. Número que muda de valor entre rascunhos é tratado como
sinal de alucinação.

**Não muda o que o texto diz.** No modo revisar, a informação permanece.

## De onde ela veio

Quatro versões do mesmo artigo foram reescritas cortando "cenário", "robusto" e
"emblemático". Entre a primeira e a última o texto encolheu 41% e o número de séries de
três subiu de oito para nove: mais denso em tique, menor em palavras, igual em sotaque.
Esse corpus definiu a ordem de trabalho da skill, e um segundo corpus, escrito já sob
as regras, mostrou o efeito colateral oposto, o texto estéril de tanto fugir de tique.
As duas análises estão em `references/exemplos.md`.

A base bibliográfica é Othon Garcia (*Comunicação em Prosa Moderna*), manuais de
redação da imprensa brasileira, crônica brasileira e estudos de tradução do inglês para
o português. Cada referência cita as fontes com ano e link.

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

Ask an AI agent for a text in Brazilian Portuguese and you get prose with no
grammatical errors and no author: abstract nouns doing human verbs, fragments in
parallel, tricolons everywhere, and paragraphs that announce instead of adding
anything. Asking it to "sound more natural" swaps the vocabulary and keeps the
architecture, which is where the accent actually lives.

This skill fixes the architecture. It gathers a brief before writing, runs research
subagents that must return sources, imitates a voice model taken from your own
writing, revises in three passes from argument down to punctuation, and counts the
usual tells before delivering. It also covers what English-language style tools miss:
the spaced em dash convention, English-to-Portuguese calques, Brazilian nominalization
and typography.

## Licença

MIT. Autor: Nilson Miranda.
