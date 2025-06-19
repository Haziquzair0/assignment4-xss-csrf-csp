
# Assignment 4: XSS, CSRF, and CSP Security in Laravel To-Do App

## Content Security Policy (CSP)
- Implemented via custom middleware (`app/Http/Middleware/ContentSecurityPolicy.php`).
- Registered globally in `app/Http/Kernel.php`.
- CSP header restricts all scripts, styles, images, and fonts to same-origin.

## XSS Defense
- All user-generated content is escaped using Blade’s `{{ }}` syntax.
- No `{!! !!}` is used for user input.
- Tested by entering `<script>alert(1)</script>` in forms; it is not executed.

## CSRF Defense
- All forms use the `@csrf` directive.
- Laravel’s CSRF middleware is enabled by default.
- Tested by removing the CSRF token and submitting a form; a 419 error is returned.

## Same-Origin Policy
- Enforced via CSP: `default-src 'self'`.
