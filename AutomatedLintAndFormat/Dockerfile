FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["AutomatedLintAndFormat/AutomatedLintAndFormat.csproj", "AutomatedLintAndFormat/"]
RUN dotnet restore "AutomatedLintAndFormat/AutomatedLintAndFormat.csproj"
COPY . .
WORKDIR "/src/AutomatedLintAndFormat"
RUN dotnet build "AutomatedLintAndFormat.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "AutomatedLintAndFormat.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "AutomatedLintAndFormat.dll"]
