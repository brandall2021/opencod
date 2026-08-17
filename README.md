# OpenCode Skills

Colección completa de skills instaladas para [OpenCode](https://opencode.ai) — asistente de programación con IA.

## Resumen

| Categoría | Cantidad | Fuente |
|-----------|----------|--------|
| Marketing & Growth | 38 | `obra/superpowers` |
| Design & UI/UX | 16 | `obra/superpowers` + globales |
| Development Process | 15 | `obra/superpowers` |
| Local / Extra | 2 | `/home/proyecto/.agents/skills` |
| OpenCode Core | 11 | `/root/.config/opencode/skills` |
| **Total** | **82** | |

---

## Instalación Rápida

```bash
# 1. Clonar el repo de superpowers (contiene todas las skills)
git clone https://github.com/obra/superpowers.git /tmp/superpowers

# 2. Copiar skills de proyecto (marketing + design)
cp -r /tmp/superpowers/skills/* /home/brandall/desarrollo/.agents/skills/

# 3. Copiar skills globales (design + UI)
cp -r /tmp/superpowers/skills/* /root/.agents/skills/

# 4. Copiar skills locales que ya están instaladas en esta PC
for skill in code-review-and-quality grill-with-docs; do
  src="/home/proyecto/.agents/skills/$skill/SKILL.md"
  dst="/home/brandall/desarrollo/.agents/skills/$skill/SKILL.md"
  [ -f "$dst" ] && continue
  mkdir -p "$(dirname "$dst")"
  cp "$src" "$dst"
done

# 5. Configurar opencode.json para cargar el plugin
cat > ~/.config/opencode/opencode.json << 'EOF'
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": [
    "superpowers@git+https://github.com/obra/superpowers.git"
  ]
}
EOF

# 6. Verificar instalación
ls /home/brandall/desarrollo/.agents/skills/
ls /root/.agents/skills/
ls /home/brandall/desarrollo/.agents/skills/code-review-and-quality/
ls /home/brandall/desarrollo/.agents/skills/grill-with-docs/
```

---

## Instalación por Skill

### Marketing & Growth (38 skills)

```bash
# Crear directorio de skills del proyecto
mkdir -p /home/brandall/desarrollo/.agents/skills/

# Todas las skills de marketing
for skill in ab-testing ad-creative ads ai-seo analytics aso brandkit churn-prevention cold-email co-marketing community-marketing content-strategy copy-editing copywriting cro customer-research directory-submissions emails free-tools lead-magnets launch marketing-council marketing-ideas marketing-loops marketing-plan marketing-psychology offers onboarding paywalls popups pricing product-marketing programmatic-seo prospecting public-relations referrals revops sales-enablement schema seo-audit signup site-architecture sms social; do
  mkdir -p /home/brandall/desarrollo/.agents/skills/$skill
  cp /tmp/superpowers/skills/$skill/SKILL.md /home/brandall/desarrollo/.agents/skills/$skill/
done
```

### Design & UI/UX (16 skills)

```bash
# Skills de diseño (proyecto)
for skill in design-taste-frontend gpt-taste high-end-visual-design image image-to-code imagegen-frontend-mobile imagegen-frontend-web industrial-brutalist-ui minimalist-ui redesign-existing-projects stitch-design-taste ui-ux-pro-max; do
  mkdir -p /home/brandall/desarrollo/.agents/skills/$skill
  cp /tmp/superpowers/skills/$skill/SKILL.md /home/brandall/desarrollo/.agents/skills/$skill/
done

# Skills de diseño (globales - disponibles en todos los proyectos)
for skill in animation-vocabulary emil-design-eng frontend-design review-animations; do
  mkdir -p /root/.agents/skills/$skill
  cp /tmp/superpowers/skills/$skill/SKILL.md /root/.agents/skills/$skill/
done
```

### Skills locales instaladas en esta PC (2 skills)

```bash
# Copiar solo si no existen en el proyecto
for skill in code-review-and-quality grill-with-docs; do
  src="/home/proyecto/.agents/skills/$skill/SKILL.md"
  dst="/home/brandall/desarrollo/.agents/skills/$skill/SKILL.md"
  [ -f "$dst" ] && continue
  mkdir -p "$(dirname "$dst")"
  cp "$src" "$dst"
done
```

| Skill | Comando | Descripción |
|-------|---------|-------------|
| `code-review-and-quality` | `cp /home/proyecto/.agents/skills/code-review-and-quality/SKILL.md /home/brandall/desarrollo/.agents/skills/code-review-and-quality/SKILL.md` | Revisión de código y calidad |
| `grill-with-docs` | `cp /home/proyecto/.agents/skills/grill-with-docs/SKILL.md /home/brandall/desarrollo/.agents/skills/grill-with-docs/SKILL.md` | Entrevista para planificar y documentar |

### Development Process (15 skills)

```bash
# Skills de proceso (incluidas con el plugin superpowers)
# Se cargan automáticamente al instalar el plugin en opencode.json
# Ubicación: /root/.cache/opencode/packages/superpowers@git+https:/github.com/obra/superpowers.git/node_modules/superpowers/skills/

# Para forzar instalación manual:
for skill in brainstorming dispatching-parallel-agents executing-plans finishing-a-development-branch full-output-enforcement receiving-code-review requesting-code-review subagent-driven-development systematic-debugging test-driven-development using-git-worktrees using-superpowers verification-before-completion writing-plans writing-skills; do
  mkdir -p /home/brandall/desarrollo/.agents/skills/$skill
  cp /tmp/superpowers/skills/$skill/SKILL.md /home/brandall/desarrollo/.agents/skills/$skill/
done
```

### OpenCode Core Skills (11 skills)

```bash
# Skills preinstaladas en OpenCode - ya disponibles en la sesión
# Ubicación: /root/.config/opencode/skills/
# NO requieren instalación adicional

# Listar todas las skills core:
ls /root/.config/opencode/skills/
```

| Skill | Descripción |
|-------|-------------|
| `api-design-principles` | Diseño de APIs REST y GraphQL |
| `brainstorming` | Exploración creativa antes de implementar |
| `changelog-automation` | Generación automática de changelogs |
| `customize-opencode` | Configuración de opencode |
| `error-handling-patterns` | Patrones de manejo de errores |
| `frontend-design` | Diseño visual para UI |
| `interface-design` | Diseño de interfaces (dashboards, SaaS, etc.) |
| `postgresql` | Diseño de esquemas PostgreSQL |
| `prompt-engineering-patterns` | Optimización de prompts para LLMs |
| `systematic-debugging` | Depuración sistemática de bugs |
| `vercel-react-best-practices` | Mejores prácticas React/Next.js |

---

## Listado Completo de Skills

### Marketing & Growth

| Skill | Comando | Descripción |
|-------|---------|-------------|
| `ab-testing` | `cp /tmp/superpowers/skills/ab-testing/SKILL.md ...` | Tests A/B y experimentos |
| `ad-creative` | `cp /tmp/superpowers/skills/ad-creative/SKILL.md ...` | Creatividad para ads |
| `ads` | `cp /tmp/superpowers/skills/ads/SKILL.md ...` | Campañas publicitarias |
| `ai-seo` | `cp /tmp/superpowers/skills/ai-seo/SKILL.md ...` | SEO para motores de IA |
| `analytics` | `cp /tmp/superpowers/skills/analytics/SKILL.md ...` | Tracking y medición |
| `aso` | `cp /tmp/superpowers/skills/aso/SKILL.md ...` | App Store Optimization |
| `brandkit` | `cp /tmp/superpowers/skills/brandkit/SKILL.md ...` | Brand guidelines |
| `churn-prevention` | `cp /tmp/superpowers/skills/churn-prevention/SKILL.md ...` | Reducción de churn |
| `cold-email` | `cp /tmp/superpowers/skills/cold-email/SKILL.md ...` | Emails fríos B2B |
| `co-marketing` | `cp /tmp/superpowers/skills/co-marketing/SKILL.md ...` | Co-marketing y partners |
| `community-marketing` | `cp /tmp/superpowers/skills/community-marketing/SKILL.md ...` | Gestión de comunidades |
| `content-strategy` | `cp /tmp/superpowers/skills/content-strategy/SKILL.md ...` | Estrategia de contenido |
| `copy-editing` | `cp /tmp/superpowers/skills/copy-editing/SKILL.md ...` | Edición de copy |
| `copywriting` | `cp /tmp/superpowers/skills/copywriting/SKILL.md ...` | Escritura de copy |
| `cro` | `cp /tmp/superpowers/skills/cro/SKILL.md ...` | Optimización de conversión |
| `customer-research` | `cp /tmp/superpowers/skills/customer-research/SKILL.md ...` | Investigación de clientes |
| `directory-submissions` | `cp /tmp/superpowers/skills/directory-submissions/SKILL.md ...` | Envío a directorios |
| `emails` | `cp /tmp/superpowers/skills/emails/SKILL.md ...` | Secuencias de email |
| `free-tools` | `cp /tmp/superpowers/skills/free-tools/SKILL.md ...` | Herramientas gratuitas |
| `lead-magnets` | `cp /tmp/superpowers/skills/lead-magnets/SKILL.md ...` | Lead magnets |
| `launch` | `cp /tmp/superpowers/skills/launch/SKILL.md ...` | Lanzamientos |
| `marketing-council` | `cp /tmp/superpowers/skills/marketing-council/SKILL.md ...` | Consejo de expertos |
| `marketing-ideas` | `cp /tmp/superpowers/skills/marketing-ideas/SKILL.md ...` | Ideas de marketing |
| `marketing-loops` | `cp /tmp/superpowers/skills/marketing-loops/SKILL.md ...` | Workflows recurrentes |
| `marketing-plan` | `cp /tmp/superpowers/skills/marketing-plan/SKILL.md ...` | Planes de marketing |
| `marketing-psychology` | `cp /tmp/superpowers/skills/marketing-psychology/SKILL.md ...` | Psicología del marketing |
| `offers` | `cp /tmp/superpowers/skills/offers/SKILL.md ...` | Diseño de ofertas |
| `onboarding` | `cp /tmp/superpowers/skills/onboarding/SKILL.md ...` | Onboarding de usuarios |
| `paywalls` | `cp /tmp/superpowers/skills/paywalls/SKILL.md ...` | Paywalls y feature gates |
| `popups` | `cp /tmp/superpowers/skills/popups/SKILL.md ...` | Popups y overlays |
| `pricing` | `cp /tmp/superpowers/skills/pricing/SKILL.md ...` | Decisiones de pricing |
| `product-marketing` | `cp /tmp/superpowers/skills/product-marketing/SKILL.md ...` | Marketing de producto |
| `programmatic-seo` | `cp /tmp/superpowers/skills/programmatic-seo/SKILL.md ...` | SEO programático |
| `prospecting` | `cp /tmp/superpowers/skills/prospecting/SKILL.md ...` | Generación de prospects |
| `public-relations` | `cp /tmp/superpowers/skills/public-relations/SKILL.md ...` | PR y earned media |
| `referrals` | `cp /tmp/superpowers/skills/referrals/SKILL.md ...` | Programas de referidos |
| `revops` | `cp /tmp/superpowers/skills/revops/SKILL.md ...` | Revenue operations |
| `sales-enablement` | `cp /tmp/superpowers/skills/sales-enablement/SKILL.md ...` | Collateral de ventas |
| `schema` | `cp /tmp/superpowers/skills/schema/SKILL.md ...` | Schema markup |
| `seo-audit` | `cp /tmp/superpowers/skills/seo-audit/SKILL.md ...` | Auditorías SEO |
| `signup` | `cp /tmp/superpowers/skills/signup/SKILL.md ...` | Optimización de signup |
| `site-architecture` | `cp /tmp/superpowers/skills/site-architecture/SKILL.md ...` | Arquitectura de sitio |
| `sms` | `cp /tmp/superpowers/skills/sms/SKILL.md ...` | Marketing SMS/MMS |
| `social` | `cp /tmp/superpowers/skills/social/SKILL.md ...` | Redes sociales |

### Design & UI/UX

| Skill | Comando | Descripción |
|-------|---------|-------------|
| `animation-vocabulary` | `cp /tmp/superpowers/skills/animation-vocabulary/SKILL.md ...` | Glosario de animaciones |
| `design-taste-frontend` | `cp /tmp/superpowers/skills/design-taste-frontend/SKILL.md ...` | UI/UX Engineer Senior |
| `emil-design-eng` | `cp /tmp/superpowers/skills/emil-design-eng/SKILL.md ...` | Filosofía Emil Kowalski |
| `frontend-design` | `cp /tmp/superpowers/skills/frontend-design/SKILL.md ...` | Diseño visual distintivo |
| `gpt-taste` | `cp /tmp/superpowers/skills/gpt-taste/SKILL.md ...` | Motion engineer GSAP |
| `high-end-visual-design` | `cp /tmp/superpowers/skills/high-end-visual-design/SKILL.md ...` | Diseño de agencia premium |
| `image` | `cp /tmp/superpowers/skills/image/SKILL.md ...` | Imágenes para marketing |
| `image-to-code` | `cp /tmp/superpowers/skills/image-to-code/SKILL.md ...` | Imagen → código web |
| `imagegen-frontend-mobile` | `cp /tmp/superpowers/skills/imagegen-frontend-mobile/SKILL.md ...` | Screens móviles premium |
| `imagegen-frontend-web` | `cp /tmp/superpowers/skills/imagegen-frontend-web/SKILL.md ...` | Referencias de diseño web |
| `industrial-brutalist-ui` | `cp /tmp/superpowers/skills/industrial-brutalist-ui/SKILL.md ...` | Interfaces brutalistas |
| `minimalist-ui` | `cp /tmp/superpowers/skills/minimalist-ui/SKILL.md ...` | Interfaces editoriales |
| `redesign-existing-projects` | `cp /tmp/superpowers/skills/redesign-existing-projects/SKILL.md ...` | Upgrade a calidad premium |
| `review-animations` | `cp /tmp/superpowers/skills/review-animations/SKILL.md ...` | Revisión de animaciones |
| `stitch-design-taste` | `cp /tmp/superpowers/skills/stitch-design-taste/SKILL.md ...` | Design system Stitch |
| `ui-ux-pro-max` | `cp /tmp/superpowers/skills/ui-ux-pro-max/SKILL.md ...` | UI/UX intelligence |

### Development Process

| Skill | Comando | Descripción |
|-------|---------|-------------|
| `brainstorming` | Incluido con plugin | Antes de trabajo creativo |
| `dispatching-parallel-agents` | Incluido con plugin | Tareas paralelas |
| `executing-plans` | Incluido con plugin | Ejecución de planes |
| `finishing-a-development-branch` | Incluido con plugin | Integración de branches |
| `full-output-enforcement` | Incluido con plugin | Código completo sin truncar |
| `receiving-code-review` | Incluido con plugin | Manejo de feedback |
| `requesting-code-review` | Incluido con plugin | Solicitud de review |
| `subagent-driven-development` | Incluido con plugin | Desarrollo con subagentes |
| `systematic-debugging` | Incluido con plugin | Debugging sistemático |
| `test-driven-development` | Incluido con plugin | TDD |
| `using-git-worktrees` | Incluido con plugin | Workspaces aislados |
| `using-superpowers` | Incluido con plugin | Guía del sistema |
| `verification-before-completion` | Incluido con plugin | Verificación pre-merge |
| `writing-plans` | Incluido con plugin | Escritura de planes |
| `writing-skills` | Incluido con plugin | Creación de skills |

### OpenCode Core Skills

| Skill | Descripción |
|-------|-------------|
| `api-design-principles` | Diseño de APIs REST y GraphQL |
| `brainstorming` | Exploración creativa antes de implementar |
| `changelog-automation` | Generación automática de changelogs |
| `customize-opencode` | Configuración de opencode |
| `error-handling-patterns` | Patrones de manejo de errores |
| `frontend-design` | Diseño visual para UI |
| `interface-design` | Diseño de interfaces (dashboards, SaaS, etc.) |
| `postgresql` | Diseño de esquemas PostgreSQL |
| `prompt-engineering-patterns` | Optimización de prompts para LLMs |
| `systematic-debugging` | Depuración sistemática de bugs |
| `vercel-react-best-practices` | Mejores prácticas React/Next.js |

---

## Estructura de Directorios

```
~/.config/opencode/
├── opencode.json              # Config con plugin superpowers
└── plugins/
    └── claude-mem.js          # Plugin de memoria

/home/brandall/desarrollo/.agents/skills/   # Skills de proyecto
├── ab-testing/SKILL.md
├── ad-creative/SKILL.md
├── ads/SKILL.md
└── ... (56 skills)

/root/.agents/skills/                       # Skills globales
├── animation-vocabulary/SKILL.md
├── emil-design-eng/SKILL.md
├── frontend-design/SKILL.md
└── ... (16 skills)

/root/.cache/opencode/packages/superpowers@*/  # Plugin superpowers
└── node_modules/superpowers/skills/           # Skills de proceso
    ├── brainstorming/SKILL.md
    ├── systematic-debugging/SKILL.md
    └── ... (15 skills)
```

---

## Verificar Instalación

```bash
# Contar skills instaladas
echo "Skills de proyecto:"
ls /home/brandall/desarrollo/.agents/skills/ | wc -l

echo "Skills globales:"
ls /root/.agents/skills/ | wc -l

echo "Skills de superpowers:"
ls /root/.cache/opencode/packages/superpowers@git+https:/github.com/obra/superpowers.git/node_modules/superpowers/skills/ | wc -l

# Listar todas
ls /home/brandall/desarrollo/.agents/skills/
ls /root/.agents/skills/
```

---

## Licencia

MIT
