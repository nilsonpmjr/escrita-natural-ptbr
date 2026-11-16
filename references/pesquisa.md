# Pesquisa com subagentes

O briefing do usuário é o piso do texto, não o teto. Pesquisa é o que separa artigo
com mundo dentro de resumo de resumo. Este arquivo é o protocolo: quantos subagentes,
com que ângulo, com que prompt e o que fazer com o que volta.

## Quando despachar

Despache sempre que o texto precisar afirmar alguma coisa sobre o mundo: número,
data, caso, histórico, comparação, regra, quem disse o quê.

Pule quando o texto for inteiramente sobre material que o usuário já entregou, como
reescrever um e-mail, revisar um relatório interno ou organizar uma nota pessoal.
Nesses casos, avise que pulou e por quê.

## Quantos e como

De dois a quatro subagentes, **despachados na mesma mensagem** para rodarem em
paralelo. Cada um com um ângulo, nunca dois com a mesma pergunta. Use o tipo de
agente de propósito geral com acesso a busca web.

| Ângulo | O que ele traz | Quando incluir |
|---|---|---|
| Fatos e números | Estatística com fonte, ano e metodologia; ordem de grandeza; série histórica | Quase sempre |
| Casos concretos | Incidente, projeto, decisão, com data, lugar e gente envolvida | Quase sempre |
| Origem e histórico | Como o assunto chegou até aqui, quem criou, o que mudou e quando | Tema com camada técnica ou institucional |
| Contraditório | Quem discorda da tese, com o melhor argumento deles | Texto de opinião ou análise |
| Linguagem do público | Como esse público fala do assunto: termo que usa, dúvida que repete, queixa comum | Público que você não conhece bem |

Quatro ângulos é teto prático. Além disso o retorno começa a se repetir e a síntese
custa mais do que rende.

## Prompt do subagente

Adapte os colchetes e mantenha o resto. As restrições existem porque sem elas o
retorno vem em forma de artigo de SEO, que é exatamente o material que contamina o
texto final.

```
Pesquise [tema], ângulo: [ângulo]. O resultado alimenta um artigo em português do
Brasil para [público], publicado em [contexto].

O que eu quero:
- fato verificável, com fonte, ano e link direto;
- caso concreto com data, lugar e quem estava envolvido;
- número com origem rastreável, e a metodologia quando existir;
- fala de alguém identificado, quando houver.

O que eu não quero:
- resumo do tema, definição de dicionário, panorama geral;
- conteúdo que pareça gerado por IA: post de SEO genérico sem evidência, "guia
  definitivo", listicle, blog de agência sem autor;
- fonte que só cita outra fonte. Vá até a original.

Prioridade de fonte: documento oficial, artigo acadêmico, imprensa com repórter
assinando, documentação de quem construiu a coisa, relato em primeira pessoa.
[Se o tema for língua, estilo ou uso do português: selecione por autoridade e
pertinência. Para registro e terminologia, confira exemplos atuais do público-alvo.
Data recente não é evidência de autoria por IA; fonte antiga pode fundamentar
coesão sem servir de modelo de vocabulário contemporâneo.]

Formato do retorno, uma linha por achado:
AFIRMAÇÃO | NÚMERO OU DATA | FONTE, ANO | LINK | confiança alta ou média ou baixa

No fim, escreva a seção "não encontrei", listando o que procurei e não achei, e o que
achei mas não consegui confirmar em fonte primária. Não preencha lacuna com estimativa.
```

## O que fazer com o retorno

1. **Cruze.** Achado que aparece em um único lugar e não é fonte primária entra como
   "confiança baixa" ou não entra.
2. **Descarte o repetido.** Dois subagentes trazendo o mesmo número não confirmam nada
   se a fonte for a mesma.
3. **Monte o dossiê** antes de escrever: afirmação, evidência, fonte, onde vai ser
   usada no texto. O que não tiver lugar no texto fica fora do dossiê.
4. **Um número por argumento.** Sete números empilhados em quatro frases não provam
   nada além de "isso é grande". Escolha o que faz trabalho e corte o resto.
5. **Use o contraditório.** O melhor argumento de quem discorda entra como concessão,
   antes da sua refutação. Texto que só apresenta o próprio lado soa a material
   promocional, e material promocional soa a IA.
6. **Carregue as lacunas para a entrega.** O que a pesquisa não achou vira frase
   honesta no texto ("não há dado público sobre isso") ou vira nota para o usuário.
   Nunca vira estimativa disfarçada de fato.

## Regras que não se negociam

- Fonte que você não abriu não vira citação. Se o subagente devolveu link, confira
  antes de afirmar em cima dele.
- Número que muda de valor entre rascunhos é sinal de alucinação. Volte ao dossiê.
- Nome próprio, cargo e data se copiam do dossiê, não da memória.
- Dado sob sigilo, de cliente ou de trabalho não publicado não entra em texto público,
  ainda que a pesquisa confirme. Isso é decisão de autorização, não de pesquisa.
- Ao entregar o texto, diga em três linhas o que veio da pesquisa e não estava no
  briefing, e o que ficou em aberto.
