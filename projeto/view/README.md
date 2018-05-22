# View

Como já foi dito as `View's` são referentes à apresentação do conteúdo ao usuário.

## [Layout](https://docs.microsoft.com/pt-br/aspnet/core/mvc/views/layout?view=aspnetcore-2.0)

A maioria dos aplicativos Web tem um layout comum que fornece aos usuários uma experiência consistente durante sua navegação de uma página a outra. O layout normalmente inclui elementos comuns de interface do usuário, como o cabeçalho do aplicativo, elementos de menu ou de navegação e rodapé.

![Layout]({{ 'assets/images/projeto/view/page-layout.png' | relative_url }})

Os layouts reduzem o código duplicado em exibições, ajudando-os a seguir o princípio [DRY (Don't Repeat Yourself)](http://deviq.com/don-t-repeat-yourself/).

![Pastas]({{ 'assets/images/projeto/view/pasta.png' | relative_url }})

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - WebApplication1</title>

    <environment names="Development">
        <link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.css" />
        <link rel="stylesheet" href="~/css/site.css" />
    </environment>
    <environment names="Staging,Production">
        <link rel="stylesheet" href="https://ajax.aspnetcdn.com/ajax/bootstrap/3.3.6/css/bootstrap.min.css"
              asp-fallback-href="~/lib/bootstrap/dist/css/bootstrap.min.css"
              asp-fallback-test-class="sr-only" asp-fallback-test-property="position" asp-fallback-test-value="absolute" />
        <link rel="stylesheet" href="~/css/site.min.css" asp-append-version="true" />
    </environment>
</head>
<body>
    <div class="navbar navbar-inverse navbar-fixed-top">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                    <span class="sr-only">Toggle navigation</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                <a asp-area="" asp-controller="Home" asp-action="Index" class="navbar-brand">WebApplication1</a>
            </div>
            <div class="navbar-collapse collapse">
                <ul class="nav navbar-nav">
                    <li><a asp-area="" asp-controller="Home" asp-action="Index">Home</a></li>
                    <li><a asp-area="" asp-controller="Home" asp-action="About">About</a></li>
                    <li><a asp-area="" asp-controller="Home" asp-action="Contact">Contact</a></li>
                </ul>
                @await Html.PartialAsync("_LoginPartial")
            </div>
        </div>
    </div>
    <div class="container body-content">
        @RenderBody()
        <hr />
        <footer>
            <p>&copy; 2016 - WebApplication1</p>
        </footer>
    </div>

    <environment names="Development">
        <script src="~/lib/jquery/dist/jquery.js"></script>
        <script src="~/lib/bootstrap/dist/js/bootstrap.js"></script>
        <script src="~/js/site.js" asp-append-version="true"></script>
    </environment>
    <environment names="Staging,Production">
        <script src="https://ajax.aspnetcdn.com/ajax/jquery/jquery-2.2.0.min.js"
                asp-fallback-src="~/lib/jquery/dist/jquery.min.js"
                asp-fallback-test="window.jQuery">
        </script>
        <script src="https://ajax.aspnetcdn.com/ajax/bootstrap/3.3.6/bootstrap.min.js"
                asp-fallback-src="~/lib/bootstrap/dist/js/bootstrap.min.js"
                asp-fallback-test="window.jQuery && window.jQuery.fn && window.jQuery.fn.modal">
        </script>
        <script src="~/js/site.min.js" asp-append-version="true"></script>
    </environment>

    @RenderSection("scripts", required: false)
</body>
</html>
```

No projeto vemos, dentro da pasta `Views` os arquivos `_ViewStart.cshtml` e `_ViewImports.cshtml`

Esses arquivos definem configurações comuns da `Views`.

O arquivo `_ViewStart.cshtml` tem a definição do layout padrão

```csharp
@{
    Layout = "_Layout";
}
```

O arquivo `_ViewImports.cshtml` tem a definição dos `using's` comuns

```csharp
@using UI.Web
@using UI.Web.Models
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers
```

## [Razor](https://docs.microsoft.com/pt-br/aspnet/core/mvc/razor-pages/?view=aspnetcore-2.0&tabs=visual-studio#razor-pages)

O `Razor` é uma engine de templates incorporada ao ASP.NET Core para criação de views.

Há uma mescla de código `HTML` e código `C#-Like` para criar uma visualização de conteúdo.


```html
<!--código omitido -->
<title>@ViewData["Title"] - WebApplication1</title>

<environment names="Development">
  <link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.css" />
  <link rel="stylesheet" href="~/css/site.css" />
</environment>
<environment names="Staging,Production">
  <link rel="stylesheet" href="https://ajax.aspnetcdn.com/ajax/bootstrap/3.3.6/css/bootstrap.min.css"
    asp-fallback-href="~/lib/bootstrap/dist/css/bootstrap.min.css"
    asp-fallback-test-class="sr-only" asp-fallback-test-property="position" asp-fallback-test-value="absolute" />
  <link rel="stylesheet" href="~/css/site.min.css" asp-append-version="true" />
  </environment>
</head>

<!--código omitido -->
<li><a asp-area="" asp-controller="Home" asp-action="Index">Home</a></li>
<li><a asp-area="" asp-controller="Home" asp-action="About">About</a></li>
<li><a asp-area="" asp-controller="Home" asp-action="Contact">Contact</a></li>
```

Para organização de código e melhoria em performance recomendo lerem o site [Browser Diet](https://browserdiet.com/pt/).

Muitos dos princípios apontados no sites são seguidos no template `MVC` do ASP.NET Core.

## [Partial views](https://docs.microsoft.com/pt-br/aspnet/core/mvc/views/partial?view=aspnetcore-2.0)

Uma exibição parcial é uma exibição renderizada dentro de outra exibição. A saída HTML gerada pela execução da exibição parcial é renderizada na exibição de chamada (ou pai). Assim como exibições, as exibições parciais usam a extensão de arquivo .cshtml.

Síncrono

```html
<!-- código de uma view -->
@Html.Partial("AuthorPartial")
```

Assíncrono

```html
<!-- código de uma view -->
@await Html.PartialAsync("AuthorPartial")
```

Passando dados

```html
@await Html.PartialAsync("PartialName", customViewData)
```

## View Fracamente Tipada

```csharp
public IActionResult About()
{
    ViewData["Message"] = "Your application description page.";

    ViewData["Address"] = new ViewModels.Address
    {
        Street = "One Microsoft Way",
        City = "Redmond",
        State = "WA",
        PostalCode = "98052-6399"
    };

    return View();
}
```

```html
@{
    ViewData["Title"] = "About";
}
<h2>@ViewData["Title"]</h2>
<h3>@ViewData["Message"]</h3>

<p>Alterado.</p>

@await Html.PartialAsync("_Address", @ViewData["Address"])
```

## View Fortemente Tipada

` UI.Web.ViewModels.Address.cs`

```csharp
namespace UI.Web.ViewModels
{
    public class Address
    {
        public string Street { get; set; }
        public string City { get; set; }

        public string State { get; set; }
        public string PostalCode { get; set; }
    }
}
```

`HomeController.cs`

```csharp
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";

    var address = new ViewModels.Address
    {
        Street = "One Microsoft Way",
        City = "Redmond",
        State = "WA",
        PostalCode = "98052-6399"
    };

    return View(address);
}
```

Utilizando com view fortemente tipada

`Views/Home/Contact.cs`

```html
@model UI.Web.ViewModels.Address

<h2>Contact</h2>
<address>
    @Model.Street<br>
    @Model.City, @Model.State @Model.PostalCode<br>
    <abbr title="Phone">P:</abbr> 425.555.0100
</address>
```

Utilizando com partial view

`Views/Home/Contact.cs`

```html
<--! código omitido -->
<h2>Contact</h2>
@await Html.PartialAsync("_Address", Model)
```