# escrita-natural-ptbr

Skill para escrever e revisar textos em português brasileiro com IA, com atenção
à clareza, à precisão técnica e aos maneirismos que deixam a leitura artificial.

O foco é o português profissional de hoje: palavras correntes, raciocínio bem
encadeado e termos técnicos que o público reconhece. Serve para artigos técnicos,
documentação, relatórios, e-mails, newsletters e outros textos de trabalho.

## Instalação

No projeto atual:

```bash
npx skills add nilsonpmjr/escrita-natural-ptbr
```

Para disponibilizar em todos os seus projetos:

```bash
npx skills add nilsonpmjr/escrita-natural-ptbr -g
```

A instalação usa a CLI `skills`. Escolha um dos agentes compatíveis oferecidos
por ela.

## Como usar

Peça ao agente para usar a skill e informe o texto ou o que você quer escrever.
Quanto mais claro for o público e o objetivo, melhor ele consegue ajustar a escrita.

**Para revisar:**

```text
Use a skill escrita-natural-ptbr para revisar o artigo abaixo.
O público é de desenvolvedores backend. Preserve o conteúdo técnico e a minha voz,
mas corrija repetições, trechos artificiais e traduções desnecessárias.

[cole o artigo]
```

**Para escrever:**

```text
Use a skill escrita-natural-ptbr para escrever um artigo sobre falhas de
controle de acesso em APIs. O público é de profissionais de segurança.
Quero um texto explicativo para o blog da equipe, com cerca de 800 palavras.
Use o caso e os dados abaixo como ponto de partida.

[cole o material]
```

Se faltar uma informação importante, o agente pode perguntar antes de começar.
Você também pode fornecer um texto seu como referência de voz.

## O que ela procura melhorar

A revisão começa pelo raciocínio: o que o texto explica, como cada parágrafo
contribui e onde falta desenvolvimento. Depois vêm as frases, o vocabulário e a
pontuação. Isso ajuda a evitar uma revisão que apenas troca palavras e mantém
os mesmos problemas de construção.

Entre os pontos de atenção estão introduções genéricas, conclusões repetitivas,
frases picadas, estruturas repetidas, jargão vago e afirmações sem sustentação.
As orientações de estilo devem respeitar o gênero, o público e a voz do autor.

Exemplo ilustrativo de revisão:

> **Antes:** No cenário atual, é fundamental ressaltar a importância de realizar
> uma análise robusta dos logs antes de proceder com o rollback.
>
> **Depois:** Analise os logs antes de fazer o rollback.

O exemplo corta o preâmbulo e preserva a orientação técnica. Em um texto real,
a revisão também precisa manter condições, ressalvas e informações necessárias.

### Termos técnicos em inglês

A terminologia segue o uso da área. Termos como `deploy`, `rollback`, `endpoint`,
`payload` e `timeout` podem permanecer quando forem habituais para o público.
Quando o leitor precisar, o agente explica o conceito sem exigir uma tradução.

O mesmo critério vale para palavras como feedback, workshop e compliance:
a existência de uma alternativa em português não torna a substituição obrigatória.
Nomes de produtos, código, identificadores e rótulos de interface são preservados.

As referências clássicas ajudam na coesão e na construção do argumento. O
vocabulário e o registro devem corresponder ao contexto atual do texto.

## Como funciona

A skill tem dois modos:

| Modo | Trabalho principal |
|---|---|
| Escrever | Entender o pedido, organizar a explicação ou o argumento, pesquisar quando necessário e redigir para o público definido |
| Revisar | Reorganizar e melhorar o texto fornecido, preservando seu sentido e suas informações |

Nos dois modos, a revisão passa por argumento e parágrafo, frase, palavra e
pontuação. Ao final, há uma verificação de padrões de repetição, ritmo, coesão e
sustentação das afirmações. As contagens ajudam a localizar possíveis problemas;
não são uma garantia de qualidade.

Quando o texto exige pesquisa externa, a skill orienta o uso de subagentes com
ângulos diferentes e fontes verificáveis. Essa etapa depende das ferramentas
disponíveis no agente. Quando todo o material necessário já foi fornecido, como
na revisão de um e-mail, a pesquisa pode ser dispensada.

A skill orienta o agente a não inventar fatos ou fontes. Ainda é necessário
conferir a precisão técnica e os dados antes de publicar.

## Estrutura do repositório

As instruções ficam em [SKILL.md](SKILL.md). As referências detalham partes do
processo e são consultadas conforme a tarefa.

| Referência | Conteúdo |
|---|---|
| [Briefing](references/briefing.md) | Público, objetivo, voz e formato |
| [Pesquisa](references/pesquisa.md) | Busca de evidências, seleção de fontes e síntese |
| [Estruturas](references/estruturas.md) | Padrões de construção que deixam o texto artificial |
| [Fluência](references/fluencia.md) | Ritmo, coesão e desenvolvimento do raciocínio |
| [Calques e terminologia](references/calques.md) | Traduções literais, jargão e escolhas de vocabulário conforme o contexto |
| [Pontuação](references/pontuacao.md) | Convenções de pontuação e apresentação |
| [Exemplos](references/exemplos.md) | Análises de textos e exemplos de revisão |

## Origem

O projeto nasceu da dificuldade de gerar bons textos técnicos em português com IA.
A análise de sucessivas versões de um artigo mostrou que substituir palavras
marcadas como “típicas de IA” pouco ajudava quando a estrutura continuava repetitiva.
Outra dificuldade foi o excesso de cortes, que deixava o texto fragmentado.

Essas observações orientaram o processo de revisão. A base reúne estudos de
linguagem, manuais de redação e exemplos de prosa brasileira, com fontes indicadas
nas referências. As orientações de uso atual e terminologia técnica complementam
essa base.

## Licença

[MIT](LICENSE). Autor: Nilson Miranda.
