← [Repository Root](../README.md)

---

### Scenario 1 – White Label Site Creation

Websites are built using the predefined White-Label Component Library. Designers work within strict component boundaries, selecting existing blocks and variations rather than creating new layouts from scratch. This approach ensures fast development, consistent branding, predictable QA, and low engineering cost, but limits visual creativity. 


## AI Acceleration Opportunities for Scenario 1 - White Label Site Creation
- [1. Layout Assembly (partially validated in tests)](option-1.md)
- [2. Additional Opportunity: Theme Builder for Existing Components (Non-AI)](option-2.md)
- [3. AI-Generated UI Implementations for Backend Component Contracts](option-3.md)



## Prerequisites Before Implementing Scenario 1 Opportunities

Today, our websites are built in a traditional Drupal way: Drupal acts as both the CMS and the rendering layer, and the frontend is delivered through a Drupal theme (Twig templates). This setup is stable, well-understood, and works reliably for our current projects.

However, all opportunities described under Scenario 1 – White Label Site Creation assume a different architecture: Drupal used as a headless CMS and a separate Next.js frontend consuming its content via APIs. In other words, Drupal would focus only on managing and exposing content, while Next.js would take over all rendering and presentation responsibilities.([v3.gatsbyjs.com](https://v3.gatsbyjs.com/docs/glossary/decoupled-drupal/?utm_source=chatgpt.com))

Before any of the Scenario 1 features (AI layout assembly, Theme Builder, or AI-generated UI implementations) can be planned or developed, the following foundational work is required:

### 1\. Moving from Traditional Drupal to Headless / Decoupled Drupal

* Enable and configure Drupal’s API layer (JSON:API, REST, or GraphQL) to expose all relevant content, components, and configuration needed by the frontend.([xerago.com](https://www.xerago.com/xtelligence/headless-drupal?utm_source=chatgpt.com))  
* Define how pages, blocks, and reusable components are represented in the API (including ordering, nesting, translations, and market variations).  
* Accept that Drupal will no longer be responsible for rendering HTML; it will serve structured data that a separate frontend application consumes.

Drupal is widely used in this way and is considered a valid and mature option for a headless CMS, thanks to its API-first capabilities and existing ecosystem around decoupled stacks.([acquia.com](https://www.acquia.com/blog/decoupled-vs-headless-cms?utm_source=chatgpt.com))

### 2\. Introducing a Next.js Frontend with SSR

* Build a Next.js application that consumes Drupal APIs and renders all pages and components on the frontend.  
* Implement server-side rendering (SSR) and/or incremental static regeneration (ISR) for SEO, performance, and first-load speed, following modern industry practices for React-based frontends.([Unimity](https://unimity.com/insights/decoupled-drupal-architecture?utm_source=chatgpt.com))  
* Create a mapping layer that takes Drupal’s headless output (e.g., an ordered list of components for a page) and renders the corresponding React components in the correct order and with the correct props.

### 3\. Caching and Performance Strategy

In a headless setup, we lose Drupal’s traditional page rendering and theming layer, but we do not lose caching entirely. Instead, caching needs to be redesigned:

* Cache API responses on the Drupal side where possible.  
* Use edge/CDN caching and Next.js features (SSR/ISR) to achieve fast page loads and good Core Web Vitals.([Fabrity](https://fabrity.com/drupal-headless-explained-when-to-go-decoupled-and-when-not-to/?utm_source=chatgpt.com))  
* Define how content invalidation, revalidation, and “clear cache” operations propagate from Drupal to the Next.js frontend.

This is more complex than the classic “Drupal \+ Twig \+ page cache” model and requires careful planning.

### 4\. Rebuilding “Out-of-the-Box” Drupal Features on the Frontend

In a traditional Drupal theme, many features come “for free”: menus, breadcrumbs, SEO meta output, content preview, display modes, and layout controls. In a headless architecture, a lot of this must be rebuilt or re-integrated on the frontend side:([Fabrity](https://fabrity.com/drupal-headless-explained-when-to-go-decoupled-and-when-not-to/?utm_source=chatgpt.com))

* navigation and menu rendering  
* SEO metadata handling (titles, descriptions, canonical URLs, Open Graph, etc.)  
* content preview and editorial workflows  
* error states, 404/500 pages, redirects, and localization behavior

These are not blockers, but they are additional engineering cost that must be acknowledged up front.

### 5\. Editorial and Workflow Considerations

* Editors are used to seeing a near-final preview of the page inside Drupal. In a headless model, preview needs to be implemented between Drupal and Next.js (for example, via dedicated preview routes or tools like “Next.js for Drupal”).([Drupal.org](https://www.drupal.org/docs/develop/decoupled-drupal/decoupled-drupal-stacks?utm_source=chatgpt.com))  
* Changes in component order (e.g., moving the FAQ section above the product slider) must be reflected in the API payload and respected by the Next.js rendering layer.  
* Training and documentation are needed so editors understand what remains in Drupal and what moves to the frontend application.

---

### Is Drupal a Valid Option for a Headless Approach?

Yes. Drupal is considered a strong choice for headless/decoupled architectures because it is API-first, exposes content via JSON:API, REST, or GraphQL, and has dedicated tooling such as Next.js for Drupal that focuses on seamless editing, preview, and multi-site headless setups.([acquia.com](https://www.acquia.com/blog/decoupled-vs-headless-cms?utm_source=chatgpt.com))

The trade-off is not about “Can Drupal do it?” but about increased complexity and cost: decoupling adds an extra frontend stack, requires reimplementation of some “out-of-the-box” features, and makes sense primarily when we want modern frontend capabilities, multi-channel delivery, or the kind of AI/React-based workflows described in Scenario 1.([Fabrity](https://fabrity.com/drupal-headless-explained-when-to-go-decoupled-and-when-not-to/?utm_source=chatgpt.com))  