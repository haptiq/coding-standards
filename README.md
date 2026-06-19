# Haptiq Coding Standards

PHPCS ruleset for WordPress projects developed at Haptiq.

Combines [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards) with [PHPCompatibilityWP](https://github.com/PHPCompatibility/PHPCompatibilityWP) to catch both style violations and WordPress/PHP version compatibility issues.

## Installation

```bash
composer require --dev haptiq/coding-standards
```

The [Composer installer plugin](https://github.com/PHPCSStandards/composer-installer) registers the standard automatically — no manual PHPCS path configuration needed.

## Usage

Run PHPCS with the `HaptiqWordPress` standard:

```bash
vendor/bin/phpcs --standard=HaptiqWordPress src/
```

Or copy the provided `phpcs.xml.dist` to your project root as `phpcs.xml` and run:

```bash
vendor/bin/phpcs
```

## What it checks

| Rule group | Default severity | What it covers |
|---|---|---|
| `WordPress-Core` | warning | WordPress coding style and conventions |
| `WordPress-Extra` | warning | Stricter WordPress best practices |
| `PHPCompatibilityWP` | warning | PHP and WP API version compatibility |

All violations are warnings by default — they are reported but do not block CI. See [Adjusting severity](#adjusting-severity) to promote specific groups to errors.

**Targets:** PHP 7.4–8.4 · WordPress 6.8+

## Adjusting severity

To promote a rule group to an error in your project's `phpcs.xml`:

```xml
<rule ref="HaptiqWordPress/WordPress-Core">
    <type>error</type>
</rule>
```

## Excluding rules

```xml
<rule ref="HaptiqWordPress">
    <exclude name="WordPress.Files.FileName"/>
</rule>
```

## Adding docblock enforcement

`WordPress-Docs` is available but not included by default. Add it to your `phpcs.xml`:

```xml
<rule ref="WordPress-Docs"/>
```
