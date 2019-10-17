---
layout: docs
title: Visão Geral do docassemble
short_title: Documentação
order: 20
---

**docassemble** é uma plataforma para criação de aplicações web
mobile-friendly chamadas [Interviews] (Entrevistas). Estas perguntam
uma questão de cada vez de até atingirem seu objetivo. O objetivo
pode ser a apresentação de um parecer, a criação de um documento 
assinado, o envio de um cadastro, ou outra coisa. Execute a [Demonstration] 
(Demonstração) para ter uma ideia de como aplicações **docassemble** são.

Você pode executar **docassemble** na sua máquina, mas a maior parte 
das pessoas executa "na nuvem", em serviços de hospedagem como 
[Amazon Web Services], [Digital Ocean], ou outros. A página de [Deploy]
descreve uma variedade de formas pelas quais você pode ter a sua
própria instância do  **docassemble** funcionando. VocÊ pode instalar
**docassemble** num servidor usando [Docker] ou, se for um expert, seguir
as instruções detalhadas de [Installation]. Na maioria dos casos, a 
[Administration] e [Configuration] do **docassemble** podem ser gerenciados
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
usando [Objects]. Quando você quer coletar um ou mais pedações de informações
relacionadas, você pode fazê-lo em [Groups] tais como [lists] e [dictionaries].

Existem outros tipos de blocos além de blocos de [`question`].

[Initial Blocks] definem opções para toda a entrevista, tais como 
[features] especiais do questionário ou as [screen parts] padrão.

Blocos de [Code] permitem que variáveis sejam definidas mediante computação.
O código é escrito em [Python]. Para escrever uma entrevista, você não precisa
de saber muito sobre [Python], além de como escrever instruções "if/then/else".

{% highlight yaml %}
code: |
  if autor.municipio == reu.municipio:
    foro_competente = True
{% endhighlight %}

VocÊ pode mesmo usar lógica fuzzy com a funcionalidade de [Machine
Learning] do **docassemble**.

**docassemble** decide quais questões fazer, e a ordem na qual eles são
feitas, de acordo com a [Interview Logic]. Você pode especificar a ordem
das questões com grande detalhamento se quiser, ou pode apenas definir 
o objetivo final e deixar o **docassemble** descobrir a melhor ordem de
execução.

Um uso popular das entrevistas é a montagem de [Documents], daí o nome
**docassemble** - document + assembly (montagem).  Você pode redigir templates
de documentos em [DOCX] ou [PDF]. Você também pode escrever documentos do mesmo
modo que escreve questões, em texto puro usando [Markup] para indicar formatação.

Na medida em que suas entrevistas se tornam mais sofisticadas, você vai achar
útil invocar [Functions] para fazer coisas tais como conjugar verbos, computar
diferenças entre datas, ou oferecer ao usuário links que realizam [actions] especiais.

**docassemble** possui um sistema de [User Login] que permite usuários criarem
contas, salvarem suas respostas e reiniciarem suas entrevistas posteriormente.

Since **docassemble** is a free and open-source application, it is
designed to be interoperable with other applications.  There are a
variety of ways to work with [External Data]; you can move information
easily into and out of a **docassemble** interview session.  There is
also a full-featured [API] for interacting with **docassemble**
programmatically.  You can also design your own [Custom Front Ends].

Developers can prototype and test their interviews in the browser, using
the interview developers' [Playground].

Once you get a **docassemble** server [up and running], go through the
[Hello World] tutorial to learn more about how interviews work.  As
you become more experienced using the system, you may want to explore
using other [Development Workflows] than just the [Playground].

One of **docassemble**'s most powerful features is its ability to
operate multi-user interviews through the [Roles] feature.  For
example, a user could fill out an interview and then an attorney could
enter the interview to evaluate the information and provide legal
advice, which the user would see the next time they log in.

Using the [Background Tasks] features, you can have your interviews do
things on the server at times other than times when the user presses a
button to advance to a new page.  Time-intensive tasks can run in the
[background].  The interview can [evaluate user input] before the user
submits it.  Interviews can do things [when the user is not logged
in], like send a reminder [e-mail] to a user about a deadline as the date
approaches.

**docassemble** is a multi-purpose platform, but it is particularly
designed for [Legal Applications], and has special functionality for
that specific purpose.

If you need to make an interview available in more than one language,
**docassemble**'s [Language Support] features can help you manage
translations.  **docassemble** also has a number of features for
[Accessibility] by persons with disabilities.

**docassemble** was built on the model of the open-source software
development world.  Interviews can be bundled into [Packages], which
can be shared on [GitHub] or moved between servers as ZIP files.

The mobile-friendly web interface is the primary way that users will
run interviews, but there is also the option of making interviews
available via [Text Messaging].

When you deploy your interviews, there are a variety of ways you can
provide support to your users.  The [Live Help] features allow
operators to communicate with users using on-line chat.  Operators can
see users' screens and even take control if necessary.  If
communication by phone is necessary, operators can provide users with
a special phone number and code that forwards a call without revealing
the operator's actual phone number.

**docassemble** has excellent [Scalability] when deployed in the
cloud, so you don't have to worry about what will happen if your
interviews get a lot of traffic.

If your interviews will process sensitive information, **docassemble**
has a number of [Security] features to keep that information safe,
such as server-side encryption.

Developers will invariably make mistakes and encounter [Errors].
**docassemble** tries to provide helpful error messages in the browser
or in logs stored on the server.

If you get stuck, you can seek out [Support] from the **docassemble**
community, in particular by posting a question on the **docassemble**
[Slack].  You might also find that there is an example interview in
the [Recipes] that will help you solve your problem.

**docassemble** is free software available with a highly permissive
open-source [License].  The software is updated frequently, and you
can see what new features are available by reading the [Change Log].

Note that if you have been using **docassemble** for a long time, you
need learn about the necessity of doing a [Python Upgrade].

# <a name="using documentation"></a>Using the documentation

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

[Hello World]: {{ site.baseurl }}/docs/helloworld.html
[Interviews]: {{ site.baseurl }}/docs/interviews.html
[Initial Blocks]: {{ site.baseurl }}/docs/initial.html
[Blocos de Questão]: {{ site.baseurl }}/docs/questions.html
[Setting Variables]: {{ site.baseurl }}/docs/fields.html
[Question Modifiers]: {{ site.baseurl }}/docs/modifiers.html
[Code]: {{ site.baseurl }}/docs/code.html
[Interview Logic]: {{ site.baseurl }}/docs/logic.html
[Markup]: {{ site.baseurl }}/docs/markup.html
[Documents]: {{ site.baseurl }}/docs/documents.html
[Objects]: {{ site.baseurl }}/docs/objects.html
[Groups]: {{ site.baseurl }}/docs/groups.html
[Functions]: {{ site.baseurl }}/docs/functions.html
[External Data]: {{ site.baseurl}}/docs/external.html
[Legal Applications]: {{ site.baseurl }}/docs/legal.html
[Special Variables]: {{ site.baseurl }}/docs/special.html
[Language Support]: {{ site.baseurl }}/docs/language.html
[Accessibility]: {{ site.baseurl }}/docs/accessibility.html
[Roles]: {{ site.baseurl }}/docs/roles.html
[background tasks]: {{ site.baseurl }}/docs/background.html
[Background Tasks]: {{ site.baseurl }}/docs/background.html
[Machine Learning]: {{ site.baseurl }}/docs/ml.html
[Text Messaging]: {{ site.baseurl }}/docs/sms.html
[API]: {{ site.baseurl}}/docs/api.html
[Custom Front Ends]: {{ site.baseurl }}/docs/frontend.html
[User Login]: {{ site.baseurl }}/docs/users.html
[Live Help]: {{ site.baseurl }}/docs/livehelp.html
[Development Workflows]: {{ site.baseurl }}/docs/development.html
[Playground]: {{ site.baseurl }}/docs/playground.html
[Packages]: {{ site.baseurl }}/docs/packages.html
[Errors]: {{ site.baseurl }}/docs/errors.html
[Support]: {{ site.baseurl }}/docs/support.html
[Recipes]: {{ site.baseurl }}/docs/recipes.html
[Administration]: {{ site.baseurl }}/docs/admin.html
[Installation]: {{ site.baseurl }}/docs/installation.html
[Docker]: {{ site.baseurl }}/docs/docker.html
[Configuration]: {{ site.baseurl }}/docs/config.html
[Scalability]: {{ site.baseurl }}/docs/scalability.html
[Security]: {{ site.baseurl }}/docs/security.html
[Change Log]: {{ site.baseurl }}/docs/changelog.html
[Python Upgrade]: {{ site.baseurl }}/docs/twotothree.html
[License]: {{ site.baseurl }}/docs/license.html
[actions]: {{ site.baseurl }}/docs/functions.html#actions
[Demonstration]: {{ site.baseurl }}/demo.html
[YAML]: https://en.wikipedia.org/wiki/YAML
[Python]: https://en.wikipedia.org/wiki/Python_%28programming_language%29
[GitHub]: https://github.com/
[Reserved Names]: {{ site.baseurl }}/docs/special.html#reserved
[demonstration]: {{ site.baseurl }}/demo.html
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
[lists]: {{ site.baseurl }}/docs/groups.html#gather list
[dictionaries]: {{ site.baseurl }}/docs/groups.html#gather dictionary
[features]: {{ site.baseurl }}/docs/initial.html#features
[screen parts]: {{ site.baseurl }}/docs/questions.html#screen parts
[up and running]: {{ site.baseurl }}/deploy.html
[background]: {{ site.baseurl }}/docs/background.html#background
[evaluate user input]: {{ site.baseurl }}/docs/background.html#check in
[when the user is not logged in]: {{ site.baseurl }}/docs/background.html#scheduled
[e-mail]: {{ site.baseurl }}/docs/functions.html#send_email
[Slack]: https://join.slack.com/t/docassemble/shared_invite/enQtMjQ0Njc1NDk0NjU2LTUyOGIxMDcxYzg1NGZhNDY5NDI2ZTVkMDhlOGJlNTgzZTUwYzNhYTJiMTJmMDYzYjQ0YWNmNjFiOTE5NmQzMjc
