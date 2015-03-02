Créez un serveur qui route toute requête vers le chemin
`/foo/bar/baz/file.html` vers un fichier présent dans un répertoire, par
exemple `public/file.html`.  Ce fichier contiendrait :

```html
<html>
    <head><title>Salut les répertoires</title></head>
    <body>
        Salut les répertoires
    </body>
</html>
```

-----------------------------------------------------------------

## Conseils

Les gestionnaires peuvent être un objet avec un chemin de répertoire :

```js
handler: {
    directory: { path: './public' }
}
```

Les routes utilisant un gestionnaire de type répertoire doivent inclure
un paramètre `path` à la fin de leur chemin de route.  Le chemin préfixe
de la route n’a pas besoin de correspondre au répertoire associé sur le
disque, et le nom du paramètre de chemin est sans importance.

```js
path: "/chemin/vers/quelquepart/{param}"
```

Attention, dans la pratique, vous devrez fournir un chemin absolu pointant
vers un fichier `public` situé dans le répertoire courant.  Vous aurez
sans doute besoin du module noyau `path`, de sa fonction `join()`, et de
la variable globale `__dirname` pour y arriver.