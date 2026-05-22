FROM mcr.microsoft.com/dotnet/sdk:8.0 as build
WORKDIR /src

COPY . .
RUN dotnet restore "DevOpsProject/DevOpsProject.CommunicationControl.API.csproj"
RUN dotnet publish "DevOpsProject/DevOpsProject.CommunicationControl.API.csproj" -c Release -o /app/published

FROM mcr.microsoft.com/dotnet/aspnet:8.0 as runtime
WORKDIR /app

COPY --from=build /app/published .

USER app
EXPOSE 8080
ENTRYPOINT [ "dotnet", "DevOpsProject/DevOpsProject.CommunicationControl.API.dll" ]
