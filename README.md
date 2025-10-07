# Flowbite Blazor Examples

A collection of example pages and components demonstrating the Flowbite Blazor component library � a set of Blazor components inspired by the look and feel of the Flowbite JavaScript UI library (similar in spirit to Flowbite React).

- Flowbite Blazor website: https://www.flowbite-blazor.org
- Flowbite (primary) website: https://flowbite.com

## Project Structure

- `Pages/` Razor pages (routable UI)
- `Layout/` shared layout components (navbar, sidebar, footer)
- `Components/` reusable components (e.g., `Components/AppVersion.razor`)
- `Services/` application services; `Domain/` POCO models (e.g., `Domain/Pokemon.cs`)
- `wwwroot/` static assets; `wwwroot/css/app.css` (Tailwind entry), `wwwroot/css/app.min.css` (built)
- Solution and project at root (`FlowbiteBlazorExamples.sln`, `FlowbiteBlazorExamples.csproj`); docs in `docs/`

## Quickstart

1. Restore and build

   ```sh
   dotnet restore
   dotnet build
   ```

2. Run the app

   ```sh
   dotnet run
   ```

   Then open http://localhost:5269/

3. Optional: enable Hot Reload during development

   ```sh
   dotnet watch
   ```

## Tailwind CSS

This repo uses Tailwind CSS for styling, matching Flowbite�s design language.

- Install Tailwind CLI (Mac/Linux example):

  ```sh
  mkdir ./tools && cd ./tools && \
    curl -sLO https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-macos-arm64 && \
    chmod +x tailwindcss-macos-arm64 && \
    mv tailwindcss-macos-arm64 tailwindcss
  ```

- Install Tailwind CLI (Windows example):

  ```sh
  mkdir ./tools -Force
  Invoke-WebRequest -Uri "https://github.com/tailwindlabs/tailwindcss/releases/latest/download/tailwindcss-windows-x64.exe" -OutFile "tools/tailwindcss.exe" -UseBasicParsing
  ```

- Build CSS:

  ```sh
  tools/tailwindcss.exe -c tailwind.config.js -i wwwroot/css/app.css -o wwwroot/css/app.min.css --minify
  ```

- Optional (Node):

  ```sh
  postcss wwwroot/css/app.css -o wwwroot/css/app.min.css
  ```

## Development

- Use `dotnet watch` for hot reload.
- Profiles are configured in `Properties/launchSettings.json`.
- Prefer Tailwind utilities; keep custom styles in `wwwroot/css/app.css`.

## Contributing

See `CONTRIBUTING.md` for local setup details, workflow, and guidelines (coding style, commits/PRs, and testing).

## Security

- Do not commit secrets; prefer environment variables or user secrets.
- When using dynamic Tailwind class names, update the `safelist` in `tailwind.config.js`.

## License

This repository contains examples for the Flowbite Blazor component library. Unless otherwise stated, content is provided for demonstration purposes.