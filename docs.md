---
layout: docs
title: Visão Geral do docassemble
short_title: Documentação
order: 20
---

**docassemble** é uma plataforma para criação de aplicações web
mobile-friendly chamadas [Entrevistas]. Estas perguntam
uma questão de cada vez de até atingirem seu objetivo. O objetivo
pode ser a apresentação de um parecer, a criação de um documento 
assinado, o envio de um cadastro, ou outra coisa. Execute a [Demonstração] 
(Demonstração) para ter uma ideia de como aplicações **docassemble** são.

Você pode executar **docassemble** na sua máquina, mas a maior parte 
das pessoas executa "na nuvem", em serviços de hospedagem como 
[Amazon Web Services], [Digital Ocean], ou outros. A página de [Deploy]
descreve uma variedade de formas pelas quais você pode ter a sua
própria instância do  **docassemble** funcionando. VocÊ pode instalar
**docassemble** num servidor usando [Docker] ou, se for um expert, seguir
as instruções detalhadas de [Instalação]. Na maioria dos casos, a 
[Administração] e [Configuração] do **docassemble** podem ser gerenciados
pela interface web.

# <a name="intro"></a>Introdução ao **docassemble**

Desenvolvedores de entrevistas escrevem-nas em [YAML], um formato 
puro texto que é legível por seres humanos e por máquinas. Em nosso
texto iremos nos referir às entrevistas por este nome, para manter a
coerência com o texto original. Entretanto, achamos mais fácil pensar 
nas entrevistas como questionários ou formulários web.

Uma entrevisa consiste de múltiplos "blocos". Blocos são pedações de 
texto separados por `---`, que é um separador de registro em [YAML]. 
Por exemplo:

{% include demo-side-by-side.html demo="turnips-worms" %}

Você pode clicar na imagem acima para ver a entrevista em ação.
Se você passar o mouse sobre o código fonte, reticências aparecerão
no canto inferior direito; se você clicar nas reticências, você
verá o [YAML] completo da entrevista.

Alguns blocos são [Blocos de Questão] que representam as telas que o 
usuário irá de fato ver, como nos exemplos acima. A estrutura básica
de um bloco de questões é simples, mas existem vários [Question
Modifiers] possíveis, que podem fazer com que suas telas realizem
diferentes tarefas.

A informação recolhida do usuário é armazenada em "variáveis", e o 
propósito da maioria dos blocos de questão é [Setting Variables]. 
Você pode usar quaisquer nomes de variável que quiser, exceto alguns
nomes de [Special Variables] que possuem seu valor pré definido.

**docassemble** suporta [many different types] de variáveis -- mesmo
[file uploads] e [touchscreen signatures]. Uma das características mais 
poderosas é a habilidade de armazenar informações numa forma estruturada
usando [Objetos]. Quando você quer coletar um ou mais pedações de informações
relacionadas, você pode fazê-lo em [Grupos] tais como [listas] e [dicionários].

Existem outros tipos de blocos além de blocos de [`question`].

[Blocos Iniciais] definem opções para toda a entrevista, tais como 
[funcionalidades] especiais do questionário ou as [screen parts] padrão.

Blocos de [Código] permitem que variáveis sejam definidas mediante computação.
O código é escrito em [Python]. Para escrever uma entrevista, você não precisa
de saber muito sobre [Python], além de como escrever instruções "if/then/else".

{% highlight yaml %}
code: |
  if autor.municipio == reu.municipio:
    foro_competente = True
{% endhighlight %}

Você pode mesmo usar lógica fuzzy com a funcionalidade de [Machine
Learning] do **docassemble**.

**docassemble** decide quais questões fazer, e a ordem na qual eles são
feitas, de acordo com a [Lógica da Entrevista]. Você pode especificar a ordem
das questões com grande detalhamento se quiser, ou pode apenas definir 
o objetivo final e deixar o **docassemble** descobrir a melhor ordem de
execução.

Um uso popular das entrevistas é a montagem de [Documentos], daí o nome
**docassemble** - document + assembly (montagem).  Você pode redigir templates
de documentos em [DOCX] ou [PDF]. Você também pode escrever documentos do mesmo
modo que escreve questões, em texto puro usando [Markup] para indicar formatação.

Na medida em que suas entrevistas se tornam mais sofisticadas, você vai achar
útil invocar [Funções] para fazer coisas tais como conjugar verbos, computar
diferenças entre datas, ou oferecer ao usuário links que realizam [ações] especiais.

**docassemble** possui um sistema de [User Login] que permite usuários criarem
contas, salvarem suas respostas e reiniciarem suas entrevistas posteriormente.

Como **docassemble** é uma aplicação livre e em código aberto, ela foi 
projetada para ser interoperável com outras aplicações.
Existem várias formas de se trabalhar com [Dados Externos]; você pode
facilmente movimentar informação para dentro ou para fora do de uma seção
de entrevista **docassemble**. Também existe uma completa [API] para interação
com o **docassemble** programaticamente. Você pode também desenvolver seu próprio
[Front End Customizado].

Desenvolvedores podem prototipar e testar suas entrevistas no navegador, usando
o [Playground] para desenvolvedores.

Assim que você obtiver seu servidor **docassemble** [em execução], percorra o
tutorial [Olá, Mundo!] para aprender os primeiros passos de como funcionam as
entrevistas. Na medida em que você adquirir mais experiência, você deve explorar
outros [Fluxos de Desenvolvimento] diferentes do [Playground].

Uma das funcionalidades mais poderosas do **docassemble** é sua capacidade de 
executar entrevistas multi-usuário por meio de sua funcinonalidade de [Papéis].
Por exemplo, um usuário poderia preencher uma entrevista e um advogado poderia
acessá-la para avaliar a informação e fornecer aconselhamento jurídico, que 
o usuário veria da próxima vez que acessasse o sistema.

A funcionalidade de [Tarefas em Background] você pode programar que a entrevista
realize tarefas no servidor em momentos distintos da entrada de dados pelo usuário.
Tarefas que requerem tempo pode ser executadas em [background]. A entrevista
pode [avaliar entradas do usuário] antes de o usuário submetê-la. Entrevistas podem
realizar tarefas [quando o usuário não estiver logado], tais como enviar um [e-mail]
para um usuário quando um prazo estiver prestes a se esgotar.

**docassemble** é uma plataforma multi-propósito, mas foi particularmente
desenhada para [Aplicações Legais], e possui funcionalidades especiais para
este propósito.

Se você precisar de disponibilizar uma entrevista em mais de um idioma,
as funcionalidades de [Suporte a Idiomas] podem auxiliá-lo a gerenciar 
traduções. **docassemble** também possui várias funcionalidades para 
[Acessibilidade] por pessoas com deficiências.

**docassemble** foi desenvolvido de acordo com o modelo do mundo do
software livre. Entrevistas podem ser transformadas em [Packages], que
podem ser compartilhados no [GitHub] ou transportadas entre servidores
como arquivos ZIP.

A interface web mobile-friendly é a forma principal que os usuários terão acesso
ao executar entrevistas, mas também existe a opção de realização de entrevistas
por meio de [SMS].

Quando você implantar suas entrevistas, existem várias formas de oferecer
suporte ao usuário. A funcionalidade de [Live Help] permite que operadores
comuniquem-se com os usuários usando um chat on-line. Operadores podem
ver as telas dos usuários e podem assumir o controle se necessário. Se
a comunicação por telefone dor necessária, operadores pode fornecer ao usuário
um número de telefone e um código especiais que transmite a ligação para 
outro número sem revelar o número real do operador.

 **docassemble** possui excelente [Escalabilidade] quando implantado
 na nuvem. Deste modo, você não precisa se preocupar quando suas entrevistas
 receberem muito tráfego.

 Se suas entrevistas forem processar informação sensível, **docassemble**
 possui diversas funcionalidades de [Segurança] que mantém os dados seguros, 
 tais como criptografia no servidor.

 Desenvolvedores invariavelmente cometem e encontram [Erros].
**docassemble** tenta fornecer mensagens de erro úteis no navegador ou
em logs armazenados no servidor.

Se você ficar empacado, você pode procurar [Suporte] da comunidade 
**docassemble**, particulamente postando uma questão no [Slack] - apenas
em inglês. 

Para suporte em português entre em contato com a equipe da
[Sílex Sistemas].

Você também pode encontrar exemplos úteis nas nossas [Receitas].

**docassemble** é um software livre disponibilizado de acordo com a
licença em código MIT, que é muito permissiva [Licença]. O software
é atualizado frequentemente, e você pode acompanhar as novas 
funcionalidades pelo [Change Log].

Observe que se você tiver usado o **docassemble** por muito tempo,
você precisa de [Atualização do Python].

# <a name="using documentation"></a>Usando a Documentação

The **docassemble** documentation is intended more as a reference
guide than as a manual that you have to read before getting started.

The best way to learn about **docassemble** is to start creating your
own interview.  Start by following along with the "Hello, world"
[tutorial] that explains how to create a simple interview.  Once you
get that working, you can experiment with adding more questions to it.

The best way to learn about more advanced **docassemble** features is
to study working examples.  The sections of this documentation site
contain a number of side-by-side examples comparing source code to
screenshots.  You can click on the screenshots to run the interviews.
The code next to the screenshots is often only an excerpt of the full
interview.  To see the full source code of the interview, hover over
the source code and click the button that appears in the lower right
corner.  In addition, while you are developing interviews in the
[Playground], you can browse working examples of many of
**docassemble**'s features.

There is also a full-featured sample interview linked from the
[demonstration page].  While you are using the interview you can click
"Source" in the navigation bar to toggle display of the source code
for the question and an explanation of the path **docassemble** took
to decide to ask that question.

# <a name="toc"></a>Sections of the documentation

<ul class="interiortoc">
{% for section in site.data.docs %}
<li>{{ section.title }}</li>
<ul>
{% include docs_section.html items=section.docs %}
</ul>
{% endfor %}
</ul>

[Olá, Mundo!]: {{ site.baseurl }}/docs/helloworld.html
[Entrevistas]: {{ site.baseurl }}/docs/interviews.html
[Blocos Iniciais]: {{ site.baseurl }}/docs/initial.html
[Blocos de Questão]: {{ site.baseurl }}/docs/questions.html
[Setting Variables]: {{ site.baseurl }}/docs/fields.html
[Question Modifiers]: {{ site.baseurl }}/docs/modifiers.html
[Código]: {{ site.baseurl }}/docs/code.html
[Lógica da Entrevista]: {{ site.baseurl }}/docs/logic.html
[Markup]: {{ site.baseurl }}/docs/markup.html
[Documentos]: {{ site.baseurl }}/docs/documents.html
[Objetos]: {{ site.baseurl }}/docs/objects.html
[Grupos]: {{ site.baseurl }}/docs/groups.html
[Funções]: {{ site.baseurl }}/docs/functions.html
[Dados Externos]: {{ site.baseurl}}/docs/external.html
[Aplicações Legais]: {{ site.baseurl }}/docs/legal.html
[Special Variables]: {{ site.baseurl }}/docs/special.html
[Suporte a Idiomas]: {{ site.baseurl }}/docs/language.html
[Acessibilidade]: {{ site.baseurl }}/docs/accessibility.html
[Papéis]: {{ site.baseurl }}/docs/roles.html
[Tarefas em Background]: {{ site.baseurl }}/docs/background.html
[Tarefas em Background]: {{ site.baseurl }}/docs/background.html
[Machine Learning]: {{ site.baseurl }}/docs/ml.html
[SMS]: {{ site.baseurl }}/docs/sms.html
[API]: {{ site.baseurl}}/docs/api.html
[Front End Customizado]: {{ site.baseurl }}/docs/frontend.html
[User Login]: {{ site.baseurl }}/docs/users.html
[Live Help]: {{ site.baseurl }}/docs/livehelp.html
[Fluxos de Desenvolvimento]: {{ site.baseurl }}/docs/development.html
[Playground]: {{ site.baseurl }}/docs/playground.html
[Packages]: {{ site.baseurl }}/docs/packages.html
[Erros]: {{ site.baseurl }}/docs/errors.html
[Suporte]: {{ site.baseurl }}/docs/support.html
[Receitas]: {{ site.baseurl }}/docs/recipes.html
[Administração]: {{ site.baseurl }}/docs/admin.html
[Instalação]: {{ site.baseurl }}/docs/installation.html
[Docker]: {{ site.baseurl }}/docs/docker.html
[Configuração]: {{ site.baseurl }}/docs/config.html
[Escalabilidade]: {{ site.baseurl }}/docs/scalability.html
[Segurança]: {{ site.baseurl }}/docs/security.html
[Change Log]: {{ site.baseurl }}/docs/changelog.html
[Atualização do Python]: {{ site.baseurl }}/docs/twotothree.html
[Licença]: {{ site.baseurl }}/docs/license.html
[ações]: {{ site.baseurl }}/docs/functions.html#actions
[Demonstração]: {{ site.baseurl }}/demo.html
[YAML]: https://en.wikipedia.org/wiki/YAML
[Python]: https://en.wikipedia.org/wiki/Python_%28programming_language%29
[GitHub]: https://github.com/
[Reserved Names]: {{ site.baseurl }}/docs/special.html#reserved
[Demonstração]: {{ site.baseurl }}/demo.html
[demonstration page]: {{ site.baseurl}}/demo.html
[tutorial]: {{ site.baseurl}}/docs/helloworld.html
[Playground]: {{ site.baseurl}}/docs/playground.html
[Digital Ocean]: https://www.digitalocean.com/
[Amazon Web Services]: https://aws.amazon.com/ec2/
[many different types]: {{ site.baseurl }}/docs/fields.html#data types
[file uploads]: {{ site.baseurl }}/docs/fields.html#file
[touchscreen signatures]: {{ site.baseurl }}/docs/fields.html#signature
[`question`]: {{ site.baseurl }}/docs/questions.html#question
[Deploy]: {{ site.baseurl }}/deploy.html
[DOCX]: {{ site.baseurl }}/docs/documents.html#docx template file
[PDF]: {{ site.baseurl }}/docs/documents.html#pdf template file
[listas]: {{ site.baseurl }}/docs/groups.html#gather list
[dicionários]: {{ site.baseurl }}/docs/groups.html#gather dictionary
[funcionalidades]: {{ site.baseurl }}/docs/initial.html#features
[screen parts]: {{ site.baseurl }}/docs/questions.html#screen parts
[em execução]: {{ site.baseurl }}/deploy.html
[background]: {{ site.baseurl }}/docs/background.html#background
[avaliar entradas do usuário]: {{ site.baseurl }}/docs/background.html#check in
[quando o usuário não estiver logado]: {{ site.baseurl }}/docs/background.html#scheduled
[e-mail]: {{ site.baseurl }}/docs/functions.html#send_email
[Slack]: https://join.slack.com/t/docassemble/shared_invite/enQtMjQ0Njc1NDk0NjU2LTUyOGIxMDcxYzg1NGZhNDY5NDI2ZTVkMDhlOGJlNTgzZTUwYzNhYTJiMTJmMDYzYjQ0YWNmNjFiOTE5NmQzMjc
[Sílex Sistemas]: https://www.silexsistemas.com.br