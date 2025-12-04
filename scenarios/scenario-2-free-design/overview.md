← [Repository Root](../README.md)

---

### Scenario 2 — Free Design Site Creation (Custom Figma Designs)


Websites in this scenario are designed from scratch in Figma, without the constraints of the White Label Component Library. Designers explore unique layouts, custom visual styles, and creative storytelling elements. Once the design is approved, developers traditionally translate the Figma file into code, implement responsive behavior, build all components manually, and integrate the final output into the CMS. This approach offers maximum creative freedom but is also the most time-consuming and error-prone in terms of translating design to functional code.

AI tools can accelerate parts of this workflow, but not through automation — **through assisted slicing and structured handoff**. Several tools were tested to evaluate real-world feasibility.

---

### **1. Builder.io (Figma Plugin + Flux) — Most Promising and Most Accurate**

Builder.io was tested using the specification described in the document:
[https://docs.google.com/document/d/1CHxWd5ItlKAqWnc7XJ0i7RBTCjF5kKM3KS7SjUTil2k/](https://docs.google.com/document/d/1CHxWd5ItlKAqWnc7XJ0i7RBTCjF5kKM3KS7SjUTil2k/)

A template Astro project with Builder.io rules was prepared:
[https://github.com/dejstdm/astro-brand-starter--test-4](https://github.com/dejstdm/astro-brand-starter--test-4)

These rules guide the AI on:

* how components must be created
* how structure and constraints map from Figma to code
* how typography, spacing, colors, and component patterns should behave

**Key Findings:**

* With a correctly prepared Figma file (following the rules above), Builder.io achieves **very high accuracy** — close to pixel-perfect.
* The process is *not automated*. Each component still needs to be manually:

  * copy/pasted from Figma into Builder.io
  * assigned correct component type
  * connected to the design system tokens
* Builder.io’s Figma plugin requires designers to:

  * copy/paste the Typography frame and let Builder.io create a typography system
  * copy/paste the Colors frame and let Builder.io generate color variables
  * import spacing and other primitives manually

This significantly accelerates the slicing process but **does not eliminate it**.

**Figma file used for testing:**
[https://www.figma.com/design/BQVTUivEIwMe4bdk9H72ml/Builder.io-test](https://www.figma.com/design/BQVTUivEIwMe4bdk9H72ml/Builder.io-test)

When all instructions were correctly followed, the result was “almost perfect,” but still not automatic conversion.
Builder.io remains the strongest candidate today because:

* it supports **two-way Git integration**
* it supports **more than 10 frontend frameworks**, including **Astro**, which outputs code closest to plain HTML or Twig-like structures
* it allows highly customized AI rules defined at the project level

---

### **2. Figma Make — Strong Figma Integration, but Not Mature Yet**

Figma Make was tested using this design file:
[https://www.figma.com/design/O5IQr5UDBoQKiL4uFDQvga/eCommerce-Website-%7C-Web-Page-Design-%7C-UI-KIT-%7C-Interior-Landing-Page--Community-](https://www.figma.com/design/O5IQr5UDBoQKiL4uFDQvga/eCommerce-Website-%7C-Web-Page-Design-%7C-UI-KIT-%7C-Interior-Landing-Page--Community-)

**Key Findings:**

* Figma Make recreated the page with React components surprisingly well for basic structures.
* However, it failed on more complex elements — especially the slider in the *Inspiration* section, which could not be made functional or visually correct despite multiple prompts and detailed instructions.
* This is likely because Figma Make relies on a **limited internal component set**, and if a design doesn’t match those components, it struggles to reproduce it accurately.
* Figma Make currently has a **one-way Git integration**:

  * You can open a Git repo inside Figma Make
  * But you cannot push changes back smoothly
    This severely limits real-world workflow usability.

Still, because Figma Make is a **native Figma tool**, and Figma is actively developing it, its accuracy and usefulness will likely improve.

---

### **3. Other Tools (e.g., Rocket.new, Lovable)**

**Lovable**

* Not useful for this scenario.
* Its generation style is too opinionated and not focused on replicating precise designs.

**Rocket.new**

* Works well with direct Figma file links.
* Generates clean React + Tailwind code.
* But interpretation is **too loose**.
* Result is visually nice, but nowhere near pixel-perfect.
* Not suitable when accurate implementation of a client-approved Figma design is required.

---

### **Conclusion for Scenario 2**

AI cannot automate custom design-to-code conversion, but it *can* substantially accelerate slicing when:

* design follows a strict Figma specification
* Builder.io project includes well-defined AI rules
* components and tokens are imported with a controlled workflow

**Builder.io is currently the most viable option**, especially when using:

* Astro output (for HTML/Twig-like flexibility)
* Two-way Git integration
* A structured Figma preparation workflow

Figma Make is promising but not reliable enough yet for client-facing production work.






### **Important Note on Architecture**

In Scenario 2, the objective is to extract high-quality frontend code from a Figma design and then integrate that code into our **existing Drupal-based workflow**. Because the final output is standard HTML/React/Astro code that we manually adapt into our current system, **there is no requirement to switch Drupal to headless mode**. The CMS continues to operate in the traditional, theme-based rendering model, and the AI-generated code simply accelerates the slicing and component-building phase.

In other words:
**Scenario 2 focuses on speeding up front-end production from custom designs, not on altering the underlying Drupal architecture.**



