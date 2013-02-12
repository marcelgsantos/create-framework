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