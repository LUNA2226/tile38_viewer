# ===== BUILD =====
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copia tudo
COPY . .

# Mostra estrutura (debug definitivo)
RUN ls -R

# Publica automaticamente o único projeto encontrado
RUN dotnet publish -c Release -o /publish

# ===== RUNTIME =====
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "tile38_viewer.dll"]