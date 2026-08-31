# Estruturas de IA em português

Os tiques desta lista foram levantados em análise forense de quatro versões de um
mesmo artigo técnico, reescrito com ajuda de IA. Entre a v1 e a v4 o
autor cortou vocabulário suspeito ("cenário", "robusto", "emblemático") e o texto
continuou soando artificial. O motivo é que o problema não estava nas palavras.
Estava na arquitetura das frases, e ela sobreviveu intacta às quatro reescritas.

Duas medidas do mesmo corpus dão a dimensão: a v4 tem 41% menos palavras que a v1
e **nove** tricolons contra oito. A densidade de tique subiu enquanto o texto
encolhia.

Por isso a ordem de revisão importa. Comece pela estrutura. Trocar palavra por
sinônimo mais simples é a parte fácil e não resolve quase nada sozinha.

## 1. Sintagma nominal abstrato como sujeito de verbo humano

O tique mais grave e o mais difícil de enxergar. O texto trata de gente atacando
sistema, mas quem ocupa a posição de sujeito é um conceito.

| Evite | Por quê |
|---|---|
| "A conformidade não enxerga essa dinâmica." | Conformidade não tem olho. |
| "O olhar ofensivo mostra o real." | Olhar não mostra, quem mostra é quem olhou. |
| "Essa escala trouxe o crime organizado." | Escala não traz ninguém. |
| "O UUID derruba a enumeração." | UUID não derruba nada. |
| "A ameaça deixou o campo teórico." | Ameaça não se locomove. |
| "O Open Finance alterou essa equação." | Equação é metáfora morta e o sujeito é abstrato. |
| "A falha residia na regra de negócio." | Falha não reside. |
| "Cada parceiro amplia a área exposta." | O parceiro não fez nada, quem integrou fez. |

**Conserto:** pergunte quem fez. Coloque essa pessoa no sujeito. Quando não houver
pessoa específica, use "você", "a gente", "o time", "quem".

> Antes: "O UUID derruba a enumeração, não a autorização, e é justamente aí que cria uma falsa sensação de segurança."
>
> Depois: "Com UUID, ninguém adivinha o identificador da conta ao lado. Mas quem já tiver esse identificador continua conseguindo usá-lo. O time confundiu uma coisa com a outra e dormiu tranquilo."

## 2. Simetria compulsiva

IA produz três itens por padrão. Prosa humana usa dois, quatro, cinco, ou um só,
conforme o assunto pede.

| Padrão | Exemplo do corpus |
|---|---|
| Tricolon de infinitivos | "Ao abrir APIs, conectar parceiros e colocar dados e pagamentos em circulação" |
| Tricolon de infinitivos (de novo) | "capaz de consultar saldo, acessar extrato e movimentar o dinheiro" |
| Anáfora tripla | "Sem XSS, sem SQL injection e sem enumeração trivial" |
| Diplose (repete a palavra na virada) | "Um piso alto. E um piso alto não detém um atacante determinado." |
| Fragmentos nominais paralelos | "No controle de acesso, onde... Na lógica de pagamento, que... No consentimento, provando... E na superfície, onde..." |

**Conserto:** conte as séries de três em um parágrafo. Se houver mais de uma,
quebre. Tire um item, acrescente um quarto, ou desmonte a série em oração.

## 3. Frase-manchete abrindo parágrafo

Sete dos nove parágrafos da v4 abrem com sintagma nominal + verbo declarativo:
"O padrão brasileiro é sólido.", "Uma API financeira carrega autoridade.",
"O Open Finance alterou essa equação."

Cada parágrafo anuncia a própria tese antes de mostrar qualquer coisa. O leitor
sente monotonia sem saber nomear a causa: é sempre tese, desenvolvimento, tese,
desenvolvimento.

**Cuidado, o problema não é o tópico frasal.** Othon Garcia pesquisou centenas de
parágrafos e achou a ideia-núcleo na abertura em mais de 60% deles. Abrir parágrafo
pela tese é brasileiro e legítimo. O que denuncia IA é a soma de três coisas: a
abertura é slogan abstrato em vez de afirmação com conteúdo, o resto do parágrafo
só reformula a abertura, e todos os parágrafos usam a mesma forma sintática. Veja
[fluencia.md](fluencia.md), seção "Tópico frasal e a nuance sobre a frase de
abertura".

**Regra operacional:** se o parágrafo pode ser resumido pela primeira frase sem
perda, o parágrafo não desenvolveu nada. Ou você acrescenta fato, exemplo ou causa,
ou corta o parágrafo inteiro. Aplicada ao corpus, essa regra elimina dois parágrafos
da v4 e reescreve três aberturas.

**Conserto:** varie a entrada. Abra com cena, com número, com fala, com
circunstância de tempo e lugar, com o meio de uma ação. Nenhum dos nove parágrafos
da v4 abria assim.

## 4. Anúncio e transição vazia

A frase que avisa que vem um exemplo. O leitor percebe sozinho quando o exemplo
começa.

- "Uma avaliação recente ilustra isso com precisão." (sobreviveu em v2, v3 e v4)
- "Esse novo cenário exige uma mudança de perspectiva."
- "O olhar crítico que falta é o do adversário."
- "Quatro frentes concentram aquilo que atacantes já exploram em produção."

A v2 tem quatro frases seguidas de anúncio antes de qualquer conteúdo. É o pior
trecho do corpus.

**Conserto:** entre direto na cena. "Ano passado testamos uma plataforma de
Banking as a Service que era, honestamente, das mais bem-feitas que eu já vi."

## 5. Contraste binário

Fórmula de slide, não de texto.

| Padrão | Exemplo do corpus |
|---|---|
| "A faz X. B faz Y." | "A conformidade descreve o mínimo. O olhar ofensivo mostra o real." |
| "não é X. É Y." | "o prejuízo não é um simples vazamento. É a identidade de alguém sendo usada." |
| "não é X, é Y" na mesma frase | "O UUID derruba a enumeração, não a autorização" |
| "não apenas X, mas também Y" | calque de *not only... but also* |
| "não se trata de X, e sim de Y" | mesma fórmula em outra roupa |
| "o alvo não é X. O foco é Y." | "o alvo não é listar vulnerabilidades. O foco é reconstruir a cadeia" |

**Conserto:** afirme Y e siga. A negação prévia é rampa de acesso que o leitor não
pediu. Quando a oposição for mesmo o argumento, mostre os dois lados agindo, não
dois substantivos abstratos em espelho.

## 6. Concessão-refutação em fórmula

O movimento "elogio genérico, adjetivo de LLM, reviravolta repetindo a palavra" é
uma das cadências mais reconhecíveis de texto gerado.

> "O padrão brasileiro é sólido. [...] Um piso alto. E um piso alto não detém um atacante determinado."

**Conserto:** seja específico no elogio e específico na ressalva.

> "O FAPI-BR é bem desenhado: mTLS, OAuth 2.0, a mesma coisa que o pessoal do Reino Unido usa. Mas padrão define o que todo participante tem que ter. Não define o que acontece quando alguém que já está dentro resolve testar os limites."

## 7. Pergunta retórica respondida pelo autor

Feita, respondida e depois comentada. Três movimentos onde cabe um.

> "Bastou uma única pergunta: o que consigo fazer com um token que o sistema aceita como legítimo? Responder a essa pergunta é o nosso trabalho."

A v4 tirou o ponto de interrogação e piorou: "uma única reflexão prática sobre o
que um adversário consegue fazer" é a mesma pergunta amputada.

**Conserto:** conte o que você fez. "O que eu fiz ali não foi quebrar nada. Peguei
um token que o sistema já tinha aceitado e fui ver até onde ele ia."

## 8. Fecho circular

Três frases, zero informação nova, eco do título. O parágrafo mais dispensável das
quatro versões.

> "A conformidade exige o mínimo, mas o teste ofensivo revela o que há de crítico por trás da operação. No Open Finance, entre estar certificado e estar seguro está a conta do cliente. Descobrir o que um adversário consegue fazer com um acesso legítimo é a pergunta que bancos e fintechs precisam começar a fazer sobre suas próprias APIs."

Na v4, a curva de informação sobe até o parágrafo 7 e depois desce até o fim. O
texto terminaria melhor no 7, cem palavras mais curto.

**Conserto:** o último parágrafo precisa acrescentar um fato, uma consequência ou
uma imagem que ainda não apareceu.

> "Aquela falha estava em produção havia meses. Passou por auditoria, passou por scanner, passou por certificação. Só não tinha passado por ninguém disposto a tentar roubar dinheiro dela."

## 9. Lista disfarçada de prosa

Tirar o marcador não cura o bullet. No corpus, a mesma lista de quatro itens
rotulados sobreviveu em três disfarces:

1. v1, bullets com negrito e dois-pontos.
2. v3, frase única de 88 palavras com ponto e vírgula separando os quatro.
3. v4, quatro fragmentos sem verbo principal, todos abrindo com preposição
   contraída e três fechando em oração relativa.

**Conserto:** se os itens não se encadeiam, não é lista, é catálogo. Ou você
transforma em raciocínio, em que o item seguinte usa o anterior, ou você corta
para o que interessa e desenvolve de verdade.

> "Testamos quatro coisas. Se dá para trocar o número de uma conta na requisição e receber o extrato de outra pessoa. Se dá para repetir uma transferência que o sistema deveria contar uma vez só. Se um consentimento cancelado realmente corta o acesso. E o que os parceiros menores, plugados na mesma malha, deixam aberto sem saber."

## 10. Frase-punchline isolada

A frase curta de efeito no fim do parágrafo, ou sozinha, para dar peso. A v1 tinha
quatorze frases de até seis palavras, quase um quarto do total.

- "Essas duas respostas raramente coincidem."
- "Nenhum dos dois casos disparou alerta."
- "Nenhum certificado impediu isso."
- "Essa pergunta é o olhar ofensivo."

Três delas aparecem seguidas em um parágrafo de quatro frases.

**Conserto:** uma por texto, se tanto. Emenda o resto na frase anterior.

## 11. Advérbio em -mente decorativo

| Ocorrência | Problema |
|---|---|
| "ampliam **silenciosamente** a área exposta" | Nada ali faria barulho. O advérbio personifica. |
| "funcionou **exatamente** como desenhada" | Só existe para dar cadência. |
| "ilustra isso **com precisão**" | Ou ilustra ou não ilustra. |
| "é **justamente** aí que cria" | Ênfase sem conteúdo. |
| "a estrutura passaria **facilmente**" | Já está em "passaria com folga". |

**Conserto:** corte. Se o advérbio carrega informação, transforme em fato:
"passou por três auditorias sem ninguém levantar a mão".

## 12. Estatística empilhada

Sete números em quatro frases, e nenhum deles muda o argumento. Todos servem para
dizer "isso é grande".

> "O ecossistema brasileiro ultrapassou 128 milhões de consentimentos ativos e projeta 720 bilhões de chamadas de API em escala global. [...] O Banco Central registrou 33 incidentes de fraude em menos de cinco meses de 2026, quase metade dos 76 episódios de 2025 inteiro, e o custo médio de violação de dados no setor financeiro brasileiro atingiu R$ 7,19 milhões."

Sinal de alerta adicional: no mesmo corpus, "quatro das dez categorias do OWASP"
virou "três das dez" na versão seguinte. Número que muda de valor entre rascunhos
é forte indício de alucinação, assim como nomes de ferramentas e campanhas que não
aparecem em fonte nenhuma.

**Conserto:** um número por argumento, e ele tem que fazer trabalho. Verifique
cada um contra a fonte. Corte o resto.

## 13. Ausência de mundo concreto

O corpus inteiro não tem pessoa nomeada, data, hora, fala de ninguém, nome de sala,
sequer um "na terça de manhã". Sobrou um único fato duro na v4: "mais de R$ 200
mil". Texto sem mundo concreto soa a resumo de resumo, e essa é a impressão geral
que o leitor chama de "cara de IA" mesmo sem identificar nenhum tique isolado.

**Conserto:** toda seção precisa de pelo menos uma âncora no mundo. Uma data. Um
valor. Uma tela. Uma frase que alguém disse na reunião.
