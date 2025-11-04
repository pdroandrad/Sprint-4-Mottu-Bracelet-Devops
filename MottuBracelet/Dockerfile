# Imagem base do .NET para rodar a aplicação
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 80
ENV ASPNETCORE_URLS=http://+:80

# Imagem para build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copia tudo e restaura dependências
COPY . .
RUN dotnet restore

# Publica a aplicação
RUN dotnet publish -c Release -o /app/publish

# Imagem final que vai rodar o app
FROM base AS final
WORKDIR /app
COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "MottuBracelet.dll"]
