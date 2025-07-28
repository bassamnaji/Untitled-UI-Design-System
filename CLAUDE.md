# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

- `npm run storybook` - Start Storybook development server on port 6006
- `npm run build-storybook` - Build Storybook for production
- `npm run lint` - Run ESLint with auto-fix on components directory
- `npm run lint:check` - Run ESLint without fixing
- `npm run prettier` - Format code with Prettier
- `npm run prettier:check` - Check code formatting
- `npm run type-check` - Run TypeScript type checking
- `npm run test` - Run full test suite (type-check + lint:check + prettier:check)

## Architecture Overview

This is **Untitled UI React**, a component library built with:
- **React 19.1** with TypeScript 5.8
- **Tailwind CSS v4.1** for styling
- **React Aria Components** for accessibility
- **Storybook** for component development and documentation
- **Vite** for build tooling

### Project Structure

```
components/
├── base/           # Basic UI components (buttons, inputs, etc.)
├── application/    # Complex application components (navigation, tables, etc.)
├── foundations/    # Icons, logos, and fundamental design elements
├── shared-assets/  # Reusable assets (illustrations, patterns, etc.)
└── internal/       # Internal utilities for Storybook

hooks/              # Custom React hooks
utils/              # Utility functions
styles/             # Global CSS and theme definitions
```

### Component Architecture

Components follow a consistent pattern:
- **Component file** (e.g., `button.tsx`) - Main component implementation
- **Demo file** (e.g., `buttons.demo.tsx`) - Component usage examples
- **Story file** (e.g., `buttons.story.tsx`) - Storybook configuration

### Key Patterns

**Styling System:**
- Uses `sortCx()` utility for organizing Tailwind classes in style objects
- `cx()` function (from `@/utils/cx`) for conditional class merging with tailwind-merge
- Components use structured style objects with `common`, `sizes`, and `colors` variants

**Component Props:**
- TypeScript interfaces with comprehensive prop definitions
- Support for both button and link variants using discriminated unions
- React Aria Components integration for accessibility

**Import Aliases:**
- `@/` - Root directory
- `@/components/*` - Components directory
- `@/utils/*` - Utils directory  
- `@/hooks/*` - Hooks directory

### Technology Stack Details

**Styling:**
- Tailwind CSS v4.1 with custom theme in `styles/theme.css`
- Custom variants: `dark`, `label`, `focus-input-within`
- Custom utilities: `scrollbar-hide`, `transition-inherit-all`
- tailwindcss-react-aria-components plugin for React Aria integration

**Component Development:**
- React Aria Components for accessible UI primitives
- Motion library for animations
- Embla Carousel for carousel components
- Recharts for data visualization
- React Hook Form for form handling

**Development Tools:**
- ESLint with TypeScript, React, and accessibility rules
- Prettier for code formatting
- Storybook for component development and testing

## Code Conventions

- Use TypeScript with strict mode enabled
- Follow React Aria patterns for accessibility
- Prefer functional components with hooks
- Use `"use client"` directive for client-side components
- Import React types explicitly (e.g., `import type { FC } from "react"`)
- Use consistent file naming: kebab-case for files, PascalCase for components
- Organize imports: React imports first, then third-party, then local imports with `@/` aliases