# Paraglide JS

## Pros

-   Type safe
-   Has next plugin
-   Has treeshaking
-   No async import, only used messages are included in the bundle
-   Usage is intuitive

```typescript
m.hello();
m.loginHeader({ name: "Samuel" });
```

## Cons

-   Doesnt support nesting
-   Treeshaking loads all languages for a translation key
-   Custom `Link` component is required?

```diff
- import { Link, usePathname, useRouter, redirect, permanentRedirect} from "next/navigation"
+ import { Link, usePathname, useRouter, redirect, permanentRedirect} from "@/lib/i18n"
```

# next-intl

## Pros

-   Type safe
-   Supports nesting
-   Usage is okay

```tsx
const t = useTranslations("Index");
return <h1>{t("title")}</h1>;
```

## Cons

-   Has to load messages every request?
    > next-intl creates a configuration once per request
-   Docs are confusing
    -   Something something middleware
    -   https://github.com/amannn/next-intl/issues/814 middleware size issue

```typescript
const locales = ["en", "de"];

export default getRequestConfig(async ({ locale }) => {
	if (!locales.includes(locale as any)) notFound();

	return {
		messages: (await import(`../messages/${locale}.json`)).default,
	};
});
```

# i18next(react-i18next)

## Pros

-   Nested json ('look.deeper')
-   Namespace ('look:deeper')
-   Fallback logic `i18next.t(['firstkey', 'secondkey'])`
-   Formatting `'{{count, number}} cakes'` => `11,111 cakes` (Can add custom formatters)
-   Typesafe

## Cons

-   Too much
