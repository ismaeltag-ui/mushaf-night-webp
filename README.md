# mushaf-night-webp

Les pages des cinq éditions du mushaf de [CoranRevise](https://coranrevise.expo.app)
en **version de nuit**, déjà inversées. Ce dépôt ne sert qu'à héberger des images,
il n'y a pas de code.

| Dossier | Édition | Pages de jour d'origine |
| --- | --- | --- |
| `hafs/` | Mushaf tajwid de Dar al-Maarifah, Hafs | `mushaf-tajweed-webp/images` |
| `warsh/` | Mushaf tajwid de Dar al-Maarifah, Warsh | `mushaf-warsh-webp/images` |
| `madani/` | Mushaf de Médine (1405), dessin de Quran.com | `mushaf-warsh-webp/madani` |
| `qfa-warsh/` | Warsh de l'application « Al Quran » | `mushaf-warsh-webp/qfa-warsh` |
| `qfa-qalun/` | Qālūn de l'application « Al Quran » | `mushaf-warsh-webp/qfa-qalun` |

## Pourquoi

La nuit était obtenue dans l'application par un filtre posé à l'affichage :
inversion, puis rotation de teinte de 180° pour rendre aux règles de tajwid
leurs couleurs. Sur Android, ce filtre fait dessiner la page dans une couche
hors écran, redessinée à chaque mot pendant la récitation ; sur iPhone, React
Native l'ignore, et la page restait de jour. Des pages déjà inversées
s'affichent comme des pages ordinaires.

## Ce qui a été fait

Script `tools/night-pages.py` du dépôt de l'application, sur chaque page de jour :

1. composition sur `#E3E3E1`, le papier peint sous le filtre ;
2. inversion, puis rotation de teinte de 180° avec la matrice de la
   spécification des filtres — celle qu'appliquait Android ;
3. le papier devient exactement `#1C1C1E`, la teinte des masques de l'application.

Les pages de jour n'ont que 256 couleurs au plus et la transformation agit couleur
par couleur : elle est calculée sur la table des couleurs, **sans aucune perte**.
Chaque page est un WebP sans perte, opaque, aux dimensions de la page de jour.

## Provenance et licence

Les mêmes que les pages de jour dont elles dérivent : voir les README de
[`mushaf-tajweed-webp`](https://github.com/ismaeltag-ui/mushaf-tajweed-webp) et de
[`mushaf-warsh-webp`](https://github.com/ismaeltag-ui/mushaf-warsh-webp). Ce dépôt
ne revendique aucun droit sur les œuvres ; toute demande des ayants droit sera
honorée sans délai.
