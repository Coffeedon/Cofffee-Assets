# Logos, custom themes & tutorials

On this repo you can find the custom logos, themes and other assets created for the [Mastodon.Coffee](https://mastodon.coffe/) instance.

## Instructions for admins
Download the custom themes you want from the /styles folder and add them to your Mastodon installation.

### To use a pre-made theme:

Let's use the Modern Dark theme as an example.

1. **Fetch the files.** Add your desired custom CSS/SCSS to `app/javascript/styles`. You can copy/merge the entire `styles` folder from the root of this repo into the root of your Mastodon deployment.

```
app/
  javascript/
    styles/
    moder-dark.scss                            | **new**
      contrast/
        ...
      fonts/
        ...
      modern/                            | **new**
        dark.scss                            | **new**
        style.scss                              | **new**
```


        2. **Add your theme to the config.** This is what [the default themes.yml](https://github.com/tootsuite/mastodon/blob/master/config/themes.yml) looks like in Mastodon. To make your custom theme visible in settings, you need to add a new line in the form `themeName: path/to/theme.scss`. For example, the modern-dark theme would require adding `modern-dark: styles/modern-dark.scss` as a new line.

        ```
        default: styles/application.scss
        contrast: styles/contrast.scss
        mastodon-light: styles/mastodon-light.scss
        modern-dark: styles/modern-dark.scss      | **new**
        ```

        3. **Add a human-friendly name for the theme (optional).** You can edit each desired language's locale file in `config/locales/[lang].yml` to add a localized string name for your theme's `themeName` as added in the previous step. For example, [the default `config/locales/en.yml`](https://github.com/tootsuite/mastodon/blob/041ff5fa9a45f7b8d1048a05a35611622b6f5fdb/config/locales/en.yml#L942-L945) contains localizations for the three default themes that ship with Mastodon, into the `en`glish language. You need to do this for every language you expect your users to use, or else they will see the unlocalized `themeName` directly.

        ```
          themes:
            contrast: Mastodon (High contrast)
            default: Mastodon (Dark)
            mastodon-light: Mastodon (Light)
            modern-dark: Modern Dark              | **new**
        ```

        4. **Compile theme assets and restart.** Run `RAILS_ENV=production bundle exec rails assets:precompile` and restart your Mastodon instance for the changes to take effect.
