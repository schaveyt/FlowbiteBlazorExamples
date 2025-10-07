# Repository Guidelines

## Project Structure & Module Organization
- `Pages/` Razor pages (e.g., `Pages/Home.razor`) — routable UI.
- `Layout/` shared layout components (navbar, sidebar, footer).
- `Components/` reusable components (e.g., `Components/AppVersion.razor`).
- `Services/` application services; `Domain/` POCO models (e.g., `Domain/Pokemon.cs`).
- `wwwroot/` static assets; `wwwroot/css/app.css` (Tailwind entry), `wwwroot/css/app.min.css` (built).
- Solution and project at root (`FlowbiteBlazorExamples.sln`, `FlowbiteBlazorExamples.csproj`); docs in `docs/`.

## Build, Test, and Development Commands
- `dotnet restore` — restore NuGet packages.
- `dotnet build` — build the solution.
- `dotnet run` — run the app (profiles in `Properties/launchSettings.json`).
- `dotnet watch` — hot reload during development.
- CSS: `tools/tailwindcss.exe -c tailwind.config.js -i wwwroot/css/app.css -o wwwroot/css/app.min.css --minify` — rebuild Tailwind.
- Optional (Node): `postcss wwwroot/css/app.css -o wwwroot/css/app.min.css` if PostCSS is installed.

## Coding Style & Naming Conventions
- C#: 4-space indent; braces on new line; favor expression-bodied members when clear.
- Naming: `PascalCase` types/properties; `camelCase` locals/params; `_camelCase` private fields.
- Razor: PascalCase component filenames; one component per file; extract logic to `.razor.cs` partials as it grows.
- CSS: Prefer Tailwind utilities; keep custom styles in `wwwroot/css/app.css`.

## Testing Guidelines
- No test project yet. If adding tests, use `xUnit` and `bUnit` for components.
- Name tests `<Thing>Tests.cs`; place under `tests/` and add to the solution.
- Run with `dotnet test`.

## Commit & Pull Request Guidelines
- Commits: small and focused; use Conventional Commits when possible (`feat:`, `fix:`, `docs:`).
- PRs: include purpose, screenshots for UI changes, linked issues, and manual test steps.
- Verify before PR: solution builds, Tailwind CSS compiled, no console errors.

## Security & Configuration Tips
- Don’t commit secrets; prefer environment variables or user secrets.
- When using dynamic Tailwind class names, update the `safelist` in `tailwind.config.js`.

## Markdown Formatting Rules
- Use fenced code blocks with triple backticks and a language hint.
- Prefer `sh` for shell commands; use `pwsh` only for Windows-specific PowerShell.
- Surround all fenced code blocks with a blank line before and after.
- Keep code blocks copy-paste friendly: no prompts like `$` or `PS>`.
- Use inline code ticks for commands, file paths, and identifiers.
- Avoid smart quotes or non-ASCII punctuation; use plain ASCII quotes and hyphens.
- Use `-` for list markers with a single space (e.g., `- item`).

## Razor Page Styling
- Prefer Tailwind CSS, especially Flowbite look and file.

## UI & Forms Conventions
- Pages & routing
  - Use PascalCase filenames (e.g., `Pages/Login.razor`) and lowercase routes (e.g., `@page "/login"`).
  - Include `<PageTitle>` per page for correct document titles.
  - Keep simple logic inline; move growing logic into `.razor.cs` partials.
- Navigation
  - Add new routes to `Layout/AppSidebar.razor` using `SidebarItem` with a clear label and appropriate Flowbite icon.
  - Maintain logical ordering (Home → examples → utilities); use `ArrowRightToBracketIcon` for auth-related links.
- Flowbite components
  - Wrap forms in `Card` for visual grouping; pair `Label` with `TextInput` using matching `For`/`Id`.
  - Buttons: `ButtonColor.Primary` for primary actions; `ButtonColor.Light` for secondary/social.
  - Icons: prefer Flowbite icons (`Flowbite.Icons`, `.Extended`) instead of raw SVGs; ensure `_Imports.razor` includes namespaces.
- Forms & validation
  - Use `EditForm` with `DataAnnotationsValidator` and `ValidationSummary`.
  - Bind to a small POCO model with `[Required]`, `[EmailAddress]`, etc.; use `OnValidSubmit` for handling.
  - For production logic, inject services under `Services/` instead of console stubs.
- Layout & styling
  - Center auth forms with Tailwind utilities, not custom CSS (e.g., `min-h-[calc(100vh-8rem)] flex items-center justify-center p-4`).
  - Keep custom CSS minimal and in `wwwroot/css/app.css`; prefer Tailwind + Flowbite utilities.
- Tailwind & build
  - After adding pages with new classes, rebuild CSS:
    `tools/tailwindcss.exe -c tailwind.config.js -i wwwroot/css/app.css -o wwwroot/css/app.min.css --minify`.
  - If using dynamic class names, update the `safelist` in `tailwind.config.js`.
- Accessibility
  - Ensure each `TextInput` has a corresponding `Label` via `Id`/`For`.
  - Use semantic headings and descriptive link text; add `aria-*` as needed.
