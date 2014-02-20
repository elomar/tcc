# Referencial Teórico

Esse capítulo visa explicar, de forma sucinta, o processo e tecnologias utilizados no desenvolvimento do Design Quips. O conhecimento de tais assuntos é necessário para que se possa compreender o desenvolvimento do projeto. A seção de "Processo de Desenvolvimento" trata do conceito de processos ágeis e suas principais características, e aborda as fases e práticas do processo utilizado para desenvolvimento de software na ZURB. A seção de "Tecnologias Utilizadas" trata principalmente do framework Ruby on Rails, plataforma na qual o projeto foi desenvolvido, e aborda ainda algumas das tecnologias e ferramentas auxiliares utilizadas durante o desenvolvimento.

# Processo de Desenvolvimento

Processos de software definem um conjunto distinto de atividades, ações, tarefas, marcos e produtos de trabalho que são necessários para fazer engenharia de software (engenharia de software). Tais processos podem ter uma definição formal de seus componentes; ou serem informais e surgirem naturalmente a medida que um projeto avança. É importante notar que não existe projeto de software "sem processo;" mesmo que não se siga um processo definido, o conjunto de etapas e as práticas seguidas num projeto constituem um processo (procurar referência?).

O processo utilizado no desenvolvimento do Design Quips é um processo ágil, mas adequado a realidade centrada em design da ZURB. Para entender esse processo é necessário discutir as tanto as origens e princípios dos processos ágeis como um todo quanto a filosofia e características da empresa ZURB e como elas influenciaram no processo resultante.

## Processos Ágeis

Desenvolvimento Ágil é uma espécie de movimento na área de engenharia de software que surgiu com o intuito de reavaliar as práticas e métodos sendo utilizadas na indústria, para aumentar a produtividade e as chances de sucesso de projetos de software.  Os ideais desse movimento estão presentes no Manifesto de Desenvolvimento Ágil de Software e na lista de Princípios do Software Ágil, documentos escritos em 2001 numa reunião de experientes desenvolvedores e líderes de times de desenvolvimento. O Manifesto diz:

> Estamos descobrindo maneiras melhores de desenvolver 
software, fazendo-o nós mesmos e ajudando outros a 
fazerem o mesmo. Através deste trabalho, passamos a valorizar: 

> Indivíduos e interações mais que processos e ferramentas
> Software em funcionamento mais que documentação abrangente
> Colaboração com o cliente mais que negociação de contratos
> Responder a mudanças mais que seguir um plano

> Ou seja, mesmo havendo valor nos itens à direita,
valorizamos mais os itens à esquerda.

Os Princípios do Software Ágil transformam a filosofia do Manifesto Ágil em itens mais concretos. Entre eles estão inclusos "Nossa maior prioridade é satisfazer o cliente
através da entrega contínua e adiantada de software com valor agregado," "Entregar frequentemente software funcionando, de poucas semanas a poucos meses, com preferência à menor escala de tempo," "O método mais eficiente e eficaz de transmitir informações para e entre uma equipe de desenvolvimento é através de conversa face a face," e "Software funcionando é a medida primária de progresso."

Processos Ágeis são uma implementação concreta da filosofia ágil, baseando-se em seus valores e princípios. XP e SCRUM são os mais conhecidos exemplos de processos ágeis, e tem em comum entregas constantes, espaço para mudanças no escopo, e participação dos interessados durante todo o desenvolvimento. Tais processos se opões claramente a processos mais tradicionais baseados no modelo de cascata, que se baseiam numa documentação extensiva de todo o software nas etapas iniciais do projeto, fases sequenciais e bem definidas, e uma falta de acompanhamento  do projeto pelos seus interessados durante a fase de desenvolvimento.

## Processo de desenvolvimento ZURB

Para se compreender o processo de desenvolvimento ZURB é preciso primeiro conhecer a empresa ZURB em si. Uma discussão de sua história, atuação e valores é necessária para que fiquem claras as motivações e raciocínios por trás das práticas adotadas.

### A empresa ZURB

A ZURB se define como "um time unido que designers de produto que ajudam empresas a desenharem melhores sites, serviços e produtos online." (referência site) Eles atuam em quatro áreas distintas relacionadas ao design de produtos web: consultoria, software livre, aplicativos web, e educação. 

Consultoria é o foco da empresa, que oferece serviços de estratégia de design, design de interação, e design de interface voltados principalmente para startups de tecnologia, mas que também serve grandes clientes como Facebook, Yahoo, McAfee, e Netflix. Sua atuação na área de software livre consiste principalmente em desenvolver e manter o Foundation Framework, um framework responsivo para o desenvolvimento do front-end de aplicações web. O Foundation é um dos 20 projetos mais populares na ferramenta de colaboração GitHub (referencia), e um dos frameworks de front-end mais utilizados atualmente. A ZURB possui ainda uma suite de aplicativos web voltados para agências e departamentos de design. A suite inclui Influence, uma ferramenta para a criação de apresentações; Verify, que permite criar pesquisas para coletar e analisar dados sobre telas ou páginas web; Solifidy, ferramenta para criação de protótipos clicáveis para a validação de fluxos de usuário; e Notable, ferramenta que permite compartilhas notas e comentários sobre detalhes específicos em telas, rascunhos, ou desenhos. Por fim, o braço de educação da empresa é responsável por treinamentos, online e para empresas, sobre design web, uso do Foundation Framework, e outros tópicos relacionados a design de produtos; e um conjunto de sites de referência para designers, que vão desde  Word, um glossário de termos relacionados a design de produtos, a Triggers, uma coleção de padrões de comportamento, motivadores psicológicos e influências cognitivas. O Design Quips, tema desse trabalho, é um desses sites.

O foco em design que se nota na atuação da empresa se reflete também no seu quadro de funcionários. Cerca de dois terços do dos funcionários são designers e líderes de design, com o terço restante composto por auxiliares administrativos, escritores, e desenvolvedores, e representantes comerciais. Outra característica do quadro de funcionários é que não existem gerentes, e há pouca hierarquia. Designers trabalham diretamente com os clientes e são responsáveis pela maioria dos projetos, com o suporte de um líder de design, que responde diretamente ao CEO. A empresa conta ainda, além de seus funcionários, com três ou quatro estagiários. Estagiários são contratados para as funções de designer ou desenvolvedor por períodos de três a seis meses. Cada estagiário recebe um projeto específico, que se torna seu foco durante o estágio, e na realização de tal ele trabalha junto com o restante do time. Além de seu projeto os estagiários podem ainda se envolver com trabalhos para clientes e outros projetos internos da empresa. Como estagiário, o projeto sob minha responsabilidade foi o Design Quips.

Uma estrutura horizontal é uma reflexão de um dos principais valores adotados na ZURB: a colaboração. Trabalhar junto é considerado essencial, e muitas das práticas adotadas no processo de trabalho existem para possibilitar e incentivar a colaboração tanto de designers entre si quanto entre designers e desenvolvedores ou escritores. Comunicação é um dos outros valores fundamentais para a empresa. Projetos são sempre desenvolvidos num ambiente aberto, clientes tem acesso constante e freqüente ao trabalho dos designers, e até dados financeiros da empresa são compartilhados com os funcionários. Um terceiro valor que é parte integral do trabalho da ZURB é a autonomia. Designers com mais experiência são promovidos a Líderes de Design, mas as responsabilidades adicionais de um líder se concentram mais em orientar e auxiliar designers que a propriamente controlar e gerenciar seu trabalho. Designers e desenvolvedores são responsáveis por suas decisões, e tem autonomia e liberdade em como tocar seus projetos. A forma que esses três valores - colaboração, comunicação e autonomia -  influenciam o dia a dia da ZURB ficará mais claro ao discutirmos as práticas adotadas no processo de desenvolvimento.

Um outro fator que influencia o processo de desenvolvimento é a estrutura física da empresa. O escritório é organizado num formato de *open-plan,* ou plano aberto. Não existem divisórias entre os funcionários ou escritórios individuais. Todos, incluindo o CEO, trabalham em conjuntos de 4 mesas espalhadas ao longo do segundo andar do prédio. Escritórios de plano aberto são um assunto controverso e pesquisas apontam para uma queda na produtividade em espaços do tipo, citando fatores como barulho e interrupções (referências positiva e negativa). Tais fatores são balanceados na ZURB pela existência de espaços individuais usados quando funcionários precisam de mais concentração, como sofás confortáveis e espaços em corredores; e salas a prova de som usadas para pequenas reuniões entre times ou com clientes. O escritório conta ainda com uma mesa de reuniões que acomoda todos os funcionários, um terraço, e uma cozinha completa. Como é típico em escritórios de tecnologia na região, a cozinha está sempre estocada com diversos lanches e bebidas.

(foto do escritório)

(foto de uma sala de reuniões) 

### Práticas do Processo de Desenvolvimento ZURB

As práticas discutidas aqui são descritas da forma que aconteceram no projeto Design Quips, mas em sua maior parte se aplicam a todos os projetos de desenvolvimento da empresa. Além disso, as ideias por trás das práticas e algumas das práticas em si se aplicam não só a projetos de desenvolvimento mas a todas as áreas de atuação da empresa.

Uma das práticas mais adotadas é a de formar times multi-disciplinares. Projetos de desenvolvimento contam sempre com, além um desenvolvedor, um designer e um editor. (procurar referencia sobre o que é e vantagens de multidisciplinary team) Todos trabalham juntos e se comunicam com freqüência.

Algumas das práticas adotadas vem do XP (Extreme Programming). Manter um ritmo sustentável, por exemplo, é prática comum. A maioria dos funcionários trabalha num ritmo de 40 horas por semana, e não existe pressão social para trabalhar excessivamente como existe em muitas empresas do tipo. Exceções acontecem quando prazos de entrega importante se aproximam, mas por tempo limitado. Uma situação que aconteceu durante meu estágio ilustra bem essa prática: um funcionário recém-contratado se sentiu sob muita pressão e passou a trabalhar cerca de 10 horas por dia; foi então aconselhado a diminuir um pouco suas responsabilidades nos projetos que estava envolvido e a pedir mais ajuda aos seus colegas mais experientes ao invés de trabalhar em excesso.

Praticam-se também integração contínua e pequenos releases. Código é compartilhado entre o time ou colocado em produção diversas vezes ao dia, e até funcionalidades em desenvolvimento são disponibilizadas nos repositórios de código dos projetos para que todos os membros do time tenham acesso.

A prática de equipe integral, pela qual o time de um projeto deve conter um usuário final disponível para responder questões do time, acontece naturalmente já que os projetos lá desenvolvidos são voltados a designers ou empresas de design.

Ainda do XP, adota-se a prática de propriedade coletiva do código. Todos os desenvolvedores são responsáveis por todas as partes do código. Não existem "nichos" que são propriedade de um desenvolvedor em particular, e não é preciso pedir permissão antes de alterar algo no projeto. Até o código de front-end, feito por e de responsabilidade dos designers, pertence a todos no projeto e é alterado por desenvolvedores.

Uma das práticas mais relevantes adotadas na ZURB é uma curta reunião de toda a empresa toda manhã, similar ao "Stand Up meeting" do XP ou ao "Daily Scrum" do Scrum. A reunião durava cerva de 15 minutos e acontecia todo dia antes que o expediente começasse. A princípio cada funcionário tinha alguns segundos para dizer o que seria seu foco naquele dia de trabalho e que tipo de ajuda precisaria. Quando a equipe ficou muito grande para reuniões desse tipo, mudou-se o formato: o CEO e os líderes de time faziam anúncios relevantes a todos, e depois cada funcionário conversava com três pessoas com quem fosse colaborar naquele dia.

Além da reunião diária, toda segunda os desenvolvedores se reuniam para uma retrospectiva da semana anterior e planejamento de alto nível da semana seguinte. Nessa reunião discutiam-se metas alcançadas na semana, empecilhos ao desenvolvimento de projetos e possíveis soluções, e compartilhavam-se técnicas ou bibliotecas que pudessem servir a todos. Designers também faziam uma reunião semanal semelhante.

Algumas das práticas que aconteciam na empresa tinha por objetivo não aumentar a produtividade ou atingir metas de trabalho, mas sim melhorar o convívio, fortalecer laços entre os funcionários e estimulá-los criativamente.

Entre essas práticas sociais, se destacam pequenos exercícios chamados "Friday 15," nome que se deve ao fato de que tais exercícios duravam cerca de 15 minutos e aconteciam toda sexta-feira. O conteúdo dos exercícios variava, mas eram quase sempre atividades em grupo com um teor criativo. Como exemplo, houveram competições de avião de papel, desafios de CSS, e construção coletiva de haikus. Todos participam dos exercícios, até mesmo escritores e contadores. Outras práticas sociais orquestradas pela empresa incluem almoços servidos na empresa três vezes por semana, e atividades sociais que aconteciam em datas comemorativas como um churrasco na semana da independência americana.

### Etapas do desenvolvimento de um projeto

Um projeto de desenvolvimento na ZURB não segue um processo definido com etapas bem definidas e separadas. Ainda assim, é possível perceber diferentes fases em um projeto, que possuem ritmos próprios e onde conjuntos diferentes de práticas e tarefas são adotadas. As etapas aqui descritas aplicam-se a criação de novos projetos e ao lançamento de grandes mudanças em projetos existentes. Uma peculiaridade do processo da ZURB é que não existem "unidades de trabalho," como iterações do XP ou Sprints do SCRUM. O desenvolvimento é contínuo, e avançam-se etapas de desenvolvimento de acordo com a situação do projeto ao invés de seguindo prazos bem definidos.

A primeira etapa é a de concepção, etapa onde acontece um planejamento de alto nível do projeto. Nessa etapa o idealizador do projeto e um ou dois designers discutem e fazem sessões de brainstorming para gerar um plano do projeto. Esse plano possibilita o início do desenvolvimento, mas não é de forma alguma compreensivo, detalhado ou fixo. Pelo contrário, ele descreve apenas características cruciais do projeto a ser desenvolvido, descrições gerais e alto nível de possíveis funcionalidades, e pode ser abandonado a qualquer momento. Não há preocupação em manter os planos atualizados ou modificá-los para refletir a realidade do projeto. Na maioria dos projetos esse plano consiste de esboços de tela feitos em papel. Em projetos mais complexos na fase de concepção se desenvolvem ainda wireframes e protótipos HTML de algumas das funcionalidades mais importantes. A concepção é a etapa mais curta do projeto, durando na maioria dos casos cerca de uma semana; mas podendo durar não mais que uma sessão de brainstorming de duas horas.

Após a concepção começa o desenvolvimento, fase mais longa de qualquer projeto. Essa fase geralmente é liderada pelo designer responsável pelo projeto, que prioriza tarefas e cria protótipos de interface; a partir dos quais desenvolvedores implementam funcionalidades. Todos do time interagem com freqüência para discutirem e aperfeiçoarem detalhes das tarefas, e todos estão sempre atualizados no andamento do projeto como um todo através das reuniões diárias e semanais. Quando alguma dificuldade é encontrada pede-se ajuda aos líderes de design e de engenharia, e sempre que marcos importantes são atingidos o time reúne-se com um líder de design para apresentar o andamento do projeto e solicitar críticas. Uma vez que as funcionalidades foram desenvolvidas completamente e aperfeiçoadas levando em consideração as críticas de um líder de design, considera-se completa a etapa de desenvolvimento e começa o lançamento.

O início da etapa de lançamento é marcado por uma reunião com o CEO. Nessa reunião o CEO avalia o projeto e apresenta suas críticas, e um cronograma inicial de lançamento é elaborado. O cronograma consiste de datas de lançamento interno, revisão pelo CEO, e lançamento externo. Outros funcionários são adicionados ao projeto conforme necessário para lidar com tarefas relacionadas ao lançamento propriamente dito: um desenvolvedor extra pode ser alocado ao projeto para preparar a infra-estrutura necessária, por exemplo, e um editor para escrever cópia para o site e preparar o anúncio do lançamento. O foco do desenvolvimento passa a ser melhorar a experiência e corrigir possíveis bugs. Na data de lançamento interno o projeto é anunciado para todos os funcionários, que utilizam e oferecem críticas sobre o projeto. Pode haver uma ou mais reuniões adicionais com o CEO para acompanhar os ajustes feitos a partir de suas críticas iniciais e dos comentários dos outros funcionários, e o andamento das tarefas de lançamento. Quando todas as pendências são resolvidas, o projeto é lançado oficialmente com um anúncio no blog corporativo da empresa.

Depois do lançamento o time é realocado para outros projetos, mas o processo de desenvolvimento não acaba aí: começa a etapa de acompanhamento. O time de desenvolvimento como um todo fica responsável por garantir o contínuo funcionamento do projeto, e de atualizar o projeto quando houverem mudanças no guia visual global da empresa; escritores passar a produzir com regularidade conteúdo para o projeto, se for o caso; e designers podem revisitar o projeto para ajustarem funcionalidades ou fazerem melhoras visuais. Esse processo de acompanhamento e melhoria contínuo não tem prazo definido, e continua acontecendo enquanto o projeto existir como uma propriedade ZURB.

# Tecnologias Utilizadas

A ZURB prefere utilizar tecnologias que possibilitem fazer protótipos rápidos e facilitem a interação entre designers e desenvolvedores. A possibilidade de fazer protótipos rápidos é necessária devido a sua cultura que prioriza colocar software em produção pra melhorá-lo com base no uso real e fazer pequenos experimentos. Além disso, tecnologias que permitem prototipação rápida são geralmente mais produtivas, e produtividade é essencial na ZURB dada a grande carga de trabalho distribuída entre um pequeno time de desenvolvimento. Facilitar a interação entre designers e desenvolvedores é o outro fator crucial na escolha de uma tecnologia, porque a empresa possui muito mais designers e desenvolvedores, e ambos colaboram frequentemente nos projetos. É preciso que a tecnologia torne possível que designers façam mudanças no projeto sem necessitar da ajuda de desenvolvedores, e que a curva de aprendizado seja pequena o suficiente de forma a permitir designers a compreenderem a organização e estrutura do projeto.

Das tecnologias utilizadas na ZURB, duas são comuns a todos os projetos de desenvolvimento e constituem seu suporte principal: o framework de desenvolvimento de aplicações web Ruby on Rails, e o framework de front-end responsivo Foundation.

## Ruby on Rails

O site do Ruby on Rails apresenta a seguinte definição:

> Ruby on Rails é um framework de desenvolvimento web (gratuito e de código aberto) otimizado para a produtividade sustentável e a diversão do programador. Ele permite que você escreva código de forma elegante, favorecendo a convenção ao invés da configuração.

Plekhanova dá uma introdução mais compreensiva ao framework:

> Rails foi desenvolvido pela Basecamp Inc. (anteriormente 37Signals Inc.), in Chicago, EUA, para um aplicativo de gerenciamento de projetos collaborative chamado Basecamp. Rails foi lançado como um projeto de código aberto em Julho de 2004, e a versão 1.0 veio em Dezembro de 2005. Rails é escrito em Ruby e segue os princípios de desenvolvimento ágil, melhora produtividade e acelera o desenvolvimento. 

Ruby é "uma linguagem dinâmica, open source com foco na simplicidade e na produtividade. Tem uma sintaxe elegante de leitura natural e fácil escrita." (site oficial)

Projetos desenvolvidos utilizando Ruby on Rails seguem uma arquitetura MVC. Modelo-Visão-Controle é um paradigma introduzido no Smalltalk 80, e apresentado por Krasner e Pope no artigo "A Description of the Model-View-Controller User Interface Paradigm in the Smalltalk-80 System" ("Uma descrição do paradigma de interface de usuário Modelo-Visão-Controle no sistema Smalltalk-80") em 1988. Segundo eles, o modelo de uma aplicação é a o software específico do domínio, ou a implementação da estrutura central da aplicação; a visão lida com tudo que é gráfico, recupera dados do modelo, e apresenta tais dados; e controle contém a interface entre seus modelos e visões associados e os dispositivos de entrada (teclado, mouse, hora). Essa definição é centrada em sistemas desktop, e todo framework web que se diz MVC adapta esses conceitos a sua maneira. No Rails, os modelos representam tabelas do banco de dados e implementam o padrão ActiveRecord - ou seja, cada objeto representa uma linha do banco e é responsável por sua própria persistência; a visão é composta por código HTML e pequenos trechos de código Ruby, e é responsável por gerar o HTML final da interface com o usuário; e o controle é a camada que trata que trata das requisições do usuário, recuperando dados do modelo e com eles alimentando a visão.

(figura MVC clássico, do paper)

(figura MVC rails)

Além do MVC, dois outros princípios são centrais a arquitetura de aplicações Rails: Convenção sobre configuração e DRY ("Não se repita"). Convenção sobre configuração é a ideia de que deve-se seguir padrões do framework para decisões comuns do que ter que configurá-las. Esse princípio se manifesta, por exemplo, na convenção de que toda tabela deve ter uma chave primária chamada "id," e que portanto não é necessário configurar uma; e no mecanismo que seleciona, a partir de dados da requisição, que ação do controle invocar e que visão utilizar, com configuração mínima. É possível fugir da maioria das convenções do Rails, mas seguí-las resulta em menos código, mais consistência, e mais produtividade. DRY é o princípio que de um conceito deve ser implementado em um lugar. Por exemplo, os atributos de um modelo são definidos apenas como campos de suas tabelas no banco - não é preciso repetir a definição no código do modelo. Para auxiliar o programador a não ter que se repetir o Rails fornece ainda uma estrutura que facilita compartilhar código entre várias partes do sistema, com cada camada do sistema contando com pacotes específicos onde código comum pode ser adicionado e que são automaticamente injetados em todos os componentes da camada.
Parte da produtividade prometida pelo Ruby on Rails vem desses princípios de arquitetura e organização citados, da automatização de tarefas comuns, e de componentes e bibliotecas reusáveis trazidas pelo framework. Outra parte vem de uma gama de bibliotecas de código livre que complementam suas funcionalidades e facilitam o desenvolvimento de novos projetos. Existem bibliotecas para automatização de deploys, integração com serviços de terceiros, autenticação, autorização, e vários outros funcionalidades comuns à aplicações web. Uma busca por projetos Ruby no popular repositórios de projetos de código livre GitHub traz mais de 500 mil projetos, um indicativo de quão ativa é a comunidade ao redor do Ruby on Rails.

## Foundation

Foundation é um framework para o desenvolvimento do front-end de aplicações web. Segundo o site oficial, Foundation teve suas origens no guia de estilo da ZURB em 2008, que era usado em todo projeto de cliente. Eventualmente eles decidiram que precisavam de um framework que permitisse fazer protótipos rapidamente. A ZURB juntou então seus CSS globais, plugins jQuery, elementos comuns e melhores práticas, e os transformou no Foundation, cuja primeira versão foi lançada em 2011.

Foundation fornece, entre outras coisa, um sistema de grade, navegação, botões e plugins. O sistema de grade divide o layout da página em 12 colunas, e permite controlar o posicionamento de elementos através de diretivas simples que de tamanho e posicionamento em relação a grade. A grade do Foundation é responsiva e funciona em praticamente qualquer dispositivo que possa acessar a internet, e suporta aninhamento, deslocamentos, apresentações específicas para determinados dispositivos, entre outras funcionalidades. Para navegação o Foundation fornece componentes de menu "off-canvas," estilo de menu popular em aplicativos móveis onde o menu parece estar escondido fora da tela, e aparece quando se clica num botão específico; paginação; e menus globais e locais. Os botões do Foundation são versáteis, com tamanho, prioridade, e estado facilmente customizáveis. Os plugins incluídos fornecem funcionalidades como validação de formulários, galeria de imagens, e exibição rotativa de imagens.

(figura menu off-canvas: escondido/mostrando)

A prática de desenvolvimento de front-end mais fortemente defendida pelo Foundation é o design responsivo. Esse termo foi cunhado por Ethan Marcotte num texto na renomada publicação "A List Apart," quando juntou três técnicas existentes - layout de grade flexível, imagens flexíveis, e "media queries" do CSS - para criar layouts que não assumem uma resolução fixa e ao invés disso se adaptam ao tamanho da tela do dispositivo cliente. Essa abordagem surgiu como uma resposta ao crescente número de diferentes dispositivos capazes de acessar a internet, de smartphones a consoles de vídeo game, e pelo rápido crescimento no acesso a internet através de dispositivos móveis. Entre março de Maio de 2009 e Maio de 2013, tráfego vindo de dispositivos móveis passou de 0.9% pra 15% do tráfego global da internet.

(figure design responsivo tela grande/pequena)

Em suma, Foundation faz traz mais produtividade para o desenvolvimento do front-end de uma aplicação através de uma estrutura de layout baseado numa grade responsiva e um conjunto de componentes prontos reusáveis.

--

referências

agile manifesto

Engenharia de Software
Roger Pressman
6a edição - McGrawHill

http://zurb.com/studios

https://github.com/search?p=2&q=stars%3A%3E1&s=stars&type=Repositories

http://zurb.com/friday15

http://www.rubyonrails.com.br

http://ibit.temple.edu/wp-content/uploads/2011/03/IBITWebframeworks.pdf

https://www.ruby-lang.org/pt/

https://github.com/search?q=forks%3A%3E-1&type=Repositories&ref=advsearch&l=Ruby

http://kanjiteacher.googlecode.com/svn-history/r203/Non-Code/Papers/Krasner1988_and_Pope_MCV.pdf

http://foundation.zurb.com

http://alistapart.com/article/responsive-web-design/

Responsive Web Design with HTML5 and CSS3

http://www.kpcb.com/insights/2013-internet-trends