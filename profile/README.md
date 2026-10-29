<h1 align="center">
<img src="https://raw.githubusercontent.com/EOQual/pixoscope/main/resources/eoqual_rounded.png" width="220">
</h1><br>

# EOQual

**Qualité, validation, calibration et prototypage pour les chaînes de traitement d'observation de la Terre (EO)**

## 🚀 Vue d'ensemble

**EOQual** est un ensemble de librairies Python, installables indépendamment, dédiées à
l'évaluation, la correction et le prototypage de traitements d'images d'observation de la
Terre. Chaque module se concentre sur un domaine précis et documente ses méthodes, ses
limites et l'origine (licence) du code repris à des tiers.

EOQual fait le lien entre l'expérimentation R&D et l'industrialisation de chaînes de
traitement EO.

## 📦 Modules publics

| Module | Rôle | Installation |
|---|---|---|
| [eoqual-metrics](https://github.com/EOQual/eoqual-metrics) | Métriques de qualité image Full-Reference (SSIM, erreurs pixel, corrélation, perceptuelles, spectrales) et No-Reference (BRISQUE/NIQE/PIQE, netteté multi-algorithmes dont MTF@Nyquist par méthode slanted-edge) | `pip install git+https://github.com/EOQual/eoqual-metrics.git` |
| [eoqual-measure](https://github.com/EOQual/eoqual-measure) | Mesures physiques contrôlées de la qualité image (mire, bord choisi, source ponctuelle) : MTF par bord incliné (4 estimateurs comparés, ISO 12233), variance du bruit (6 estimateurs, courbe bruit–luminance), rapport de Strehl et énergie encerclée ; mesures radiométriques de capteur (obscurité, PTC, PRNU/DSNU, linéarité, pixels défectueux, spectre du bruit, CNR) et simulateur de capteur à vérité connue — **en cours de développement** ⚠️ | `pip install git+https://github.com/EOQual/eoqual-measure.git` |
| [eoqual-demosaicing](https://github.com/EOQual/eoqual-demosaicing) | 26 méthodes de démosaïçage Bayer, de l'interpolation simple aux méthodes à interpolation résiduelle (AHD, RI/GBTF/MLRI, LSLCD...) | `pip install git+https://github.com/EOQual/eoqual-demosaicing.git` |
| [eoqual-destriping](https://github.com/EOQual/eoqual-destriping) | 9 méthodes de correction de bruit de strioscopie (appariement statistique, ondelettes, variationnelles, deep learning) | `pip install git+https://github.com/EOQual/eoqual-destriping.git` |
| [eoqual-denoising](https://github.com/EOQual/eoqual-denoising) | 17 méthodes de débruitage d'images (filtres, variation totale, ondelettes, non locales dont NL-Bayes en couleur et NL-Ridge réimplémentés sous MIT, réseaux pré-entraînés via DeepInverse), stabilisation de variance du bruit poisson-gaussien des images brutes (Anscombe généralisée, inverse exacte non biaisée), optimisation bayésienne des paramètres et benchmark — **en cours de développement** ⚠️ | `pip install git+https://github.com/EOQual/eoqual-denoising.git` |
| [eoqual-core](https://github.com/EOQual/eoqual-core) | Socle numérique commun aux modules (numpy/scipy seulement) : TFD d'image sans artefacts de bord, chaîne ESF → LSF → MTF, motifs de Bayer, PSF (Airy, Strehl, énergie encerclée) — installé automatiquement avec les modules qui l'utilisent | `pip install git+https://github.com/EOQual/eoqual-core.git` |
| [eoqual-viz](https://github.com/EOQual/eoqual-viz) | Fonctions graphiques génériques communes aux modules (numpy/plotly seulement) : heatmap 2D interactive, comparaison de courbes/coupes avec repères verticaux — installé automatiquement avec les modules qui l'utilisent. Ne remplace pas [pixoscope](https://github.com/EOQual/pixoscope) (application de visualisation autonome, pas une bibliothèque) | `pip install git+https://github.com/EOQual/eoqual-viz.git` |
| [pixoscope](https://github.com/EOQual/pixoscope) | Visualisateur d'images léger (TIFF/BigTIFF multi-Go, sans dépendance SIG) — application autonome, pas une librairie importable | `pip install git+https://github.com/EOQual/pixoscope.git` |

> ⚠️ **eoqual-measure et eoqual-denoising sont en cours de développement.** Leurs méthodes sont validées sur
> données simulées ou images de test mais pas encore qualifiées sur données réelles ; l'API peut
> évoluer et des bugs ou des anomalies sont possibles. Merci de les signaler par une issue sur le dépôt du module.

Chaque module documente son propre catalogue de méthodes (`README.md`), le détail
technique de chacune (`REFERENCE_TECHNIQUE.md`) et l'audit des licences du code tiers
adapté (`THIRD_PARTY_LICENSES.md`).

`eoqual-metrics` calcule des **indicateurs** de qualité, y compris sans référence sur une
scène quelconque ; `eoqual-measure` fournit des **mesures physiques** sur cible ou protocole
contrôlé. Les briques de calcul qu'ils partagent avec les autres modules vivent dans
`eoqual-core`.

## 📊 Cas d'usage typiques

* Validation de produits dérivés satellite
* Calibration d'algorithmes de restitution
* Comparaison de plusieurs approches de traitement
* Prototypage de chaînes de traitement avant industrialisation
* Suivi de qualité en production

## Installation

Chaque module s'installe indépendamment (voir tableau ci-dessus). Namespace unifié :

```python
import eoqual.metrics
import eoqual.measure
import eoqual.demosaicing
import eoqual.destriping
import eoqual.denoising
import eoqual.core
import eoqual.viz
```

## 🤝 Contribuer

Bug, méthode manquante, algorithme à ajouter, erreur de licence : ouvrez une issue sur
le dépôt du module concerné.

## 📄 Licence

MIT — voir `license.txt` de chaque dépôt public.
