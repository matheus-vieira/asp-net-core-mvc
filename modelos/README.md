# [Associação de Modelos](https://docs.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-2.1)

A associação de modelos (model binding) do .NET Core converte os dados recebidos em objetos que a controller consegue manipular.

Utilização padrão de rotas:

```csharp
public async Task<IActionResult> Login(LoginViewModel model, string returnUrl = null)
{
  // lógica
}
```

## Validação de modelos

Para validação o .NET Core dá suporte através da [validação de modelo](https://docs.microsoft.com/en-us/aspnet/core/mvc/models/validation?view=aspnetcore-2.1) decorando propriedades com atributos.

Esses atributos, além da validação no lado do servidor, são tranformados em validações no lado do cliente. Assim são validados antes de chegar à controller.

```csharp
using System.ComponentModel.DataAnnotations;

public class LoginViewModel
{
  [Required]
  [EmailAddress]
  public string Email { get; set; }

  [Required]
  [DataType(DataType.Password)]
  public string Password { get; set; }

  [Display(Name = "Remember me?")]
  public bool RememberMe { get; set; }
}
```

Ao chegar na controller apenas utilizamos `ModelState.IsValid` para verificar o objeto recebido.

```csharp
public async Task<IActionResult> Login(LoginViewModel model, string returnUrl = null)
{
  // Something wrong is not right
  if (!ModelState.IsValid)
    return View(model);

  // Validations has passed
  // continue with the logic
}
```

No lado do cliente é automaticamente gerado validações utilizando a [biblioteca de validação do jQuery](https://jqueryvalidation.org/).