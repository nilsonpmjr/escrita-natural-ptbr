# Exemplo trabalhado: as três passadas em texto real

Todo o material aqui sai da versão 4 do artigo "O olhar crítico que bancos e
fintechs precisam a partir de agora", usado aqui como corpus. Nenhum fato foi
acrescentado. As reescritas usam apenas o que já estava no original.

## Passada 1, argumento e parágrafo

Mapa da v4, uma linha por parágrafo, dizendo o que cada um acrescenta.

| # | Parágrafo | Acrescenta? |
|---|---|---|
| 1 | Segurança era medida por conformidade; Open Finance mudou isso | sim, é a premissa |
| 2 | Token carrega autoridade de pessoa real | sim, define o que está em jogo |
| 3 | As quatro frentes que testamos | **não**, é índice de assuntos |
| 4 | FAPI-BR é sólido, mas piso alto não detém atacante | sim, concessão e refutação |
| 5 | O ambiente avaliado era exemplar | sim, monta o caso |
| 6 | Ainda assim movemos R$ 200 mil | sim, o clímax |
| 7 | Isso é BOLA na camada de negócio; UUID derruba enumeração, não autorização | sim, **o melhor parágrafo do texto**, o único que explica um mecanismo |
| 8 | O ataque dependeu de uma reflexão sobre o token | **não**, reformula o 6 em abstrato |
| 9 | Conformidade exige o mínimo, teste ofensivo revela o crítico | **não**, repete 1, 4 e o título |

Três dos nove parágrafos não acrescentam nada, e eles estão nas bordas. A curva de
informação sobe até o parágrafo 7 e despenca. **O texto terminaria melhor no 7, cem
palavras mais curto.**

O parágrafo 3 é o caso mais interessante. Ele nasceu como quatro bullets com negrito
na v1, virou uma frase de 88 palavras com ponto e vírgula na v3, e virou quatro
fragmentos sem verbo na v4. Três disfarces do mesmo bullet. Tirar o marcador não cura
a lista.

**Decisão da passada 1:** cortar os parágrafos 8 e 9, transformar o 3 em raciocínio
encadeado ou cortá-lo, terminar no 7.

## Passada 2, frase

### Sujeito abstrato praticando verbo humano

> ❌ "O UUID derruba a enumeração, não a autorização, e é justamente aí que cria uma falsa sensação de segurança."
>
> ✅ "Com UUID, ninguém adivinha o identificador da conta ao lado. Mas quem já tiver esse identificador continua conseguindo usá-lo. O time confundiu uma coisa com a outra e dormiu tranquilo."

> ❌ "A conformidade não enxerga essa dinâmica."
>
> ✅ "O checklist responde se o controle existe. Não responde se ele segura alguém tentando passar por cima dele."

### Fragmento nominal em série

> ❌ "No controle de acesso, onde basta alterar um identificador na requisição para expor dados de outro cliente. Na lógica de pagamento, que opera na camada de negócio e escapa aos scanners automatizados. No consentimento e no token, provando que um token válido não é sinônimo de acesso legítimo. E na superfície do ecossistema, onde cada novo parceiro e integração ampliam silenciosamente a área exposta."
>
> ✅ "Testamos quatro coisas. Se dá para trocar o número de uma conta na requisição e receber o extrato de outra pessoa. Se dá para repetir uma transferência que o sistema deveria contar uma vez só. Se um consentimento cancelado realmente corta o acesso. E o que os parceiros menores, plugados na mesma malha, deixam aberto sem saber."

Quatro fragmentos sem verbo principal viram quatro orações com verbo. O paralelismo
some porque a estrutura de cada uma muda.

### Concessão-refutação em fórmula

> ❌ "O padrão brasileiro é sólido. O FAPI-BR se apoia em OAuth 2.0 e OpenID Connect, com mTLS e TLS 1.2 ou superior, a mesma base do Open Banking britânico e australiano. Um piso alto. E um piso alto não detém um atacante determinado."
>
> ✅ "O FAPI-BR é bem desenhado: OAuth 2.0, OpenID Connect, mTLS, a mesma base que o pessoal do Reino Unido e da Austrália usa. Mas padrão define o que todo participante tem que ter. Não define o que acontece quando alguém que já está dentro resolve testar os limites."

Note o que saiu: o adjetivo "sólido", a frase-punchline "Um piso alto." e a diplose
que repete "piso alto" na virada.

### Transição que não informa

> ❌ "Uma avaliação recente ilustra isso com precisão. Analisamos, sob escopo autorizado e controlado, uma plataforma de Banking as a Service que estava entre as mais bem estruturadas do mercado."
>
> ✅ "Testamos uma plataforma de Banking as a Service que era, honestamente, das mais bem-feitas que já vimos."

A frase de aviso sai inteira. O leitor percebe sozinho quando o exemplo começa. E
"com precisão" não significa nada: ou ilustra, ou não ilustra.

### Fecho circular

> ❌ "A conformidade exige o mínimo, mas o teste ofensivo revela o que há de crítico por trás da operação. No Open Finance, entre estar certificado e estar seguro está a conta do cliente. Descobrir o que um adversário consegue fazer com um acesso legítimo é a pergunta que bancos e fintechs precisam começar a fazer sobre suas próprias APIs."
>
> ✅ "Aquela falha passou por auditoria, passou por scanner, passou por certificação. Só não tinha passado por ninguém disposto a tentar roubar dinheiro dela."

## Passada 3, palavra e pontuação

| Original | Correção | Motivo |
|---|---|---|
| "ampliam **silenciosamente** a área exposta" | "abrem um pedaço de superfície que ninguém viu passar" | advérbio decorativo, nada ali faria barulho |
| "funcionou **exatamente** como desenhada" | "fez o que tinha que fazer" | advérbio só dá cadência |
| "é **justamente** aí que cria" | corte | ênfase sem conteúdo |
| "passaria com folga" e "seria **facilmente** aprovada" | escolha um | redundância entre versões |
| "O padrão brasileiro é **sólido**" | "é bem desenhado" | adjetivo-esponja de LLM |
| "sob escopo autorizado e controlado" | mova para nota ou para a primeira menção do trabalho | disclaimer jurídico no meio da narrativa quebra o ritmo |
| "escapa aos scanners automatizados" | "scanner não vê" | nominalização e voz distante |

O texto não tinha travessão nenhum nas quatro versões, e os dois-pontos caíram de
doze na v1 para um na v4. Essa foi a métrica que mais melhorou no conjunto, e mostra
que a passada 3 já estava sendo feita. O problema era que só ela estava sendo feita.

## O trecho final, reescrito

Aplicando as três passadas ao miolo do artigo:

> Testamos uma plataforma de Banking as a Service que era, honestamente, das mais
> bem-feitas que já vimos. mTLS, certificados digitais, credenciais de cliente, e
> todo objeto de negócio identificado por UUID, sem nenhum padrão sequencial para
> adivinhar. Sem XSS, sem SQL injection, sem enumeração trivial. Passaria com folga
> por qualquer checklist e por qualquer scanner.
>
> Movemos mais de R$ 200 mil de uma conta que não era nossa.
>
> A falha estava na regra de negócio. O endpoint de transferência decidia qual conta
> debitar a partir de um cabeçalho que o próprio chamador mandava. O servidor
> confiava naquele identificador sem checar se a conta pertencia a quem estava
> autenticado. Bastou informar o UUID de um terceiro como origem e a nossa conta
> como destino. De quebra, atravessamos a segregação que deveria isolar os parceiros
> uns dos outros.
>
> É falha de autorização em nível de objeto, a mesma família do IDOR, só que na
> camada de lógica de negócio. Não era o IDOR clássico de identificador sequencial.
> Com UUID, ninguém adivinha o identificador da conta ao lado, mas quem já tiver
> esse identificador continua conseguindo usá-lo. O time confundiu uma coisa com a
> outra e dormiu tranquilo. Scanner não interpreta essa camada, e checklist
> regulatório não a exige. A autenticação fez o que tinha que fazer. O problema
> nunca foi a autenticação.
>
> Aquela falha passou por auditoria, passou por scanner, passou por certificação. Só
> não tinha passado por ninguém disposto a tentar roubar dinheiro dela.

O que mudou, em resumo: o clímax ganhou parágrafo próprio, o sujeito virou gente
("movemos", "o time", "ninguém"), a série de três se desfez, os advérbios saíram, os
dois parágrafos de eco foram cortados, e o texto termina numa imagem em vez de numa
tese repetida.
