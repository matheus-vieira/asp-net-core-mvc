# [ASP.NET Core MVC](https://docs.microsoft.com/en-us/aspnet/core/mvc/overview?view=aspnetcore-2.1)

> O ASP.NET Core MVC é uma estrutura avançada
> para a criação de aplicativos Web e API's
> usando o padrão Model-View-Controller

## MVC

O padrão de arquitetura MVC (Model-View-Controller) que separa a aplicaçã em 3 camadas principais: Modelos, Exibições e Controladores.

O objeto é atingir a SoC (do inglês Separation of Concern, Separação de Conceitos).

O fluxo básico de uma aplicação MVC é:

> Requisições são encaminhadas à `C`ontroller
>
> A controladora se utiliza de uma `M`odel para obter os recursos
>
> Após ter os dados encaminha-os para `V`iew para a exibição

![MVC]({{ 'assets/images/mvc.png' | relative_url }})