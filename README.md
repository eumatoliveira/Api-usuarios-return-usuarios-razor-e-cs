# API de Cadastro Blazor

Este projeto é uma aplicação Blazor que consome uma API para listar usuários.

## Tecnologias Utilizadas

- Blazor
- .NET 6
- C#
- HTTP Client

## Pré-requisitos

- .NET 6 SDK: [Download .NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)

## Instalação

1. Clone o repositório:
   ```sh
   git clone https://github.com/eumatoliveira/Api-usuarios-return-usuarios-razor-e-cs.git
   ```
2. Navegue até o diretório do projeto:
   ```sh
   cd Api-usuarios-return-usuarios-razor-e-cs
   ```

## Construção e Execução

1. Restaure as dependências do projeto:
   ```sh
   dotnet restore
   ```

2. Compile o projeto:
   ```sh
   dotnet build
   ```

3. Execute o projeto:
   ```sh
   dotnet run
   ```

4. Abra o navegador e navegue até `https://localhost:5001/usuarios` para ver a lista de usuários.

## Estrutura do Código

O código principal está localizado no arquivo `Index.razor`:

```razor
@page "/usuarios"

<h3>Usuários</h3>

@if (usuarios == null)
{
    <p>Carregando...</p>
}
else
{
    <ul>
        @foreach (var user in usuarios)
        {
            <li>@user.Name - @user.Email</li>
        }
    </ul>
}

@code {
    private List<Usuario> usuarios;

    protected override async Task OnInitializedAsync()
    {
        var http = new HttpClient { BaseAddress = new Uri("https://jsonplaceholder.typicode.com") };
        usuarios = await http.GetFromJsonAsync<List<Usuario>>("users");
    }

    public class Usuario
    {
        public string Name { get; set; }
        public string Email { get; set; }
    }
}
```

## Contribuição

Sinta-se à vontade para abrir issues e pull requests para melhorias e correções.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
