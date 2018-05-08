# [Rotas](http://netcoders.com.br/aplicando-solid-com-c-srp/)

O ASP.NET Core MVC utiliza um sistema de [roteamento](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-2.1).

Esse roteamento mapeia URL's tornando-as amigáveis e pesquisáveis.

Facilita para o uso de [SEO (Search Engine Optimization)](https://marketingdeconteudo.com/o-que-e-seo/).

Utilização padrão de rotas:

```csharp
routes.MapRoute(
    name: "Default",
    template: "{controller=Home}/{action=Index}/{id?}"
);
```

Ao navegarmos para a url `http://localhost:5000`

![Home]({{ 'rotas/home.jpg | relative_url }})

Roteamento por atributo:

```csharp
[Route("api/[controller]")]
public class ProductsController : Controller
{
  [HttpGet("{id}")]
  public IActionResult GetProduct(int id)
  {
    ...
  }
}
```



A rota padrão diz que o formato da url deve ser:

`/<nome da controladora>/<nome da ação a ser executada>/<parâmetro opcional>`

Por exemplo ao criar um projeto do tipo MVC:

```bash
dotnet new mvc -o Route
```

e executá-lo:

```bash
dotnet run -p Route/Route.csproj
```

Ao navegarmos para a url `http://localhost:5000` vemos a página Home normalmente.

Caso alteramos a rota padrão no método `Configure` do arquivo `Startup.cs`, conforme abaixo

```csharp
app.UseMvc(routes =>
{
    routes.MapRoute(
        name: "default",
        template: "{controller=Products}/{action=Index}/{id?}");
});
```

Pare a execução anterior com `ctrl+c` e rode novamente

```bash
dotnet run -p Route/Route.csproj
```

Ao navegarmos para a url `http://localhost:5000` vemos a página de erro 404.

Porém se navegarmos para a url `http://localhost:5000/Home` vemos a página Home novamente.