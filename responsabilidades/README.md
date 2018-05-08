# [Princípio da Responsabilidade Única](http://netcoders.com.br/aplicando-solid-com-c-srp/)

No momento que conseguimos ter a separação de conceitos conseguimos atingir um princípio de arquitetura de software chamado Princípio da Responsabilidade Única presente nos padrões SOLID

> [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))
>
> Conjunto de padrões de programação orientada a objetos
> 
> S -> [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle)
> 
> O -> [Open/closed principle](https://en.wikipedia.org/wiki/Open/closed_principle)
> 
> L -> [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)
> 
> I -> [Interface segregation principle](https://en.wikipedia.org/wiki/Interface_segregation_principle)
> 
> D -> [Dependency inversion principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle)
> 

[Camadas Adicionais](http://deviq.com/kinds-of-models/)


## Responsabilidade Do Modelo

Lógica de negócio e estado a aplicação são responsabilidades atribuídas ao modelo.

> ViewModel
>
> Modelos com lógicas de apresentação de conteúdo
> 
> Views fortemente tipadas se utilizam de modelos próprios.
>
> A Controller popula a ViewModel e repassa à View
>
> Lógicas com uma maior complexidade deve ser implementadas em ViewModels

## Responsabilidade do Controlador

Controla qual modelo e exibição será utilizada.

Pontos de entrada de aplicações Web ou API's.

Controladores cuidam da interação com o usuário da aplicação.

Requisições são encaminhadas (utilizando rotas, que veremos mais adiante) para a controladora responsável (PeopleController, ProductsController, etc.).

> [DRY (Don't Repeat Yourself)](http://deviq.com/don-t-repeat-yourself/)
>
> Ações se repetem em diversos pontos da aplicação.
> 
> Pense em utilia o princípio de Não Se Repitir.
>
> Em controllers podemos utilizar [filtros](https://docs.microsoft.com/en-us/aspnet/core/mvc/overview?view=aspnetcore-2.1#filters)

## Responsabilidades da Exibição

Apresentar as informações para o usuário é a responsabilidade da View.

Para isso temos a utilização de mecanismo de template chamado [Razor](https://docs.microsoft.com/en-us/aspnet/core/mvc/overview?view=aspnetcore-2.1#razor-view-engine). Com este mecanismo utilizamos códigos em marcações HTML.

Views devem conter o mínimo de lógica possível!

Caso exista alguma complexidade maior para exibir algum conteúdo considere a utilização de ViewModel ou [View Components](https://docs.microsoft.com/en-us/aspnet/core/mvc/views/view-components?view=aspnetcore-2.1).