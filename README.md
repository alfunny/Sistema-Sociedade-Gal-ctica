# Sistema-Sociedade-Galactica

# Descrição base de dados
Estrelas são corpos celestes identificados pela sua designação de catálogo estelar, além de conter
informações como nome, classificação estelar, e massa. Além disso, estrelas possuem coordenadas
celestes, que também podem ser utilizadas para referenciar estrelas de forma única. Estrelas dão
origem a Sistemas, onde cada um é identificado pela sua estrela principal, podendo também ter um
nome associado. Planetas compõem outra classificação de corpos celestes, usualmente orbitando
estrelas, sendo identificados pelas suas respectivas designações astronômicas, além de conter
informações como massa, raio, composição atmosférica, e classificação planetária. Tanto planetas
quanto estrelas podem orbitar alguma estrela, onde são armazenadas informações sobre a órbita,
tais como distância mínima e máxima de entre os dois corpos, e o período de translação. Toda
estrela deve obrigatoriamente compor um sistema ou orbitar direta/indiretamente uma estrela que
compõe um sistema. Podem existir planetas errantes, i.e., que não orbitam estrelas, e planetas que
orbitam mais de uma estrela, i.e., em sistemas múltiplos.
Na galáxia, existem Espécies de seres vivos, podendo ser inteligentes ou não, identificadas pelos
seus nomes científicos. Toda espécie tem um planeta de origem. Conjuntos substanciais de
membros da mesma espécie inteligente podem formar Comunidades, identificadas pelas suas
respectivas espécies e nomes, onde pode-se armazenar informações adicionais como a quantidade
de habitantes de cada comunidade. As comunidades normalmente habitam planetas, onde é
armazenado o histórico de Habitações, com seus respectivos planetas, comunidades, e datas de
início e fim. Um planeta pode abrigar múltiplas comunidades em um determinado período de tempo,
e comunidades podem migrar ou ser realocadas entre planetas.
As Federações são grandes organizações formadas por várias nações, sendo identificadas pelo seu
nome e contendo a informação sobre a sua data de fundação. Uma Nação é qualquer entidade
governamental presente na galáxia, sendo identificada pelo seu nome, além de conter informações
sobre a quantidade de planetas controlados por ela. Cada nação só pode estar associada a uma
federação, e a federação só pode existir se tiver pelo menos uma nação associada. Os planetas
cadastrados no sistema podem ser dominados por nações, sendo mantido um histórico de
Dominância, composta pela nação, pelo planeta e pelas datas de início e fim dessa dominância.
Na galáxia, existem ainda Facções, que são grupos ideológicos que podem estar presentes em
diversas nações, as quais também abrigam várias facções. Elas são identificadas pelo seu nome, e
contém informações da quantidade de nações em que está presente e sobre qual a sua ideologia
predominante, podendo ser: progressista, totalitária, tradicionalista. As comunidades dos planetas
também podem se filiar a uma facção, sendo esta capaz de atender várias comunidades em nações
que a abrigam.
Entre as diversas nações existentes, podem existir Líderes, membros influentes das nações que
desempenham papéis-chave para o seu desenvolvimento. Líderes são identificados pelos seus
respectivos Cadastros de Pessoa Intergalática (CPIs), além de terem informações armazenadas
como nome, cargo, nação, facção, e espécie. Um Líder cadastrado no sistema sempre deve estar
associado a uma nação. Os cargos de líderes representam de maneira geral seus papéis em suas
respectivas nações, podendo ser: comandante, oficial ou cientista. Cada facção deve ter um único
líder para comandá-la, este sendo associado a uma nação onde a facção está presente, e um líder
pode participar de apenas de uma facção.

# Modelo Relacional
![image](https://github.com/alfunny/Sistema-Sociedade-Galactica/assets/72526633/d61784da-3ac9-4743-8db4-737c1ef592f1)

# Usuarios
Deve ser criada uma tabela chamada USERS, para armazenar os usuários do sistema, com os
seguintes atributos: Userid (ID sintético), Password, IdLider (id na tabela de origem - Lider). A
chave primária deve ser Userid, e o atributo IdLider deve ser único, referenciando a tabela de
líderes. O atributo Password deve utilizar a função md5 do SGBD para armazenar os dados.
Os líderes já cadastrados na base deverão ser cadastrados manualmente na tabela USERS, i.e.,
deve ser criado um procedimento (PL/SQL) para encontrar líderes sem respectivas tuplas na tabela
USERS e inserí-los com uma senha padrão. O procedimento pode ser executado manualmente,
via SQL Developer. Além disso, deve ser criada uma tabela chamada LOG_TABLE para
armazenar o log de acessos e operações dos usuários do sistema, com os seguintes atributos:
Userid (associado à table a USERS), timestamp, message. A tabela de logs deverá ser mantida
por chamadas da aplicação.
As funcionalidades a serem implementadas no projeto serão diferentes para cada tipo de
usuário/líder, que é definido pelo seu cargo. O controle das permissões de acesso às
funcionalidades deve ser feito pela aplicação. Existem também funcionalidades adicionais para
líderes que estão associados a facções cadastradas (líderes de facção). Os tipos de usuários são:
  ● Líder de facção: Pode gerenciar aspectos da própria facção da qual é líder
  ● Cientista: Pode gerenciar informações astronômicas (estrelas, planetas, sistemas)
  ● Comandante: Pode gerenciar aspectos da própria nação
  ● Oficial: Pode apenas visualizar informações referentes à própria nação

# Orientações sobre interfaces de usuário
Para organizar o protótipo implementado, sugerimos a seguinte configuração de telas/interfaces de
usuário:
  ● Interface 1: Interface de login. Após feita a autenticação, a Interface 2 poderá ser exibida
  ● Interface 2: Interface de overview. Deve apresentar o nome de usuário autenticado. Além
disso, podem ser apresentadas informações de overview de acordo com o usuário e
links/botões que permitam a execução das funcionalidades. Também deve haver um
caminho para a Interface 3
  ● Interface 3: Interface de relatórios. Deverão ser apresentados botões ou algo análogo para
exibir os relatórios possíveis, de acordo com o usuário logado.
É permitido utilizar quaisquer frameworks de interface de usuário, seja por interface gráfica ou
frameworks baseados em sistemas web, desde que não violem as orientações anteriores.

# Obrigatório no desenvolvimento de protótipo
  ● Defina pelo menos uma view com junção na implementação das funcionalidades. A visão
deve ser parte da estratégia de implementação. Justifique a relevância da view. . Se
necessário, crie triggers para implementar o comportamento correto de operações DML na
visão.
  ● Implemente índices adicionais para otimizar consultas de interesse.
  ● Implemente procedimentos e/ou funções usando pacotes.
  ● Implemente triggers relacionados às funcionalidades do protótipo.
  ● Faça o devido tratamento de erros e exceções, com mensagens claras para o usuário,
indicando o problema e como proceder.
  ● Defina transações.
  ● Todas as operações de usuários devem ser realizadas via interface gráfica. Na correção,
será considerado, por exemplo, se a entrada de dados é simplesmente a digitação de uma
informação que já existe na base de dados ou se são feitos filtros que listam na interface as
informações pertinentes para o usuário selecionar o que precisa.

# Documentação
  ● Documentação interna:
    ○ explicação do objetivo de cada consulta e das soluções de implementação;
    ○ explicação da funcionalidade de visões, triggers, procedimentos, funções e pacotes.
  ● Documentação externa:
    ○ lista dos softwares, ferramentas, linguagem e APIs utilizados, incluindo as versões;
    ○ indicação do que contém cada arquivo, destacando principalmente os scripts com
códigos SQL e PL/SQL, e arquivos com código relacionado ao acesso à base de
dados;
  ● comentários, discussões e explicações necessárias para a correção, incluindo comentários
sobre as funcionalidades extras;
  ● não inclua código na documentação externa.

