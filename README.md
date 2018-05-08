# [ASP.NET Core MVC](https://docs.microsoft.com/en-us/aspnet/core/mvc/overview?view=aspnetcore-2.1)

> O ASP.NET Core MVC é uma estrutura avançada
> para a criação de aplicativos Web e API's
> usando o padrão Model-View-Controller

> Definição da Microsoft:
> 
> A estrutura do ASP.NET Core MVC é uma estrutura de apresentação leve, de software livre e altamente testável, otimizada para uso com o ASP.NET Core.
>
> ASP.NET Core MVC fornece uma maneira com base em padrões para criar sites dinâmicos que habilitam uma separação limpa de preocupações.
>
> Ele lhe dá controle total sobre a marcação, dá suporte ao desenvolvimento amigável a TDD e usa os padrões da web mais recentes.

## MVC

O padrão de arquitetura MVC (Model-View-Controller) que separa a aplicação em 3 camadas principais: Modelos, Exibições e Controladores.

O objeto é atingir a [SoC](https://www.c-sharpcorner.com/UploadFile/56fb14/understanding-separation-of-concern-and-Asp-Net-mvc/) (do inglês Separation of Concern, Separação de Conceitos).

O fluxo básico de uma aplicação MVC é:

> Requisições são encaminhadas à `C`ontroller
>
> A controladora se utiliza de uma `M`odel para obter os recursos
>
> Após ter os dados encaminha-os para `V`iew para a exibição

![MVC]({{ 'assets/images/mvc.png' | relative_url }})

> Na imagem podemos notar alguma dependências:
> 
> Controller: depende da Model e View (caso seja API não temos)
>
> View: depende da Model
>
> Model: Não temos dependência 

No momento que conseguimos separar as responsabilidades temos uma melhora na manutenção, pois sabemos onde alterações devem ser feitas.

>
> Tenha cuidado para que alterações se mantenham em seu escopo.
>
> Por exemplo:
> 
> Se for apenas uma alteração na apresentação do conteúdo
> uma alteração na View é suficiente.
>

[Responsabilidades]({{ 'responsabilidades' | relative_url }})

[Rotas]({{ 'rotas' | relative_url }})