# Slate base

## Explanation

Starting point for Shopify theme builds, using Slate.

This project uses Shopify's Slate framework for theme compiling and syncing: https://shopify.github.io/slate/

Slate also contains many of the features of the predecessor Theme Kit: https://shopify.github.io/themekit/. Although largely undocumented, they can be very powerful and some of their usage is explained below. Hopefully in due course, Slate will allow access to these commands natively.

## Setup

1. Pull down and ensure latest copy of repo
2. Ensure Node is installed
3. Navigate to theme folder (usually develop/)
4. Run `npm install -g @shopify/slate` to install Slate globally and test with `slate -v`
5. Run `curl -s https://raw.githubusercontent.com/Shopify/themekit/master/scripts/install | sudo python` to install Theme Kit globally
6. Run `npm install` to install package dependencies
7. Review workflow in next section

**IMPORTANT: Consider using Node v6 because v8 has some unpredictable bugs with Slate: https://github.com/Shopify/slate/issues/243#issuecomment-340762586**

## Workflow

1. Pull down and ensure latest copy of repo if you did not do so in Setup instructions
2. If working with other developers, run `theme download --dir=src` to grab latest of deployed development theme
3. Review Git log to ensure any new files/changes seem logical
4. If you run `slate watch`, you should begin syncing with Shopify when files change
5. If you run `slate start`, it will perform a deploy and then begin watching

**IMPORTANT: Be aware that working on the same file as another developer could cause some conflicts.**

## IMPORTANT NOTES

Slate works based on a `config.yml` file in the root of the theme - `config/settings_data.json` and `locales/*` can be edited by other developers/the client via Shopify's online admin interface. As a result, these are ignored from the `config.yml` to prevent accidental overwriting.

If you want to allow them to be synced by Slate, comment them out from the `ignore_files` list but *HERE BE DRAGONS* (AKA please be careful)

The production environment is always, purposefully `readonly` in `config.yml` as deployment to live is a separate process.

Reading up on Slate/Theme Kit and their respective commands is useful:
- https://shopify.github.io/slate/commands/
- https://shopify.github.io/themekit/

## Further reference

- https://shopify.github.io/slate/
- https://shopify.github.io/themekit/
