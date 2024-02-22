# JavaScript

## Manipulation des tableaux

### Array.push() vs l'opérateur Spread

Array.push() et l'opérateur spread (...) sont tous deux utilisés pour ajouter des éléments à des tableaux en JavaScript, mais ils présentent des différences importantes :

#### Array.push():

- Modifie le tableau d'origine: Cette méthode ajoute des éléments directement à la fin du tableau sur lequel vous l'appelez. Cela signifie que le tableau d'origine est modifié de manière permanente.
- Retourne la nouvelle longueur: Il retourne la nouvelle longueur du tableau modifié.
- Peut ajouter un ou plusieurs éléments: Vous pouvez ajouter un ou plusieurs éléments en tant qu'arguments à la méthode.

**Sources :**
- https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/push

**Ajout d'éléments à un tableau :**
```js
const arr = [1, 2, 3];

// Modifier le tableau d'origine
arr.push(4);  // arr devient [1, 2, 3, 4]

// Créer un nouveau tableau avec des éléments ajoutés
const newArr = [...arr, 5];  // newArr devient [1, 2, 3, 4, 5]

```

**Combinaison de tableaux :**
```js
const arr1 = [1, 2];
const arr2 = [3, 4];

// Créer un nouveau tableau avec des éléments combinés
const combinedArr = [...arr1, ...arr2];  // combinedArr devient [1, 2, 3, 4]

```

#### Opérateur Spread:

- **Crée un nouveau tableau :** Cet opérateur développe les éléments individuels d'un itérable (comme un tableau, une chaîne ou un objet) dans un nouveau tableau. Il ne modifie pas le tableau d'origine.
- **Peut combiner des tableaux :** Vous pouvez l'utiliser pour combiner plusieurs tableaux en un seul.
- **Peut être utilisé dans divers contextes :** Outre l'ajout d'éléments, il peut être utilisé pour les appels de fonction, l'expansion des propriétés d'objet et plus encore.

**Sources :** 
- https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators/Spread_syntax

#### En résumé :

**Tableau comparatif :**

| Fonctionnalité                            | Array.push() | Opérateur Spread (...) |
| ----------------------------------------- | ------------ | ---------------------- |
| Modifie le tableau d'origine              | Oui          | Non                    |
| Retourne la nouvelle longueur             | Oui          | Non                    |
| Ajoute un/plusieurs éléments              | Oui          | Oui                    |
| Crée un nouveau tableau                   | Non          | Oui                    |
| Combine des tableaux                      | Non          | Oui                    |
| Utilisation au-delà de l'ajout d'éléments | Non          | Oui                    |

- Utilisez `Array.push()` lorsque vous souhaitez modifier directement le tableau d'origine et que vous avez besoin de la nouvelle longueur.

- Utilisez l'opérateur spread ... lorsque vous souhaitez créer un nouveau tableau, combiner plusieurs tableaux ou l'utiliser dans d'autres contextes comme les appels de fonction.

#### Performance :

Pour ajouter 10 éléments à un tableau, Array.push() nécessiterait 10 appels à la méthode, tandis que l'opérateur spread ne nécessiterait qu'un seul appel.
Dans ce cas pour une grande quantité de données l'opérateur spread est conseillé.

### Boucle vs Array Map

Boucles et Array.map() sont deux méthodes courantes pour parcourir et traiter des tableaux en JavaScript, chacune avec ses avantages et ses inconvénients. Choisir la bonne méthode dépend de vos besoins spécifiques.

#### Boucle:

- **Contrôle précis** : Offre un contrôle granulaire sur chaque élément du tableau. Vous pouvez facilement modifier, sauter ou arrêter l'itération en fonction de conditions spécifiques.
- **Flexibilité** : Adaptable à des scénarios plus complexes où vous avez besoin de modifier le tableau d'origine ou effectuer des tâches supplémentaires en cours d'itération.
- **Plus verbose** : Nécessite plus de code par rapport à Array.map().
> [!NOTE]
> **Contrôle granulaire** : la capacité de gérer et d'influencer chaque élément d'un ensemble de manière précise et individuelle

```js
const numbers = [1, 2, 3, 4, 5];
let doubledNumbers = [];

for (let i = 0; i < numbers.length; i++) {
  doubledNumbers.push(numbers[i] * 2);
}

console.log(doubledNumbers); // [2, 4, 6, 8, 10]

```

#### Array.map() :

- Concision: Syntaxe concise et lisible, facile à comprendre et à maintenir.
Création d'un nouveau tableau: Crée un nouveau tableau contenant les résultats de la fonction appliquée à chaque élément du tableau d'origine, ne modifiant pas celui-ci.
- Fonction pure : La fonction passée à Array.map() ne doit pas avoir d'effets secondaires, ce qui la rend plus prévisible et testable.
- Limité au traitement individuel : Moins flexible que les boucles, car elle ne permet pas de modifier le tableau d'origine ou d'effectuer des actions conditionnelles complexes.

```js
const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map(number => number * 2);

console.log(doubledNumbers); // [2, 4, 6, 8, 10]

```

map est une méthode de l'objet array.
Pour avoir un autre tableau en résultat.

Si on fait une fonction callback à l'intérieur ça n'aura pas d'incidence sur le tableau d'origine.
[a,a,a].map((b)=>)
[b,b,b]

element, index : on pourra manipuler le tableau avec son index.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map

#### En résumé :

**Utilisez une boucle si :**
Vous avez besoin d'un contrôle granulaire sur chaque élément du tableau.
Vous devez modifier le tableau d'origine en cours d'itération.
Vous devez effectuer des actions conditionnelles complexes.

**Utilisez Array.map() si :**
Vous voulez créer un nouveau tableau à partir du tableau d'origine.
Vous avez besoin d'une solution concise et lisible.
Vous souhaitez éviter les effets secondaires et améliorer la testabilité.

#### Complément :

**`Array.from()` :**

La méthode `Array.from()` permet de créer une nouvelle instance d'Array (une copie superficielle) à partir d'un objet itérable ou semblable à un tableau. (Transforme en tableau un objet).
```js
Array.from(document.querySelectorAll('ol li'));
```
**Source :**
-https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/from

**`Array.isArray()`:**
La méthode `Array.isArray()` permet de déterminer si l'objet passé en argument est un objet Array, elle renvoie true si le paramètre passé à la fonction est de type Array et false dans le cas contraire.

**Source :**
- https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray

> [!NOTE]
> Array est une structure, une structure peut imiter une structure.