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
| [eoqual-demosaicing](https://github.com/EOQual/eoqual-demosaicing) | 26 méthodes de démosaïçage Bayer, de l'interpolation simple aux méthodes à interpolation résiduelle (AHD, RI/GBTF/MLRI, LSLCD...) | `pip install git+https://github.com/EOQual/eoqual-demosaicing.git` |
| [eoqual-destriping](https://github.com/EOQual/eoqual-destriping) | 9 méthodes de correction de bruit de strioscopie (appariement statistique, ondelettes, variationnelles, deep learning) | `pip install git+https://github.com/EOQual/eoqual-destriping.git` |
| [pixoscope](https://github.com/EOQual/pixoscope) | Visualisateur d'images léger (TIFF/BigTIFF multi-Go, sans dépendance SIG) — application autonome, pas une librairie importable | `pip install git+https://github.com/EOQual/pixoscope.git` |

Chaque module documente son propre catalogue de méthodes (`README.md`), le détail
technique de chacune (`REFERENCE_TECHNIQUE.md`) et l'audit des licences du code tiers
adapté (`THIRD_PARTY_LICENSES.md`).

## 🔒 Et le reste ?

EOQual couvre également la déconvolution, le débruitage, le rééchantillonnage et
l'analyse de résolution (PSF/MTF, polynômes de Zernike). Ces modules existent et sont
utilisés en interne chez Magellium ; ils ne sont pas publiés sur ce dépôt GitHub.

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
import eoqual.demosaicing
import eoqual.destriping
```

## 🤝 Contribuer

Bug, méthode manquante, algorithme à ajouter, erreur de licence : ouvrez une issue sur
le dépôt du module concerné.

## 📄 Licence

MIT — voir `license.txt` de chaque dépôt public.
