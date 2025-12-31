# Flutter Project Structure Reference

Based on [Flutter Project Structure by Andrea Bizzotto](https://codewithandrea.com/articles/flutter-project-structure/)

## Recommended: Feature-First Architecture

Use **feature-first** (layers inside features) for medium to large Flutter apps.

## The Four Architectural Layers

1. **Presentation**: widgets, states, and controllers
2. **Application**: services (orchestration logic)
3. **Domain**: models and business logic
4. **Data**: repositories, data sources, and DTOs

## Recommended Project Structure

```
lib/
├── src/
│   ├── common_widgets/          ← Shared UI components
│   ├── constants/               ← App-wide constants
│   ├── exceptions/              ← Exception definitions
│   ├── features/
│   │   ├── authentication/
│   │   │   ├── application/     ← Services
│   │   │   ├── data/            ← Repositories, data sources
│   │   │   ├── domain/          ← Models, business logic
│   │   │   └── presentation/    ← Widgets, screens, controllers
│   │   ├── cart/
│   │   │   ├── application/
│   │   │   ├── data/
│   │   │   ├── domain/
│   │   │   └── presentation/
│   │   ├── products/
│   │   │   ├── application/
│   │   │   ├── data/
│   │   │   ├── domain/
│   │   │   └── presentation/
│   │   │       ├── product_screen/    ← Sub-features if needed
│   │   │       └── products_list/
│   │   └── orders/
│   ├── localization/            ← Multi-language support
│   ├── routing/                 ← Navigation config
│   └── utils/                   ← Utility functions
```

## What Defines a Feature?

**Critical**: A feature is a **functional requirement** that helps the user complete a task—NOT individual screens.

Good feature examples:
- `authentication/` - Sign in, sign up, sign out
- `cart/` - Add to cart, view cart, update quantities
- `checkout/` - Payment, shipping, order confirmation
- `orders/` - View past orders, order details

Bad approach: One folder per screen (scatters related code).

## Layer Responsibilities

### Presentation Layer
Contains:
- Screen widgets
- Reusable feature-specific widgets
- Controllers (state management)
- UI state classes

Does NOT contain:
- API calls
- Business rules
- Data transformation

### Application Layer
Contains:
- Services that orchestrate domain/data operations
- Complex business workflows
- Feature-specific use cases

### Domain Layer
Contains:
- Model classes
- Business logic
- Validation rules
- Domain exceptions

Does NOT contain:
- UI code
- API/database code

### Data Layer
Contains:
- Repositories (data access abstraction)
- Data sources (API clients, local DB)
- DTOs (Data Transfer Objects)
- Data mappers

## Shared Code Guidelines

Top-level folders (`common_widgets/`, `utils/`, etc.) should contain **minimal** code.

If shared code grows large, reconsider:
- Should this be a feature?
- Are feature boundaries correct?

## Red Flags

1. **Screen-per-folder**: Creating `lib/screens/home/`, `lib/screens/profile/` scatters feature code
2. **Fat shared folders**: `common/` or `utils/` with 50+ files means features need refactoring
3. **Cross-layer imports**: Presentation importing directly from data layer
4. **Missing layers**: Feature has only `presentation/` with business logic in widgets

## Test Structure

Mirror the lib structure exactly:
```
test/
└── src/
    └── features/
        └── authentication/
            ├── application/
            ├── data/
            ├── domain/
            └── presentation/
```
