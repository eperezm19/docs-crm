# Sistema de UI - Documentación

## Visión General

Este documento describe el proceso de creación y mantenimiento del sistema de UI para el proyecto. El sistema de UI será la base para mantener consistencia visual y mejorar la productividad del equipo de desarrollo.

## Arquitectura del Sistema de UI

### Estructura Propuesta

```
src/
├── app/                     # App router de Next.js
│   └── global.css/          # Archivo de configuracion tailwind css v4
├── features/                # Dominios de negocio (ej. dashboard, clientes, etc.)
├── shared/
│   └── ui-kit/              # UI System (librería visual base)
│       ├── components/      # Wrappers personalizados sobre shadcn/ui
│       │   ├── atoms/      # Componentes atómicos
│       │   │   ├── button/
│       │   │   │   ├── button.tsx
│       │   │   │   └── index.ts
│       │   │   ├── input/
│       │   │   └── icon/
│       │   ├── molecules/  # Componentes moleculares
│       │   │   ├── form-field/
│       │   │   ├── search-bar/
│       │   │   └── card/
│       │   ├── organisms/  # Componentes orgánicos
│       │   │   ├── header/
│       │   │   ├── sidebar/
│       │   │   └── data-table/
│       │   └── templates/  # Templates de páginas
│       │       ├── dashboard-layout/
│       │       └── auth-layout/
│       ├── primitives/     # Componentes base copiados desde shadcn/ui (no modificar)
│       └── stories/        # Documentación y testing de componentes
│           ├── atoms/      # Stories de componentes atómicos
│           │   ├── button/
│           │   │   ├── button.tsx
│           │   │   └── index.ts
│           │   ├── input/
│           │   └── icon/
│           ├── molecules/  # Stories de componentes moleculares
│           │   ├── form-field/
│           │   ├── search-bar/
│           │   └── card/
│           ├── organisms/  # Stories de componentes orgánicos
│           │   ├── header/
│           │   ├── sidebar/
│           │   └── data-table/
│           ├── templates/  # Stories de templates
│           │   ├── dashboard-layout/
│           │   └── auth-layout/
│           ├── examples/   # Ejemplos de uso y casos de estudio
│           │   ├── forms/
│           │   ├── dashboards/
│           │   └── workflows/
│           └── index.ts    # Barrel export de todas las stories
```

### Ejemplo de global.css

```css
@import "tailwindcss";

/* Tema base de shadcn/ui */
:root {
  --radius: 0.625rem;
  --background: oklch(1 0 0);
  --foreground: oklch(0.145 0 0);
  --card: oklch(1 0 0);
  --card-foreground: oklch(0.145 0 0);
  --popover: oklch(1 0 0);
  --popover-foreground: oklch(0.145 0 0);
  --primary: oklch(0.205 0 0);
  --primary-foreground: oklch(0.985 0 0);
  --secondary: oklch(0.97 0 0);
  --secondary-foreground: oklch(0.205 0 0);
  --muted: oklch(0.97 0 0);
  --muted-foreground: oklch(0.556 0 0);
  --accent: oklch(0.97 0 0);
  --accent-foreground: oklch(0.205 0 0);
  --destructive: oklch(0.577 0.245 27.325);
  --border: oklch(0.922 0 0);
  --input: oklch(0.922 0 0);
  --ring: oklch(0.708 0 0);
  --chart-1: oklch(0.646 0.222 41.116);
  --chart-2: oklch(0.6 0.118 184.704);
  --chart-3: oklch(0.398 0.07 227.392);
  --chart-4: oklch(0.828 0.189 84.429);
  --chart-5: oklch(0.769 0.188 70.08);
  --sidebar: oklch(0.985 0 0);
  --sidebar-foreground: oklch(0.145 0 0);
  --sidebar-primary: oklch(0.205 0 0);
  --sidebar-primary-foreground: oklch(0.985 0 0);
  --sidebar-accent: oklch(0.97 0 0);
  --sidebar-accent-foreground: oklch(0.205 0 0);
  --sidebar-border: oklch(0.922 0 0);
  --sidebar-ring: oklch(0.708 0 0);

  /* Tokens personalizados de Figma */
  --radius: 0.65rem;

  /* Neutral 1 */
  --neutral-bg-1-rest: #ffffff;
  --neutral-bg-1-pressed: #e0e0e0;
  --neutral-bg-1-selected: #ebebeb;

  /* Neutral 2 */
  --neutral-bg-2-rest: #ffffff;
  --neutral-bg-2-pressed: #e0e0e0;
  --neutral-bg-2-selected: #ebebeb;

  /* Neutral 3 */
  --neutral-bg-3-rest: #fafafa;
  --neutral-bg-3-pressed: #dbdbdb;
  --neutral-bg-3-selected: #e6e6e6;

  /* Neutral canvas */
  --neutral-bg-canvas-rest: #f5f5f5;

  /* Neutral disabled */
  --neutral-bg-disabled-rest: #e6e6e6;

  /* Neutral Foreground 1 */
  --neutral-foreground-1-rest: #242424;

  /* Neutral Foreground 2 */
  --neutral-foreground-2-rest: #616161;

  /* Neutral Foreground 3 */
  --neutral-foreground-3-rest: #808080;

  /* Neutral Foreground Disabled 1 */
  --neutral-foreground-disabled-1-rest: #bdbdbd;

  /* Neutral Stroke 1 */
  --neutral-stroke-1-rest: #d1d1d1;
  --neutral-stroke-1-pressed: #b3b3b3;

  /* Neutral Stroke Disabled */
  --neutral-stroke-disabled-rest: #e0e0e0;

  /* Brand Background 1 */
  --brand-bg-1-rest: #006dc4;
  --brand-bg-1-pressed: #0e4775;
  --brand-bg-1-selected: #0f548c;

  /* Brand Disabled */
  --brand-disabled: #cce7fd;

  /* Brand Foreground 1 */
  --brand-foreground-1-rest: #006dc4;
  --brand-foreground-1-pressed: #0e4775;
  --brand-foreground-1-selected: #0f548c;

  /* Brand Stroke 1 */
  --brand-stroke-1-rest: #006dc4;
  --brand-stroke-1-pressed: #0e4775;

  /* Content Tab */
  --content-tab-rest: #006dc4;
  --content-tab-pressed: #fafafa;

  /* Content Logo */
  --content-logo-rest: #479ef5;
  --content-logo-pressed: #000000;

  /* Content Button */
  --content-button-rest: #006dc4;
  --content-button-pressed: #0e4775;
  --content-button-selected: #0f548c;

  /* Status Red */
  --status-red: #dc2f02;
  --status-red-medium: #ea8267;
  --status-red-light: #fceae6;

  /* Status Warning */
  --status-warning: #fff9e6;
  --status-warning-medium: #ffdb66;
  --status-warning-light: #fff9e6;

  /* Status Success */
  --status-success: #38b000;
  --status-success-medium: #7dd057;
  --status-success-light: #d4f7c3;

  /* Colores extendidos */
  --warning: oklch(0.84 0.16 84);
  --warning-foreground: oklch(0.28 0.07 46);
}

.dark {
  --background: oklch(0.145 0 0);
  --foreground: oklch(0.985 0 0);
  --card: oklch(0.205 0 0);
  --card-foreground: oklch(0.985 0 0);
  --popover: oklch(0.269 0 0);
  --popover-foreground: oklch(0.985 0 0);
  --primary: oklch(0.922 0 0);
  --primary-foreground: oklch(0.205 0 0);
  --secondary: oklch(0.269 0 0);
  --secondary-foreground: oklch(0.985 0 0);
  --muted: oklch(0.269 0 0);
  --muted-foreground: oklch(0.708 0 0);
  --accent: oklch(0.371 0 0);
  --accent-foreground: oklch(0.985 0 0);
  --destructive: oklch(0.704 0.191 22.216);
  --border: oklch(1 0 0 / 10%);
  --input: oklch(1 0 0 / 15%);
  --ring: oklch(0.556 0 0);
  --chart-1: oklch(0.488 0.243 264.376);
  --chart-2: oklch(0.696 0.17 162.48);
  --chart-3: oklch(0.769 0.188 70.08);
  --chart-4: oklch(0.627 0.265 303.9);
  --chart-5: oklch(0.645 0.246 16.439);
  --sidebar: oklch(0.205 0 0);
  --sidebar-foreground: oklch(0.985 0 0);
  --sidebar-primary: oklch(0.488 0.243 264.376);
  --sidebar-primary-foreground: oklch(0.985 0 0);
  --sidebar-accent: oklch(0.269 0 0);
  --sidebar-accent-foreground: oklch(0.985 0 0);
  --sidebar-border: oklch(1 0 0 / 10%);
  --sidebar-ring: oklch(0.439 0 0);

  /* Tokens personalizados de Figma - Modo oscuro */
  /* Neutral 1 */
  --neutral-bg-1-rest: #000000;
  --neutral-bg-1-pressed: #2e2e2e;
  --neutral-bg-1-selected: #242424;

  /* Neutral 2 */
  --neutral-bg-2-rest: #1f1f1f;
  --neutral-bg-2-pressed: #4d4d4d;
  --neutral-bg-2-selected: #424242;

  /* Neutral 3 */
  --neutral-bg-3-rest: #333333;
  --neutral-bg-3-pressed: #616161;
  --neutral-bg-3-selected: #575757;

  /* Neutral canvas */
  --neutral-bg-canvas-rest: #141414;

  /* Neutral disabled */
  --neutral-bg-disabled-rest: #575757;

  /* Neutral Foreground 1 */
  --neutral-foreground-1-rest: #ffffff;

  /* Neutral Foreground 2 */
  --neutral-foreground-2-rest: #d6d6d6;

  /* Neutral Foreground 3 */
  --neutral-foreground-3-rest: #adadad;

  /* Neutral Foreground Disabled 1 */
  --neutral-foreground-disabled-1-rest: #5c5c5c;

  /* Neutral Stroke 1 */
  --neutral-stroke-1-rest: #4d4d4d;
  --neutral-stroke-1-pressed: #7a7a7a;

  /* Neutral Stroke Disabled */
  --neutral-stroke-disabled-rest: #424242;

  /* Brand Background 1 */
  --brand-bg-1-rest: #479ef5;
  --brand-bg-1-pressed: #96c6fa;
  --brand-bg-1-selected: #77b7f7;

  /* Brand Disabled */
  --brand-disabled: #003662;

  /* Brand Foreground 1 */
  --brand-foreground-1-rest: #479ef5;
  --brand-foreground-1-pressed: #96c6fa;
  --brand-foreground-1-selected: #77b7f7;

  /* Brand Stroke 1 */
  --brand-stroke-1-rest: #479ef5;
  --brand-stroke-1-pressed: #96c6fa;

  /* Content Tab */
  --content-tab-rest: #479ef5;
  --content-tab-pressed: #333333;

  /* Content Logo */
  --content-logo-rest: #479ef5;
  --content-logo-pressed: #333333;

  /* Content Button */
  --content-button-rest: #479ef5;
  --content-button-pressed: #96c6fa;
  --content-button-selected: #77b7f7;

  /* Status Red */
  --status-red: #dc2f02;
  --status-red-medium: #ea8267;
  --status-red-light: #fceae6;

  /* Status Warning */
  --status-warning: #fff9e6;
  --status-warning-medium: #ffdb66;
  --status-warning-light: #fff9e6;

  /* Status Success */
  --status-success: #38b000;
  --status-success-medium: #7dd057;
  --status-success-light: #d4f7c3;

  /* Colores extendidos - Modo oscuro */
  --warning: oklch(0.41 0.11 46);
  --warning-foreground: oklch(0.99 0.02 95);
}

/* Configuración de Tailwind CSS v4 */
@theme inline {
  /* Colores base de shadcn/ui */
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-popover: var(--popover);
  --color-popover-foreground: var(--popover-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-destructive: var(--destructive);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);

  /* Colores extendidos */
  --color-warning: var(--warning);
  --color-warning-foreground: var(--warning-foreground);

  /* Tokens personalizados de Figma */
  --color-neutral-bg-1-rest: var(--neutral-bg-1-rest);
  --color-neutral-bg-1-pressed: var(--neutral-bg-1-pressed);
  --color-neutral-bg-1-selected: var(--neutral-bg-1-selected);
  --color-neutral-bg-2-rest: var(--neutral-bg-2-rest);
  --color-neutral-bg-2-pressed: var(--neutral-bg-2-pressed);
  --color-neutral-bg-2-selected: var(--neutral-bg-2-selected);
  --color-neutral-bg-3-rest: var(--neutral-bg-3-rest);
  --color-neutral-bg-3-pressed: var(--neutral-bg-3-pressed);
  --color-neutral-bg-3-selected: var(--neutral-bg-3-selected);
  --color-neutral-bg-canvas-rest: var(--neutral-bg-canvas-rest);
  --color-neutral-bg-disabled-rest: var(--neutral-bg-disabled-rest);
  --color-neutral-foreground-1-rest: var(--neutral-foreground-1-rest);
  --color-neutral-foreground-2-rest: var(--neutral-foreground-2-rest);
  --color-neutral-foreground-3-rest: var(--neutral-foreground-3-rest);
  --color-neutral-foreground-disabled-1-rest: var(
    --neutral-foreground-disabled-1-rest
  );
  --color-neutral-stroke-1-rest: var(--neutral-stroke-1-rest);
  --color-neutral-stroke-1-pressed: var(--neutral-stroke-1-pressed);
  --color-neutral-stroke-disabled-rest: var(--neutral-stroke-disabled-rest);
  --color-brand-bg-1-rest: var(--brand-bg-1-rest);
  --color-brand-bg-1-pressed: var(--brand-bg-1-pressed);
  --color-brand-bg-1-selected: var(--brand-bg-1-selected);
  --color-brand-disabled: var(--brand-disabled);
  --color-brand-foreground-1-rest: var(--brand-foreground-1-rest);
  --color-brand-foreground-1-pressed: var(--brand-foreground-1-pressed);
  --color-brand-foreground-1-selected: var(--brand-foreground-1-selected);
  --color-brand-stroke-1-rest: var(--brand-stroke-1-rest);
  --color-brand-stroke-1-pressed: var(--brand-stroke-1-pressed);
  --color-content-tab-rest: var(--content-tab-rest);
  --color-content-tab-pressed: var(--content-tab-pressed);
  --color-content-logo-rest: var(--content-logo-rest);
  --color-content-logo-pressed: var(--content-logo-pressed);
  --color-content-button-rest: var(--content-button-rest);
  --color-content-button-pressed: var(--content-button-pressed);
  --color-content-button-selected: var(--content-button-selected);
  --color-status-red: var(--status-red);
  --color-status-red-medium: var(--status-red-medium);
  --color-status-red-light: var(--status-red-light);
  --color-status-warning: var(--status-warning);
  --color-status-warning-medium: var(--status-warning-medium);
  --color-status-warning-light: var(--status-warning-light);
  --color-status-success: var(--status-success);
  --color-status-success-medium: var(--status-success-medium);
  --color-status-success-light: var(--status-success-light);

  /* Border radius */
  --radius: var(--radius);
}

/* Estilos base */
* {
  @apply border-border;
}

body {
  @apply bg-background text-foreground;
}
```

## Tecnologías del Sistema de UI

### Core Technologies

- **Next.js 15** - Framework base
- **React 19** - Biblioteca de componentes
- **TypeScript** - Tipado estático
- **Tailwind CSS** - Framework de utilidades

### Componentes y Herramientas

- **Shadcn/ui** - Base de componentes
- **Radix UI** - Componentes primitivos accesibles
- **Framer Motion** - Animaciones
- **React Hook Form** - Manejo de formularios
- **Zod** - Validación de esquemas

### Herramientas de Desarrollo

- **Storybook** - Documentación y testing de componentes
- **Chromatic** - Visual testing
- **Figma** - Diseño y tokens

## Proceso de Desarrollo

### 1. Definición de Design Tokens

#### Colores

````

### Ejemplo de extensión de componentes shadcn/ui

#### Flujo de trabajo para extender componentes

1. **Instalar componente base de shadcn/ui**
```bash
npx shadcn@latest add button
````

2. **Crear wrapper personalizado en `shared/ui-kit/components/`**
3. **Extender con nuevas variantes y estilos personalizados**

#### Ejemplo: Button personalizado

**1. Componente base de shadcn/ui (en `shared/ui-kit/primitives/`)**

```tsx
// shared/ui-kit/primitives/button.tsx
import * as React from "react";
import { Slot } from "@radix-ui/react-slot";
import { cva, type VariantProps } from "class-variance-authority";
import { cn } from "@/lib/utils";

const buttonVariants = cva(
  "inline-flex items-center justify-center whitespace-nowrap rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive:
          "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        outline:
          "border border-input bg-background hover:bg-accent hover:text-accent-foreground",
        secondary:
          "bg-secondary text-secondary-foreground hover:bg-secondary/80",
        ghost: "hover:bg-accent hover:text-accent-foreground",
        link: "text-primary underline-offset-4 hover:underline",
      },
      size: {
        default: "h-10 px-4 py-2",
        sm: "h-9 rounded-md px-3",
        lg: "h-11 rounded-md px-8",
        icon: "h-10 w-10",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
);

export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {
  asChild?: boolean;
}

const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, asChild = false, ...props }, ref) => {
    const Comp = asChild ? Slot : "button";
    return (
      <Comp
        className={cn(buttonVariants({ variant, size, className }))}
        ref={ref}
        {...props}
      />
    );
  }
);
Button.displayName = "Button";

export { Button, buttonVariants };
```

**2. Wrapper personalizado con tokens de Figma**

```tsx
// shared/ui-kit/components/button.tsx
import * as React from "react";
import { cva, type VariantProps } from "class-variance-authority";
import { cn } from "@/lib/utils";
import {
  Button as ButtonPrimitive,
  buttonVariants,
} from "../primitives/button";

// Nuevas variantes personalizadas usando tokens de Figma
const customButtonVariants = cva(
  "inline-flex items-center justify-center whitespace-nowrap rounded-md text-sm font-medium transition-all duration-200 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50",
  {
    variants: {
      variant: {
        // Variantes base de shadcn/ui
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive:
          "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        outline:
          "border border-input bg-background hover:bg-accent hover:text-accent-foreground",
        secondary:
          "bg-secondary text-secondary-foreground hover:bg-secondary/80",
        ghost: "hover:bg-accent hover:text-accent-foreground",
        link: "text-primary underline-offset-4 hover:underline",

        // Nuevas variantes personalizadas usando tokens de Figma
        brand:
          "bg-brand-bg-1-rest text-brand-foreground-1-rest hover:bg-brand-bg-1-pressed active:bg-brand-bg-1-selected",
        brandOutline:
          "border border-brand-stroke-1-rest text-brand-foreground-1-rest hover:bg-brand-bg-1-rest hover:text-brand-foreground-1-rest",
        neutral:
          "bg-neutral-bg-1-rest text-neutral-foreground-1-rest hover:bg-neutral-bg-1-pressed active:bg-neutral-bg-1-selected",
        neutralSecondary:
          "bg-neutral-bg-2-rest text-neutral-foreground-1-rest hover:bg-neutral-bg-2-pressed active:bg-neutral-bg-2-selected",
        success: "bg-status-success text-white hover:bg-status-success-medium",
        warning:
          "bg-status-warning text-neutral-foreground-1-rest hover:bg-status-warning-medium",
        error: "bg-status-red text-white hover:bg-status-red-medium",
      },
      size: {
        // Tamaños base de shadcn/ui
        default: "h-10 px-4 py-2",
        sm: "h-9 rounded-md px-3",
        lg: "h-11 rounded-md px-8",
        icon: "h-10 w-10",

        // Nuevos tamaños personalizados
        xs: "h-7 rounded px-2 text-xs",
        xl: "h-12 rounded-lg px-10 text-base",
        "2xl": "h-14 rounded-lg px-12 text-lg",
      },
      state: {
        default: "",
        loading: "opacity-75 cursor-not-allowed",
        disabled:
          "opacity-50 cursor-not-allowed bg-neutral-bg-disabled-rest text-neutral-foreground-disabled-1-rest",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
      state: "default",
    },
  }
);

export interface CustomButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof customButtonVariants> {
  asChild?: boolean;
  loading?: boolean;
  leftIcon?: React.ReactNode;
  rightIcon?: React.ReactNode;
}

const CustomButton = React.forwardRef<HTMLButtonElement, CustomButtonProps>(
  (
    {
      className,
      variant,
      size,
      state,
      loading = false,
      leftIcon,
      rightIcon,
      children,
      disabled,
      asChild = false,
      ...props
    },
    ref
  ) => {
    const Comp = asChild ? Slot : "button";

    // Determinar el estado del botón
    const buttonState = loading
      ? "loading"
      : disabled
      ? "disabled"
      : state || "default";

    return (
      <Comp
        className={cn(
          customButtonVariants({ variant, size, state: buttonState, className })
        )}
        ref={ref}
        disabled={disabled || loading}
        {...props}
      >
        {loading && (
          <svg
            className="animate-spin -ml-1 mr-2 h-4 w-4"
            fill="none"
            viewBox="0 0 24 24"
          >
            <circle
              className="opacity-25"
              cx="12"
              cy="12"
              r="10"
              stroke="currentColor"
              strokeWidth="4"
            />
            <path
              className="opacity-75"
              fill="currentColor"
              d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
            />
          </svg>
        )}
        {!loading && leftIcon && <span className="mr-2">{leftIcon}</span>}
        {children}
        {!loading && rightIcon && <span className="ml-2">{rightIcon}</span>}
      </Comp>
    );
  }
);
CustomButton.displayName = "CustomButton";

export { CustomButton, customButtonVariants };
```

**3. Ejemplo de uso en features**

```tsx
// features/dashboard/components/dashboard-button.tsx
import { CustomButton } from "@/shared/ui-kit/components/button";
import { PlusIcon, ArrowRightIcon } from "lucide-react";

export function DashboardButton() {
  return (
    <div className="space-y-4">
      {/* Botón con variante personalizada */}
      <CustomButton variant="brand" size="lg">
        Crear nuevo cliente
      </CustomButton>

      {/* Botón con iconos */}
      <CustomButton
        variant="brandOutline"
        leftIcon={<PlusIcon className="h-4 w-4" />}
        rightIcon={<ArrowRightIcon className="h-4 w-4" />}
      >
        Agregar elemento
      </CustomButton>

      {/* Botón con estado de carga */}
      <CustomButton variant="success" loading={true}>
        Guardando...
      </CustomButton>

      {/* Botón neutral */}
      <CustomButton variant="neutral" size="sm">
        Cancelar
      </CustomButton>
    </div>
  );
}
```

**4. Barrel export en `shared/ui-kit/index.ts`**

```tsx
// shared/ui-kit/index.ts
export { CustomButton } from "./components/button";
export { Button as ButtonPrimitive } from "./primitives/button";

// Re-exportar otros componentes personalizados
export { CustomInput } from "./components/input";
export { CustomCard } from "./components/card";
// ... más exports
```

#### Ventajas de este enfoque:

1. **Separación clara**: Componentes primitivos sin modificar vs wrappers personalizados
2. **Reutilización**: Los wrappers pueden usar múltiples primitivos
3. **Consistencia**: Tokens de diseño aplicados uniformemente
4. **Flexibilidad**: Nuevas variantes sin afectar componentes base
5. **Mantenibilidad**: Fácil actualización de shadcn/ui sin perder personalizaciones

#### Flujo de trabajo recomendado:

1. `npx shadcn@latest add [component]` → Se instala en `primitives/`
2. Crear wrapper en `components/` con nuevas variantes
3. Usar el wrapper personalizado en features
4. Mantener primitivos sin modificar para actualizaciones

### Documentación con Storybook

#### Configuración de Storybook para Atomic Design

**1. Estructura de carpetas siguiendo Atomic Design**

```
src/
├── app/                     # App router de Next.js
│   └── global.css/          # Archivo de configuracion tailwind css v4
├── features/                # Dominios de negocio (ej. dashboard, clientes, etc.)
├── shared/
│   └── ui-kit/              # UI System (librería visual base)
│       ├── components/      # Wrappers personalizados sobre shadcn/ui
│       │   ├── atoms/      # Componentes atómicos
│       │   │   ├── button/
│       │   │   │   ├── button.tsx
│       │   │   │   └── index.ts
│       │   │   ├── input/
│       │   │   └── icon/
│       │   ├── molecules/  # Componentes moleculares
│       │   │   ├── form-field/
│       │   │   ├── search-bar/
│       │   │   └── card/
│       │   ├── organisms/  # Componentes orgánicos
│       │   │   ├── header/
│       │   │   ├── sidebar/
│       │   │   └── data-table/
│       │   └── templates/  # Templates de páginas
│       │       ├── dashboard-layout/
│       │       └── auth-layout/
│       ├── primitives/     # Componentes base copiados desde shadcn/ui (no modificar)
│       └── stories/        # Documentación y testing de componentes
│           ├── atoms/      # Stories de componentes atómicos
│           │   ├── button/
│           │   │   ├── button.tsx
│           │   │   └── index.ts
│           │   ├── input/
│           │   └── icon/
│           ├── molecules/  # Stories de componentes moleculares
│           │   ├── form-field/
│           │   ├── search-bar/
│           │   └── card/
│           ├── organisms/  # Stories de componentes orgánicos
│           │   ├── header/
│           │   ├── sidebar/
│           │   └── data-table/
│           ├── templates/  # Stories de templates
│           │   ├── dashboard-layout/
│           │   └── auth-layout/
│           ├── examples/   # Ejemplos de uso y casos de estudio
│           │   ├── forms/
│           │   ├── dashboards/
│           │   └── workflows/
│           └── index.ts    # Barrel export de todas las stories
```

**2. Configuración de Storybook**

```js
// .storybook/main.ts
import type { StorybookConfig } from "@storybook/nextjs";

const config: StorybookConfig = {
  stories: [
    "../src/shared/ui-kit/stories/**/*.stories.@(js|jsx|mjs|ts|tsx)",
    "../src/shared/ui-kit/stories/**/*.mdx",
  ],
  addons: [
    "@storybook/addon-links",
    "@storybook/addon-essentials",
    "@storybook/addon-onboarding",
    "@storybook/addon-interactions",
    "@storybook/addon-themes",
    "@storybook/addon-a11y",
    "@storybook/addon-viewport",
  ],
  framework: {
    name: "@storybook/nextjs",
    options: {},
  },
  docs: {
    autodocs: "tag",
  },
  staticDirs: ["../public"],
};

export default config;
```

**3. Ejemplo de Story para Button (Atomic Design - Atoms)**

```tsx
// src/shared/ui-kit/stories/atoms/button.stories.tsx
import type { Meta, StoryObj } from "@storybook/react";
import { CustomButton } from "../../components/atoms/button/button";

const meta: Meta<typeof CustomButton> = {
  title: "Design System/Atoms/Button",
  component: CustomButton,
  parameters: {
    layout: "centered",
    docs: {
      description: {
        component: `
## CustomButton Component

Un botón personalizado que extiende shadcn/ui con tokens de diseño de Figma.

### Características:
- **Variantes**: default, brand, neutral, success, warning, error
- **Tamaños**: xs, sm, default, lg, xl, 2xl
- **Estados**: loading, disabled
- **Iconos**: leftIcon, rightIcon
- **Accesibilidad**: Compatible con ARIA

### Uso:
\`\`\`tsx
import { CustomButton } from "@/shared/ui-kit/components/atoms/button";

<CustomButton variant="brand" size="lg">
  Crear cliente
</CustomButton>
\`\`\`
        `,
      },
    },
  },
  argTypes: {
    variant: {
      control: { type: "select" },
      options: [
        "default",
        "destructive",
        "outline",
        "secondary",
        "ghost",
        "link",
        "brand",
        "brandOutline",
        "neutral",
        "neutralSecondary",
        "success",
        "warning",
        "error",
      ],
      description: "Variante visual del botón",
    },
    size: {
      control: { type: "select" },
      options: ["xs", "sm", "default", "lg", "xl", "2xl", "icon"],
      description: "Tamaño del botón",
    },
    state: {
      control: { type: "select" },
      options: ["default", "loading", "disabled"],
      description: "Estado del botón",
    },
    loading: {
      control: { type: "boolean" },
      description: "Muestra spinner de carga",
    },
    disabled: {
      control: { type: "boolean" },
      description: "Deshabilita el botón",
    },
    leftIcon: {
      control: { type: "boolean" },
      description: "Muestra icono a la izquierda",
    },
    rightIcon: {
      control: { type: "boolean" },
      description: "Muestra icono a la derecha",
    },
  },
  tags: ["autodocs"],
};

export default meta;
type Story = StoryObj<typeof meta>;

// Story base
export const Default: Story = {
  args: {
    children: "Button",
    variant: "default",
    size: "default",
  },
};

// Story con todas las variantes
export const Variants: Story = {
  render: () => (
    <div className="flex flex-wrap gap-4">
      <CustomButton variant="default">Default</CustomButton>
      <CustomButton variant="brand">Brand</CustomButton>
      <CustomButton variant="brandOutline">Brand Outline</CustomButton>
      <CustomButton variant="neutral">Neutral</CustomButton>
      <CustomButton variant="neutralSecondary">Neutral Secondary</CustomButton>
      <CustomButton variant="success">Success</CustomButton>
      <CustomButton variant="warning">Warning</CustomButton>
      <CustomButton variant="error">Error</CustomButton>
    </div>
  ),
  parameters: {
    docs: {
      description: {
        story: "Todas las variantes disponibles del botón personalizado.",
      },
    },
  },
};

// Story con todos los tamaños
export const Sizes: Story = {
  render: () => (
    <div className="flex items-center gap-4">
      <CustomButton variant="brand" size="xs">
        XS
      </CustomButton>
      <CustomButton variant="brand" size="sm">
        SM
      </CustomButton>
      <CustomButton variant="brand" size="default">
        Default
      </CustomButton>
      <CustomButton variant="brand" size="lg">
        LG
      </CustomButton>
      <CustomButton variant="brand" size="xl">
        XL
      </CustomButton>
      <CustomButton variant="brand" size="2xl">
        2XL
      </CustomButton>
    </div>
  ),
  parameters: {
    docs: {
      description: {
        story: "Diferentes tamaños disponibles para el botón.",
      },
    },
  },
};

// Story con estados
export const States: Story = {
  render: () => (
    <div className="flex flex-wrap gap-4">
      <CustomButton variant="brand">Normal</CustomButton>
      <CustomButton variant="brand" loading={true}>
        Loading
      </CustomButton>
      <CustomButton variant="brand" disabled={true}>
        Disabled
      </CustomButton>
    </div>
  ),
  parameters: {
    docs: {
      description: {
        story: "Estados del botón: normal, cargando y deshabilitado.",
      },
    },
  },
};

// Story con iconos
export const WithIcons: Story = {
  render: () => (
    <div className="flex flex-wrap gap-4">
      <CustomButton variant="brand" leftIcon={<PlusIcon className="h-4 w-4" />}>
        Agregar
      </CustomButton>
      <CustomButton
        variant="brandOutline"
        rightIcon={<ArrowRightIcon className="h-4 w-4" />}
      >
        Continuar
      </CustomButton>
      <CustomButton
        variant="neutral"
        leftIcon={<SearchIcon className="h-4 w-4" />}
        rightIcon={<FilterIcon className="h-4 w-4" />}
      >
        Buscar
      </CustomButton>
    </div>
  ),
  parameters: {
    docs: {
      description: {
        story: "Botones con iconos a la izquierda, derecha o ambos lados.",
      },
    },
  },
};

// Story interactivo
export const Interactive: Story = {
  args: {
    children: "Click me",
    variant: "brand",
    size: "default",
  },
  play: async ({ canvasElement }) => {
    const canvas = within(canvasElement);
    const button = canvas.getByRole("button");
    await userEvent.click(button);
  },
};
```

**4. Ejemplo de Story para FormField (Atomic Design - Molecules)**

```tsx
// src/shared/ui-kit/stories/molecules/form-field.stories.tsx
import type { Meta, StoryObj } from "@storybook/react";
import { FormField } from "../../components/molecules/form-field/form-field";
import { CustomInput } from "../../components/atoms/input/input";
import { CustomButton } from "../../components/atoms/button/button";

const meta: Meta<typeof FormField> = {
  title: "Design System/Molecules/FormField",
  component: FormField,
  parameters: {
    layout: "padded",
    docs: {
      description: {
        component: `
## FormField Component

Un campo de formulario que combina label, input y mensaje de error.

### Características:
- **Label**: Etiqueta descriptiva
- **Input**: Campo de entrada personalizado
- **Error**: Mensaje de error opcional
- **Required**: Indicador de campo requerido
- **Help Text**: Texto de ayuda opcional

### Uso:
\`\`\`tsx
import { FormField } from "@/shared/ui-kit/components/molecules/form-field";

<FormField
  label="Email"
  required
  error="Email inválido"
  helpText="Ingresa tu email corporativo"
>
  <CustomInput type="email" placeholder="ejemplo@empresa.com" />
</FormField>
\`\`\`
        `,
      },
    },
  },
  argTypes: {
    label: {
      control: { type: "text" },
      description: "Etiqueta del campo",
    },
    required: {
      control: { type: "boolean" },
      description: "Indica si el campo es requerido",
    },
    error: {
      control: { type: "text" },
      description: "Mensaje de error",
    },
    helpText: {
      control: { type: "text" },
      description: "Texto de ayuda",
    },
  },
  tags: ["autodocs"],
};

export default meta;
type Story = StoryObj<typeof meta>;

export const Default: Story = {
  render: (args) => (
    <FormField {...args}>
      <CustomInput placeholder="Ingresa tu nombre" />
    </FormField>
  ),
  args: {
    label: "Nombre",
    required: false,
  },
};

export const WithError: Story = {
  render: (args) => (
    <FormField {...args}>
      <CustomInput placeholder="Ingresa tu email" />
    </FormField>
  ),
  args: {
    label: "Email",
    required: true,
    error: "Email inválido",
  },
};

export const WithHelpText: Story = {
  render: (args) => (
    <FormField {...args}>
      <CustomInput placeholder="Ingresa tu contraseña" type="password" />
    </FormField>
  ),
  args: {
    label: "Contraseña",
    required: true,
    helpText: "Mínimo 8 caracteres, incluir mayúsculas y números",
  },
};

export const FormExample: Story = {
  render: () => (
    <form className="space-y-4 max-w-md">
      <FormField label="Nombre completo" required>
        <CustomInput placeholder="Juan Pérez" />
      </FormField>

      <FormField
        label="Email"
        required
        error="Email inválido"
        helpText="Usa tu email corporativo"
      >
        <CustomInput type="email" placeholder="juan@empresa.com" />
      </FormField>

      <FormField label="Teléfono">
        <CustomInput placeholder="+1 (555) 123-4567" />
      </FormField>

      <div className="flex gap-2">
        <CustomButton variant="brand" type="submit">
          Guardar
        </CustomButton>
        <CustomButton variant="neutral" type="button">
          Cancelar
        </CustomButton>
      </div>
    </form>
  ),
  parameters: {
    docs: {
      description: {
        story: "Ejemplo completo de un formulario usando FormField.",
      },
    },
  },
};
```

**5. Ejemplo de Story para DataTable (Atomic Design - Organisms)**

```tsx
// src/shared/ui-kit/stories/organisms/data-table.stories.tsx
import type { Meta, StoryObj } from "@storybook/react";
import { DataTable } from "../../components/organisms/data-table/data-table";
import { CustomButton } from "../../components/atoms/button/button";
import { PlusIcon, SearchIcon, FilterIcon } from "lucide-react";

const meta: Meta<typeof DataTable> = {
  title: "Design System/Organisms/DataTable",
  component: DataTable,
  parameters: {
    layout: "padded",
    docs: {
      description: {
        component: `
## DataTable Component

Una tabla de datos completa con búsqueda, filtros, paginación y acciones.

### Características:
- **Búsqueda**: Filtrado por texto
- **Filtros**: Filtros avanzados
- **Paginación**: Navegación entre páginas
- **Acciones**: Botones de acción por fila
- **Responsive**: Adaptable a diferentes pantallas
- **Accesibilidad**: Compatible con lectores de pantalla

### Uso:
\`\`\`tsx
import { DataTable } from "@/shared/ui-kit/components/organisms/data-table";

<DataTable
  data={clientes}
  columns={columnas}
  searchPlaceholder="Buscar clientes..."
  onAdd={() => console.log("Agregar cliente")}
/>
\`\`\`
        `,
      },
    },
  },
  argTypes: {
    data: {
      control: { type: "object" },
      description: "Datos de la tabla",
    },
    columns: {
      control: { type: "object" },
      description: "Configuración de columnas",
    },
    searchPlaceholder: {
      control: { type: "text" },
      description: "Placeholder del campo de búsqueda",
    },
    showFilters: {
      control: { type: "boolean" },
      description: "Muestra panel de filtros",
    },
    showPagination: {
      control: { type: "boolean" },
      description: "Muestra paginación",
    },
  },
  tags: ["autodocs"],
};

export default meta;
type Story = StoryObj<typeof meta>;

// Datos de ejemplo
const sampleData = [
  {
    id: 1,
    name: "Juan Pérez",
    email: "juan@empresa.com",
    company: "TechCorp",
    status: "active",
    lastContact: "2024-01-15",
  },
  {
    id: 2,
    name: "María García",
    email: "maria@startup.com",
    company: "StartupXYZ",
    status: "inactive",
    lastContact: "2024-01-10",
  },
  {
    id: 3,
    name: "Carlos López",
    email: "carlos@consulting.com",
    company: "ConsultingPro",
    status: "active",
    lastContact: "2024-01-20",
  },
];

const sampleColumns = [
  {
    key: "name",
    label: "Nombre",
    sortable: true,
  },
  {
    key: "email",
    label: "Email",
    sortable: true,
  },
  {
    key: "company",
    label: "Empresa",
    sortable: true,
  },
  {
    key: "status",
    label: "Estado",
    render: (value: string) => (
      <span
        className={`px-2 py-1 rounded-full text-xs ${
          value === "active"
            ? "bg-status-success-light text-status-success"
            : "bg-status-red-light text-status-red"
        }`}
      >
        {value === "active" ? "Activo" : "Inactivo"}
      </span>
    ),
  },
  {
    key: "lastContact",
    label: "Último contacto",
    sortable: true,
  },
  {
    key: "actions",
    label: "Acciones",
    render: (_, row) => (
      <div className="flex gap-2">
        <CustomButton variant="neutral" size="sm">
          Editar
        </CustomButton>
        <CustomButton variant="error" size="sm">
          Eliminar
        </CustomButton>
      </div>
    ),
  },
];

export const Default: Story = {
  args: {
    data: sampleData,
    columns: sampleColumns,
    searchPlaceholder: "Buscar clientes...",
    showFilters: true,
    showPagination: true,
  },
};

export const WithoutFilters: Story = {
  args: {
    data: sampleData,
    columns: sampleColumns,
    searchPlaceholder: "Buscar clientes...",
    showFilters: false,
    showPagination: true,
  },
};

export const EmptyState: Story = {
  args: {
    data: [],
    columns: sampleColumns,
    searchPlaceholder: "Buscar clientes...",
    showFilters: true,
    showPagination: false,
  },
  parameters: {
    docs: {
      description: {
        story: "Estado cuando no hay datos disponibles.",
      },
    },
  },
};

export const LoadingState: Story = {
  args: {
    data: [],
    columns: sampleColumns,
    searchPlaceholder: "Buscar clientes...",
    loading: true,
  },
  parameters: {
    docs: {
      description: {
        story: "Estado de carga mientras se obtienen los datos.",
      },
    },
  },
};
```

**6. Ejemplo de Story para Casos de Uso (Examples)**

```tsx
// src/shared/ui-kit/stories/examples/forms.stories.tsx
import type { Meta, StoryObj } from "@storybook/react";
import { FormField } from "../../components/molecules/form-field/form-field";
import { CustomInput } from "../../components/atoms/input/input";
import { CustomButton } from "../../components/atoms/button/button";

const meta: Meta = {
  title: "Design System/Examples/Forms",
  parameters: {
    layout: "padded",
    docs: {
      description: {
        component: `
## Formularios de Ejemplo

Casos de uso reales de formularios en el CRM.

### Tipos de formularios:
- **Registro de cliente**: Formulario completo de registro
- **Edición de perfil**: Formulario de actualización
- **Búsqueda avanzada**: Formulario con filtros
- **Configuración**: Formulario de preferencias
        `,
      },
    },
  },
  tags: ["autodocs"],
};

export default meta;
type Story = StoryObj<typeof meta>;

export const ClientRegistration: Story = {
  render: () => (
    <div className="max-w-2xl mx-auto p-6 bg-neutral-bg-1-rest rounded-lg">
      <h2 className="text-2xl font-bold mb-6 text-neutral-foreground-1-rest">
        Registro de Cliente
      </h2>

      <form className="space-y-6">
        <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
          <FormField label="Nombre" required>
            <CustomInput placeholder="Juan" />
          </FormField>

          <FormField label="Apellido" required>
            <CustomInput placeholder="Pérez" />
          </FormField>
        </div>

        <FormField
          label="Email"
          required
          helpText="Email corporativo del cliente"
        >
          <CustomInput type="email" placeholder="juan@empresa.com" />
        </FormField>

        <FormField label="Empresa" required>
          <CustomInput placeholder="TechCorp Inc." />
        </FormField>

        <FormField label="Teléfono">
          <CustomInput placeholder="+1 (555) 123-4567" />
        </FormField>

        <FormField
          label="Notas"
          helpText="Información adicional sobre el cliente"
        >
          <textarea
            className="w-full p-3 border border-neutral-stroke-1-rest rounded-md"
            rows={3}
            placeholder="Observaciones importantes..."
          />
        </FormField>

        <div className="flex gap-3 pt-4">
          <CustomButton variant="brand" type="submit">
            Guardar Cliente
          </CustomButton>
          <CustomButton variant="neutral" type="button">
            Cancelar
          </CustomButton>
        </div>
      </form>
    </div>
  ),
  parameters: {
    docs: {
      description: {
        story: "Formulario completo para registro de nuevos clientes.",
      },
    },
  },
};

export const AdvancedSearch: Story = {
  render: () => (
    <div className="max-w-4xl mx-auto p-6 bg-neutral-bg-2-rest rounded-lg">
      <h2 className="text-xl font-semibold mb-4 text-neutral-foreground-1-rest">
        Búsqueda Avanzada
      </h2>

      <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
        <FormField label="Nombre o Email">
          <CustomInput placeholder="Buscar por nombre o email..." />
        </FormField>

        <FormField label="Empresa">
          <CustomInput placeholder="Filtrar por empresa" />
        </FormField>

        <FormField label="Estado">
          <select className="w-full p-3 border border-neutral-stroke-1-rest rounded-md">
            <option value="">Todos los estados</option>
            <option value="active">Activo</option>
            <option value="inactive">Inactivo</option>
            <option value="prospect">Prospecto</option>
          </select>
        </FormField>
      </div>

      <div className="flex gap-3 mt-4">
        <CustomButton
          variant="brand"
          leftIcon={<SearchIcon className="h-4 w-4" />}
        >
          Buscar
        </CustomButton>
        <CustomButton variant="neutral">Limpiar Filtros</CustomButton>
      </div>
    </div>
  ),
  parameters: {
    docs: {
      description: {
        story: "Formulario de búsqueda avanzada con múltiples filtros.",
      },
    },
  },
};
```

**7. Barrel export para todas las stories**

```tsx
// src/shared/ui-kit/stories/index.ts
// Atoms
export * from "./atoms/button.stories";
export * from "./atoms/input.stories";
export * from "./atoms/icon.stories";

// Molecules
export * from "./molecules/form-field.stories";
export * from "./molecules/search-bar.stories";
export * from "./molecules/card.stories";

// Organisms
export * from "./organisms/header.stories";
export * from "./organisms/sidebar.stories";
export * from "./organisms/data-table.stories";

// Templates
export * from "./templates/dashboard-layout.stories";
export * from "./templates/auth-layout.stories";

// Examples
export * from "./examples/forms.stories";
export * from "./examples/dashboards.stories";
export * from "./examples/workflows.stories";
```

**8. Configuración de Addons para Testing**

```js
// .storybook/main.ts (extensión)
import type { StorybookConfig } from "@storybook/nextjs";

const config: StorybookConfig = {
  // ... configuración anterior
  addons: [
    "@storybook/addon-links",
    "@storybook/addon-essentials",
    "@storybook/addon-interactions",
    "@storybook/addon-themes",
    "@storybook/addon-a11y",
    "@storybook/addon-viewport",
    "@storybook/addon-coverage", // Para testing
    "@storybook/test-runner", // Para testing
  ],
  framework: {
    name: "@storybook/nextjs",
    options: {},
  },
  features: {
    interactionsDebugger: true,
  },
};

export default config;
```

**9. Scripts de package.json**

```json
{
  "scripts": {
    "storybook": "storybook dev -p 6006",
    "build-storybook": "storybook build",
    "test-storybook": "test-storybook",
    "chromatic": "npx chromatic --project-token=your-token"
  }
}
```

#### Ventajas de esta configuración:

1. **Atomic Design**: Organización clara por niveles de complejidad
2. **Screaming Architecture**: La estructura de carpetas comunica la intención
3. **Documentación automática**: Autodocs generan documentación automáticamente
4. **Testing visual**: Chromatic para testing visual
5. **Accesibilidad**: Addon a11y para verificar accesibilidad
6. **Temas**: Soporte para modo claro/oscuro
7. **Interactividad**: Play functions para testing de interacciones
