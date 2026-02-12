# Mavre Works — Design Brief para iteración de diseño, copy y UI

Documento de datos para que ChatGPT (u otro LLM) pueda iterar sobre el diseño, copy y UI del sitio mavreworks.com.

---

## 1. CONTEXTO Y POSICIONAMIENTO

**Mavre Works** es un productized builder de sistemas digitales de producción — no una agencia creativa ni estudio de branding.

**Posicionamiento actual:**
- Production-grade digital systems
- Sistemas web, herramientas internas y fundaciones de software
- Enfoque en: impacto en ingresos, escalabilidad, confiabilidad a largo plazo
- Filtro de fit: no landing pages rápidas, no branding experimental; sí equipos con requisitos claros y stakes reales

**Tono de copy:** técnico, calmado, orientado a sistemas, sin marketing fluff.

---

## 2. DESIGN SYSTEM (mantener consistencia)

### Colores
| Token | Hex | Uso |
|-------|-----|-----|
| base | #FAFAFA | Background principal |
| surface | #FFFFFF | Cards, nav |
| surfaceAlt | #F5F5F5 | Inputs, áreas secundarias |
| primary | #171717 | Texto principal |
| secondary | #525252 | Texto secundario |
| muted | #A3A3A3 | Texto muted, labels |
| accent | #262626 | Acentos sutiles |
| border | #E5E5E5 | Bordes |
| system-accent | #2563EB | Solo hover, expandido, indicadores |

### Tipografía
- **sans:** Inter (300, 400, 500, 600)
- **mono:** JetBrains Mono (400, 500)
- **display:** DM Sans (usado en hero headline)

### Escala de texto
- H1: `text-5xl md:text-7xl lg:text-8xl`
- H2 sección: `text-2xl font-normal tracking-tight`
- H3: `text-sm font-medium` o `text-lg font-medium`
- Body: `text-sm`, `text-xs`
- Micro: `text-[10px]`

### Espaciado
- Secciones: `py-24 px-6 md:px-12`
- Contenedor max: `max-w-[1080px]` (algunos `max-w-[640px]`, `max-w-[900px]`)
- Gaps: `gap-4`, `gap-6`, `gap-8`, `gap-10`, `gap-12`, `gap-16`, `gap-20`

### Componentes clave
- **Glass wrapper (cards):** `p-2 rounded-2xl bg-gradient-to-b from-white/60 to-white/10 border border-white/50 shadow-[0_20px_40px_-15px_rgba(0,0,0,0.1)] backdrop-blur-sm`
- **Scroll reveal:** `scroll-reveal` + IntersectionObserver para fade-in
- **Bordes:** `border-t border-border`, `ring-1 ring-black/5`

---

## 3. ESTRUCTURA ACTUAL DEL SITIO

1. **Nav** — fixed, rounded pill, links + lang toggle + CTA
2. **Hero** — headline, subtitle, CTAs, micro-line
3. **What We Build** — título + 4 items en grid 2x2
4. **Selected Work** — grid 2 cols, 5 proyectos con cards expandibles
5. **Mavre Works Blueprint** — 4 pasos en grid 4 cols
6. **Technical Standards** — 3 cards
7. **Contact** — form + micro copy
8. **Footer** — brand, links, legal

---

## 4. SECCIÓN "WHAT WE BUILD" — ESTADO ACTUAL

**Layout:** Grid 2 cols, 4 items iguales.

**Contenido (EN):**
| Key | Title | Description |
|-----|-------|-------------|
| whatwebuild.item1 | Revenue Websites | High-performance sites built to convert, rank, and remain maintainable for years. No throwaway marketing pages. |
| whatwebuild.item2 | Internal Systems | Tools that replace spreadsheets and manual processes. Operational clarity, fewer errors, reliable automation. |
| whatwebuild.item3 | MVP & Product Foundations | Validate fast without building tech debt. Architecture that survives product-market fit, not just the first demo. |
| whatwebuild.item4 | Automation & Integrations | Connect your systems, eliminate repetitive work, and scale operations without adding headcount. |

**Contenido (ES):**
| Key | Title | Description |
|-----|-------|-------------|
| whatwebuild.item1 | Sitios de Ingresos | Sitios de alto rendimiento construidos para convertir, posicionar y mantenerse durante años... |
| whatwebuild.item2 | Sistemas Internos | Herramientas que reemplazan hojas de cálculo y procesos manuales... |
| whatwebuild.item3 | MVP y Fundaciones de Producto | Valida rápido sin acumular deuda técnica... |
| whatwebuild.item4 | Automatización e Integraciones | Conecta tus sistemas, elimina trabajo repetitivo... |

**HTML actual (clase):**
```html
<div class="grid grid-cols-1 md:grid-cols-2 gap-x-10 gap-y-10">
  <div class="flex flex-col gap-3 scroll-reveal">
    <h3 class="text-sm font-medium text-primary" data-i18n="whatwebuild.item1.title">...</h3>
    <p class="text-xs text-secondary leading-relaxed" data-i18n="whatwebuild.item1.desc">...</p>
  </div>
  ...
</div>
```

---

## 5. SECCIÓN "SELECTED WORK" — REFERENCIA BENTO

**Layout:** Grid 2 cols, cards con rotación sutil (`md:rotate-1`, `md:-rotate-1`), último item `md:col-span-2 md:w-2/3 md:mx-auto`.

**Estructura de cada card:**
1. **Glass wrapper** (gradient, border, shadow)
2. **Inner card** (bg-white, rounded-xl, shadow-sm)
3. **Visual area** (aspect-[16/9], icono placeholder, "Expand preview")
4. **Content** (título, status badge, categoría, descripción)
5. **Preview expandible** (slider horizontal con 4 slides + dots + link)
6. **Tech tags** (border-dashed, font-mono)

**Clases clave por card:**
- Card: `project-card group relative md:rotate-1 hover:rotate-0 hover:scale-[1.01] hover:z-10 transition-all duration-500 ease-out scroll-reveal`
- Glass: `relative h-full p-2 rounded-2xl bg-gradient-to-b from-white/60 to-white/10 border border-white/50 shadow-[0_20px_40px_-15px_rgba(0,0,0,0.1)] backdrop-blur-sm`
- Inner: `h-full bg-white rounded-xl shadow-sm ring-1 ring-black/5 overflow-hidden flex flex-col`

---

## 6. PROPUESTA: BENTO BOX PARA "WHAT WE BUILD" / "WHAT WE HIGHLIGHT"

**Objetivo:** Convertir la sección actual en un bento box visualmente alineado con Selected Work, mostrando "lo que resaltamos" (what we highlight) con:
- Cards de tamaño variable (algunas más grandes, otras más pequeñas)
- Estilo glass similar a Selected Work
- Íconos o micro-elementos visuales
- Layout asimétrico (ej: 2+2, o 1 grande + 3 pequeñas, o patrón tipo bento Apple)

**Posibles estructuras bento:**
- **4 celdas:** 2 cols × 2 rows, celdas de igual tamaño
- **Bento 5:** 1 celda ancha arriba (Revenue Websites) + 3 abajo (Internal, MVP, Automation)
- **Bento 6:** Grid 3×2 con variación de spans (col-span-2 para algunos items)
- **Asimétrico:** 1 grande (2 cols), 2 medianas, 1 pequeña

**Contenido a mostrar en cada celda:**
- Título corto
- Descripción 1–2 líneas
- Opcional: ícono, número, o micro-metrica

**Referencias de diseño bento:**
- Apple Marketing sites (product grids)
- Linear.app homepage sections
- Vercel / Raycast style bento grids
- Dribbble: "bento grid website"
- Awwwards: "bento box layout"

---

## 7. COPY COMPLETO (EN + ES)

### Hero
| Key | EN | ES |
|-----|----|----|
| hero.status | Accepting Q2 Projects | Aceptando Proyectos Q2 |
| hero.headline.precision | Production-grade | Sistemas |
| hero.headline.digital | digital | digitales |
| hero.headline.products | systems. | de producción. |
| hero.subtitle | We build web platforms, internal tools, and software foundations that scale with your business. Designed for revenue impact and long-term reliability. | Construimos plataformas web, herramientas internas y fundaciones de software que escalan con tu negocio. Diseñados para impacto en ingresos y confiabilidad a largo plazo. |
| hero.cta.viewWork | View Work | Ver Trabajos |
| hero.cta.bookCall | Book a Call | Agendar Llamada |
| hero.micro | Limited availability · SOP-driven execution · Serious builds only | Disponibilidad limitada · Ejecución basada en SOP · Solo proyectos serios |

### Nav
| Key | EN | ES |
|-----|----|----|
| nav.work | Work | Trabajos |
| nav.capabilities | Capabilities | Capacidades |
| nav.contact | Contact | Contacto |
| nav.cta | Get Quote → | Cotiza aquí → |

### What We Build
(Véase sección 4)

### Work
| Key | EN | ES |
|-----|----|----|
| work.title | Selected Work | Trabajos Seleccionados |
| work.subtitle | A curation of recent client engagements and internal R&D. | Una selección de proyectos recientes con clientes e I+D interno. |

### Blueprint
| Key | EN | ES |
|-----|----|----|
| blueprint.title | Mavre Works Blueprint | Metodología Mavre Works |
| blueprint.subtitle | A structured delivery system built on clarity, iteration, and operational discipline. | Un sistema de entrega estructurado basado en claridad, iteración y disciplina operacional. |
| blueprint.step1.label | 01 — Alignment | 01 — Alineación |
| blueprint.step2.label | 02 — System Design | 02 — Diseño de Sistema |
| blueprint.step3.label | 03 — Build & Iterate | 03 — Construir e Iterar |
| blueprint.step4.label | 04 — Deploy & Stabilize | 04 — Desplegar y Estabilizar |

### Capabilities
| Key | EN | ES |
|-----|----|----|
| capabilities.title | Technical Standards | Estándares Técnicos |
| capabilities.card1.title | Architecture | Arquitectura |
| capabilities.card2.title | Accessibility | Accesibilidad |
| capabilities.card3.title | Reliability | Confiabilidad |

### Contact
| Key | EN | ES |
|-----|----|----|
| contact.title | Work with us | Trabaja con nosotros |
| contact.subtitle | We take on a limited number of projects. If you're building something revenue-critical and need production-grade execution, let's talk. | Tomamos un número limitado de proyectos. Si estás construyendo algo crítico para ingresos y necesitas ejecución de nivel producción, hablemos. |
| contact.micro | Not the right fit for quick landing pages or experimental branding. Best for teams with clear requirements and real stakes. | No somos el fit correcto para landing pages rápidas o branding experimental. Mejor para equipos con requisitos claros y stakes reales. |

---

## 8. SISTEMA i18n

**Implementación:** `data-i18n="key.path"` en elementos + objeto `translations` en JS con `en` y `es`.

**Flujo:** `setLanguage(lang)` actualiza `document.querySelectorAll('[data-i18n]')` y placeholders de inputs.

**Placeholders:** `contact.emailPlaceholder`, `contact.websitePlaceholder`, `contact.messagePlaceholder`.

---

## 9. RESTRICCIONES TÉCNICAS

- **Stack:** HTML estático, Tailwind via CDN, vanilla JS
- **Sin:** React, Vue, frameworks pesados
- **Animaciones:** CSS transitions, `scroll-reveal` con IntersectionObserver
- **Sin modales** para previews (expand inline)
- **Responsive:** breakpoints `md:` (768px), `lg:` (1024px)

---

## 10. BÚSQUEDAS SUGERIDAS PARA INSPIRACIÓN

1. **Bento box layouts:** "bento grid website design", "bento box UI pattern"
2. **Secciones de servicios:** "agency services section design", "productized services layout"
3. **Cards glass style:** "glass morphism card design", "frosted glass UI"
4. **Sitios de referencia:** linear.app, vercel.com, stripe.com, raycast.com
5. **Dribbble:** "bento grid", "services grid", "agency landing page"
6. **Awwwards:** "digital agency", "product studio"

---

## 11. TAREAS SUGERIDAS PARA ITERACIÓN

1. **Rediseñar "What We Build"** como bento box con cards de tamaño variable, estilo glass, alineado con Selected Work.
2. **Agregar sección "What We Highlight"** (opcional) como bento con: SOP-driven delivery, response 24h, limited projects, etc.
3. **Explorar variaciones de bento** (4, 5, 6 celdas) sin romper el grid existente.
4. **Mantener i18n** en todas las nuevas keys.
5. **No cambiar** typography scale, layout grids, o spacing rhythm del resto del sitio.

---

## 12. PROYECTOS (para referencia de estructura)

| Proyecto | Status | URL | Categoría |
|----------|--------|-----|------------|
| Kar & Ma | Live | consorciokarma.com | Client · Production System |
| Jopi Crew | — | jopi-crew.vercel.app | Client · Marketing Platform |
| TravelKey | Private | — | Product · MVP Architecture |
| Digi Detox | Private | — | R&D · Behavioral Prototype |
| ComputerVisionApp | Beta | — | Prototype |

---

*Documento generado para iteración de diseño. Última actualización: Feb 2026.*
