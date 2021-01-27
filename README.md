# OHO WordPress Install

The OHO Base Install allows developers to quickly configure new WordPress
projects with OHO's default installation settings. The install is based on the
[Bedrock](https://github.com/roots/bedrock) project, with OHO-specific
customizations. We maintain a fork of the project, because files not managed by
Composer are pulled from VCS when running `composer create-project`.

## Installation Instructions

1. Create a new WordPress project in the current directory with
   `composer create-project oho-wp/install 
   --repository-url=https://admin@ohosite1100@packagist.ohodev.com 
   --stability=dev .`.
2. Update `.env` with the correct values.
  * Replace the `DB_` keys with the correct database information for the current
    environment.
  * Replace `WP_HOME` with the current environment homepage URL, with leading
    protocol and without trailing slash.
  * Visit https://roots.io/salts.html and to generate a salt key, and replace
    all instances of `generateme` with the generated salt.
  * Retrieve the Advanced Custom Fields Pro license key from 1Password (search
    for "ACF License") and add it to the `ACF_PRO_KEY` key.
3. Run `composer update` to install Advanced Custom Fields Pro.
4. Visit the site at `/wp` to run the WordPress installer.

## Multisite

If this is a multisite install, the package
[roots/multisite-url-fixer](https://github.com/roots/multisite-url-fixer) must
be added to the project with `composer require roots/multisite-url-fixer`.

## WP-CLI

[WP CLI](https://wp-cli.org) is included as a project dependency, and can be run
through Composer with the command: `composer wp ...`.

## Troubleshooting

* If Composer fails with the error "curl: (60) SSL certificate problem: unable 
  to get local issuer certificate", you can change the packagist.ohodev.com 
  url to "http" and run the `composer create-projct` command above with the 
  `--no-secure-http` flag added.
