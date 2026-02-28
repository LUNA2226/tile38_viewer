FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src

# copiar todo o projeto
COPY . .

# entrar na pasta correta
WORKDIR /src/src/viewer

# restaurar
RUN dotnet restore tile38_viewer.csproj

# build
RUN dotnet build tile38_viewer.csproj -c Release

# publicar
RUN dotnet publish tile38_viewer.csproj -c Release -o /app/publish


# imagem final
FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /app

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "tile38_viewer.dll"]