# Cristian Querol Alves — Premium Portfolio Landing Page
## Comprehensive Design & Development Plan

---

## 1. NARRATIVA GENERAL & ARCO EMOCIONAL

**Concepto Central:**
*"Craftsman of Digital Experiences"* — Un desarrollador fullstack que no solo construye, sino que crea experiencias significativas. Barcelona como epicentro de inspiración europea, calidad como religión, detalles como diferenciador.

**Arco Emocional del Visitante:**
1. **Entrada (Hero)**: Impacto visual y claridad instantánea. "¿Quién es este tipo?" + "¿Qué construye?"
2. **Descubrimiento (About)**: Conexión humana. Entender la filosofía, la pasión, la ubicación.
3. **Admiración (Selected Work)**: Ver pruebas concretas. Proyectos brillantes que demuestran craft.
4. **Confianza (Expertise & Process)**: "Sé exactamente cómo trabaja y qué puede lograr para mí."
5. **Acción (CTA)**: Invitación irresistible a colaborar.

**Paleta Emocional:**
- **Sofisticación**: Fondos oscuros, espaciado generoso, tipografía de lujo.
- **Calidez**: Acentos en terracota/oro inspirados en arquitectura Barcelona (sombras, ladrillos históricos).
- **Energía técnica**: Sutiles elementos de motion que sugieren velocidad, precisión, movimiento de datos.
- **Accesibilidad emocional**: Nada frío. Conversacional, reflexivo, invitador.

---

## 2. ESTRUCTURA DE SECCIONES & PROPUESTA ÚNICA

### **2.1 Hero Section** (100vh)
**Propósito**: Establecer tono e identidad de inmediato.

**Elementos Únicos**:
- Nombre (Cristian) en tipografía grande y kerneada perfectamente.
- Rol + ubicación en secundaria elegante: "Fullstack Developer · Barcelona, Spain"
- Tagline emotivo: "Crafting seamless experiences across the stack."
- Dos CTAs de distinto peso: "Explore Work" (primario) + "Let's Talk" (secundario)
- Indicador de scroll elegante (chevron con micro-animación GSAP)
- **Fondo**: Gradiente sutil + posible parallax element (forma orgánica de bajo contraste o patrón geométrico minimalista)
- **Motion**: Fade-in suave de elementos con stagger, posible parallax sutil en background en scroll.

**Técnica GSAP**: 
- Timeline con entrance animations (opacity + slight scale).
- Scroll chevron loop infinito con pulsación sutil.
- Parallax background suave al scroll.

---

### **2.2 About / The Journey** (120-150vh)
**Propósito**: Establecer conexión humana y credibilidad.

**Layout Propuesto**:
- Texto narrativo en una columna (markdown-style, cálido y reflexivo).
- Posible imagen/ilustración asimétrica a la derecha (que parallaxea al scroll).
- Grid de 3-4 valores/principios: "Pixel Perfect", "Scalable Thinking", "Craft First", "User Obsessed"

**Contenido Narrativo**:
> *"Barcelona molded me. The attention to architecture, the Mediterranean light, the blend of legacy and innovation—it's in every line of code I write. I'm not just a developer; I'm someone who believes that technology should feel like art, and art should work like technology."*

**Secciones**:
- Origin story (breve, impactante)
- Philosophy (3-4 principios con iconografía)
- Ubicación + disponibilidad

**Técnica GSAP**:
- Parallax de imagen vs. texto (ligeras velocidades diferentes).
- Reveal de valores con staggered animations en scroll.

---

### **2.3 Selected Work** (300vh+)
**Propósito**: Demostrar capabilities y craft visual.

**Estrategia de Layout**:
Horizontal scroll premium (o tarjetas large con reveal elegante):
- **5 Proyectos** a 100% viewport width cada uno.
- Scroll horizontal smooth + indicador visual de progreso.
- Cada tarjeta: imagen grande, overlay con info (proyecto, rol, stack tags), CTA "View Case Study"

**Proyectos Sugeridos**:

| Proyecto | Descripción | Stack | Rol |
|----------|-------------|-------|-----|
| **Aether** | Collaboration platform AI-native con real-time sync | Next.js, Supabase, Anthropic API, GSAP | Full-stack Lead |
| **Vespera** | E-commerce headless de lujo (joyería/design) | Next.js, Shopify API, Stripe, 3D Product | Lead Developer |
| **Forge** | Internal dashboard SaaS + real-time analytics | React, WebSockets, D3.js, PostgreSQL | Full-stack Architect |
| **Lumen** | Design system + interactive documentation | Next.js, Storybook, Tailwind, custom animations | Designer + Dev |
| **Horizon** | Fintech app con data visualization + insights | Next.js, Chart.js, Open Banking API, WebGL | Full-stack Engineer |

**Modal / Case Study**:
Cuando clicas en un proyecto:
- Modal cinematográfico (GSAP open animation: blur + fade de background, slide-up suave del contenido)
- **Contenido**:
  - Hero image grande
  - Rol + Reto (el problema)
  - Solución + Approach
  - Stack technologies (badges)
  - Resultados medibles (KPIs, métricas)
  - Insights + learnings
  - Links (Live project / Repository)
- **Cierre**: Escape key o botón close elegante con animación reversa.
- **Scroll interno**: Smooth (Lenis), con indicador visual.

**Técnica GSAP**:
- Horizontal scroll con ScrollTrigger pinned.
- Hover effects en tarjetas: imagen parallax + overlay revelado.
- Modal: animaciones de entrada/salida con timeline GSAP.

---

### **2.4 Craft & Expertise** (150vh)
**Propósito**: Mostrar profundidad sin ser un list genérico.

**Estrategia de Visualización Interactiva**:
Opción elegida: **"Constellation of Skills"** — Grid flexible donde skills se agrupan por categoría (Frontend, Backend, Design, Tools, Data & Analytics).

**Diseño**:
- Título: "Craft & Expertise"
- Descripción corta: "A full-stack skillset refined through diverse projects and continuous learning."
- Categorías como pestañas o pills animadas.
- Al seleccionar: Skills dentro se revelan con stagger animation.
- Cada skill tiene un badge con color y hover effect (glow, scale).

**Categorías Propuestas**:
- **Frontend Engineering**: React, Next.js, TypeScript, Tailwind, GSAP, D3.js, WebGL
- **Backend & Infrastructure**: Node.js, Express, PostgreSQL, MongoDB, Supabase, AWS, Docker
- **Design Systems & UX**: Figma, Accessibility (WCAG), Component Architecture, Design Thinking
- **Emerging Tech**: AI/ML Integration, Real-time Systems, WebSockets, GraphQL
- **Tools & Practices**: Git, GitHub, CI/CD, Testing, Performance Optimization

**Técnica GSAP**:
- Reveal animado de skills al seleccionar categoría (timeline con stagger).
- Hover effects en badges (glow, scale, color shift).

---

### **2.5 Process / Approach** (200vh)
**Propósito**: Mostrar methodology y confianza en proceso.

**Estructura**: 5 pasos con storytelling visual.

**Pasos**:
1. **Discovery** — Entender, preguntar, investigar. (Icono: brújula)
2. **Strategy** — Planificar arquitectura y experiencia. (Icono: blueprint/mapa)
3. **Design** — Prototipar y validar visualmente. (Icono: paleta/boceto)
4. **Build** — Implementar con precisión y calidad. (Icono: martillo/código)
5. **Optimize** — Refinar, medir, iterar. (Icono: ajusta/brújula)

**Layout**:
- Timeline vertical o secuencia horizontal con pinned elements.
- Cada paso: icono grande + título + descripción (2-3 líneas, conversacional).
- Possible animated illustrations o subtle motion graphics.
- Lineas conectoras que se revelan al scroll.

**Técnica GSAP**:
- Pinned section con scroll-triggered reveal de cada paso.
- Lineas animadas (SVG stroke-dasharray reveal).
- Staggered fade-in de contenido.

---

### **2.6 Experience & Recognition** (Opcional, ~150vh)
**Propósito**: Credibilidad institucional (si aplica).

**Elementos**:
- Timeline de experiencia: empresas, roles, años, breve descripción.
- Clientes/empresas relevantes (logos si existen).
- Formación, certificaciones.
- Reconocimientos: awards, publicaciones, speaking, etc.

**Diseño**:
- Timeline vertical con alternancia izq/dcha.
- Hover effects para revelar más detalles.
- Smooth scroll reveal.

---

### **2.7 Let's Build Something / Contact** (100vh)
**Propósito**: Conversión clara + invitación a acción.

**Diseño**:
- Grande, invitador, sin ruido.
- Título: "Let's Build Something Great Together"
- Descripción corta: "Whether you're looking for a full-stack expert, technical leadership, or a fresh perspective on your project—I'd love to hear about it."
- **Formulario**:
  - Nombre, Email, Proyecto/Mensaje (textarea)
  - Botón Submit animado (hover effect GSAP)
  - Integración básica (FormSubmit.co o similar) para demostración; en producción sería backend propio.
- **Info de contacto**:
  - Email principal (clickable)
  - Links sociales (GitHub, LinkedIn, Twitter — iconos con hover)
  - Disponibilidad: "Currently Open for: Freelance Projects · Full-time Roles · Advisory"
  - Ubicación: Barcelona 🌍

**Técnica GSAP**:
- Formulario entrada en viewport: fade-in + slight slide-up.
- Hover effects en inputs y botones.
- Social icons con hover magnético (GSAP magnetism effect).

---

### **2.8 Footer** (Completo)
- Links: Home, Work, About, Contact
- Social links
- Copyright + "Designed & Built by Cristian Querol Alves"
- Light theme hint o small credit

---

## 3. SISTEMA DE DISEÑO COMPLETO

### **3.1 Paleta de Colores**

```
FONDOS & NEUTROS:
- Deep Navy (primary background): #0A0C10
- Secondary bg (lighter sections): #0F1117
- Text Primary (cream): #F5F3F0
- Text Secondary (muted): #A8A4A0
- Border/Divider: #1A1E26

ACENTOS (Barcelona-inspired warmth):
- Terracota Primary: #C75B39
- Gold Secondary: #D4A373
- Coral Light: #E8A084 (para highlights)

UTILIDAD:
- Success: #10B981
- Warning: #F59E0B
- Error: #EF4444
```

### **3.2 Tipografía**

```
Heading (Premium, geometric):
- Font: Space Grotesk (o Inter Bold 700)
- Sizes: 
  - H1 (Hero): 5rem+ (responsive down to 2.5rem mobile)
  - H2 (Section titles): 3rem (1.5rem mobile)
  - H3: 1.5rem

Body & Narrative:
- Font: Inter (400, 500)
- Size: 1rem (base)
- Line height: 1.6 (narrative), 1.5 (info)
- Letter spacing: 0 (default), -0.02em (headings)

Accents / Tags / Code:
- Monospace: JetBrains Mono (si hay código) o similar
```

### **3.3 Espaciado (8px grid system)**

```
Spacing scale:
- 2xs: 0.25rem (2px)
- xs: 0.5rem (4px)
- sm: 1rem (8px)
- md: 1.5rem (12px)
- lg: 2rem (16px)
- xl: 3rem (24px)
- 2xl: 4rem (32px)
- 3xl: 6rem (48px)
- 4xl: 8rem (64px)

Margins/Padding for sections:
- Top/Bottom: 4xl–6xl (64–96px) between major sections
- Left/Right: xl–2xl (24–32px) padding on container
```

### **3.4 Elevación & Shadow System**

```
Shadows (layered depth):
- None: 0 (flat, minimal elevation)
- sm: 0 2px 8px rgba(0,0,0,0.15)
- md: 0 8px 24px rgba(0,0,0,0.25)
- lg: 0 16px 48px rgba(0,0,0,0.35)
- xl: 0 24px 64px rgba(0,0,0,0.40)

Glassmorphism (si aplica):
- Background: rgba(255,255,255,0.05)
- Backdrop-filter: blur(10px)
- Border: 1px solid rgba(255,255,255,0.1)
```

### **3.5 Motion Language**

**Timing:**
- Subtle/micro: 200–300ms
- Standard: 400–600ms
- Cinematic: 800ms–1.2s

**Easing (GSAP):**
- UI interactions: `power2.inOut`
- Entrances: `back.out` o `elastic.out` (sutil)
- Parallax/scroll: `linear` o `power1.inOut`
- Modals: `power3.inOut`

**Principles:**
- Purpose-driven: cada animación comunica algo.
- Respeta `prefers-reduced-motion` (disable animations).
- Performance first: hardware acceleration, minimal repaints.

---

## 4. ESTRATEGIA DE ANIMACIONES GSAP POR SECCIÓN

### **Hero**
```
Timeline:
1. Background parallax container: pinned, parallax factor 0.3
2. Fade-in nombre: opacity 0→1, duration 0.8s, ease "power2.out"
3. Stagger sobre rol/tagline: opacity 0→1, translateY(-10px→0), duration 0.6s, delay 0.2s
4. CTA buttons: scale 0.9→1, opacity 0→1, duration 0.5s, delay 0.4s
5. Chevron: infinite pulsation (opacity + scale loop)
6. On scroll: Parallax parallax-factor 0.5 en background, fade + translateY en text
```

### **About**
```
- Parallax imagen: factor -0.3 vs. texto factor 0.2 (ligera separación)
- Valores grid: staggered reveal (opacity + scale) en scroll
- Uso de ScrollTrigger markers: { markers: false } en prod
```

### **Selected Work**
```
- Horizontal scroll: ScrollTrigger.horizontal() con pinned section
- Tarjetas: hover triggers GSAP timeline (imagen parallax + overlay fade)
- Modal abierto: 
  1. Background blur (via filter GSAP)
  2. Contenido slide-up con timing 0.6s, ease "back.out"
- Modal cierre: reverso de entrada, mas rápido (0.3s)
```

### **Craft & Expertise**
```
- Categoría cambio: skills revelan con stagger (0.1s entre items)
- Badges: hover glow + scale 1.05x
```

### **Process**
```
- Timeline vertical: cada paso se revela en scroll con staggered timing
- Lineas conectoras: SVG stroke-dasharray reveal (duration 0.8s per step)
- Icono rotaciones sutiles al hover
```

### **Contact**
```
- Entrada sección: fade-in al llegar al viewport
- Form inputs: focus states animados (border color, glow)
- Botón submit: hover state (background shift + scale)
- Social icons: magnetic hover effect (GSAP magnetism helper)
```

---

## 5. STACK TÉCNICO & JUSTIFICACIÓN

```
CORE FRAMEWORK:
✓ Next.js 15 (App Router)
  → Latest, SSR-ready, image optimization built-in
  → API routes para formularios (si quieres backend propio)

✓ TypeScript
  → Type safety, mejor DX, refactoring confiable

✓ Tailwind CSS
  → Utility-first, performante, fácil customización

ANIMACIONES & MOTION:
✓ GSAP 3 + ScrollTrigger
  → Industry standard, performance superior, exactitud
  → Parallax, pinning, scroll-triggered animations
  → Timeline control fino

✓ Lenis
  → Smooth scroll ultra-premium (no jank)
  → Integración limpia con GSAP ScrollTrigger

COMPONENTES & ICONOS:
✓ Lucide-react
  → Iconos limpios, tree-shakeable

✓ Custom components (no shadcn generic)
  → Button, Card, Modal con identidad propia

TIPOGRAFÍA:
✓ next/font (Geist, Space Grotesk, Inter)
  → Self-hosted, zero layout shift, performance óptima

HERRAMIENTAS DE DESARROLLO:
✓ ESLint + Prettier
  → Code quality y consistency

✓ Vercel deployment
  → Zero-config, edge functions (si needed), CDN global

RENDERING:
✓ Client Components (donde necesario para GSAP)
✓ Server Components (layout, content estático)
  → Mejor balance performance/interactividad

TESTING / PERFORMANCE:
✓ Lighthouse targets: 95+ (Performance, Accessibility, Best Practices)
✓ Core Web Vitals optimized
```

---

## 6. ESTRATEGIA DE ACCESIBILIDAD, PERFORMANCE & SEO

### **6.1 Accesibilidad (WCAG 2.1 AA+)**

- **Motion**:
  - `prefers-reduced-motion` respetado (disable GSAP animations si activado)
  - Chevrons, parallax, etc. → fallback static version

- **Keyboard Navigation**:
  - Tab order lógico (tabIndex, focus visible)
  - Modales: focus trap + escape key
  - Buttons/links: aria-labels donde sea necesario

- **Color Contrast**:
  - Text (cream #F5F3F0 sobre navy #0A0C10): ~15:1 ratio ✓
  - Acentos terracota sobre dark: 7:1+ ratio ✓

- **Semantic HTML**:
  - `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`
  - Headings hierarchy: h1 → h2 → h3

- **Images**:
  - alt text descriptivos
  - Next.js Image para lazy loading + optimization

- **Forms**:
  - Labels explícitos (no placeholders only)
  - Error messages claras
  - Success feedback

---

### **6.2 Performance Optimization**

- **Code Splitting**:
  - Lazy load sections (next/dynamic)
  - GSAP plugins only loaded si needed

- **Image Optimization**:
  - next/image (automatic format, sizes, lazy loading)
  - WebP + fallbacks
  - Responsive srcset

- **Bundle Size**:
  - Tree-shake unused Tailwind utilities
  - GSAP modular (core + plugins needed only)
  - Minify CSS/JS (Next.js auto)

- **Caching**:
  - Static export donde possible
  - Cache headers (Vercel edge caching)

- **Lighthouse Targets**:
  - Performance: 95+
  - Accessibility: 95+
  - Best Practices: 95+
  - SEO: 95+

---

### **6.3 SEO**

- **Meta Tags**:
  - Title: "Cristian Querol Alves — Fullstack Web Developer · Barcelona"
  - Description: "Crafting seamless digital experiences. Fullstack engineer specializing in modern web technologies, design systems, and product-focused solutions."
  - OG tags (image, title, description)

- **Structured Data**:
  - JSON-LD person schema (name, contact, location)
  - Organization schema (si aplica)

- **Mobile Optimization**:
  - Responsive from 320px+
  - Touch-friendly CTAs (48px+ tap targets)

- **Sitemap / Robots**:
  - next-sitemap o manual
  - robots.txt

---

## 7. CÓMO CADA SECCIÓN CONTRIBUYE A COHERENCIA & PREMIUM FEEL

| Sección | Propósito | Coherencia Premium |
|---------|-----------|-------------------|
| Hero | Intro impactante | Tipografía grande + espaciado generoso + fondo limpio |
| About | Conexión personal | Narrativa cálida + asimetría + parallax sutil |
| Work | Prueba de skills | Showcase cinematográfico + hover polish + modales premium |
| Expertise | Credibilidad técnica | Interactividad elegante, no lista plana |
| Process | Confianza metodológica | Timeline visual + animaciones secuenciales |
| Contact | Conversión | Invitación clara + formulario pulido |
| Footer | Cierre profesional | Links + info esencial, diseño coherente |

**Hilo conductor**: Cada sección es más específica y detallada que la anterior. Ritmo de revelación controlado. Transiciones suaves entre secciones (uso de color, espaciado, motion). Nada se siente apresado o genérico.

---

## 8. ARQUITECTURA DE ARCHIVOS

```
cristian-portfolio/
├── .cursor/
│   └── rules/
│       ├── code-quality.md
│       ├── component-architecture.md
│       ├── gsap-patterns.md
│       ├── accessibility.md
│       └── design-system.md
├── .github/
│   └── workflows/
│       └── deploy.yml (Vercel, Lighthouse)
├── public/
│   ├── images/
│   │   ├── hero/
│   │   ├── projects/
│   │   └── ...
│   ├── fonts/ (if self-hosting)
│   └── favicons/
├── src/
│   ├── app/
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   ├── globals.css
│   │   └── error.tsx
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Header.tsx
│   │   │   ├── Navigation.tsx
│   │   │   ├── Footer.tsx
│   │   │   └── SectionWrapper.tsx
│   │   ├── sections/
│   │   │   ├── Hero.tsx
│   │   │   ├── About.tsx
│   │   │   ├── SelectedWork.tsx
│   │   │   ├── Expertise.tsx
│   │   │   ├── Process.tsx
│   │   │   ├── Experience.tsx
│   │   │   └── Contact.tsx
│   │   ├── ui/
│   │   │   ├── Button.tsx
│   │   │   ├── Card.tsx
│   │   │   ├── Modal.tsx
│   │   │   ├── Badge.tsx
│   │   │   ├── Input.tsx
│   │   │   └── Textarea.tsx
│   │   └── project/
│   │       ├── ProjectCard.tsx
│   │       └── CaseStudyModal.tsx
│   ├── hooks/
│   │   ├── useGsapAnimation.ts
│   │   ├── useScrollTrigger.ts
│   │   ├── useMotionPreference.ts
│   │   └── useWindowSize.ts
│   ├── lib/
│   │   ├── gsap-config.ts
│   │   ├── animation-utils.ts
│   │   ├── constants.ts
│   │   └── tailwind-theme.ts
│   ├── data/
│   │   ├── projects.ts
│   │   ├── skills.ts
│   │   ├── experience.ts
│   │   └── process-steps.ts
│   ├── styles/
│   │   ├── animations.css
│   │   └── typography.css
│   └── utils/
│       ├── cn.ts
│       └── helpers.ts
├── .env.local (si needed)
├── tailwind.config.ts
├── tsconfig.json
├── next.config.ts
├── package.json
├── eslint.config.js
├── .prettierrc
├── PLAN.md (este archivo)
└── README.md (instrucciones finales)
```

---

## 9. STACK TÉCNICO ESPECÍFICO

```json
{
  "dependencies": {
    "next": "^15.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "typescript": "^5.0.0",
    "tailwindcss": "^3.4.0",
    "gsap": "^3.12.0",
    "lenis": "^1.1.0",
    "lucide-react": "^latest",
    "clsx": "^2.0.0"
  },
  "devDependencies": {
    "@types/node": "^20.0.0",
    "@types/react": "^18.0.0",
    "eslint": "^8.0.0",
    "prettier": "^3.0.0",
    "autoprefixer": "^10.4.0",
    "postcss": "^8.4.0"
  }
}
```

---

## 10. PRÓXIMOS PASOS INMEDIATOS

1. ✅ **Este PLAN.md** — completado
2. 🔄 **Cursor Rules** (`.cursor/rules/`) — definir estándares estrictos
3. 🔄 **Inicializar Next.js 15** — proyecto limpio, ESLint, Prettier, Tailwind
4. 🔄 **Configuración base** — theme personalizado, layout root
5. 🔄 **Componentes UI custom** — Button, Card, Modal, Badge (sin shadcn)
6. 🔄 **Secciones una por una** — Hero → About → Work → Expertise → Process → Contact
7. 🔄 **Animaciones GSAP** — integración suave por sección
8. 🔄 **Responsive & Mobile** — mobile-first approach
9. 🔄 **Accesibilidad** — audit final, prefers-reduced-motion, keyboard nav
10. 🔄 **Performance & SEO** — Lighthouse, Core Web Vitals, meta tags
11. 🔄 **Pulido visual** — refinement final de timing, easing, spacing
12. 🔄 **Deploy a Vercel** — instruye al usuario final

---

**¡Comencemos!** Este sitio va a ser excepcional.
