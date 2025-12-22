# Katre

Katre est un langage de programmation à pile.

Katre est :
- [x] compilé
- [x] natif
- [x] complet au sens de Turing (voir exemples/007-rule110.katre)
- [ ] auto-aubergé
- [ ] statiquent typé

## À FAIRE

- documente la mémoire
- tests
- document la simulation

## Opérations

### Arithmétiques

- `+` - place le résultat de l'addition en haut de la pile
```
a = dépile()
b = dépile()
empile(b + a)
```
- `-` - place le résultat de la soustraction en haut de la pile
```
a = dépile()
b = dépile()
empile(b - a)
```
- `*` - place le résultat de la multiplication en haut de la pile
```
a = dépile()
b = dépile()
empile(b * a)
```
- `divmod` - place le quotient et le reste de la division en haut de la pile
```
a = dépile()
b = dépile()
empile(b / a)
empile(b % a)
```

### Binaires

Ces opérations permettent de manipuler les bits des valeurs.

- `<<` - décale les bits de `b` par `a` vers la gauche et place le résultat en haut de la pile
```
a = dépile()
b = dépile()
empile(b << a)
```
- `>>` - décale les bits de `b` par `a` vers la droite et place le résultat en haut de la pile
```
a = dépile()
b = dépile()
empile(b >> a)
```
- `^` - place en haut de la pile la résultat d'un ou-exclusif binaire
```
a = dépile()
b = dépile()
empile(b ^ a)
```
- `&` - place en haut de la pile la résultat d'un et binaire
```
a = dépile()
b = dépile()
empile(b & a)
```
- `|` - place en haut de la pile la résultat d'un ou-inclusif binaire
```
a = dépile()
b = dépile()
empile(b | a)
```

### Relationnelles

Ces opérations permettent d'effectuer des comparaisons entre deux valeurs.

- `=` - empile 1 si `a` est égale à `b` sinon 0
```
a = dépile()
b = dépile()
si b = a
    empile(1)
sinon
    empile(0)
end
```
- `<` - empile 1 si `a` est strictement inférieur à `b` sinon 0
```
a = dépile()
b = dépile()
si b < a
    empile(1)
sinon
    empile(0)
end
```
- `>` - empile 1 si `a` est strictement supérieur à `b` sinon 0
```
a = dépile()
b = dépile()
si b > a
    empile(1)
sinon
    empile(0)
end
```
- `<=` - empile 1 si `a` est inférieur ou égal à `b` sinon 0
```
a = dépile()
b = dépile()
si b <= a
    empile(1)
sinon
    empile(0)
end
```
- `>=` - empile 1 si `a` est supérieur ou égal à `b` sinon 0
```
a = dépile()
b = dépile()
si b >= a
    empile(1)
sinon
    empile(0)
end
```

### Contrôle de flux

Ces instructions permettent de rediriger le flux d'exécution du programme.

- `si <conséquente> fin` - consomme la valeur en haut de la pile, et exécute `<conséquente>` si elle est vraie, sinon continue l'exécution après `fin`
```
a = dépile()
si a = 1
    <conséquente>
fin
```

- `si <conséquente> sinon <alternative> fin` - consomme la valeur en haut de la pile, et exécute `<conséquente>` si elle est vraie, exécute `<alternative>`
```
a = dépile()
si a = 1
    exécute <conséquente>
sinon
    exécute <alternaive>
```

- `tantque <prédicat> fais <conséquente> fin` - exécute `<conséquente>` tantque le `<prédicat>` est vrai
```
tantque:
    prédicat = dépile()
    si prédicat = 1
        exécute <conséqente>
        reprends à tantque
```

### Manipulatio de la mémoire

- `mem` - place l'adresse de base de la mémoire sur la pile
```
empile(mem)
```
- `.` - écris un octet dans l'adresse donnée
```
a = dépile()
adresse = dépile()
écris_octet(adresse, a)
```
- `,` - lis un octet de l'adresse donnée, et place la valeur sur la pile
```
adresse = dépile()
a = lis_octet(adresse)
empile(a)
```

### Manipulation de la pile

- `dup` - duplique l'élément en haut de la pile
```
a = dépile()
empile(a)
empile(a)
```
- `enjambe` - place une copie du deuxième élément de la pile en haut de celle-ci
```
a = dépile()
b = dépile()
empile(b)
empile(a)
empile(b)
```
- `lâche` - supprime l'élément en haut de la pile
```
dépile()
```
- `permute` - permute les deux éléments en haut de la pile
```
a = dépile()
b = dépile()
empile(a)
empile(b)
```

### Appel système

Ces opérations sont temporaires tant que le langage est en développement.

- `appelsys1` - performe un appel système Linux ave 1 argument
- `appelsys2` - performe un appel système Linux ave 2 arguments
- `appelsys3` - performe un appel système Linux ave 3 arguments

### Débogage

- `cliche` - consomme la valeur en haut de la pile et imprime-la dans la sortie standarde
```
a = dépile()
imprime(a)
```
