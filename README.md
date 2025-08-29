# 📊 ShadCN Dashboard - Demo Template MBT

Dashboard construido con Next.js 15, shadcn/ui y Tailwind CSS v4. 
Este proyecto presenta una interfaz de usuario completa con componentes reutilizables, gestión de temas y visualización de datos interactiva.

![Dashboard Preview]
<img width="1246" height="976" alt="image" src="https://github.com/user-attachments/assets/4fa77f63-0de5-48fa-9af2-4eaa2d0537b2" />
<img width="1256" height="969" alt="image" src="https://github.com/user-attachments/assets/e6e91e2e-5c20-499c-beaf-9d20c725e870" />


## ✨ Características

- 🎨 **Diseño Moderno**: Interface limpia y profesional con shadcn/ui
- 🌙 **Modo Oscuro/Claro**: Alternancia automática de temas con next-themes
- 🎭 **Múltiples Temas**: Sistema de temas dinámico (Default, Blue, Green, Amber, Mono)
- 📱 **Responsive**: Totalmente adaptable a dispositivos móviles
- 📊 **Visualización de Datos**: Gráficos interactivos con Recharts
- 📋 **Tabla de Datos**: Tabla completa con sorting, filtros y drag & drop
- 🧩 **Componentes Modulares**: Arquitectura de componentes reutilizables
- ⚡ **Rendimiento Optimizado**: Powered by Next.js 15 con Turbopack
- 🎯 **TypeScript**: Tipado completo para mejor desarrollo

## 🛠️ Stack Tecnológico

- **Framework**: [Next.js 15](https://nextjs.org/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **UI Components**: [shadcn/ui](https://ui.shadcn.com/)
- **Icons**: [Tabler Icons](https://tabler.io/icons) & [Lucide React](https://lucide.dev/)
- **Charts**: [Recharts](https://recharts.org/)
- **Drag & Drop**: [@dnd-kit](https://dndkit.com/)
- **Theme Management**: [next-themes](https://github.com/pacocoursey/next-themes)
- **Notifications**: [Sonner](https://sonner.emilkowal.ski/)
- **Language**: TypeScript

## 🚀 Inicio Rápido

### Prerequisitos

- Node.js 18+ 
- pnpm, npm, yarn o bun

### Instalación

1. **Clona el repositorio**
```bash
git clone https://github.com/tu-usuario/shadcn-dashboard.git
cd shadcn-dashboard
```

2. **Instala las dependencias**
```bash
npm install
# o
pnpm install
# o
yarn install
# o
bun install
```

3. **Ejecuta el servidor de desarrollo**
```bash
npm run dev
# o
pnpm dev
# o
yarn dev
# o
bun dev
```

4. **Abre tu navegador**
Navega a [http://localhost:3000](http://localhost:3000) para ver la aplicación.

## 🏗️ Arquitectura del Proyecto

El proyecto **NO sigue una arquitectura tradicional como MVC o MVVM**. En su lugar, utiliza una **arquitectura basada en componentes de React** con el patrón de **App Router de Next.js 13+**. Específicamente:

### 📁 **Arquitectura de Componentes React + Next.js App Router**

```
<code_block_to_apply_changes_from>
shadcn-dashboard/
├── app/                    # 🎯 App Router (Rutas y Layouts)
│   ├── layout.tsx         # Layout raíz con providers
│   ├── page.tsx           # Página home
│   ├── dashboard/
│   │   ├── page.tsx       # Página del dashboard
│   │   └── data.json      # Datos estáticos
│   └── globals.css        # Estilos globales
├── components/            # 🧩 Componentes UI
│   ├── ui/               # Componentes base (shadcn/ui)
│   ├── providers/        # Context Providers
│   └── [feature-components] # Componentes específicos
├── hooks/                # 🪝 Custom Hooks (lógica reutilizable)
├── lib/                  # 🛠️ Utilidades y helpers
└── public/               # 📁 Assets estáticos
```

### 🎨 **Patrones de Diseño Implementados:**

1. **Component-Based Architecture**
   - Cada funcionalidad es un componente independiente
   - Composición de componentes para crear interfaces complejas

2. **Provider Pattern**
   ```typescript
   // En layout.tsx
   <ThemeProvider>
     <ActiveThemeProvider>
       {children}
     </ActiveThemeProvider>
   </ThemeProvider>
   ```

3. **Custom Hooks Pattern**
   ```typescript
   // hooks/use-mobile.ts
   export function useMobile() {
     // Lógica reutilizable
   }
   ```

4. **Compound Component Pattern**
   - Usado en componentes como `Sidebar`, `DataTable`, etc.

### 🔄 **Flujo de Datos:**

```
State Management:
├── Global State → Context Providers (Theme, etc.)
├── Local State → useState en componentes
├── Server State → Next.js App Router
└── UI State → Componentes individuales
```

### 📊 **Separación de Responsabilidades:**

| Capa | Responsabilidad | Ejemplos |
|------|----------------|----------|
| **App Router** | Routing, Layouts, Metadata | `app/layout.tsx`, `app/dashboard/page.tsx` |
| **Components** | UI Logic, Presentation | `components/data-table.tsx`, `components/chart-area-interactive.tsx` |
| **Hooks** | Business Logic, Reusable Logic | `hooks/use-mobile.ts` |
| **Lib** | Utilities, Helpers | `lib/utils.ts` |
| **Providers** | Global State Management | `components/providers/theme-provider.tsx` |

### 🎯 **No es MVC/MVVM porque:**

- **No hay Controllers/ViewModels explícitos**: La lógica está distribuida en hooks y componentes
- **No hay Models tradicionales**: Los datos vienen de JSON estático y props
- **No hay separación estricta M-V-C**: Todo está integrado en el paradigma de componentes React

### 🚀 **Ventajas de esta Arquitectura:**

✅ **Modularidad**: Componentes reutilizables  
✅ **Escalabilidad**: Fácil agregar nuevas funcionalidades  
✅ **Mantenibilidad**: Separación clara de responsabilidades  
✅ **Performance**: Server Components + Client Components optimizados  
✅ **Developer Experience**: TypeScript + Hot Reload + shadcn/ui  

**Conclusión**: Proyecto usa una **arquitectura moderna de React/Next.js basada en componentes** que es más flexible y adecuada para aplicaciones frontend modernas que las arquitecturas tradicionales MVC/MVVM.

## 🎨 Personalización de Temas

El dashboard incluye un sistema de temas robusto con las siguientes opciones:

- **Default**: Tema neutro clásico
- **Blue**: Tema azul profesional  
- **Green**: Tema verde natural
- **Amber**: Tema ámbar cálido
- **Mono**: Tema monoespacio para desarrolladores

Cada tema está disponible en versión **normal** y **scaled** (compacta).

### Agregar un Nuevo Tema

1. Define las variables CSS en `app/globals.css`:
```css
.theme-custom {
  --primary: /* tu color primario */;
  --primary-foreground: /* color del texto */;
}
```

2. Agrega el tema en `components/theme-selector.tsx`:
```typescript
{
  name: "Custom",
  value: "custom",
}
```

## 📊 Componentes Principales

### Dashboard Layout
- **AppSidebar**: Navegación lateral con menús colapsibles
- **SiteHeader**: Header con selector de temas y toggle de modo
- **SectionCards**: Tarjetas de métricas y estadísticas
- **ChartAreaInteractive**: Gráficos de área interactivos
- **DataTable**: Tabla avanzada con filtros y drag & drop

### UI Components
Todos los componentes están basados en shadcn/ui y son completamente personalizables:
- Buttons, Cards, Tables
- Dropdowns, Selects, Inputs
- Dialogs, Sheets, Tooltips
- Y muchos más...

## 🔧 Scripts Disponibles

```bash
# Desarrollo con Turbopack
npm run dev

# Build de producción
npm run build

# Ejecutar en producción
npm run start

# Linting
npm run lint
```

### Otras opciones
- **Netlify**: Compatible con builds estáticos
- **Railway**: Despliegue automático con Git
- **Docker**: Containerización disponible

## 📝 Licencia

Este proyecto está bajo la Licencia MIT. Ve el archivo [LICENSE](LICENSE) para más detalles.

---
