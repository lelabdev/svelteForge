# 🧪 SVELTE-FORGE

A CLI boilerplate generator for SvelteKit projects using modular fragments.  
Install a fresh SvelteKit app and enrich it with optional features like auth,
UI libraries, state management, and more — all from one command.

🌐 ## Landing Page
[https://svelteforge.lelab.dev/](https://svelteforge.lelab.dev/)

---

---

## 🚀 How It Works

This CLI tool:

1. Prompts you for your project name.
2. Bootstraps a fresh SvelteKit app using `pnpm create svelte@latest`.
3. Installs dependencies via `pnpm install`.
4. Asks which optional fragments (features) you want to add.
5. Copies relevant code from `fragments/` and installs required packages.

---

## 🛠 Usage

```bash
pnpm dlx tsx index.ts
```

```bash
p dlx tsx ~/1Dev/Projects/Lelab/SvelteForge/svelteForge/index.ts
```

Then follow the prompts:

📦 Project name

✅ Choose optional features

---

📁 Project Structure

.
├── index.ts # Main CLI entry
├── fragments.json # List of available fragments
├── fragments/
│ ├── sessionstore/
│ │ └── src/ # Code to inject into the generated SvelteKit project
│ ├── skeletonui/
│ └── betterauth/
└── ...

---

## 🧩 How to Add or Update a Fragment

When adding a new fragment or updating an existing one, follow these steps:

1. Create or update the code in fragments/<your-fragment>/src/

This folder should mirror the structure you want injected into the src/
of the generated project.

Example: fragments/supabase/src/lib/supabase.ts will end up in my-project/src/lib/supabase.ts.

2. Add or update the entry in fragments.json

Each fragment must be declared in this file with:

name: folder name inside /fragments

label: question shown to the user

default: whether to pre-select it

dependencies: list of NPM packages (optional)

Example:

```json
{
  "name": "supabase",
  "label": "Add Supabase integration?",
  "default": false,
  "dependencies": ["@supabase/supabase-js"]
}
```

> 🔥 Don’t forget: if you don’t add the fragment here, it won’t show up in the CLI!

3. (Optional) Update package.json of the CLI itself

If your CLI needs runtime dependencies (e.g. uuid, prompts, etc.), add them with:

pnpm add your-package

> But most fragment-specific dependencies are handled during project generation,
> not in the CLI's own package.json.

---

📦 Dependencies

All dependencies defined in fragments.json are automatically installed with:

`pnpm add ...`

You don’t need to install them manually.

---

## 🧽 Tips

Keep fragments atomic and reusable

Avoid mixing unrelated logic in one fragment

Test fragment installation after updating it

Use meaningful labels so users understand what they’re enabling

---

## 📣 License

MIT — build cool things and share freely!

---

Created by [LeLab](https://lelab.dev)  
Code & issues: [github.com/lelab](https://github.com/lelab)
Created by [LeLab](https://lelab.dev)  
Code & issues: [github.com/lelab](https://github.com/lelab)
