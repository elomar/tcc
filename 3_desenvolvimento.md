tcc-desenvolvimento

# Desenvolvimento do Design Quips

Uma vez apresentados o processo e as tecnologias utilizadas durante o projeto Design Quips, apresentam-se agora o resultado obtido e a aplicação concreta do processo. A apresentação do resultado traz os objetivos visados com a criação do Design Quips e como sua implementação atinge estes objetivos. A aplicação do processo traz uma descrição detalhada do que aconteceu no desenvolvimento do projeto em cada uma das fases descritas.

## Resultado

Design Quips surgiu a partir de uma realidade sobre o trabalho de designers percebida pela ZURB: a maior parte de decisões relacionadas a design era tomada com base em intuição, sem suporte concreto. Isso muitas vezes tornava difícil convencer clientes, que não conseguiam ver vantagens concretas ou entender o raciocínio por trás de cada decisão.

O Design Quips é, como a solução imaginada para tal problema, um repositório de fatos e estatísticas sobre tendências web, dados demográficos, uso de dispositivos para acesso a internet, e qualquer outra informação relacionada ao desenvolvimento web. Ele permite que designers busquem facilmente dados que justifiquem suas escolhas. Como repositório de informações atualizadas, serve ainda como fonte de aprendizado sobre o estado da web e sua evolução. Retomando o que foi dito na introdução, os objetivos específicos do projeto eram:

* Fornecer dados estatísticos sobre demografia de usuários de tecnologia, tendências de mercado, e outros assuntos relacionados ao trabalho de um designer;
* Fornecer ainda referências e fontes para cada dado, possibilitando uma pesquisa mais aprofundada sobre o assunto;
* Apresentar tais dados de forma simples, permitindo uma visualização rápida e tornando a coleta de dados prática para o designer;
* Permitir a busca e filtragem de dados por vários critérios, para que o designer possa encontrar facilmente o subconjunto de dados da coleção relevante para seu trabalho;
* E, por fim, permitir que editores e escritores da ZURB possam adicionar novos dados a coleção.

Os primeiros objetivos são atingidos pela parte pública do sistema. A página inicial lista os dados existentes, e permite filtras informações relacionadas a uma certa característica demográfica, plataforma, ou dispositivo, e ainda a buscar por qualquer texto. Tal mecanismo permite de buscas simples, como qualquer informação relacionada a "Facebook," até buscas mais complexas, como apenas informações relacionadas a mulheres jovens, sobre a plataforma iOS, de dispositivos móveis, e que contenham o texto "crescimento." A listagem é atualizada automaticamente quando os filtros são alterados, e ao invés de paginação usa uma espécie de lista infinita: um botão "Ver mais" traz mais resultados enquanto houverem resultados disponíveis. A API Javascript pushState permite que essas funcionalidades sejam implementadas sem quebrar o funcionamento do histórico do navegador (HTML5). A página de detalhes de um dado permite ainda  ver a origem da informação, onde o usuário pode se aprofundar no que é mencionado, e funcionalidades acessórias como uma uma listagem de dados relacionados, e uma lista de categorias.

(screenshot home pública)

(screenshot show)

O objetivo de permitir que editores e escritores da ZURB possam adicionar novos dados a coleção é atingido pela parte administrativa da aplicação. Para cuidar da autenticação e autorização o Design Quips integra-se ao sistema Platform, um sistema da própria ZURB que funciona como uma espécie de provedor OAuth e centraliza as credenciais de usuários. O Platform permite ainda autenticação via Facebook, Twitter ou Google+. O componente central da parte administrativa é a listagem de dados. Essa listagem destaca dados que possuem algum problema, como não terem categorias ou não informarem o período a que se referem, facilitando o trabalho dos editores de corrigirem dados falhos. Editores podem ainda ver o uso de cada categoria no sistema, funcionalidade que auxilia o trabalho de consolidar categorias e eliminar as que caíram em desuso. O cadastro de novos dados pode ser feito através da importação de um arquivo CSV seguindo um padrão pré-definido, ou através de um formulário de cadastro. O formulário é otimizado para o fluxo de  trabalho comum dos editores, permitindo analisar diversas fontes e cadastrar vários dados de cada sem repetir dados comuns e sem precisar sair da página de cadastro.

(screenshot listagem admin)

(screenshot tags)

(screenshot formulário de cadastro) 

Além das funcionalidades implementadas para atingir os objetivos principais do projeto, foram implementadas duas funcionalidades acessórias presentes em todas as propriedades da ZURB: o cadastro numa lista de email, gerenciada em outro sistema; e a exibição de propagandas dos classificados de empregos e de parceiros da ZURB.

(screenshot email)

(screenshot ads)

O Design Quips, como lançado ao fim do projeto, cumpriu os objetivos a que se propôs. A próxima seção descreve como se chegou a esse resultado, através de uma aplicação concreta das etapas e práticas do processo ZURB discutidas anteriormente.

## Desenvolvimento do Projeto

O desenvolvimento do projeto se deu nas quatro etapas discutidas no referencial teórico: a concepção, que antecedeu o início do meu estágio; o desenvolvimento, que ocupou a maior parte dos três meses de estágio; o lançamento, nas semanas finais da minha participação no projeto; e o acompanhamento, fase que começou com a minha saída da ZURB e continua em andamento.

### Concepção

Quando eu entrei no projeto a concepção do Design Quips já havia sido feita. No meu primeiro dia de trabalho tive uma reunião com o líder de desenvolvimento e o designer responsável pelo Design Quips, onde fui apresentado os objetivos do projeto e o que havia sido produzido na fase de concepção: protótipos HTML estáticos da listagem de dados e dos detalhes de um dado, e um documento contendo cerca de 500 dados que haviam sido coletados pelo time nos meses anteriores.

(screenshot estático lista)

(screenshot estático detalhes)

Fui ainda apresentado ao time do projeto, que consistia de um designer, um editor de conteúdo, e eu como desenvolvedor. O líder de desenvolvimento também participaria do projeto como meu supervisor, e uma líder de design auxiliaria e revisaria o trabalho do designer.

### Desenvolvimento

De posse dos protótipos estáticos e da lista de dados, minha meta para a primeira semana de desenvolvimento era implementar um aplicativo básico que listasse e exibisse dados e importar pelo menos uma parte dos dados existentes. Uma vez que os protótipos estáticos foram implementados numa aplicação Rails básica, foi possível coletar críticas sobre o design de um outro editor de conteúdo da ZURB e do CEO. As críticas ao longo do projeto foram coletadas através da ferramenta Notable, produto desenvolvido pela própria ZURB e usado extensivamente no dia a dia de trabalho de todos os designers.

(screenshot notable comentários time)

Durante o restante da primeira semana trabalhei em incorporar as críticas apresentadas e na versão inicial de outras funcionalidades. Algumas das funcionalidades iniciadas nessa semana foram um console de administração dos dados, filtragem por categorias, compartilhamento em redes sociais, e busca textual. A busca textual foi implementada utilizando Sphinx, um "servidor de busca textual de código aberto, desenvolvido desde o começo com performance, relevância (qualidade da busca), e simplicidade de integração em mente. É escrito em C++ e funciona em Linux (RedHat, Ubuntu, etc), Windows, MacOS, Solaris, FreeBSD, e alguns outros sistemas." (sphinx)

Em uma reunião do time no início da segunda semana, o editor explicou que seu trabalho de encontrar novos dados consistia em uma vez por semana fazer três buscas específicas no google e extrair dados a partir dos primeiros resultados. As buscas eram "resultados pesquisa web design," resultados de imagens para "infográfico web design," e arquivos PDF com os termos "resultados pesquisa web design." Surgiu então a ideia de automatizar esse processo, e a maior parte da segunda semana foi usada para criar uma ferramenta que fizesse esse processo automaticamente. A ferramenta criada rodava automaticamente uma vez por semana, efetuava as buscas utilizando a API do Google, e criava um dado com cada resultado com o título e URL da fonte devidamente preenchidos. Esses dados criados automaticamente eram marcados como "rascunho," e só apareciam na listagem pública depois de atualizados e aprovados pelo editor. A ferramenta utilizada ainda um algoritmo LSI (Indexador Semântico Latente, do inglês "Latent Semantic Indexer") para sugerir categorias para os dados importados. Segundo o artigo que introduziu a técnica, a abordagem LSI "tira vantagem da estrutura de ordem superior implícita na associação de termos com documentos ('estrutura semântica') para melhorar a detecção de documentos relevantes com base em termos encontrados em consultas." A implementação usada foi a da biblioteca Ruby Classifier, por David Fayram (classifier). O algoritmo foi treinado inicialmente com os dados coletados até a fase de concepção, e era periodicamente re-treinado com os novos dados publicados pelo editor. Além disso, na segunda semana foi implementada a importação através de arquivo CSV e uma listagem básica das categorias para ser usada pelo editor.

A terceira semana foi dedicada a ajustes visuais e pequenas alterações na exibição de dados e nas ferramentas de busca e filtragem. Fez-se ainda uma reflexão sobre a ferramenta de importação automática de dados a partir de buscas no Google. Apesar de parecer prática na teoria, na realidade tal ferramenta não mostrou-se útil: a maioria dos resultados trazidos era de má qualidade e tinha que ser removido, e a ferramenta não lidava bem com o fato de que cada resultado de busca possuía vários dados e não um só. Essa ferramenta foi removida, e substituída por um cadastro melhorado que possibilitava ao editor cadastrar vários dados sem sair da página e sem repetir informações de fonte ou categoria para dados de um mesmo artigo. 

Na terceira semana me reuni também com o líder de desenvolvimento e um dos desenvolvedores da ZURB que me apresentaram o Platform, sistema integrado de autenticação e autorização. Na época cada propriedade da ZURB possuía seu próprio cadastro de usuários. O Design Quips seria o primeiro projeto a utilizar o cadastro unificado, e se a integração fosse bem sucedida seria estendida a todas as outras ferramentas ZURB.   O Platform era um provedor que suportava o protocolo OAuth 2, "um framework de autorização que permite a uma aplicação de terceiros obter acesso limitado a um serviço HTTP, em nome do proprietário de um recurso orquestrando uma interação de aprovação entre o proprietário do recurso e o serviço HTTP." O Design Quips delegaria autenticação ao Platform, que permitia a um usuário se autenticar via email e senha, ou via as redes sociais Facebook, Twitter, e Google+. Platform informava ainda aos clientes se o papel do usuário autenticado era de usuário comum ou administrador, informação que era suficiente para implementar autorização no Design Quips.

A quarta semana foi dedicada a integração com o Platform e a preparação para a implantação do Design Quips na estrutura de servidores da ZURB. Essa preparação foi em sua maior parte feita por um desenvolvedor do time, que tinha acesso aos servidores e conhecia a infra-estrutura existente.

Na semana seguinte fui movido para um outro projeto, e Design Quips viu pouco avanço além de alguns ajustes nas funcionalidades existentes. 

O tema da sexta semana foi ajustar o site para funcionar corretamente em dispositivos móveis. O site foi desenvolvido seguindo princípios de design responsivo, e o layout se ajustava de acordo com a resolução do cliente. As maiores mudanças implementadas nessa semana para acomodar dispositivos móveis foram uma barra de filtragem que usava elementos "select" ao invés de ícones, já que os ícones ficavam muito pequenos e difíceis de clicar em resoluções baixas; e um menu que usava a técnica "off canvas," inicialmente invisível e que parecia ser puxado de fora da tela quando o botão de menu era clivado.

(screenshot mobile toolbar)

(screenshot offcanvas menu)

Nas duas semanas seguintes mais uma vez priorizei um outro projeto, e não houveram grandes avanços no Design Quips. Foram feitos ajustes nas ferramentas administrativas a serem usadas pelo administrador, corrigida a integração com o Platform, adicionada a exibição de propagandas, e criadas as páginas de conteúdo do site. Foram duas páginas de conteúdo: uma sobre o projeto Design  Quips, que explicava a motivação por trás do projeto e como ele podia ser útil a usuários; e uma página que permitia se inscrever na lista de email do Design Quips que mensalmente envia novos dados e artigos relacionados ao conteúdo do site.

Com essas funcionalidades implementadas, deu-se por terminada a etapa de desenvolvimento e iniciou-se a o processo lançamento.

### Lançamento

A primeira tarefa da etapa de lançamento foi revisar cuidadosamente todas as funcionalidades implementadas para corrigir quaisquer falhas existentes, garantir que o design estava consistente, e checar que o sistema funcionava como devido no ambiente de produção. Uma vez feitas todas as correções que o time encontrou, o projeto foi apresentado primeiro a líder de design e depois ao CEO, que fizeram novas críticas e sugeriram novas mudanças. Nessa etapa as mudanças sugeridas eram correções e ajustes a funcionalidades existentes, e não novas funcionalidades.

Depois de incorporadas as críticas, foi feito o processo de garantia de qualidade. Tal processo consistiu em testar o site em diversos plataformas desktops e móveis. Design Quips foi testado nos navegadores Firefox, Safari, Chrome e Internet Explorer rodando em desktops, e nos dispositivos móveis iPhone 3GS e 4S, Nexus 4 e 7, Galaxy S3, Microsoft Surface, um smartphone rodando Windows Phone e um Blackberry, e as falhas encontradas foram corrigidas.

Com o site pronto e testado em diversos dispositivos, foi feita uma nova reunião com o CEO. Nessa reunião foi definida a data de lançamento e criada uma lista de tarefas do lançamento. A lista era composta por tarefas necessárias ao lançamento do Design Quips, e não mudanças no projeto em si. Entre essas tarefas estavam preparar uma apresentação que seria internamente para que todos da empresa conhecessem melhor o projeto, escrever um artigo para ser publicado no blog da empresa quando do lançamento oficial, entrar em contato com outras publicações que podiam se interessar em cobrir o lançamento, e adicionar o Design Quips às ferramentas de monitoramento usadas na ZURB.

Os itens dessa lista foram feitos ao longo da semana, pelo time e por outros membros da ZURB, e o site foi lançado dia 1 de agosto com um anúncio no blog oficial da empresa e em todas os perfis da ZURB em redes sociais.

(screenshot artigo lançamento)

### Acompanhamento

Depois do lançamento começou a etapa de acompanhamento, que consiste em acompanhar o uso do site, periodicamente reavaliar seus objetivos, e propor e implementar mudanças. A minha participação no projeto findou com o lançamento, mas é possível perceber pela evolução do Design Quips após o lançamento que o projeto continua sendo acompanhado e desenvolvido.

(screenshot novembro de 2011)

(screenshots atuais)

-- referências

http://www.amazon.com/HTML5-Up-Running-Mark-Pilgrim-ebook/dp/B0043D2E0E/ref=tmm_kin_title_0

http://sphinxsearch.com/about/sphinx/

http://www.cob.unt.edu/itds/faculty/evangelopoulos/dsci5910/LSA_Deerwester1990.pdf

http://classifier.rubyforge.org

http://tools.ietf.org/html/rfc6749