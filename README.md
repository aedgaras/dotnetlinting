# Project setup

## Installing and setting up Husky

1. Create new manifest file `dotnet new tool-manifest`.
2. Install Husky `dotnet tool install Husky`.
3. Create script for pre-commit stage `dotnet husky add pre-commit`.
4. Create script to access commit message `dotnet husky add commit-msg`.
5. Attach husky to your main project `dotnet husky attach <path-to-project-file>`.

## Setting up formaters and linters.

### Dotnet formater

1. Export `.Dotsettings` file into `.editorconfig` and store it inside root directory.
2. Add `dotnet format --verify-no-changes` command as a first command in `pre-commit`.

### XAML Styler

1. `dotnet tool install XamlStyler.Console`
2. `dotnet tool restore`
3. Add XAML Styler to your main project dependencies.
   `<Exec Command="dotnet tool install XamlStyler.Console" StandardOutputImportance="Low" StandardErrorImportance="High" WorkingDirectory=".." />`
4. Add contents for `pre-commit` from `.husky/pre-commit` line 7.

## Settings up commit message linter

1. Copy contents from `commit-msg` to your own `commit-msg`.
