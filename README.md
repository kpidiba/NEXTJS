# ▲ Next.js - Guide Complet de Veille Technologique 2026

Bienvenue dans mon document de suivi pour Next.js. Ce README est conçu pour centraliser toutes les connaissances essentielles, des fondamentaux aux fonctionnalités les plus avancées, en passant par les nouveautés des versions 15 et 16, et les ressources pour rester à jour.

---

## 📋 Table des Matières

1. [Fondamentaux Core](#-1-fondamentaux-core)
2. [Nouvelles Fonctionnalités par Version](#-2-nouvelles-fonctionnalités-par-version)
3. [Fonctionnalités Avancées & Design Patterns](#-3-fonctionnalités-avancées--design-patterns)
4. [Bibliothèques & Écosystème](#-4-bibliothèques--écosystème)
5. [Ce qui Change / Ce qui Disparaît](#-5-ce-qui-change--ce-qui-disparaît)
6. [Roadmap 2026-2027](#-6-roadmap-2026-2027)
7. [Ressources pour la Veille](#-7-ressources-pour-la-veille)

---

## 🧱 1. Fondamentaux Core

### Architecture Moderne (App Router)

- [ ] **App Router (par défaut)** : Comprendre que l'App Router est maintenant le standard. Le Pages Router est en mode maintenance.
- [ ] **Conventions de fichiers** :
  - [ ] `page.tsx` : Créer une route accessible.
  - [ ] `layout.tsx` : Interface partagée entre plusieurs pages.
  - [ ] `loading.tsx` : UI de chargement (basé sur Suspense).
  - [ ] `error.tsx` : UI d'erreur (basé sur Error Boundaries).
  - [ ] `not-found.tsx` : Page 404 personnalisée.
  - [ ] `route.ts` : API Routes (Route Handlers).

### Paradigmes de Rendu

- [ ] **Server Components (par défaut)** : Les composants sont rendus sur le serveur par défaut. Ils peuvent être `async` et accéder directement aux ressources serveur (base de données, fichiers système).
- [ ] **Client Components** : Utiliser le directive `"use client"` pour les composants qui nécessitent de l'interactivité (hooks React, événements, état local).
- [ ] **Static Site Generation (SSG)** : Pages générées à la build.
- [ ] **Server-Side Rendering (SSR)** : Pages rendues à chaque requête.
- [ ] **Incremental Static Regeneration (ISR)** : Mise à jour des pages statiques après la build.

### Data Fetching & Caching

- [ ] **`fetch()` avec Next.js** : Comprendre l'extension de l'API `fetch` native.
  - [ ] `{ cache: 'force-cache' | 'no-store' }`
  - [ ] `{ next: { revalidate: number } }` (ISR)
  - [ ] `{ next: { tags: string[] } }` (Revalidation par tag)
- [ ] **Directive `"use cache"` (Cache Components)** : Nouveau modèle de caching explicite [citation:1].
  - [ ] Niveau fichier : `'use cache'` en tête de fichier.
  - [ ] Niveau composant/fonction : `async function MyComponent() { 'use cache' }`.
- [ ] **Server Actions** : Fonctions qui s'exécutent sur le serveur, appelables depuis le client.
  - [ ] Directive `"use server"`.
  - [ ] Mutations de données et formulaires.

### APIs Dynamiques (Breaking Change v15+)

- [ ] **Async Request APIs** : Depuis Next.js 15, les APIs suivantes sont asynchrones [citation:7][citation:10] :
  - [ ] `await cookies()`
  - [ ] `await headers()`
  - [ ] `await draftMode()`
  - [ ] `await params` (dans les pages/layouts)
  - [ ] `await searchParams` (dans les pages)

### Configuration Projet

- [ ] **`create-next-app` par défaut** : Nouveau projet avec App Router, TypeScript, Tailwind CSS, et ESLint préconfigurés [citation:1].

---

## 🚀 2. Nouvelles Fonctionnalités par Version

### ✅ Next.js 14 (Octobre 2023)

- [x] **Turbopack (dev)** : 53% de démarrage plus rapide, 94% de mise à jour plus rapide.
- [x] **Server Actions (stable)** : Mutations serveur.
- [x] **Partial Prerendering (PPR) (preview)** : Combinaison de static et dynamic dans une même page.

### ✅ Next.js 15 (Mai 2025)

- [x] **React 19** : Support minimum de React 19.
- [x] **Async Request APIs** : `cookies()`, `headers()`, `params`, `searchParams` deviennent asynchrones [citation:7].
- [x] **`@next/font` intégré à `next/font`** : Plus besoin du package séparé.
- [x] **`fetch()` non caché par défaut** : Changement majeur du modèle de caching [citation:7].
- [x] **`useActionState()`** : Remplace `useFormState()` [citation:7].
- [x] **Turbopack pour les builds (beta)** : `next build --turbopack`.

### ✅ Next.js 16 (Octobre 2025 - Actuel)

- [x] **Turbopack stable par défaut** : Remplacer Webpack comme bundler par défaut [citation:1][citation:5][citation:8].
  - [x] Fast Refresh 10x plus rapide.
  - [x] Builds production 2x à 5x plus rapides.
  - [x] Cache filesystem pour les redémarrages.
- [x] **Cache Components** : Nouveau modèle avec directive `"use cache"` [citation:1][citation:5][citation:8].
  - [x] `'use cache'` pour le caching explicite.
  - [x] `revalidateTag(tag, profile)` avec profils ('hours', 'days').
  - [x] `updateTag(tag)` : Mise à jour immédiate du cache.
  - [x] `refresh()` : Re-fetch sans invalider le cache.
- [x] **React Compiler (stable)** : Mémorisation automatique, plus besoin de `useMemo`/`useCallback` manuels [citation:1][citation:5].
- [x] **`proxy.ts` remplace `middleware.ts`** : Nouveau nom pour clarifier la couche réseau [citation:1].
- [x] **Améliorations du routage** [citation:1][citation:5] :
  - [x] Déduplication des layouts (téléchargés une seule fois).
  - [x] Préfetch incrémental (segments non-cachés uniquement).
- [x] **Next.js DevTools MCP** : Intégration IA pour le debugging (contexte routing, caching) [citation:1].
- [x] **Build Adapters API (alpha)** : Personnalisation pour plateformes d'hébergement [citation:1][citation:8].
- [x] **React 19.2** : View Transitions API, `useEffectEvent`, composant `<Activity/>` [citation:1][citation:8].
- [x] **Node.js 20+ requis** : Drop support Node.js 18 [citation:1].

### 🔄 Next.js 17 (Prévu 2026)

- [ ] **Stabilisation des Build Adapters**.
- [ ] **Améliorations de l'hydratation partielle**.
- [ ] **Support étendu des Web Components**.

---

## 🏗️ 3. Fonctionnalités Avancées & Design Patterns

### Optimisation des Performances

- [ ] **Turbopack configuration avancée** :
  - [ ] `turbopackFileSystemCacheForDev: true` pour cache persistant [citation:1].
  - [ ] Fallback Webpack si nécessaire (`turbopack: false`) [citation:1].
- [ ] **React Compiler** : Activer avec `reactCompiler: true` dans `next.config.ts` [citation:1].
- [ ] **`<Image />`** : Optimisation automatique des images.
- [ ] **`<Script />`** : Chargement optimisé des scripts tiers.
- [ ] **`@next/third-parties`** : Chargement optimisé des bibliothèques tierces (Google Tag Manager, Analytics, YouTube, Maps) [citation:6].

### Patterns de Caching Avancés

- [ ] **Partial Prerendering (PPR)** : Combiner static et dynamic dans une même page.
- [ ] **Cache Components avec profils** :

```ts
'use cache'
async function getData() {
  'use cache';
  revalidateTag('data', 'hours'); // Revalidation après quelques heures
  return await fetch('https://api.example.com/data').then(r => r.json());
}
```

- **Revalidation stratégique** : Combiner `revalidateTag`, `updateTag` et `refresh()` selon les cas d'usage.

### Authentification & Sécurité

- **Better-Auth** : Solution moderne avec tokens et OAuth 2.1 [](https://dev.to/mrakdon/the-ultimate-nextjs-14-tech-stack-for-2026-a-state-of-the-union-4498).

- **Auth.js (ex-NextAuth)** : Pour l'intégration SSO entreprise.

- **Clerk** : Solution complète avec `auth()` asynchrone [](https://clerk.com/docs/guides/development/upgrading/upgrade-guides/nextjs-v6).

- **Middleware (désormais `proxy.ts`)** : Protection des routes, redirections.

### Tests

- **Vitest** : Tests unitaires rapides.

- **Playwright** : Tests E2E.

- **Testing Library** : Tests de composants React.

---

## 📚 4. Bibliothèques & Écosystème

### UI et Styling

- **Tailwind CSS** : Par défaut avec `create-next-app` [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)[](https://dev.to/mrakdon/the-ultimate-nextjs-14-tech-stack-for-2026-a-state-of-the-union-4498).

- **Shadcn UI** : 100+ composants réutilisables [](https://dev.to/mrakdon/the-ultimate-nextjs-14-tech-stack-for-2026-a-state-of-the-union-4498).

- **NextUI** : Bibliothèque de composants moderne.

- **Radix UI** : Composants headless accessibles.

- **Framer Motion** : Animations.

### Base de données & ORM

- **PostgreSQL** : Standard de l'industrie [](https://dev.to/mrakdon/the-ultimate-nextjs-14-tech-stack-for-2026-a-state-of-the-union-4498).

- **Drizzle ORM** : Type-safe, zéro runtime overhead [](https://dev.to/mrakdon/the-ultimate-nextjs-14-tech-stack-for-2026-a-state-of-the-union-4498).

- **Prisma** : Alternative mature.

- **Supabase** : Backend-as-a-Service avec PostgreSQL.

### State Management

- **Zustand** : Léger, simple, parfait avec Server Components [](https://dev.to/mrakdon/the-ultimate-nextjs-14-tech-stack-for-2026-a-state-of-the-union-4498).

- **TanStack Query** : Gestion d'état serveur.

- **Jotai** : Atomique, inspiré de Recoil.

### Formulaires

- **React Hook Form** : Performant avec validation.

- **Zod** : Validation de schémas type-safe.

- **Conform** : Validation côté serveur pour les Server Actions.

### Outils de développement

- **Next.js DevTools** : Avec intégration MCP pour l'IA [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging).

- **v0 (Vercel)** : Génération UI par IA.

- **Clerk Dashboard** : Gestion des utilisateurs.

### Concurrents émergents (Veille)

- **vinext (Cloudflare)** : Framework Vite-based compatible Next.js, builds 4x plus rapides selon benchmarks [](https://itbrief.com.au/story/cloudflare-unveils-vinext-a-vite-based-next-js-rival).
  
  - Vite 8 + Rolldown.
  
  - Déploiement natif sur Workers.
  
  - KV cache handler pour ISR.

---

## ⚠️ 5. Ce qui Change / Ce qui Disparaît

### Déprécié (à ne plus utiliser)

- ❌ **Pages Router** : Plus le défaut, en mode maintenance.

- ❌ **`middleware.ts`** : Remplacé par `proxy.ts` (Next.js 16+) [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging).

- ❌ **Node.js 18** : Version minimale requise : 20.9+ [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging).

- ❌ **Support AMP** : Retiré dans Next.js 16 [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging).

- ❌ **`next lint` command** : Dépréciée [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)[](https://nextjs.org/blog).

- ❌ **`@next/font`** : Remplacé par `next/font` [](https://nextjs.org/docs/app/guides/upgrading/version-15).

- ❌ **`useFormState()`** : Remplacé par `useActionState()` [](https://nextjs.org/docs/app/guides/upgrading/version-15).

### Changements majeurs (à migrer)

- 🔄 **APIs synchrones** : `cookies()`, `headers()`, `params` doivent être `await` [](https://nextjs.org/docs/app/guides/upgrading/version-15)[](https://clerk.com/docs/guides/development/upgrading/upgrade-guides/nextjs-v6).

- 🔄 **`fetch()` caching** : Plus caché par défaut, utiliser `cache: 'force-cache'` si besoin [](https://nextjs.org/docs/app/guides/upgrading/version-15).

- 🔄 **Route Handlers GET** : Plus cachés par défaut, utiliser `dynamic = 'force-static'` pour le caching [](https://nextjs.org/docs/app/guides/upgrading/version-15).

- 🔄 **Client-side Router Cache** : Pages non mises en cache par défaut (sauf backward/forward navigation) [](https://nextjs.org/docs/app/guides/upgrading/version-15).

### Évolutions

- 🔄 **Turbopack** : Devient le bundler par défaut (Webpack toujours disponible en fallback) [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging).

- 🔄 **Caching** : Passe d'implicite à explicite avec `"use cache"` [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)[](https://comate.baidu.com/zh/page/279eh86weoh).

- 🔄 **Middleware** : Renommé `proxy.ts` pour clarifier son rôle réseau [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging).

---

## 🗺️ 6. Roadmap 2026-2027

### Next.js 16.x (2026)

- **Stabilisation des Build Adapters**.

- **Améliorations du React Compiler**.

- **Nouvelles intégrations `@next/third-parties`** [](https://nextjs.org/docs/app/guides/third-party-libraries).

### Next.js 17 (Fin 2026)

- **Support natif amélioré des Web Components**.

- **Hydratation partielle avancée**.

- **Optimisations Turbopack supplémentaires**.

### Écosystème à surveiller

- **vinext (Cloudflare)** : Framework concurrent basé sur Vite, à surveiller pour adoption [](https://itbrief.com.au/story/cloudflare-unveils-vinext-a-vite-based-next-js-rival).

- **React 20** : Nouvelles fonctionnalités à venir.

- **Turbopack vs. Vite/Rolldown** : La guerre des bundlers continue.

---

## 📺 7. Ressources pour la Veille

### YouTube (Chaînes essentielles)

| Chaîne                                                          | Spécialité                                         | Niveau                                                                                                              |
| --------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **[Lee Robinson](https://youtube.com/@leerobinson)**            | VP Developer Experience Vercel, roadmap officielle | Tous                                                                                                                |
| **[Delba de Oliveira](https://youtube.com/@delba)**             | Tutoriels App Router, Server Actions               | Intermédiaire                                                                                                       |
| **[Theo - t3․gg](https://youtube.com/@t3dotgg)**                | Analyses opinions, actualités écosystème           | Avancé                                                                                                              |
| **[Fireship](https://youtube.com/@Fireship)**                   | News rapides (100 seconds), concepts clés          | Tous [](https://tripleten.com/blog/posts/the-best-tech-youtube-channels-for-coders-of-all-levels)                   |
| **[Web Dev Simplified](https://youtube.com/@WebDevSimplified)** | Tutoriels React/Next.js concis                     | Débutant/Intermédiaire [](https://tripleten.com/blog/posts/the-best-tech-youtube-channels-for-coders-of-all-levels) |
| **[Traversy Media](https://youtube.com/@TraversyMedia)**        | Tutoriels approfondis (1-3h)                       | Intermédiaire/Avancé [](https://tripleten.com/blog/posts/the-best-tech-youtube-channels-for-coders-of-all-levels)   |
| **[Net Ninja](https://youtube.com/@NetNinja)**                  | Crash courses, playlists thématiques               | Tous [](https://tripleten.com/blog/posts/the-best-tech-youtube-channels-for-coders-of-all-levels)                   |
| **[Code with Ania Kubów](https://youtube.com/@AniaKubow)**      | Projets ludiques, couvre Next.js                   | Débutant/Intermédiaire [](https://tripleten.com/blog/posts/the-best-tech-youtube-channels-for-coders-of-all-levels) |

### Experts à suivre (X/Twitter, LinkedIn, Blogs)

- **Lee Robinson** (@leeerob) - Vercel

- **Delba de Oliveira** (@delba_oliveira)

- **Tim Neutkens** (@timneutkens) - Cocréateur Next.js

- **Sebastian Markbåge** (@sebmarkbage) - React team

- **Guillermo Rauch** (@rauchg) - CEO Vercel

- **Josh W. Comeau** (@JoshWComeau) - Tutoriels React/Next.js

### Sites & Blogs officiels

- **[Next.js Blog](https://nextjs.org/blog)** : Source primaire [](https://nextjs.org/blog).

- **[Vercel Blog](https://vercel.com/blog)** : Annonces et études de cas.

- **[React Blog](https://react.dev/blog)** : Pour suivre les évolutions de React.

### Communautés & Newsletters

- **[Next.js Weekly](https://nextjsweekly.com/)** : Newsletter hebdomadaire.

- **[r/nextjs](https://reddit.com/r/nextjs)** : Communauté Reddit.

- **[Next.js Discord](https://nextjs.org/discord)** : Communauté officielle.

- **[This Week in React](https://thisweekinreact.com/)** : Newsletter React/Next.js.

### Outils de veille technique

- **[GitHub Next.js releases](https://github.com/vercel/next.js/releases)** : Suivre les releases.

- **[Next.js RFCs](https://github.com/vercel/next.js/discussions/categories/rfc)** : Propositions de fonctionnalités.

- **[Canary releases](https://www.npmjs.com/package/next?activeTab=versions)** : Tester les fonctionnalités en avant-première.

- **[shadcn toolkit](https://shadcnuikit.com/)** : TOOLKIT TO DEVELOP INTERFACES WITH SHADCN

### TEMPLATES

- **[SHADCN STORE CHEATSEET](https://shadcnstore.com/cheatsheet/)** : SHADCN STORE CHEATSEET

- [http://getnextjstemplates.com/](http://getnextjstemplates.com/)

---

## ✅ Ma Checklist de Compétences Next.js 2026

### Niveau Débutant

- Créer une app avec `create-next-app`

- Comprendre la différence Server/Client Components

- Créer des routes avec l'App Router (`page.tsx`, `layout.tsx`)

- Utiliser `fetch` avec les options de cache

- Naviguer avec `<Link>` et `useRouter`

- Styliser avec Tailwind CSS

### Niveau Intermédiaire

- Maîtriser les APIs asynchrones (`await cookies()`, `await params`)

- Implémenter des Server Actions

- Utiliser la directive `"use cache"` (Cache Components)

- Configurer Turbopack et le React Compiler

- Gérer l'authentification (Better-Auth, Clerk, Auth.js)

- Optimiser les images et scripts tiers

### Niveau Avancé

- Architecture complexe avec PPR (Partial Prerendering)

- Stratégies de caching avancées (`revalidateTag`, `updateTag`, `refresh`)

- Intégration base de données avec Drizzle ORM

- Configuration de `proxy.ts` pour l'authentification

- Build Adapters API pour déploiement personnalisé

- Debugging avec Next.js DevTools MCP et IA

- Migration de Pages Router vers App Router

---

## 📊 Comparatif rapide : Next.js 15 → 16

| Aspect             | Next.js 15                           | Next.js 16                                                                                                                                                                             |
| ------------------ | ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bundler**        | Webpack (défaut), Turbopack (option) | Turbopack (défaut) [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)                                                           |
| **Caching**        | Implicite, parfois complexe          | Explicite avec `"use cache"` [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)[](https://comate.baidu.com/zh/page/279eh86weoh) |
| **Middleware**     | `middleware.ts`                      | `proxy.ts` [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)                                                                   |
| **React Compiler** | Optionnel                            | Stable et recommandé [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)                                                         |
| **Build time**     | Référence                            | 2x à 5x plus rapide [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)                                                          |
| **Node.js**        | 18+                                  | 20.9+ [](https://www.syncfusion.com/blogs/post/whats-new-in-next-js-16-turbo-builds-smart-caching-ai-debugging)                                                                        |

---

*Dernière mise à jour : Février 2026*
