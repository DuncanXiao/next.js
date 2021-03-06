# With env From next.config.js

This example demonstrates setting parameters that will be used by your application and set at build time (not run time).
More specifically, what that means, is that environmental variables are programmed into the special configuration file `next.js.config` and then
returned to your react components (including `getInitialProps`) when the program is built with `next build`.

As the build process (`next build`) is proceeding, `next.config.js` is processed and passed in as a parameter is the variable `phase`.
`phase` can have the values `PHASE_DEVELOPMENT_SERVER` or `PHASE_PRODUCTION_BUILD` (as defined in `next\constants`). Based on the variable
`phase`, different environmental variables can be set for use in your react app. That is, if you reference `process.env.RESTURL_SPEAKERS`
in your react app, whatever is returned by `next.config.js` as the variable `env`, (or `env.RESTURL_SPEAKERS`) will be accessible in your
app as `process.env.RESTURL_SPEAKERS`.

## Deploy your own

Deploy the example using [ZEIT Now](https://zeit.co/now):

[![Deploy with ZEIT Now](https://zeit.co/button)](https://zeit.co/new/project?template=https://github.com/zeit/next.js/tree/canary/examples/with-env-from-next-config-js)

## How to use

### Using `create-next-app`

Execute [`create-next-app`](https://github.com/zeit/next.js/tree/canary/packages/create-next-app) with [npm](https://docs.npmjs.com/cli/init) or [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/) to bootstrap the example:

```bash
npm init next-app --example with-env-from-next-config-js
# or
yarn create next-app --example with-env-from-next-config-js
```

### Download manually

Download the example:

```bash
curl https://codeload.github.com/zeit/next.js/tar.gz/canary | tar -xz --strip=2 next.js-canary/examples/with-env-from-next-config-js
cd with-env-from-next-config-js
```

Install it and run:

```bash
npm install
npm run dev
# or
yarn
yarn dev
```

Deploy it to the cloud with [ZEIT Now](https://zeit.co/new?filter=next.js&utm_source=github&utm_medium=readme&utm_campaign=next-example) ([Documentation](https://nextjs.org/docs/deployment)).

> ## Special note
>
> `next build` does a hard coded variable substitution into your JavaScript before the final bundle is created. This means
> that if you change your environmental variables outside of your running app, such as in windows with `set` or lunix with `setenv`
> those changes will not be reflected in your running application until a build happens again (with `next build`).

## Discussion regarding this example

This example is not meant to be a reference standard for how to do development, staging and
production builds with Next. This is just one possible scenario that could be used if you want the
following behavior while you are doing development.

- When your run `next dev` or `npm run dev`, you will always use the environmental variables assigned when `isDev` is true in the example.
- When you run `next build` then `next start`, assuming you set externally the environmental variable STAGING to anything but 1, you will get the results assuming `isProd` is true.
- When your run `next build` or `npm run build` in production, if the environmental variable `STAGING` is set to `1`, `isStaging` will be set and you will get those values returned.

You can read more about this feature in thie blog post <a href="https://zeit.co/blog/next5-1" target="_blank">Next.js 5.1: Faster Page Resolution, Environment Config and More</a> (under Environment Config).
