Criando um Framework - Changelog
================================

* Parte 01
 * Aplicação básica

* Parte 02
 * Adicionar tratamento para o caso de a query string não for informada (e não gerar um warning por este motivo)
 * Adicionar tratamento contra vulnerabilidades de segurança como o XSS
 * Adicionar componente HttpFoundation do Symfony2 como dependência e reescrita do código utilizando este componente
 * Utilização de autoload automático
 * Utilização de abordagem orientada à objetos

* Parte 03
 * Adicionar página à aplicação básica com comportamento semelhante à outra página já existente
 * Isolamento de código compartilhado
 * Mapeamento de rotas para scripts
 * Controle de rotas inexistentes
 * Adicionar front controller
 * Adicionar arquivo .htaccess com URL rewriting para tornar a URL amigável e não expor o nome dos scripts PHP com acesso somente para o front controller
 * Estruturação do diretório do projeto para não manter acessíveis os scripts PHP para o cliente
 * Exibição de templates

* Parte 04
 * Refatoração de código e remoção das strings de consulta do template
 * Adicionar componente Routing do Symfony2 como dependência
 * Remoção do autoload customizado e utilização do autoload gerado pelo Composer
 * Configuração de rotas movida para um arquivo separado
 * Utilização dos nomes das rotas para os templates
 * Erros do tipo 500 gerenciados corretamente

* Parte 05
 * Refatoração de código e criação de um controller genérico
 * Criação de um controller customizável durante a definição das rotas
 * Criação de um controller customizado usando funções anônimas

* Parte 06
 * Remoção de código procedural e conversão para classes
 * Adicionar componente HttpKernel do Symfony2 como dependência
 * Alterar atributo injetado no método do controller
 * Refatoração de código utilizando o controller resolver do componente HttpKernel

* Parte 07
 * Refatoração do código do framework e da aplicação utilizando classes
 * Criação de namespaces para as classes do framework e da aplicação
 * Mover a lógica da manipulação de requisição para a classe do framework
 * Mover a lógica da aplicação para as classes da aplicação
 * Refatoração do código do front controller e da configuração do framework
 * Aplicação com quatro camadas distintas: front controller, código do framework, código da aplicação e código da configuração

* Parte 08
 * Adicionar biblioteca de testes PHPUnit como dependência para desenvolvimento
 * Criação do arquivo de configuração do PHPUnit
 * Criação do diretório de testes
 * Modificação do framework para a utilização de interfaces para permitir testes unitários utilizando dublês de teste
 * Criação do teste para erro 404 (requisição que não corresponde à nenhuma rota)
 * Criação do teste para erro 501 (qualquer outro erro de execução)
 * Criação do teste para solicitação com sucesso

* Parte 09
 * Adicionar componente EventDispatcher do Symfony2 como dependência
 * Adicionar evento à ser despachado antes do retorno da resposta
 * Refatoração dos listeners para classes próprias
 * Refatoração da aplicação para utilização de subscribers ao invés de listeners