# Settle Flutter UI/UX Architect

Skill for designing, refining, and generating production-ready Flutter Dart code for the Settle app — a premium personal debt & ledger manager. Use this skill when working on Settle's Flutter UI, design system, themes, or component architecture.

## When to Use

- Creating or refining Settle screens (Dashboard, Contacts, Contact Ledger, Debt Detail)
- Working with Settle's Flutter theme, design tokens, or component patterns
- Implementing Settle's macro-to-micro UX funnel
- Reviewing or generating Flutter code that must match Settle's design system

## App Context

Settle is a mobile FinTech app that helps individuals track money owed to them, manage contacts, send reminders, and record payments. The UX follows a strict macro-to-micro funnel: Dashboard (Home) → Contacts Directory → Contact Ledger → Debt Detail. The UI must feel clean, trustworthy, highly scannable, and comparable to apps like Revolut, Monzo, and Linear.

## Design Tokens (Flutter ThemeData)

Strictly use these hardcoded values in ThemeData and widget properties:

### Colors (ColorScheme)

| Token | Value | Usage |
|-------|-------|-------|
| `primary` | `Color(0xFF0F766E)` | Teal - Reserved for primary actions, active states, focus rings |
| `surface` | `Color(0xFFFFFFFF)` | Cards, inputs when focused |
| `background` | `Color(0xFFF7F9F8)` | App scaffold canvas |
| `inputBg` | `Color(0xFFF8FAFC)` | Soft filled inputs |
| `onSurface` | `Color(0xFF0F172A)` | Navy - Primary typography, avoids pure black |
| `onSurfaceMuted` | `Color(0xFF64748B)` | Blue-Gray - Labels, metadata |
| `success` | `Color(0xFF059669)` | Success states |
| `warning` | `Color(0xFFF59E0B)` | Warning states |
| `error` | `Color(0xFFDC2626)` | Error states |
| `outline` | `Color(0xFFE7ECEA)` | 1px borders on cards/inputs |

### Typography (TextTheme)

| Role | fontSize | fontWeight | color | letterSpacing |
|------|----------|------------|-------|---------------|
| Hero Balance | 42 | w800 | onSurface | -0.5 |
| Section Titles | 18 | w600 | onSurface | 0 |
| Card Titles / Names | 16 | w600 | onSurface | 0 |
| Body / Amounts | 15 | w500 (w700 for numbers) | onSurface | 0 |
| Micro Labels | 11 | w600 | onSurfaceMuted | 0.5 |

### Spacing & Radii

| Token | Value |
|-------|-------|
| Base Grid | 8-point system. Use 8.0, 16.0, 20.0, 24.0, 32.0 |
| Screen Padding | `EdgeInsets.symmetric(horizontal: 16.0)` |
| Section Gaps | `SizedBox(height: 24.0)` between major sections |
| Card Padding | `EdgeInsets.all(20.0)` |
| Card Radius | `BorderRadius.circular(24.0)` |
| Input/Button Radius | `BorderRadius.circular(14.0)` to `16.0` |
| Pill Radius | `BorderRadius.circular(100.0)` |

### Shadows (BoxShadow)

| Token | Color | blurRadius | offset |
|-------|-------|------------|--------|
| Soft Shadow (Cards) | `Color(0x0A0F172A)` | 12 | `Offset(0, 4)` |
| Button Shadow (Primary Actions) | `Color(0x400F766E)` | 24 | `Offset(0, 8)` |
| Focus Ring (Inputs) | `Color(0x1A0F766E)` | 0 | spreadRadius: 3 |

## Component Guidelines (Flutter Widgets)

### Navigation

**Top App Bar**: Use a custom Row inside SafeArea rather than default AppBar. Left: Back/Menu (40x40 Container with 12px radius). Center: Text title. Right: Overflow menu icon. No background color on the toolbar container.

**Bottom Navigation**: Scaffold's bottomNavigationBar or a Stack with a centered FloatingActionButton (FAB). FAB is the only global "Add" action.

### Surfaces & Cards

**Standard Card**: Container with decoration: `BoxDecoration(color: surface, border: Border.all(color: outline), borderRadius: BorderRadius.circular(24), boxShadow: [softShadow])`.

**Status Accent Card**: Use a Stack or Row with a `Container(width: 4, color: statusColor)` on the left edge of the card to indicate debt status (Red=Overdue, Orange=Partial, Green=Paid).

### Forms & Inputs

**Soft Filled Inputs**: `TextFormField` with `InputDecoration` using `fillColor: Color(0xFFF8FAFC), filled: true`.

**Borders**: `OutlineInputBorder(borderRadius: BorderRadius.circular(14.0), borderSide: BorderSide(color: outline))`. On focus, change border to primary and add a focus glow shadow to the container.

**Leading Icons**: Use `prefixIcon` in `InputDecoration` with 18x18 icons.

**Persistent Labels**: Use `labelText` in `InputDecoration` so it floats above the input, or place a Text widget directly above the `TextFormField`.

**Validation**: Change `fillColor` to pale red (`Color(0xFFFEF2F2)`) and `borderSide` to error when validation fails.

### Actions & Buttons

**Primary Action**: ElevatedButton or custom Container wrapped in GestureDetector. Style: 56px height, 16px radius, Teal bg, white text, Button Shadow. Place inside SafeArea at the bottom of the Scaffold body to remain visible during scrolling.

**Secondary Action**: TextButton or outlined Container next to the Primary Action.

**Disabled State**: Gray bg (`Color(0xFFCBD5E1)`), no shadow.

### Status & Feedback

**Chips/Pills**: Container with `BorderRadius.circular(100)`, semantic background tint (e.g., `Color(0xFFFEF2F2)` for Overdue), and semantic text color.

**Timelines**: Use a Column of Rows. Left side: Container dots connected by a vertical SizedBox line. Right side: Event details.

**Empty States**: DashedBorder container or simple Container with `Border.all(style: BorderStyle.solid, color: outline)`, an icon circle, friendly text, and a CTA button.

## UX & Interaction Principles

- **Macro to Micro**: Dashboard → Directory → Ledger → Detail.
- **Financial Hero**: The outstanding balance is always the largest visual element on the screen. Use Navy text (`onSurface`), not Teal, for financial figures.
- **Reduce Teal Usage**: Teal is strictly for primary actions, active states, and focus rings. Do not use teal for standard text or backgrounds.
- **Breathable Layouts**: Use generous whitespace (24.0 gaps) to create a premium feel. Avoid cramped lists.
- **Accessibility**: Minimum 44x44px touch targets. Color is never the only indicator of status (always pair with text/icon).
- **Keyboard Handling**: Wrap the Scaffold body in a `SingleChildScrollView` with `padding: EdgeInsets.only(bottom: MediaQuery.of(context).viewInsets.bottom)` to prevent keyboard overlap.

## Execution Prompt

When asked to create or refine a screen for the Settle app:

1. Output a complete, copy-pasteable Flutter Dart widget (e.g., `class DebtDetailScreen extends StatelessWidget`).
2. Use standard Flutter widgets (Container, Row, Column, Stack, SizedBox). Do not rely on external packages unless specifically asked (e.g., no get or flutter_bloc unless required).
3. Use inline SVG logic via Icon widgets or standard Material/Cupertino icons matching the Feather/Lucide style.
4. Ensure the layout is responsive but optimized for mobile constraints.
5. Include realistic mock data (Arabic/English names, SAR currency) directly in the widget to demonstrate visual hierarchy.
6. Provide a brief 2-3 sentence summary of the UX decisions made for that specific screen.

## Project Structure

This project follows a feature-based architecture:

- `lib/core/` - Shared widgets, theme, utilities
- `lib/features/` - Feature modules (dashboard, contacts, debts, activity, etc.)
- `lib/main.dart` - App entry point with GetX DI

## Key Files

- `lib/core/theme/app_theme.dart` - ThemeData with Settle design tokens
- `lib/core/theme/app_typography.dart` - Typography scale
- `lib/core/theme/finance_colors.dart` - Finance color roles
- `lib/core/widgets/` - Reusable Settle components
- `lib/features/dashboard/dashboard_screen.dart` - Home screen
- `lib/features/contacts/contacts_list_screen.dart` - Contacts directory
- `lib/features/contacts/contact_ledger_screen.dart` - Contact ledger
- `lib/features/debts/debt_detail_screen.dart` - Debt detail
