# Exigences non fonctionnelles — registre initial

Les objectifs chiffrés restent à décider. Aucun chiffre n'est supposé dans ce document.

| ID | Domaine | Exigence proposée | Mesure/cible |
|---|---|---|---|
| NFR-SCALE-001 | Scalabilité | Le système doit supporter la volumétrie et les pics validés par le métier | À fixer après estimation et tests de charge |
| NFR-OFF-001 | Hors ligne | Les opérations autorisées hors ligne doivent résister à une fermeture/redémarrage de l'appareil | Scénarios et durée à définir |
| NFR-SYNC-001 | Synchronisation | Les échecs de synchronisation doivent être visibles, réessayables et diagnosables | À définir |
| NFR-SEC-001 | Sécurité | Les accès et données doivent être protégés contre les accès non autorisés | Modèle de menace et exigences à préciser |
| NFR-PRIV-001 | Confidentialité | La collecte et la conservation des données doivent être limitées aux finalités validées | À définir avec responsable compétent |
| NFR-AVAIL-001 | Disponibilité | Les objectifs de disponibilité des services en ligne doivent être définis | SLO à fixer |
| NFR-PERF-001 | Performance | Les parcours critiques doivent avoir des objectifs mesurables de latence | Cibles à fixer |
| NFR-REC-001 | Reprise | Sauvegardes et restauration doivent répondre aux besoins métier | RPO/RTO à fixer |
| NFR-OBS-001 | Observabilité | Les erreurs, synchronisations et opérations critiques doivent être mesurables sans exposer de données sensibles | À préciser |
| NFR-ACC-001 | Accessibilité/utilisabilité | Les interfaces doivent être utilisables par les publics cibles et sur les appareils retenus | Tests terrain à planifier |

## Validation nécessaire
Les responsables produit, métier, sécurité et exploitation doivent fixer les seuils après avoir défini la volumétrie, les risques, le budget et les usages terrain.
