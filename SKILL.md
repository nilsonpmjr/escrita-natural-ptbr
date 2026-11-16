---
name: escrita-natural-ptbr
description: |
  Escrever e revisar texto em português do Brasil que soe escrito por um
  brasileiro, com linha de raciocínio e sem os vícios de IA. Use ao redigir ou
  revisar artigo, newsletter, post, relatório, ensaio, documentação, e-mail ou
  copy em pt-BR, em qualquer área; quando o texto tiver cara de tradução do
  inglês ou de LLM; quando pedirem para "humanizar", "naturalizar" ou "tirar
  cara de IA" de um texto em português. Levanta briefing de estilo, tema,
  contexto, tom e público antes de escrever, despacha subagentes de pesquisa
  para enriquecer o conteúdo, cobre travessão, calque, corporativês, ritmo,
  coesão e construção do argumento, e verifica o texto contra as regras antes
  de entregar.
metadata:
  autor: Nilson Miranda
  base: pesquisa em Othon Garcia, manuais de redação brasileiros, crônica
    brasileira, estudos de tradução e análise forense de corpus real
---

# Escrita natural em português

Texto de IA em português não é reconhecido pelas palavras. É reconhecido pela
arquitetura. No corpus que originou esta skill, quatro versões do mesmo artigo foram
reescritas cortando "cenário", "robusto" e "emblemático", e o resultado continuou
soando a máquina: entre a primeira e a última versão o texto encolheu 41% e o número
de séries de três **subiu** de oito para nove. Trocar palavra por sinônimo mais
simples é a parte fácil e resolve pouco.

Por isso esta skill trabalha de fora para dentro: primeiro o briefing, depois a
pesquisa, depois o argumento, o parágrafo, a frase, e só no fim a palavra e a
pontuação.

Os exemplos das referências saem de um artigo técnico de segurança, porque foi o
material disponível para análise forense. Os tiques são de língua, não de área:
valem igual para pauta de saúde, relatório financeiro, post de produto ou crônica.

## Registro contemporâneo e terminologia

O padrão é português brasileiro profissional atual, claro e preciso. Referências
clássicas ensinam coesão e argumentação; não determinam o vocabulário nem a voz de
um texto técnico de hoje. Prefira palavras correntes, sem impor informalidade nem
eliminar termos especializados necessários. Uma palavra não é inadequada só por
ser formal, antiga ou de origem estrangeira: avalie seu uso no contexto.

A terminologia segue o uso da área e do público. Preserve termos como deploy,
rollback, endpoint, payload e timeout quando forem as escolhas habituais. Explique
na primeira ocorrência quando o leitor precisar, sem tradução obrigatória. Use o
equivalente português quando ele for natural e preciso naquele contexto. Não troque
feedback por devolutiva nem workshop por oficina automaticamente.

Preserve nomes de produtos, código, identificadores e rótulos de interface. Consulte
a documentação ou exemplos atuais da área quando houver dúvida relevante sobre o
uso; não deduza inadequação apenas da origem inglesa. A amostra do autor e o padrão
editorial informado orientam as escolhas, preservando precisão e sentido.

## Duas coisas que a skill não faz

**Não inventa fato.** Nunca acrescente nome, número, data, citação ou fonte que não
venha do usuário ou de uma fonte verificada. No corpus de origem apareceram uma
ferramenta e uma campanha que não existem em fonte nenhuma, e um número que mudou de
"quatro das dez categorias" para "três das dez" entre dois rascunhos. Número que
troca de valor entre versões é sinal de alucinação. Se falta um dado, pergunte ou
escreva a frase sem ele.

**Não muda o que o texto diz.** Você pode cortar, fundir, dividir e reordenar. A
informação permanece.

## Modo escrever

### 0. Briefing, antes de qualquer linha

Texto genérico quase sempre nasce de briefing ausente, não de vocabulário ruim. Antes
de escrever, você precisa saber cinco coisas, nesta ordem: **estilo, tema, contexto,
tom e público**.

O estilo vem primeiro porque é ele que fixa o modelo de voz, e o modelo de voz decide
como as frases vão ser construídas. Perguntar tom antes de estilo inverte a
dependência: você fica com um adjetivo, "executivo", "leve", "sério", sem saber se o
texto imita crônica, reportagem explicativa, relatório ou manual. Aí o adjetivo é
lido como economia de palavras, e o texto sai telegráfico.

Leia [references/briefing.md](references/briefing.md) e levante o que faltar. Regras
do levantamento:

- **Deduza o estilo do que o usuário já deu**: o jeito como ele escreveu o pedido, o
  canal que citou, o material de referência que anexou, textos anteriores dele ou da
  publicação. Só pergunte o estilo quando não der para deduzir, e ao perguntar
  ofereça modelos de voz, não adjetivos.
- **Se o usuário não informou nada, peça o contexto antes de qualquer outra
  pergunta.** Onde publica, quem assina, o que motivou o texto. Sem contexto as
  outras perguntas não têm em que se apoiar, e você acaba oferecendo opções no vácuo.
- Aproveite o que o usuário já deu. Não pergunte o que está no pedido.
- Pergunte em **uma rodada só**, com AskUserQuestion, no máximo quatro perguntas, com
  opções concretas e um recomendado. Perguntas soltas em sequência cansam e atrasam.
- Se o usuário mandar escrever sem responder, assuma o padrão de
  [references/briefing.md](references/briefing.md), **declare a suposição em uma
  linha** e siga.
- Havendo texto anterior do autor ou da publicação, leia antes de perguntar. Amostra
  responde tom melhor que pergunta.

Feche o briefing em um bloco curto de seis linhas, estilo, tema, contexto, público,
tom, formato e extensão, e confirme com o usuário antes de gastar pesquisa em cima
dele.

### 1. A tese, em uma frase

Antes de qualquer parágrafo, escreva a frase que o texto inteiro defende. Se não
sair, você ainda não tem texto, tem tema. Texto que "fala, fala e não chega a lugar
nenhum" quase sempre é isso: tema sem tese.

Teste da negação, de Othon Garcia: escreva a negação da sua tese. Se a negação for
igualmente defensável e você não tiver fato para desempatar, a frase não está
argumentando.

Teste da escada de especificação: se a tese continua verdadeira quando você troca o
assunto por outro qualquer, ela está genérica demais. Desça degrau a degrau até
doer. "A prática dos esportes é prejudicial à saúde" desce até "a prática
indiscriminada de certos esportes violentos é prejudicial à saúde dos jovens
subnutridos".

Gênero sem tese, como documentação e release note, pula este passo e vai direto para
a pergunta que o leitor chegou fazendo.

### 2. Pesquise antes de escrever, com subagentes

Só os fatos provam. O que o usuário entrega no briefing é o ponto de partida, não o
teto. **Despache subagentes de pesquisa em paralelo**, cada um com um ângulo
diferente, antes de escrever a primeira frase. Sem isso o texto vira sequência de
afirmações genéricas, que é a origem real da sensação de vazio, muito mais do que o
vocabulário.

O protocolo completo, com os ângulos, o prompt pronto e o formato de retorno, está em
[references/pesquisa.md](references/pesquisa.md). Em resumo:

- Dispare de dois a quatro subagentes numa mesma mensagem, um por ângulo: fatos e
  números; casos concretos e incidentes datados; histórico e contexto de origem;
  visão contrária e crítica à tese.
- Cada um devolve fato verificável com fonte, ano e link, não resumo de tema.
- Todos recebem ordem de **descartar conteúdo que pareça gerado por IA**: post de SEO
  genérico sem evidência, "guia definitivo", listicle. Prioridade para fonte
  primária, academia, imprensa e documento oficial.
- Todos precisam dizer o que **não** encontraram. Lacuna declarada vale mais que
  lacuna preenchida por invenção.
- Se o tema for de língua, estilo ou uso do português, selecione fontes por
  autoridade e pertinência; para vocabulário e registro, confira o uso atual.

Depois, escolha. Um número por argumento, e ele tem que fazer trabalho. Sete números
empilhados em quatro frases não provam nada além de "isso é grande". Fato que
contraria a tese entra no texto como concessão, não some.

Pule a pesquisa quando o texto for inteiramente sobre material que o usuário já
forneceu, como reescrever um e-mail ou revisar um relatório interno. Nesse caso, diga
que pulou.

### 3. Monte a linha de raciocínio antes de redigir

Escreva uma linha por parágrafo dizendo **o que aquele parágrafo acrescenta ao
anterior**. Se você não conseguir dizer, o parágrafo não existe ainda.

Depois olhe a sequência inteira e marque os parágrafos que só anunciam o que vem, só
reformulam o que já foi dito ou só ecoam o título. No corpus de origem, três dos nove
parágrafos eram isso, e ficavam nas bordas: a abertura anunciava demais e o fecho
reafirmava demais.

Decida também onde vai o argumento mais forte, porque a ordem muda por gênero:

| Gênero | Ordem |
|---|---|
| Notícia, relatório, resumo executivo, e-mail | Mais importante primeiro, pirâmide invertida |
| Ensaio, artigo de opinião, análise, crônica | Mais forte no fim, clímax no fecho |
| Documentação, tutorial, procedimento | Ordem de execução, do pré-requisito ao resultado |
| Post curto de rede social | Primeira linha carrega a tese inteira |

### 4. Escreva

**Leia [references/exemplos.md](references/exemplos.md) antes da primeira frase.** É
o único arquivo da skill que mostra construção, e não proibição, com o antes e o
depois de cada passada em texto real. Quem pula esse arquivo escreve otimizando
contra a lista de tiques, e texto que só foge de tique fica estéril: some a
subordinação, somem as retomadas, e sobra uma sequência de asserções curtas que
ninguém falaria em voz alta.

Depois vá para [references/fluencia.md](references/fluencia.md) e escreva seguindo os
princípios de ritmo, coesão e voz, no modelo de voz que o briefing fixou. Os cinco
que mais mudam o resultado:

1. **Abra pela necessidade do leitor.** Em texto técnico, apresente o problema,
   o resultado ou a ação: "O deploy falhou porque a aplicação não encontrou o token."
   Abertura em cena é uma opção para narrativa, não uma obrigação geral.
2. **Troque o conectivo por retomada. Não corte os dois.** "Dessa forma" sai, mas
   alguma coisa entra no lugar: o núcleo do parágrafo anterior repetido por outro
   nome, um demonstrativo, um resumo de duas palavras. "Esses quatro pontos,
   encadeados, viram um caminho" não é cola burocrática, é como o português cola.
   Parágrafo que abre sem vínculo nenhum com o anterior obriga o leitor a remontar o
   fio sozinho.
3. **Varie a forma da abertura, inclusive a forma nova.** Fugir do parágrafo que abre
   com sintagma nominal e verbo declarativo não autoriza abrir todos com asserção
   curta e seca. Isso troca um molde único por outro molde único.
4. **Case cada abstração com um fato concreto no mesmo parágrafo.**
5. **Feche conforme o gênero.** Em texto técnico, conclua com o resultado, a
   limitação ou o próximo passo. Imagem e virada são recursos de narrativa.

### 5. Revise

Aplique o modo revisar ao que você escreveu. Sempre.

## Modo revisar

Três passadas, nesta ordem. A ordem importa: consertar palavra antes de consertar
estrutura é o erro que fez o corpus de origem passar por quatro versões sem melhorar.

Ao revisar texto de terceiro, levante o briefing mesmo assim, ao menos estilo,
público e tom.
Sem isso você não tem como julgar se o registro está certo, e acaba corrigindo para o
seu gosto em vez de para o leitor dele.

### Passada 1: argumento e parágrafo

Consulte [references/estruturas.md](references/estruturas.md).

- Mapeie o texto, uma linha por parágrafo, dizendo o que cada um acrescenta.
- **Corte todo parágrafo que não acrescenta.** Anúncio do que vem, reformulação do
  anterior, eco do título. Comece pelas bordas, é onde eles se escondem.
- Se o parágrafo pode ser resumido pela primeira frase sem perda, ele não
  desenvolveu nada. Acrescente fato, exemplo ou causa, ou corte o parágrafo.
- Verifique se o fecho traz alguma coisa nova. Fecho que repete a tese e ecoa o
  título é o parágrafo mais dispensável de qualquer texto.
- Toda seção precisa de pelo menos uma âncora no mundo real: uma data, um valor, uma
  tela, uma fala.
- Toda lista: os itens se encadeiam ou é catálogo? Catálogo vira prosa ou vira corte.

### Passada 2: frase

Ainda em [references/estruturas.md](references/estruturas.md), mais
[references/fluencia.md](references/fluencia.md).

- **Sujeito.** Quem faz a ação? Conceito abstrato praticando verbo humano é o tique
  mais grave e o mais difícil de ver. "A conformidade não enxerga" vira "ninguém
  perguntou".
- **Substantivo sem determinante.** "Scanner procura padrão", "Atacante não tem
  preferência", "Código limpo não cobre autorização". É sintaxe de manchete, que
  comprime porque paga por centímetro de coluna. Em prosa vira legenda de
  infográfico. Devolva o artigo, ou troque o genérico por gente: "nenhum scanner faz
  essa pergunta".
- **Coesão.** Leia só a primeira frase de cada parágrafo e marque quantas retomam
  alguma coisa do parágrafo anterior, seja por repetição, sinônimo, demonstrativo ou
  resumo. Menos da metade e o texto virou uma sequência de compartimentos estanques,
  o defeito que o Estadão descreve no §28. O conserto não é acrescentar "dessa
  forma", é devolver o referente.
- **Simetria.** Conte as séries de três no parágrafo. Mais de uma, quebre. Procure
  também anáfora, paralelismo de fragmentos e repetição da mesma palavra na virada.
- **Aberturas.** Leia só a primeira frase de cada parágrafo, em sequência. Se todas
  tiverem a mesma forma sintática, varie. O Estadão é explícito: não use
  repetidamente a mesma estrutura de frase. Conte também quantas abrem com asserção
  curta e seca: sendo o molde dominante, é a frase-manchete de novo, só que em outra
  roupa.
- **Ritmo.** Conte as frases de até oito palavras. Passando de um quinto do total, o
  texto está picado, mesmo que nunca apareçam três seguidas com a mesma estrutura, e
  é esse o teste que pega a frase soluçante de verdade. No corpus de origem, a v1
  tinha quatorze frases de até seis palavras, quase um quarto do total. Hierarquize:
  escolha as duas ou três ideias que sustentam o parágrafo, deixe em oração
  principal, rebaixe o resto a subordinada. Cuidado com o vício oposto, o período
  centopeia de oitenta palavras.
- **Punchline.** Frase curta de efeito isolada: uma por texto, se tanto, e ela conta
  tanto no fim do parágrafo quanto na entrada. "Repare no segundo." é punchline de
  abertura, e escapa de quem só procura no fim.
- **Contraste binário.** "Não é X, é Y" vira "é Y". A negação prévia é rampa que o
  leitor não pediu.
- **Pergunta retórica** respondida pelo próprio autor: conte o que você fez, em vez
  de perguntar.

### Passada 3: palavra e pontuação

Consulte [references/calques.md](references/calques.md) e
[references/pontuacao.md](references/pontuacao.md).

- **Travessão de ênfase:** troque por vírgula, dois-pontos, parênteses ou ponto. Se
  algum sobreviver por ser mesmo o melhor recurso, ponha espaço dos dois lados, que
  é a forma portuguesa. Traço colado é inglês.
- **Calque:** distinga calque de verdade, que se corrige sempre, de calque de
  frequência, estrutura portuguesa legítima que a IA repete demais. "Não apenas X,
  mas também Y" uma vez está bem; três vezes é máquina.
- **Verbo empolado:** usar, não utilizar. Ter, não possuir. Fazer, não efetuar.
- **Nominalização:** "realizar a implementação de" vira "implantar".
- **Locução inflada:** "no intuito de" vira "para".
- **Advérbio em -mente decorativo:** corte. Se carrega informação, vire fato.
- **Gerundismo:** "vou estar enviando" vira "vou enviar".
- **Passiva sem agente:** ache quem fez.
- **Léxico que denuncia LLM:** crucial, fundamental, robusto, sólido, holístico,
  mergulhar, meticuloso, no cenário atual, em suma, vale ressaltar, é importante
  notar que.
- **Tipografia:** título em caixa de sentença, nunca Title Case. Sem vírgula de
  série. Pontuação fora das aspas. Decimal com vírgula, milhar com ponto. `R$ 180`,
  não `R$ 180,00`. `de 2% a 3%`, com o símbolo repetido.
- **Listas:** frase-guia com dois-pontos, item em minúscula, ponto e vírgula no fim,
  ponto final no último. E, antes disso, pergunte se a lista precisa existir.

## Verificação antes de entregar

**Esta passada é obrigatória, sempre.** Vale para texto curto, vale quando o usuário
tem pressa e vale quando você acha que já revisou o bastante. Escrever e revisar não
bastam, porque o texto sai justamente com os tiques que você não foi procurar. Rode
a verificação no texto final, com ele na frente, nunca de memória, e quando o texto
estiver em arquivo conte de verdade, com script se for o caso: contagem de cabeça
subestima sempre.

### As contagens

| O que contar | Limite | Se estourar |
|---|---|---|
| Frases de até oito palavras | um quinto do total | hierarquize, emende na frase anterior |
| Aberturas de parágrafo que retomam o parágrafo anterior | metade, no mínimo | devolva o referente |
| Aberturas seguidas com a mesma forma sintática | duas | varie a entrada |
| Séries de três no mesmo parágrafo | uma | quebre |
| Frases-punchline no texto inteiro | uma | emende o resto |
| Travessões de ênfase | zero | vírgula, dois-pontos, parênteses ou ponto |
| Números sem fonte que você tenha visto | zero | corte, ou vá verificar |

Confira também se entrou vocabulário datado sem função, se alguma tradução tornou
o conceito menos reconhecível e se os termos continuam consistentes. Preserve usos
técnicos precisos de palavras como aplicação, conexão, escalar e suporte nativo.

### A leitura em voz alta

Leia em voz alta. O melhor teste da tradição brasileira inteira está no Estadão,
§15: **nunca escreva o que você não diria.** Se você não falaria aquela frase para
uma pessoa na sua frente, reescreva.

### As seis perguntas

| Dimensão | Pergunta |
|---|---|
| Briefing | O texto atende ao público, ao tom e ao objetivo combinados? |
| Tese | Dá para dizer em uma frase o que o texto defende? |
| Progressão | Todo parágrafo acrescenta alguma coisa ao anterior? |
| Prova | Toda afirmação forte tem fato por trás, com fonte que você viu? |
| Sujeito | Quem age nas frases são pessoas, ou conceitos? |
| Mundo | Tem data, número, nome, fala? Ou é resumo de resumo? |

Se qualquer resposta for ruim, volte para a passada 1. Não tente consertar na
passada 3.

### O que declarar na entrega

Três linhas: o que veio da pesquisa e não estava no briefing, o que os subagentes não
acharam, e qualquer contagem que tenha ficado no limite. O usuário precisa saber onde
o texto está apoiado e onde ele quase escorregou.

## Preservar a voz

Regras que impedem a skill de estragar texto bom:

- **Amostra do autor manda mais que qualquer tabela daqui.** Se houver texto
  anterior dele, leia primeiro e imite os hábitos: comprimento de frase, escolha de
  palavra, abertura de parágrafo, pontuação preferida.
- **Gíria e regionalismo deliberados ficam.** Não formalize coloquial proposital.
- **Termo técnico consagrado fica**, seja da área que for: API, token, endpoint,
  hash, phishing, ebitda, liminar, anamnese, laudo. A tabela de anglicismos vale
  para o jargão de escritório, não para o vocabulário da área. Quem decide o que
  precisa de explicação é o público que o briefing definiu.
- **Nome próprio e citação ficam.** Não corrija o português de quem você cita.
- **"A gente" é permitido** em texto de voz pessoal. Rubem Braga usa, Paulo Mendes
  Campos usa. Some em texto institucional.
- **"Você" é o padrão** ao falar com o leitor, e não alterne com "o usuário", "o
  leitor" ou "tu" no mesmo texto.
- A impessoalidade de redação escolar, "observa-se que", "medidas devem ser
  tomadas", é padrão a desativar, não marca de qualidade.

## Composição com outras skills

- **humanizer** cobre os tells universais catalogados pela Wikipedia, em inglês.
  Rode antes desta se o texto veio traduzido.
- **stop-slop** cobre estrutura em inglês e inspirou o formato desta skill. Há
  sobreposição real na passada 2.
- **copywriting** cuida da persuasão. Se a saída final for em português, rode esta
  skill depois dela.

Nenhuma das três conhece travessão espaçado, calque do inglês, nominalização
brasileira, alínea da ABNT ou a tradição da crônica. É o que esta cobre.

## Referências

- [references/briefing.md](references/briefing.md), as perguntas de estilo, tema,
  contexto, tom e público, com os modelos de voz, os padrões por gênero e a tabela
  de registro.
- [references/pesquisa.md](references/pesquisa.md), protocolo dos subagentes:
  ângulos, prompt pronto, critério de fonte e síntese do dossiê.
- [references/estruturas.md](references/estruturas.md), catorze tiques estruturais
  com evidência de corpus real.
- [references/fluencia.md](references/fluencia.md), ritmo, coesão, argumento e voz,
  a partir de Othon Garcia, dos manuais de redação e da crônica.
- [references/calques.md](references/calques.md), catálogo "evite, use" de calque,
  anglicismo, corporativês e léxico de LLM.
- [references/pontuacao.md](references/pontuacao.md), travessão, vírgula, aspas,
  números, títulos e listas à brasileira.
- [references/exemplos.md](references/exemplos.md), **leitura obrigatória antes de
  escrever**: as passadas aplicadas de ponta a ponta em dois corpora reais, com o
  antes e o depois de cada uma, e o capítulo sobre o texto que fica estéril de tanto
  fugir de tique.
