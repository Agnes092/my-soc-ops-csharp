# Project Guidelines

## Development Checklist
- **Lint**: Run `dotnet build` to check for warnings/errors
- **Build**: `cd SocOps && dotnet build` to compile
- **Test**: Manual verification (no unit tests; check component integration and localStorage persistence)

## Code Style
- Follow Blazor component patterns: PascalCase `.razor` files, `@inject` for services, `EventCallback<T>` for events
- Use custom CSS utilities from `wwwroot/css/app.css` (Tailwind-like classes: flex, gap-*, p-*, text-*, bg-*, etc.)
- Reference [.github/instructions/css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md) for styling practices
- Reference [.github/instructions/frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md) for design patterns

## Architecture
- Client-side Blazor WebAssembly app with no backend
- State managed in `BingoGameService` (scoped), pure logic in `BingoLogicService` (static)
- Components are stateless and presentational; all state changes via service events
- Game state persists to localStorage automatically

## Build and Test
- Run: `cd SocOps && dotnet run` (starts on http://localhost:5166)
- Build: `cd SocOps && dotnet build`
- Publish: `cd SocOps && dotnet publish -c Release`
- No unit tests present; verify changes manually

## Conventions
- Namespace: `SocOps.{Components|Services|Models|Data|Layout}`
- Immutability: Game logic returns new lists instead of mutating
- Event subscription: Implement `IDisposable` and unsubscribe in `Dispose()`
- localStorage key: `"bingo-game-state"` (version 1)

See [README.md](README.md) for setup and [workshop/GUIDE.md](workshop/GUIDE.md) for lab details.