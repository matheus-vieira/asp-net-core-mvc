# Criando um Projeto

Como criar um projeto web com o framework da Microsoft.

## Utilizando o Visual Studio

### Novo Projeto

Após aberto o VS2017 acesse o menu Arquivo > Novo > Projeto (File > New > Project or CTRL + Shift + n);

Isso irá abrir a janela `Novo Projeto`.

Nessa janela selecione à esquerda `.NET Core` e no centro selecione `Aplicativo Web ASP.NET Core`.

No campo `Nome` informe o nome `UI.Web` e no campo `Nome da Solução` digite `UniOpet`.

![Novo Projeto]({{ 'assets/images/projeto/novo.png' | relative_url }})

### Tipo de Projeto

Após confirmar as alterações na janela `Novo Projeto` veremos a janela `Novo Aplicativo Web ASP.NET Core - UI.Web`.

Nesta janela confirmaremos, na parte superior, o Framework `.NET Core`  e a versão `ASP.NET Core 2.0`.

Logo abaixo marcamos a opção `Aplicativo WEB (Modelo-Exibição-Controlador)`.

Confirmamos que autenticação está com o texto `Sem Autenticação` e nem o suporte ao `Docker` está marcado.

![Tipo de Projeto]({{ 'assets/images/projeto/novo-tipo.png' | relative_url }})

## Através da linha de comando

Primeiro devemos criar e acessar uma pasta chamada `UniOpet`

```bash
mkdir UniOpet
```

```bash
cd UniOpet
```

O comando pode ser realizado de uma única vez:

```bash
mkdir UniOpet && cd UniOpet
```

Agora deve ser criado a solução

```bash
dotnet new sln
```

Saída

```bash
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
Getting ready...
The template "Solution File" was created successfully.
```

Nesse momento estamos prontos para criar o nosso projeto web:

```bash
dotnet new mvc -o UI.Web
```

Saída

```bash
The template "ASP.NET Core Web App (Model-View-Controller)" was created successfully.
This template contains technologies from parties other than Microsoft, see https://aka.ms/template-3pn for details.

Processing post-creation actions...
Running 'dotnet restore' on UI.Web/UI.Web.csproj...
  Restoring packages for /home/opet/UniOpet/UI.Web/UI.Web.csproj...
  Restoring packages for /home/opet/UniOpet/UI.Web/UI.Web.csproj...
  Restore completed in 20.35 sec for /home/opet/UniOpet/UI.Web/UI.Web.csproj.
  Generating MSBuild file /home/opet/UniOpet/UI.Web/obj/UI.Web.csproj.nuget.g.props.
  Generating MSBuild file /home/opet/UniOpet/UI.Web/obj/UI.Web.csproj.nuget.g.targets.
  Restore completed in 20.62 sec for /home/opet/UniOpet/UI.Web/UI.Web.csproj.


Restore succeeded.
```

Agora adicionamos o projeto criado à solução:

```bash
dotnet sln add UI.Web/UI.Web.csproj
```

Saída

```bash
Project `UI.Web/UI.Web.csproj` added to the solution.
```

[View]({{ 'projeto/view' | relative_url }})