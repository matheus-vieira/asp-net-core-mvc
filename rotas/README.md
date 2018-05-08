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