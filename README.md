# nion digital Frontend Base

## CSS Nutzung
### Mixins, z.B. in einer `css/mixins/index.scss`
```
@forward '@node_modules/@niondigital/frontend-base/css/mixins';
```

### Variablen
Die Frontend Base bringt einige default Variablen mit, die mit Projekt-spezifischen Variablen überschrieben werden können.
In einem typischen Projekt könnte das folgendermaßen aussehen.
Man hat diverse Variablen Dateien, wie `_breakpoints.scss`, `_sizes.scss`, `_colors.scss`.
Die werden in eine `_index.scss` per `@use` geholt und dann werden die Frontend Base Variablen ins Projekt geholt und gegebenenfalls die defaults überschrieben.
```
@use 'breakpoints' as *;
@use 'sizes' as *;
@use 'colors' as *;
@forward '@node_modules/@niondigital/frontend-base/css/vars' with (
	$breakpoints: $breakpoints,
	$show-breakpoints: $show-breakpoints
);
```

Beispiel, wenn automatisch Font Style `.fs-` Klassen aus `$font-styles` und `$font-families` maps generieren möchte und z.b. die breakpoint defaults aus der Base nicht überschreiben möchte.
```
@use 'font-families' as *;
@use 'font-styles' as *;
@forward '@node_modules/@niondigital/frontend-base/css/vars' with (
  $font-families: $font-families,
  $font-styles: $font-styles
);
```

### `main.scss`
```
@use 'vars' as *;
@use 'mixins' as *;
@use '@node_modules/@niondigital/frontend-base/css/main' as *;
```