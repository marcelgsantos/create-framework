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
