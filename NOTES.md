Criando um Framework - Anotações
================================

* O Symfony2 é um conjunto reutilizável de componentes standalone PHP, desacopladas e coesivos para resolverem problemas comuns de desenvolvimento web.
* Ao invés de utilizar estes componentes de baixo nível, é possível utilizar o Symfony2, que é um full-stack framework pronto para o uso. Ou é possível também criar o seu próprio framework.
* É senso comum no desenvolvimento web que é melhor utilizar um framework já conhecido e testado sem a necessidade de se reinventar a roda. Isso é realmente verdade, porém existem algumas boas razões para se criar seu próprio framework.
* Algumas das razões são conhecer mais sobre a arquitetura de baixo nível de frameworks web modernos em geral e sobre as estruturas internas do Symfony2; criar um framework baseadas em necessidades específicas; criar um framework para diversão e aprendizado; refatorar uma aplicação antiga que necessita de uma grande dose de melhores práticas para desenvolvimento web.
* Os componentes do Symfony2 são capazes de criar qualquer abordagem de framework e não só frameworks MVC.
* Ao projetar uma aplicação é importante considerar a Separação de Responsabilidades (Separation of Concerns ou SoC em inglês).
* Os princípios fundamentais dos componentes do Symfony2 giram em torno da especificação do HTTP. Neste caso, frameworks com estas características são chamados de frameworks HTTP ou frameworks Request/Response.
* Ao projetar uma aplicação também é importante utilizar padrões de codificação (coding standards) e ser consistente.
* Para instalar os componentes do Symfony2 utiliza-se o gerenciador de dependências para PHP chamado Composer.
* No arquivo chamado `composer.json` são listadas as dependências para o projeto e o comando `composer install` realiza a instalação das dependências.
* Em PHP é necessário incluir - utilizando o método require() - os arquivos onde as classes são definidas para que possamos utilizá-las. Como isso pode acarretar em tarefas chatas e enfadonhas, com algumas convenções, podemos realizar o autoload das classes através do próprio PHP de forma automática.
* O componente ClassLoader do Symfony2 fornece um autoloader que implementa o padrão PSR-0 e, na maioria das vezes, ele é suficiente para fazer o autoload das classes de seu projeto.
* O Composer cria automaticamente um autoloader para todas as suas dependências instaladas. Neste caso, ao invés de utilizar o componente ClassLoader, pode-se apenas incluir `vendor/autoload.php`.
* Por mais simples que uma aplicação PHP possa ser ou parecer simples, algumas ações precisam ser tomadas para melhorar a robustez da aplicação.
* Algumas destas ações são: tratar query strings para o caso de não serem informadas; proteção contra vulnerabilidades de segurança como o XSS;
* Realizar o escapamento do código utilizando `htmlspecialchars` é enfadonho e propenso a erros. Neste caso, sugere-se a utilização de uma ferramenta de template como o Twig onde o escapamento do código é realizado por padrão.
* Escrever um código que seja facilmente testável também trata-se de uma característica muito importante para o desenvolvimento de uma aplicação robusta e tolerante a erros nos dias de hoje.
* É fato que é uma ótima idéia utilizar um framework do que manter sua aplicação em PHP puro. Isto permite a prevenção de erros, códigos inseguros e torna o código mais facilmente testável. Além disso, são bastante produtivos permitindo escrever códigos melhores e de forma mais rápida.
* Escrever código web é escrever sobre como interagir com HTTP. A especificação do HTTP descreve como um cliente interage com um servidor através de mensagens bem definidas de requisição e resposta (um browser interagindo com uma aplicação no servidor web, por exemplo).
* No PHP, as requisições são representadas pelas variáveis globais $_GET, $_POST, $_SESSION entre outras e as respostas são geradas por funções como echo(), header(), setcookie() entre outras.
* O primeiro passo para um código melhor é utilizar uma abordagem orientada à objetos. Este é o principal objetivo do componente HttpFoundation do Symfony2 ao substituir as variáveis globais e as funções do PHP para uma abstração orientada à objetos.
* Para utilizar este componente, basta adicioná-lo como dependência no arquivo `composer.json` e executar o comando `composer update` para a instalação do componente em questão.
* O método createFromGlobals() cria um objeto Request baseado nas atuais variáveis globais do PHP.
* O método send() de Reponse envia um objeto Response de volta para o cliente (ele primeiro envia os cabeçalhos HTTP seguidos pelo conteúdo).
* Os componentes do Symfony2 são auditados para falhas de segurança por companhias independentes. E sendo também um projeto open-source permite que outros desenvolvedores corrijam alguma potencial falha de segurança.
* Componente HttpFoundation do Symfony2 nos permitem escrever códigos mais testáveis e melhores e mais rapidamente, além de resolver parte dos problemas que enfrentamos no dia-a-dia.
* O compartilhamento de código é uma ótima premissa para se construir um framework. É interessante também considerar a criação de templates e tornar nosso código testável.
* Outro inconveniente é que para adicionar uma nova página é necessário criar um novo arquivo PHP que é exposto para o usuário através da URL pois há um mapeamento direto entre o script PHP e esta URL. Isso ocorre porque o despacho da requisição é feito diretamente pelo servidor. É uma boa prática mover este gerenciamento para o código para melhor flexibilidade. Este gerenciamento pode ser alcançado fazendo o roteamento de todas as requisições do cliente para um único script PHP.
* Expor um único script PHP para o usuário final é um padrão de projeto chamado 'front controller'.
* Podemos ocultar o nome do script do 'front controller' nas URL através de regras do servidor web utilizado. Isto torna as URLs mais amigáveis e inibe a exposição do nome do script PHP do 'front controller'.
* Utilizando o 'front controller' podemos ainda deixar os arquivos em diretórios mais seguros que não são acessados diretamente no diretório raiz da web.
* Um aspecto importante de qualquer website é o formato da URL. Graças ao mapeamento de URL é possível desacoplar a URL do código que gera a saída associada.
* O componente Routing do Symfony2 permite realizar tarefas tais como roteamento de URLs, geração de URLs, verificação de atributos, verificação de métodos HTTP entre outras tarefas.
* Dada uma coleção de rotas (RouteCollection), um objeto UrlMatcher pode encontrar a rota correspondente ao caminho da URL informada. Neste caso, um array de atributos é retornado junto com a própria rota correspondida. Caso nenhuma rota seja correspondida ao caminho da URL uma exceção será lançada.
* Utilizando o componente Routing do Symfony2 obtém-se uma facilidade enorme quando utiliza-se a correspondência e a geração de URLs em conjunto permitindo a criação de URLs relativas e absolutas de maneira fácil e prática.
* É uma boa prática realizar a separação de códigos de configuração e do framework em arquivos distintos.
* Adicionar a lógica dentro do template não é uma boa idéia, principalmente se levarmos em conta o princípio de separação de responsabilidades.
* A separação do código do template do código da lógica pode ser feito utilizando uma nova camada de código chamada de controller.
* O objetivo do controller é gerar uma resposta baseada na informação enviada pela requisição do cliente.
* A classe Request dos componentes do Symfony2 possui uma funcionalidade chamada 'attributes'. Esta funcionalidade permite incorporar informações sobre a requisição (Request) que não está diretamente relacionada aos dados da requisição HTTP.
* Utilizar a função `call_user_func()` do PHP permite a utilização de qualquer forma de callback.
* Como convenção, para cada rota, o controller associado é configurado através do atributo `_controller`.
* Na definição de um controller usando funções anônimas, é possível modificar o objeto de resposta e também passar argumentos opcionais ao template.
* Por motivos de performance, os controllers não devem ser instanciados todos de uma vez. Eles devem ser carregados tardiamente (lazy loading) somente para a rota correspondida.
* O componente HttpKernel, dos componentes do Symfony2, possui, entre outras funcionalidades, um controller resolver.
* Um controller resolver sabe como determinar o controller à ser excutado e os argumentos passados para ele através do objeto Request.
* Todos os controller resolvers implementam a interface `ControllerResolverInterface`.
* O método `getController()` baseia-se na mesma convenção explicada anteriormente: o atributo `_controller` da requisição deve conter o controller associado à requisição (Request).
* Além dos modos de callbacks existentes no PHP, o método `getController()` também suporta uma string composta do nome da classe, de dois pontos (::) e de um nome de método como um método de callback válido, por exemplo: `MyController::indexAction`.
* O controller resolver também manipula adequadamente o gerenciamento de erros. Quando não é definido o atributo `_controller` para uma determinada rota, por exemplo.
* O método `getArguments()` examina a assinatura do controller para determinar quais argumentos são passados para ele usando a API nativa de Reflection do PHP.
* O método do controller precisa ter o objeto Request como um argumento. O método `getArguments()` saberá como injetá-lo corretamente se o método do controller estiver com o type-hint definido corretamente.
* O método `getArguments()` também é capaz de injetar qualquer atributo do objeto Request. Basta que o argumento do método do controller tenha o mesmo nome do atributo.
* É possível também injetar o objeto Request e quaisquer atributos do objeto Request ao mesmo tempo. E como a correpondência é feita através do type-hint e/ou do nome dos argumentos, a ordem é indiferente neste caso.
* É possível, ainda, definir valores padrão para quaisquer argumentos que correspondam à um atributo opcional da requisição (Request).
* O controller resolver é responsável também por validar as chamadas ao controller e seus argumentos. No caso de algum problema, é lançada uma exceção com uma mensagem amigável detalhando o problema (a classe do controller não existe, método não definido, argumento sem atributo correspondente entre outros, por exemplo).
* É recomendável, ao criar um framework, encapsular o código numa classe. Isso permite tornar o código reutilizável e testável entre outros benefícios.
* Existem frameworks que contam com o simples lógica de criar um resposta (Response) associada com uma requisição (Request).
* Para classes definidas na aplicação serem carregadas pelo autoload, é necessário informar o carregamento destas classes no arquivo de configuração `composer.json`.