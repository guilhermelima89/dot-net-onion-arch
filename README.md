# Traditional Layered Architecture (Arquitetura 3 Camadas)

- UI (API)
- Business Logic (CORE)
- Data (Infrastructure)

- Todas as camadas tem acesso as dados

# Onion Architecture (Arquitetura Cebola)

- Principio da inversão de controle
- Enfrentar os desafios encontrados na arquitetura tradicional
- Melhoria na separação de responsabilidae
- Mlehoria no acoplamento

- UI - Unit Tests - WCF
- Interfaces Services
- Interfaces Repositories
- Domain

- A aplicação é construída em torno de um sistema de modelo de objeto independente

- As camadas internas definem interfaces, camadas externas implementam interfaces

- A direção do acoplamento é em direção ao centro

- Todo o código principal do aplicativo pode ser compilado e executado separadamente da infraestrutura

## Inversão de controle (IOC)

- IOC é um princípio fundamental permite delegar o fluxo de controle do programa, em termos de acesso a recursos e serviços, à estrutura dependente e não ao próprio programa

## Injeção de Dependência (DI)

- DI é usado para resolver o problema de dependências e se refere a técnicas que resolvem dependências de forma automática por meio da injeção de valores

## Separação de Camadas

Diferentes camadas do sistema são separadas de forma que cada camada tenha suas responsabilidades específicas onde cada camada também tem menos dependências de suas camadas externas

# Diferenças: camadas

## Arquitetura cebola

Na arquitetura cebola, as camadas são organizadas em círculos concêntricos, com o núcleo (lógica de negócios) no centro e camadas externas (infraestrutura, apresentação) circundando-o. Isso enfatiza a independência e a abstração das camadas internas.

## Arquitetura limpa

A arquitetura limpa também enfatiza a independência das camadas, mas organiza as camadas em anéis concêntricos, com o círculo mais interno representando a lógica de negócios, seguido por círculos concêntricos de camadas de aplicação, interface do usuário e infraestrutura. Ela também promove a inversão de dependência (Dependency Inversion Principle).

# Diferenças: dependências

## Arquitetura cebola

Na arquitetura cebola, as camadas possuem dependências hierárquicas. As camadas mais internas, que contêm a lógica de negócios, são projetadas para serem altamente independentes e têm menos dependências, enquanto as camadas externas, como a camada de infraestrutura e a camada de interface do usuário, dependem das camadas internas. As dependências fluem das camadas externas em direção à camada central mais interna.

## Arquitetura limpa

Na arquitetura limpa, as camadas geralmente possuem dependências uniformes, o que significa que cada camada é projetada para ser independente das camadas adjacentes e não deve ter dependências diretas de nível inferior ou superior. Isso contribui para a independência das camadas e facilita a manutenção e os testes do código.

# Onion_Architecture

Apresentando a Onion Architecture
A Onion Architecture é um padrão de arquitetura que propõe que o software deve ser feito em camadas, cada camada com sua própria preocupação ou responsabilidade, e, foi proposta por Jeffrey Pallermo em seu site.

A regra de ouro da arquitetura é: "Nada em um círculo interno pode saber absolutamente nada sobre algo em um círculo externo. Isso inclui métodos, classes, variáveis ou qualquer outra entidade de software nomeada." Robert C. Martin

Obs:Essa regra também existe em outras arquiteturas semelhantes, como Arquitetura Limpa (Clean Architecture).

Esta regra depende da injeção de dependência para fazer sua abstração das camadas, para que você possa isolar suas regras de negócios de seu código de infraestrutura, como repositórios e views.

As camadas de arquitetura de cebola

A Onion Architecture usa o conceito de camadas, mas são diferentes das camadas da arquitetura de três e n-camadas. Vamos ver o que cada uma dessas camadas representa e o que deve conter.

1- Camada de Domínio (a camada mais interna)

A camada de domínio reside na parte central da arquitetura Onion, e representa os objetos de negócios e o comportamento. A idéia é ter todos os seus objetos de domínio nesse núcleo. Ele contém todos os objetos de domínio do aplicativo. Além dos objetos de domínio, você também pode ter interfaces de domínio. Essas entidades de domínio não têm dependências. Objetos de domínio também são simples como deveriam ser, sem nenhum código pesado ou dependências. (Se um aplicativo for desenvolvido usando um ORM como o Entity Framework, essa camada conterá classes POCO.)

2- Camada de Repositório (Repository Layer)

Essa camada cria uma abstração entre as entidades do domínio e a lógica de negócios do aplicativo. Nesta camada, geralmente adicionamos interfaces que fornecem o comportamento de salvar e recuperar objetos, geralmente envolvendo um banco de dados. Essa camada consiste no padrão de acesso a dados, que é uma abordagem mais fracamente acoplada ao acesso a dados. Também criamos um repositório genérico e adicionamos consultas para recuperar dados da fonte, mapear os dados da fonte de dados para uma entidade comercial e persistir alterações na entidade comercial na fonte de dados.

3- Camada de Serviços (Service Layer)

A camada de serviços mantém interfaces com operações comuns, como Adicionar, Salvar, Editar e Excluir. Além disso, essa camada é usada para se comunicar com a camada da interface do usuário e a camada do repositório. A camada de serviço também pode conter lógica de negócios para uma entidade. Nesta camada, as interfaces de serviço são mantidas separadas de sua implementação, tendo em mente o acoplamento e a separação de responsabilidades.

4- Camada de Interface do Usuário (UI Layer)

É a camada mais externa e mantém responsabilidades periféricas como interface do usuário e testes. Pode ser uma aplicação Web, uma API, um projeto de Testes, etc. Essa camada possui uma implementação do padrão da injeção de dependência, para que o aplicativo construa uma estrutura fracamente acoplada e possa se comunicar com a camada interna por meio de interfaces.
