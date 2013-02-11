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
