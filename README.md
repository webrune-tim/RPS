![Rock Paper Scissors Lizard Spock](https://res.cloudinary.com/tihos/image/upload/f_auto,q_auto/v1650434815/thumbnail_lkqkqk.jpg)

# Rock Paper Scissors Lizard Spock

## The unofficial Rock Paper Scissors Lizard Spock game from The Big Bang Theory TV show

- [Sam Kass' Official Rock Paper Scissors Lizard Spock Game Rules](http://www.samkass.com/theories/RPSSL.html)
- [Big Bang Episode Reference](https://the-big-bang-theory.com/rock-paper-scissors-lizard-spock/)

## Developing

After cloning this repo, the first thing you will want to do, is to install the dependencies.

```bash
cd RPS/
pnpm install
```

I personally prefer [pnpm](https://pnpm.io/) for package management, but `npm`, and `yarn` will work just fine 😁 .

```bash
pnpm dev

# or start the server and open the app in a new browser tab
pnpm dev -- --open
```

If you use `npm`, you can use the `npm run dev` command to start the server and open the app in a new browser tab.
If you use `yarn`, you can use the `yarn run dev` command to start the server and open the app in a new browser tab.

## Building

To create a production version of your app:

```bash
pnpm run build
```

You can preview the production build with `npm run preview`.

## Deployment

### We use Cloudflare

Contact [Tim Smith](mailto:gonad2019@gmail.com) to configure Cloudflare settings for now.
