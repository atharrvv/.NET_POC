# Build stage
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src

# Copy the csproj and restore dependencies
COPY ["TextEditor.csproj", "."]
RUN dotnet restore "TextEditor.csproj"

# Copy the rest of the project files
COPY . .

# Install the EF tools as a local tool
RUN dotnet new tool-manifest --force # Create tool manifest if it doesn't exist
RUN dotnet tool install dotnet-ef --version 7.0


# Clear NuGet cache (optional, in case of restore issues)
RUN dotnet nuget locals all --clear

# Build the project
RUN dotnet build "TextEditor.csproj" -c Release -o /app/build

# Publish the app
RUN dotnet publish "TextEditor.csproj" -c Release -o /app/publish

RUN dotnet tool restore

# Apply the migrations and update the database
RUN dotnet ef migrations add InitialCreate --project /src/TextEditor.csproj --startup-project /src/TextEditor.csproj
RUN dotnet ef database update --project /src/TextEditor.csproj --startup-project /src/TextEditor.csproj

# Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS final
WORKDIR /app

# Copy the published app from the build stage
COPY --from=build /app/publish .

# Define the entry point for the container
ENTRYPOINT ["dotnet", "TextEditor.dll"]
