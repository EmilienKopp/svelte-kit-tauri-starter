# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte).


Check [https://tauri.app/v1/guides/getting-started/prerequisites] to verify that you meet the necessary prerequisites.


## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npm create svelte@latest

# create a new project in my-app
npm create svelte@latest my-app
```

Change the adapter to static:

```bash
npm install --save-dev @sveltejs/adapter-static@next
```

Edit `svelte.config.js`

```JavaScript

import adapter from '@sveltejs/adapter-static' // This was changed from adapter-auto
import preprocess from 'svelte-preprocess'

/** @type {import('@sveltejs/kit').Config} */
const config = {
  // Consult https://github.com/sveltejs/svelte-preprocess
  // for more information about preprocessors
  preprocess: preprocess(),

  kit: {
    adapter: adapter(),
  },
}

export default config
```


Edit `src/routes/layouts.ts[js]` so it contains the two following lines:

```JavaScript
export const prerender = true
export const ssr = false
```


Install Tauri CLI

```bash
npm install --save-dev @tauri-apps/cli
```

In `package.json`, add the following in "scripts":

```JSON
{
    //...,
    "scripts": {
        // ...,
        "tauri": "tauri"
    }
    // ...
}
```

## Initialize

Scaffold the Tauri app:

```bash
npm run tauri init
```

For `web assets` enter `../build`

For `URL of dev server` enter `http://localhost:5173` (same as Vite)

For `frontend dev command`, use `npm run make` (or the appropriate command for you package manager)

For `frontend build command`, enter `npm run build` (same as above, adapt if necessary)



## Developing

Now you should be ready to develop your app and launch it in dev mode using:

```bash
npm run tauri dev
```

Check [https://tauri.app/v1/guides/] if you run into any issues.

## Building

To create a production version of your app:

```bash
npm run tauri build
```

Check [https://tauri.app/v1/guides/building] for more information.