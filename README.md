# WP Landing Page

A WordPress landing page starter kit plugin built with [RollupJS](https://rollupjs.org/), [TailwindCSS](https://tailwindcss.com/) and [AlpineJS](https://github.com/alpinejs/alpine).

The plugin registers a **WP Landing Page** page template that renders a standalone page (no theme header/footer), styled with the compiled Tailwind CSS and Alpine bundle from `dist/`.

## Requirements

* [WordPress](https://wordpress.org/)
* [Node.js](https://nodejs.org/) (>= 8.9.0) and NPM

## Installation

1. Go to your plugins directory:
   ```bash
   cd project_dir/wp-content/plugins
   ```
2. Clone the repository. Keep the folder name `wp-landing-page`, because the plugin loads its template from that path:
   ```bash
   git clone https://github.com/willard/wp-landing-page
   cd wp-landing-page
   ```
3. Install dependencies and start the watcher:
   ```bash
   npm install
   npm run dev
   ```
4. In WordPress, activate **WP Landing Page** under *Plugins*.
5. Create or edit a page and choose the **WP Landing Page** template in the page attributes.

## Usage

* Edit `wp-landing-page-template.php` to change the page markup.
* Add styles in `src/style.css` and scripts in `src/main.js`.
* Configure Tailwind in `tailwind.config.js`.
* `npm run dev` watches `src/**` and rebuilds `dist/main.css` and `dist/main.js`, which the template loads.

## Project structure

```
├── dist/                          Compiled CSS and JS (output of Rollup)
├── src/
│   ├── main.js                    JS entry point (Alpine, imports style.css)
│   └── style.css                  Tailwind and custom styles
├── rollup.config.js               Rollup + PostCSS build configuration
├── tailwind.config.js             Tailwind configuration
├── wp-landing-page.php            Plugin bootstrap, registers the page template
└── wp-landing-page-template.php   The landing page template
```

## Tech stack

* [RollupJS](https://rollupjs.org/guide/en/): bundler
* [PostCSS](https://postcss.org/): CSS processing (import, nested, url, autoprefixer)
* [TailwindCSS](https://tailwindcss.com/) 1.x: utility-first CSS
* [AlpineJS](https://github.com/alpinejs/alpine) 2.x: lightweight JS interactivity

## Notes

* Tailwind `purge` is empty in `tailwind.config.js`, so `dist/main.css` contains the full Tailwind build. Add your template and source paths to `purge` before shipping to production to reduce its size.
* The template references assets with a hard-coded `?ver=1` query string. Bump it to bust caches after deploying changes.

## License

Released under the [LICENSE](LICENSE) in this repository.
