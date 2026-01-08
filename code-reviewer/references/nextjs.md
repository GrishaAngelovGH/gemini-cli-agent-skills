# Next.js Review Checklist

## 1. App Router & React Server Components (RSC)
- [ ] **Component Strategy:** Are components Server Components by default? Is `"use client"` only used when necessary (interactivity, hooks, browser APIs)?
- [ ] **Data Fetching:** Is data fetched on the server where possible?
- [ ] **Caching:** Are `fetch` requests utilizing Next.js caching and revalidation properly?

## 2. Performance & Optimization
- [ ] **next/image:** Is the `Image` component used for automatic optimization and preventing layout shift?
- [ ] **next/link:** Is `Link` used for client-side navigation?
- [ ] **Streaming:** Is `Suspense` used for granular loading states (streaming)?
- [ ] **Dynamic Imports:** Are large client components imported using `next/dynamic`?

## 3. SEO & Metadata
- [ ] **Metadata API:** Is the static or dynamic `metadata` object used instead of `<Head>` (for App Router)?
- [ ] **Sitemaps/Robots:** Are `sitemap.ts` and `robots.ts` implemented?

## 4. Server Actions
- [ ] **Security:** Are Server Actions protected by authorization checks?
- [ ] **Validation:** Is input data validated (e.g., with Zod) inside the action?
