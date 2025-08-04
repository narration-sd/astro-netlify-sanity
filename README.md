# Astro Starter Kit: Minimal

```sh
npm create astro@latest -- --template minimal
```
## Added Sanity-Astro with Studio for testing

If it worked, this minimalization would halt asking for a Sanity projectId once the Studio comes up. This takes some time in dev, while Vite does some work.

At the point of publishing this repo, in dev mode, clicking the link for the Studio will fail with blank screen.

After the time mentioned, the dev console will announce the failure:

```
08:35:12 [ERROR] [vite] error while updating dependencies:
Error: EPERM: operation not permitted, rename 'C:\vger\projects\astro\astro-netlify-sanity\node_modules\.vite\deps' -> 'C:\vger\
projects\astro\astro-netlify-sanity\node_modules\.vite\deps_temp_d6cc5895
```

Notes: 

- first, this is a Development error (npm run dev). Builds are successful and deploy fine to Netlify, producing an expected error on launching the Studio, because this minimal repo includes only enough to show the fault. As follows....

- This fault will occur on your first launch, when the development project is exercised on Windows (11 latest). An extra version of node_modules/.vite/deps will be found, due to the error.


- To assure a repeat the error, stop the dev environment and delete any deps folders in node_modules/.vite (dot-vite). Then run dev again and try the Studio launch or refresh its page. A code change will also cause a fresh deps attempt thus the error.


- Various kinds of attempts to cause Vite not to optimize deps haven't been successful stopping the evident second attempt when loading the studio module, and the lore is that this is not reliable.


- On Linux development arrangements, there is no failure at all. The hint then that @astrojs/netlify's Vite is asking something when in dev mode that isn't compatible with the Windows filesystem, at the time it tries to load the large studio component.


- Many of the persons who are attracted to Astro are likely to prefer to develop in Windows, one may suggest...


- This same code works correctly on Windows with @astrojs/netlify@6.4.1 or earlier, as does the full blog-with-Studio app it's reduced from.

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
/
├── public/
├── src/
│   └── pages/
│       └── index.astro
└── package.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Feel free to check [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).
