# Soil_degradation
Voici le workflow complet mis à jour pour détecter la dégradation des sols à Sommières avec :  

- NDVI : couverture végétale (diminue si végétation se dégrade)  
- NDWI : humidité végétation (diminue quand le sol devient plus sec)  
  | Valeur NDWI  | Interprétation             |  
| ------------ | -------------------------- |  
| **> 0.3**    | Eau libre (rivières, lacs) |  
| **0 à 0.3**  | Végétation humide          |  
| **-0.2 à 0** | Sol humide                 |  
| **< -0.2**   | Sol sec / zones urbaines   |  

- humidité du sol via SMOSMANIA (Profondeur : 0-7cm) : diminue en période de sécheresse  
- climat ERA5  
- occupation du sol (Copernicus Land Cover) : zones urbaines  
- traitement dans Google Colab  
- suppression des données brutes après traitement   
- Visualisation via matplotlib

  Interprétation : La ville de Sommières a été choisie en raison de son risque fort au retrait gonflement d'après la carte du BRGM.
Période de 30 ans d'étude de données historiques entre 1993 et 2023.  
Les graphiques montrent trois phénomènes majeurs :
1. Réchauffement climatique local  
Température en augmentation → stress hydrique.
2. Assèchement progressif des sols   
Humidité du sol en légère baisse depuis 1993.  
3. Dégradation récente de la végétation  
NDVI en baisse après 2018.  
Rique binaire évalué par année si NDVI(n) - NDVI(n-1) < -0.3 : 1 si NDVI a baissé fortement (plus de 0.03) par rapport à l’année précédente, sinon 0.  
Années critiques : 2019vs2018, 2021vs2020, 2022vs2021.  

=> Ces résultats suggèrent un risque croissant de dégradation des sols dans la ville de Sommières.
