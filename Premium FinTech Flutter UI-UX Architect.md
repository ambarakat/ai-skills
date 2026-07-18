# Premium FinTech Flutter UI/UX Architect

## Overview
**Premium FinTech Flutter UI/UX Architect** is a reusable AI skill for designing, refining, and generating production-ready Flutter/Dart code for premium FinTech, banking, crypto, and financial management applications.

Use this skill whenever working on Flutter UI, design systems, themes, component architecture, or UX flows that require a clean, trustworthy, highly scannable, and enterprise-quality experience.

---

# When to Use

Use this skill for:

- Creating or refining screens for FinTech, banking, crypto, or personal finance apps
- Designing Flutter themes and Design Systems
- Creating reusable Flutter UI components
- Building Dashboard → List → Detail UX funnels
- Reviewing Flutter code for design consistency
- Generating production-ready Flutter widgets
- Building premium financial applications comparable to Revolut, Monzo, Robinhood, and Linear

---

# App Context

This skill is intended for premium mobile financial applications.

The visual language should communicate:

- Trust
- Simplicity
- Precision
- Premium quality
- Strong visual hierarchy

The UX must always follow a Macro → Micro funnel:

Dashboard
→ Accounts / Contacts / Wallets
→ Ledger / Account Details
→ Transactions
→ Transaction Detail

Never overwhelm users with dense interfaces.

---

# Design Tokens

## Color Scheme

| Token | Value | Usage |
|--------|--------|------|
| primary | `Color(0xFF0F766E)` | Primary actions, active state, focus |
| surface | `Color(0xFFFFFFFF)` | Cards |
| background | `Color(0xFFF7F9F8)` | Scaffold |
| inputBg | `Color(0xFFF8FAFC)` | Inputs |
| onSurface | `Color(0xFF0F172A)` | Primary text |
| onSurfaceMuted | `Color(0xFF64748B)` | Labels & metadata |
| success | `Color(0xFF059669)` | Success |
| warning | `Color(0xFFF59E0B)` | Warning |
| error | `Color(0xFFDC2626)` | Error |
| outline | `Color(0xFFE7ECEA)` | Borders |

---

# Typography

| Role | Size | Weight | Color | Letter Spacing |
|------|------|--------|-------|----------------|
| Hero Balance | 42 | w800 | onSurface | -0.5 |
| Section Title | 18 | w600 | onSurface | 0 |
| Card Title | 16 | w600 | onSurface | 0 |
| Body | 15 | w500 (w700 numbers) | onSurface | 0 |
| Micro Label | 11 | w600 | onSurfaceMuted | 0.5 |

---

# Spacing

Base Grid

- 8
- 16
- 20
- 24
- 32

Screen Padding

```dart
EdgeInsets.symmetric(horizontal: 16)
```

Section Gap

```dart
SizedBox(height: 24)
```

Card Padding

```dart
EdgeInsets.all(20)
```

Card Radius

```dart
BorderRadius.circular(24)
```

Buttons & Inputs

```dart
BorderRadius.circular(14)
```

Pills

```dart
BorderRadius.circular(100)
```

---

# Shadows

## Card Shadow

```dart
BoxShadow(
  color: Color(0x0A0F172A),
  blurRadius: 12,
  offset: Offset(0,4),
)
```

## Button Shadow

```dart
BoxShadow(
  color: Color(0x400F766E),
  blurRadius: 24,
  offset: Offset(0,8),
)
```

## Focus Ring

```dart
BoxShadow(
  color: Color(0x1A0F766E),
  spreadRadius: 3,
)
```

---

# Component Guidelines

## Navigation

### App Bar

- SafeArea
- Custom Row
- No default AppBar
- Left: 40×40 button
- Center: title
- Right: overflow menu
- Transparent background

### Bottom Navigation

Use:

- `bottomNavigationBar`
- FloatingActionButton for global primary action

---

# Cards

## Standard Card

- White surface
- Outline border
- 24 radius
- Soft shadow

## Status Card

Add a 4px colored accent on the left.

Status colors:

- Green
- Orange
- Red

Never rely on color alone.

---

# Forms

Use:

```dart
TextFormField(
  decoration: InputDecoration(
    filled: true,
    fillColor: Color(0xFFF8FAFC),
  ),
)
```

Border

```dart
OutlineInputBorder(
  borderRadius: BorderRadius.circular(14),
)
```

Focused

- Primary border
- Focus glow

Validation

- Pale red fill
- Error border

---

# Buttons

## Primary

- Height: 56
- Radius: 16
- Background: Primary
- White text
- Button shadow

Place inside SafeArea at bottom.

## Secondary

Outlined button or TextButton.

## Disabled

Gray background

No shadow.

---

# Status Components

## Chips

Rounded pill

Semantic colors

Examples:

- Paid
- Pending
- Failed

---

## Timeline

Column of Rows

Left

- Dot
- Vertical line

Right

- Event
- Date
- Amount

---

## Empty State

- Icon
- Friendly text
- CTA button

---

# UX Principles

## Financial Hero

Largest element on screen.

Always use:

- onSurface

Never teal.

---

## Reduce Primary Usage

Teal is reserved for:

- CTA
- Active state
- Focus

Never body text.

---

## Breathing Space

Large spacing.

24px between sections.

Avoid dense layouts.

---

## Accessibility

Minimum tap target

44×44

Never rely solely on color.

Always pair:

- Icon
- Text
- Color

---

## Keyboard Handling

Wrap body in

```dart
SingleChildScrollView(
  padding: EdgeInsets.only(
    bottom: MediaQuery.of(context).viewInsets.bottom,
  ),
)
```

---

# Execution Prompt

Whenever asked to build or improve a FinTech screen:

1. Generate a complete copy-paste Flutter widget.
2. Use only standard Flutter widgets unless explicitly requested otherwise.
3. Use Material or Cupertino icons.
4. Keep the layout responsive and mobile-first.
5. Include realistic financial mock data.
6. Follow the design tokens exactly.
7. Follow the Macro → Micro UX hierarchy.
8. Return a short UX rationale (2–3 sentences).

---

# Recommended Project Structure

```
lib/
│
├── core/
│   ├── theme/
│   ├── widgets/
│   ├── utils/
│   └── constants/
│
├── features/
│   ├── dashboard/
│   ├── accounts/
│   ├── transactions/
│   ├── cards/
│   ├── analytics/
│   ├── profile/
│   └── settings/
│
└── main.dart
```

---

# Golden Rules

- Prioritize clarity over decoration.
- Financial figures must dominate the visual hierarchy.
- Maintain generous whitespace.
- Keep components reusable and consistent.
- Prefer composition over deeply nested widgets.
- Build production-ready, scalable Flutter code.
- Match the quality of top-tier FinTech apps such as Revolut, Monzo, Robinhood, and Linear.
