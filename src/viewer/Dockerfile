FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# copiar tudo
COPY . .

# entrar na pasta do projeto
WORKDIR /src/src/viewer

# restaurar dependências
RUN dotnet restore tile38_viewer.csproj

# publicar
RUN dotnet publish tile38_viewer.csproj -c Release -o /app/publish

# imagem final
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "tile38_viewer.dll"]