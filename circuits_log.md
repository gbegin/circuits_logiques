

# Avant-propos

Ce manuel a été rédigé en fonction de deux objectifs distincts mais
reliés. Le premier objectif était de produire un manuel de qualité, en
français, sur un sujet fondamental en électronique numérique et d'en
faire une *Ressource éducative libre (REL)*. Une recherche préalable
nous avait en effet permis de constater qu'il existe peu de manuels
récents de ce type sur le sujet. En offrant une telle ressource à la
communauté, nous espérons contribuer à rendre plus accessible la
formation dans ce domaine technologique important.

Le deuxième objectif était d'expérimenter avec une méthode de
travail permettant d'élaborer de telles ressources éducatives en
faisant appel à un ensemble d'outils libres et universellement accessibles. Le
but était aussi de s'assurer de pouvoir obtenir un document ou un ensemble de
documents sources susceptibles d'en faciliter la réutilisation, la
révision et le remixage. Le manuel est donc appelé à devenir une
preuve de concept pour le processus d'élaboration qui a été utilisé.

La matière couverte dans ce manuel correspond d'assez près au contenu
du cours [MIC1065 Circuits logiques](https://etudier.uqam.ca/cours?sigle=MIC1065), offert dans le cadre du
[baccalauréat en systèmes informatiques et électroniques](https://etudier.uqam.ca/programme?code=6526) de
l'[Université du Québec à Montréal](https://uqam.ca/). 

L'auteur, Guy Bégin, est professeur au département d'informatique de
l'Université du Québec à Montréal. Ses recherches l'ont toujours amené
à s'intéresser aux 0 et aux 1 si souvent rencontrés en circuits
logiques, mais également en télécommunications numériques, son champ
de recherche privilégié.


## Remerciements

L'auteur souhaite remercier particulièrement Yves Munn (chargé de
projets technopédagogiques), Boris Nonveiller (bibliothécaire), Rachel
Rouleau (révision linguistique) et Émile Gauvin (étudiant au
baccalauréat en systèmes informatiques et électroniques). Ce manuel a
été réalisé avec le soutien de la [fabriqueREL](https://fabriquerel.org/).


### Licence

<div class="org-center">

<div id="org92788ff" class="figure">
<p><a href="https://creativecommons.org/licenses/by/4.0/deed.fr" width="300"><img src="by-sa.svg" alt="by-sa.svg" class="org-svg" width="300" /></a> 
</p>
</div>
</div>

Le contenu de ce manuel électronique est
disponible en vertu des conditions de la
[Licence
Creative Commons Attribution - Partage dans les mêmes conditions 4.0
International](https://creativecommons.org/licenses/by-sa/4.0/deed.fr).

Vous êtes autorisé à : 

-   **Partager:** – Copier, distribuer et communiquer le matériel par tous
    moyens et sous tous formats.
-   **Adapter:** – Remixer, transformer et créer à partir du matériel pour
    toute utilisation, y compris commerciale.

Selon les conditions suivantes :

-   **Paternité:** – Vous devez citer le nom de l'auteur original.
-   **Mêmes conditions:** – Si vous remixez, transformez, ou créez à
    partir du matériel composant l'Oeuvre originale, vous devez diffuser
    l'Oeuvre modifiée avec la même licence.

Pour citer cet ouvrage: Bégin, G. (2022), Circuits logiques
combinatoires et séquentiels. Université du Québec à Montréal. Licence CC BY-SA

<div class="org-center">

<div id="org8d402bc" class="figure">
<p><a href="https://uqam.ca/" width="300"><img src="Logo_UQAM.svg" alt="Logo_UQAM.svg" class="org-svg" width="300" /></a> 
</p>
</div>
</div>


### Ressources

Les logiciels libres suivants ont été utilisés à différentes étapes,
pour la rédaction et la préparation des modèles, des images et pour la
simulation:

-   Rédaction et production
    -   [Emacs](https://www.gnu.org/software/emacs/)
    -   [LaTeX](https://www.latex-project.org/)
    -   [Git](https://git-scm.com)
    -   [Pandoc](https://pandoc.org/)
-   Schémas
    -   [Graphviz](https://graphviz.org/)
    -   [Inkscape](https://inkscape.org)
    -   [Wavedrom](https://wavedrom.com/)
    -   [Schemdraw](https://schemdraw.readthedocs.io/en/latest/)
    -   [Ditaa](https://ditaa.sourceforge.net/)
-   Simulation logique
    -   [Simulateur Digital](https://github.com/hneemann/Digital)
-   Coloration syntaxique
    -   [Pygments](https://pygments.org/docs/quickstart/)

Dans le but de faciliter l'adaptation, la réutilisation, la révision
et le remixage de cette ressource éducative libre, les documents
sources utilisés pour produire ce manuel sont accessibles via le dépôt
Github <https://github.com/gbegin/circuits_logiques/>. Le dépôt comporte
également des transparents pouvant être utilisés comme supports
d'enseignement.


# Préface

Ce manuel est une introduction au domaine de la conception des
circuits logiques, qui sont à la base de tous les systèmes numériques
modernes. Il s'adresse tout particulièrement aux personnes qui suivent
un enseignement technique, ou un premier cycle universitaire, ainsi
qu'à tous celles qui s'intéressent à l'ingénierie électronique.
Aucune connaissance préalable n'est requise pour pouvoir en assimiler
les concepts, mais une connaissance de la programmation permettra de
pousser l'expérimentation par simulation.

Les chapitres 1 à 3 de cet ouvrage sont consacrés aux concepts de base
de la logique binaire et des systèmes de numération. Ces notions sont
présentées d'un point de vue relativement abstrait qui n'est pas
étranger au fait que la logique binaire mise en oeuvre dans les
circuits numériques modernes est fondée sur des principes
mathématiques, voire philosophiques établis bien longtemps avant
l'invention de l'électronique.

Dans les trois chapitres suivants, on voit comment la logique peut
s'incarner dans des dispositifs électroniques: d'abord avec des portes
logiques simples (chapitre 4), et plus avant, avec des dispositifs
combinatoires plus complexes (chapitre 6). On présente également les
approches permettant de simplifier les circuits logiques
combinatoires, c'est-à-dire ceux dont le comportement ne dépend pas du
temps (chapitre 5).

Les circuits logiques séquentiels, qui, eux comportent de la
mémoire, sont considérés ensuite. On présente d'abord les loquets et
bascules, composants de base des circuits séquentiels (chapitre 7),
puis on aborde l'analyse (chapitre 8) et la conception (chapitre 9) de
circuits séquentiels synchrones. Le chapitre 10 présente de nombreux
types de circuits séquentiels typiques, alors que le chapitre 11 est
consacré aux différents types de mémoires.

Le chapitre 12 offre une brève introduction aux dispositifs logiques
programmables qui amènent les circuits logiques à un autre degré de
flexibilité et d'intégration.

Dans les chapitres 13 et 14, on s'intéresse à la modélisation de
circuits, en introduisant le langage descriptif VHDL, qui permet de
décrire formellement des circuits logiques pour en faire la
conception, la simulation, voire, la synthèse.

Le manuel se conclut avec des séries d'exercices (chapitre 15) qui
permettront de mettre en pratique les notions abordées.


# Table des matières

-   [Avant-propos](#org0ff06b8)
    -   [Remerciements](#orgdc0808c)
        -   [Licence](#org9b5383a)
        -   [Ressources](#org27557f3)
-   [Préface](#org4f98848)
1.  [Systèmes de numération](#org09b0bc9)
    1.  [Objectifs](#org3867377)
    2.  [Systèmes numériques](#orgf3001f2)
    3.  [Nombres binaires](#org9bdf4aa)
    4.  [Conversion binaire <-> décimal](#org82d7a64)
    5.  [Notation](#orgbccc8c8)
    6.  [Représentations compactes de nombres binaires](#org6eaeff1)
        1.  [Représentation octale](#orgea583d8)
        2.  [Représentation hexadécimale](#org3691374)
        3.  [Conversion en sens inverse](#orge3ab69b)
    7.  [Nombres binaires fractionnaires](#org1069943)
    8.  [Opérations arithmétiques binaires](#org1e02276)
        1.  [Multiplication et division par deux](#orga05f8d4)
    9.  [Compléments de nombres](#org3af7533)
        1.  [Complément à neuf et complément à un](#orgc857176)
        2.  [Complément à dix et complément à deux](#org0824f5a)
    10. [Nombres signés et codage](#org642efc2)
    11. [Opérations arithmétiques binaires](#org7a60cba)
        1.  [Addition de nombres non signés](#org1961250)
        2.  [Addition de nombres signés](#org9c24dbb)
        3.  [Soustraction de nombres signés](#orga901503)
        4.  [Extension de signe](#org50ceb31)
    12. [Codes binaires](#org10888e6)
        1.  [Code Gray](#org01c4c8e)
        2.  [Codes alphanumériques et autres](#orgb9c587d)
2.  [Logique binaire, fonctions logiques et algèbre de Boole](#orgc3ef947)
    1.  [Objectifs](#org5cee4c2)
    2.  [Logique binaire](#orgfc978c1)
        1.  [Variable binaire](#orgae07497)
        2.  [Opérations logiques](#org66848bf)
        3.  [Expression logique](#orgd2eb62f)
        4.  [Tableaux de vérité](#org6b0132a)
    3.  [Formalisme mathématique](#org25ea003)
        1.  [Définitions](#orge8f1034)
    4.  [Algèbre de Boole](#org2b9fef4)
    5.  [Algèbre de Boole à deux valeurs](#orgf3acbc0)
    6.  [Vérification des postulats](#org6c5f5f5)
3.  [Théorèmes et propriétés](#orga05310f)
    1.  [Objectifs](#org7450e4b)
    2.  [Dualité](#orge0df24c)
    3.  [Théorèmes de base](#org8222cd4)
        1.  [Autres fonctions logiques](#org5603e25)
        2.  [Fonctions de plusieurs entrées](#org2bac5f8)
        3.  [Expressions et fonctions binaires](#orgf95a58f)
    4.  [Théorèmes de DeMorgan](#org092bc54)
4.  [Portes logiques](#org2ca46a0)
    1.  [Objectifs](#orgde34ea1)
    2.  [Niveaux logiques](#org3bca4b3)
    3.  [Logique négative ou positive](#org8fc6c66)
    4.  [Symboles](#orga5c049a)
        1.  [Porte ET](#org365d765)
        2.  [Porte OU](#org7ef847a)
        3.  [Porte inverseur](#org7152e4b)
        4.  [Porte NON-OU (NOR)](#orgcfea063)
        5.  [Porte NON-ET (NAND) et NON-OU (NOR)](#orgb20e62b)
        6.  [Entrées inversées](#org47cc517)
        7.  [NAND et NOR, représentations équivalentes](#orgc5b741d)
        8.  [Porte OU-exclusif (XOR)](#orgd718f92)
        9.  [Porte NON-OU-exclusif ou Équivalence (XNOR)](#orgb6cb189)
    5.  [Universalité des NAND et NOR](#org8c44717)
    6.  [Limites physiques](#org4332831)
        1.  [Sortance (*Fan-out*)](#org75b4c0e)
        2.  [Modèles de délai](#org7a8597e)
        3.  [Porte tampon](#org2c225bc)
5.  [Simplification logique](#org911ac8d)
    1.  [Objectifs](#org4eaa479)
    2.  [Expressions équivalentes](#org03cd020)
    3.  [Formes canoniques](#org2abe653)
        1.  [Minterms et maxterms](#org91abd6c)
        2.  [Somme de produits](#orgfaf8199)
        3.  [Produit de sommes](#org006cd41)
        4.  [Conversion entre formes canoniques](#org174db38)
        5.  [Formes standard](#org70a2730)
    4.  [Objectifs de minimisation](#orgb6351f4)
    5.  [Diagrammes de Karnaugh](#org105e197)
        1.  [Procédure de simplification](#org2f09874)
        2.  [Cas facultatifs](#org5e39c17)
        3.  [Impliquants](#org70899b3)
        4.  [Impliquant premier](#orgff98c05)
        5.  [Couverture d'une fonction](#org7671a0d)
        6.  [Impliquant premier essentiel](#org5b07657)
        7.  [Sélection des impliquants](#org41f1de5)
        8.  [Minimisation avec cas facultatifs](#org631fe75)
        9.  [Minimisation avec plusieurs fonctions](#org45ba4ef)
    6.  [Tableau de couverture Quine-McCluskey](#org4e048af)
        1.  [Tableau de couverture réduit](#org7258242)
        2.  [Dominance de lignes](#orgf7864aa)
        3.  [Dominance de colonnes](#org8bf962d)
    7.  [Implémentation des fonctions simplifiées](#org9aea29c)
        1.  [Implémentation à deux niveaux](#org6f331b3)
6.  [Circuits combinatoires typiques](#org4921267)
    1.  [Objectifs](#org6b7c5be)
    2.  [Circuit combinatoire](#org9a91c1a)
    3.  [Analyse d'un circuit logique combinatoire](#org7494f27)
        1.  [Exemple](#org15cd364)
    4.  [Conception d'un circuit combinatoire](#orgb6488ad)
    5.  [Alternatives d'implémentation](#orga6b06c4)
        1.  [Implémentations via la fonction directe](#org7bf0362)
        2.  [Implémentations via la fonction complémentaire](#org090725c)
    6.  [Circuits logiques combinatoires classiques](#org74e27ad)
    7.  [Additionneur binaire](#org0d6c4d8)
        1.  [Demi-additionneur](#org937f87f)
        2.  [Additionneur complet](#orgc5453c1)
        3.  [Additionneur binaire pour $n$ bits](#orgc229c64)
        4.  [Propagation de retenue](#org3256f23)
        5.  [Anticipation de retenue](#orgc1ed758)
        6.  [Soustraction](#orgf946d76)
        7.  [Débordements](#orgae0a7a9)
    8.  [Multiplexeur](#orgc27ced6)
        1.  [Multiplexeur deux-vers-un](#org488b18c)
        2.  [Multiplexeur quatre-vers-un](#org3155df2)
    9.  [Décodeur](#orgf1cfdd4)
        1.  [Décodeur avec sortie active basse et signal de contrôle](#org259b51a)
        2.  [Implémentation de fonctions arbitraires au moyen d'un décodeur](#orgbe871d8)
    10. [Encodeur](#org6381ffe)
        1.  [Encodeur à priorité](#org39910cd)
    11. [Comparateur de magnitude](#org5877cfc)
    12. [Démultiplexeur](#org07a6991)
    13. [Encodeurs divers](#org9ec7319)
    14. [Portes à trois états et tampon de bus](#org47179c9)
7.  [Circuits séquentiels](#orgaba172b)
    1.  [Objectifs](#org1503d97)
    2.  [Modèle d'un circuit séquentiel](#orge726e6a)
    3.  [Éléments de mémoire](#org008dc5a)
    4.  [Loquets](#org83fa0ea)
        1.  [Loquet SR](#orgf160816)
        2.  [Loquet D](#org05536ad)
    5.  [Application: rebonds d'interrupteurs](#org47811cb)
    6.  [Bascules (Flip-flops)](#org4decb31)
        1.  [Bascule D](#org577cda4)
        2.  [Délais et réponse temporelle](#org9ea1076)
        3.  [Autres bascules](#org1c093d4)
        4.  [Bascule JK](#orgbfda221)
        5.  [Bascule T](#org43d3892)
        6.  [Tableaux caractéristiques](#org5925d7e)
        7.  [Équations caractéristiques](#orgaeaa135)
        8.  [Entrées asynchrones](#org0d6d7e6)
8.  [Analyse de circuits logiques séquentiels synchrones](#org36e9e5d)
    1.  [Objectifs](#org72add8f)
    2.  [Démarche d'analyse](#org971c458)
    3.  [Exemple d'analyse](#orgac16afc)
    4.  [Analyse pour des bascules JK](#orge3f71c3)
        1.  [Exemple avec bascules JK](#org2a912e0)
    5.  [Modèles de machines séquentielles](#org9f271f9)
9.  [Conception de circuits logiques séquentiels](#orgf57832d)
    1.  [Objectifs](#org00b626d)
    2.  [Conception d'un circuit séquentiel synchrone](#org4f9fa4c)
    3.  [Spécification fonctionnelle](#org5037725)
    4.  [Diagramme d'état](#org052990e)
    5.  [Tableau d'état](#orgeebcb22)
    6.  [Réduction du nombre d'états](#org7a86499)
        1.  [Tableau d'implication](#org1095183)
    7.  [Codage des états](#orge595b19)
    8.  [Décodeur d'état](#org54bb19f)
    9.  [Décodeur de sortie](#orgca7025a)
    10. [Procédure de conception](#org04eb751)
    11. [Exemple de conception](#org71003c3)
        1.  [Bascules D](#org37f5f0f)
        2.  [Autres types de bascules](#org800be2a)
    12. [États interdits](#org88418d0)
    13. [Exemple avec états *one-hot*](#orgddf5439)
10. [Circuit séquentiels: registres et compteurs](#orgd9af8f5)
    1.  [Objectifs](#org8ca4b75)
    2.  [Registres](#orgbdccebf)
        1.  [Chargement parallèle](#org38c2e39)
        2.  [Registres à décalage](#orgfb6c366)
    3.  [Compteurs](#org4b1b024)
        1.  [Compteur asynchrone](#orga0a9246)
        2.  [Compteur synchrone](#org4377ef0)
        3.  [Compteur bidirectionnel](#org24fd7ea)
        4.  [Compteur en anneau](#org837d7be)
        5.  [Compteur Johnson](#org52c1088)
        6.  [Diviseur de fréquence](#org002eb4b)
        7.  [Compteur à chargement parallèle](#orgc2e62cc)
        8.  [Compteur modulo](#org3c5d2df)
11. [Mémoires](#orgf54b202)
    1.  [Objectifs](#org52d32c0)
    2.  [Mémoires](#orgd66b304)
        1.  [Mémoires non-volatiles](#org8c6cfb8)
        2.  [Mémoires volatiles](#org18e6228)
    3.  [Adressage](#org3238b1a)
        1.  [Lecture et écriture](#org136e96e)
        2.  [Bus de données](#orgbefbbcd)
        3.  [Chronogrammes](#org2b40cb5)
    4.  [Mémoires mortes](#org83e1c79)
        1.  [Implémentation de fonctions combinatoires](#org5d71756)
        2.  [Tableau de correspondance](#orgb673136)
        3.  [Catégories de mémoires ROM](#orgae8dd91)
12. [Logique programmable](#orgd025945)
    1.  [Objectifs](#org362e0a5)
    2.  [Dispositifs programmables](#orga61b0cf)
        1.  [Matrice logique programmable (PLA)](#orgc47fba1)
        2.  [Logique à matrice programmable (PAL)](#org4d7679f)
        3.  [Logique programmable séquentielle](#org43cd37d)
    3.  [Circuits intégrés programmables](#orgd568765)
13. [Langages descriptifs et de modélisation](#org3b6d58b)
    1.  [Objectifs](#orge253891)
    2.  [Modélisation et simulation](#orgb4d3915)
    3.  [Langage VHDL](#orgb0ab10d)
    4.  [Entité](#orgf8131fb)
    5.  [Architecture](#org66a8a94)
    6.  [Signaux et assignation](#org52e23a9)
    7.  [Notes sur la syntaxe](#orgf016796)
    8.  [Concurrence](#org7710f69)
    9.  [Vecteurs de bits](#orgc6ff832)
    10. [Modèle complet](#org6c04773)
    11. [Modèle comportemental](#orgf0132a7)
    12. [Modèle flux de données](#org4f70d60)
    13. [Modèle structural](#orgbe6c50f)
    14. [Bloc processus](#orgb2fac41)
    15. [Modélisation du délai](#orgeedcb0e)
        1.  [Délai inertiel](#org1f6c05d)
        2.  [Délai de transport](#orgbe4e815)
    16. [Librairies](#org9436e31)
    17. [Encapsulation](#orgfa1f207)
    18. [Description de design en VHDL](#org8a4aa6e)
        1.  [Multiplicateur huit bits](#orgbbe159c)
    19. [Banc d'essai](#orgf77bdc6)
    20. [Instanciation](#org7e00d21)
    21. [Écoulement du temps](#org2bebf26)
    22. [Exemples de banc d'essai](#org2f77250)
        1.  [Création d'une entité vide pour le banc d'essai](#org41dbd8d)
        2.  [Instanciation du modèle à tester](#org0d59319)
        3.  [Génération de l'horloge et du signal de mise à zéro](#org7810abc)
        4.  [Stimulus](#org06d7160)
        5.  [Exemples complets](#orgf50923c)
    23. [Compilation et simulation](#org1a730aa)
14. [Préparation et simulation des modèles VHDL](#org7091919)
    1.  [Éditeurs](#org0cd2a9b)
    2.  [Simulateurs gratuits](#org0bcd3b8)
        1.  [Modelsim/Questa](#org308473f)
        2.  [Active-HDL (version étudiante)](#org32b7919)
        3.  [Vivado (Xilinx)](#org4325e4d)
        4.  [GHDL/GTKWave](#orgd6b02c1)
        5.  [EDA Playground](#orgdb5a54a)
15. [Exercices](#org26dbc29)


# Systèmes de numération


## Objectifs

-   Comprendre le fonctionnement du système de numération binaire
-   Pouvoir effectuer des conversions entre nombres en représentation
    binaire, octale, hexadécimale
-   Comprendre le rôle des compléments et la représentation de nombres signés
-   Comprendre la notation fractionnaire
-   Se familiariser avec quelques codes courants
-   Pouvoir effectuer des opérations arithmétiques sur des nombres binaires


## Systèmes numériques

Les systèmes numériques sont omniprésents dans notre monde
technologique. La grande force des systèmes numériques est leur
capacité à représenter l'information sous toutes ses formes et à
permettre la manipulation de cette information. Tout ensemble dont les
éléments peuvent être dénombrés, comme un alphabet ou un ensemble fini
de couleurs, se prête naturellement à une représentation
numérique. Mais il est également possible de représenter des
informations qui correspondent à des informations provenant
d'ensembles continus, comme par exemple des informations sonores, en
procédant à une numérisation par échantillonnage et codage. 

Une bonne façon de se familiariser avec la représentation numérique de
l'information est d'étudier le système de numération binaire. Dans un
chapitre suivant, nous étudierons les principes fondamentaux de la
logique binaire. C'est sur ces deux bases que nous pourrons établir
notre exploration des circuits logiques.


## Nombres binaires

Les nombres binaires sont essentiellement construits de la même façon
que les nombres décimaux qui nous sont plus familiers. La
différence fondamentale tient au fait qu'il n'est possible d'utiliser
que deux symboles (chiffres), 0 et 1, plutôt que les dix chiffres de 0
à 9. Les chiffres sont nommés bits (contraction de **b** inary dig
**it**).

Par exemple, le nombre décimal que nous écrivons $2843$ correspond à
$2 \times 1000 + 8 \times 100 + 4 \times 10 + 3 \times 1$. Il s'agit
d'un système positionnel, dans lequel la valeur attribuée à un chiffre
est définie par sa position et par la valeur de la **base** du système
de numération. Ainsi, pour ce nombre décimal, la base vaut 10 et on a
$2 \times 10^3 + 8 \times 10^2 + 4 \times 10^1 + 3 \times 10^0$. La
position la plus à gauche est celle dont la valeur est la plus
grande. C'est le **chiffre le plus significatif**; la position de droite
correspond au **chiffre le moins significatif**. On peut imaginer une
virgule après le chiffre le moins significatif, pour délimiter la
partie entière du nombre. D'autres chiffres, placés à droite de cette
virgule correspondraient à la partie fractionnaire. Nous y reviendrons.

Les mêmes règles positionnelles permettent d'attribuer une valeur à un
nombre binaire, en tenant compte du fait que la base vaut cette
fois-ci 2. Par exemple, la valeur attribuée au nombre binaire
$10101$ est 

$$ 1 \times 2^4 + 0 \times 2^3 + 1 \times 2^2 + 0 \times 2^1 + 1
\times 2^0 = 16+4+1= 21 $$

comme on peut voir dans le tableau [1](#org581ea45).

<table id="org581ea45" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 1 :</span> Valeur binaire du nombre \(10101\)</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Position</th>
<th scope="col" class="org-right">4</th>
<th scope="col" class="org-right">3</th>
<th scope="col" class="org-right">2</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">0</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Valeur</td>
<td class="org-right">\(2^4\)</td>
<td class="org-right">\(2^3\)</td>
<td class="org-right">\(2^2\)</td>
<td class="org-right">\(2^1\)</td>
<td class="org-right">\(2^0\)</td>
</tr>


<tr>
<td class="org-left">Valeur déc.</td>
<td class="org-right">16</td>
<td class="org-right">8</td>
<td class="org-right">4</td>
<td class="org-right">2</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">Bit</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Nous avons ici le **bit le plus significatif** à gauche et le **bit le
moins significatif** à droite. Chaque chiffre vaut deux fois plus que le
chiffre immédiatement placé à sa droite.


## Conversion binaire <-> décimal

Convertir un nombre entier binaire en nombre décimal se fait
naturellement, en s'appuyant sur les valeurs associées à la notation
positionnelle. La conversion en sens inverse, de décimal à binaire,
est un peu moins évidente. La méthode consiste à faire une division
entière du nombre (et des quotients successifs) par 2 et à noter les
restes obtenus. Le premier reste correspond au bit le moins
significatif, et le dernier, au bit le plus significatif.

Par exemple, les opérations pour convertir 37 en binaire sont résumées
dans le tableau [2](#org772ab86).

<table id="org772ab86" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 2 :</span> Étapes de conversion de 37 en binaire</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">Quotient entier</th>
<th scope="col" class="org-right">Reste</th>
<th scope="col" class="org-left">Coefficient</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">37/2</td>
<td class="org-right">18</td>
<td class="org-right">1</td>
<td class="org-left">\(a_0 = 1\)</td>
</tr>


<tr>
<td class="org-left">18/2</td>
<td class="org-right">9</td>
<td class="org-right">0</td>
<td class="org-left">\(a_1 = 0\)</td>
</tr>


<tr>
<td class="org-left">9/2</td>
<td class="org-right">4</td>
<td class="org-right">1</td>
<td class="org-left">\(a_2 = 1\)</td>
</tr>


<tr>
<td class="org-left">4/2</td>
<td class="org-right">2</td>
<td class="org-right">0</td>
<td class="org-left">\(a_3 = 0\)</td>
</tr>


<tr>
<td class="org-left">2/2</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">\(a_4 = 0\)</td>
</tr>


<tr>
<td class="org-left">1/2</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">\(a_5 = 1\)</td>
</tr>
</tbody>
</table>

On obtient ainsi 100101.


## Notation

Puisque les notations de nombres binaires, octaux, hexadécimaux ou
décimaux font appel à des chiffres qui sont tous tirés du même
ensemble, il y a un risque d'ambiguïté si on ne connaît pas la base
utilisée. Par exemple 11 peut soit s'interpréter comme onze (si on
suppose la base 10) ou comme trois (si on suppose la base 2). À
moins que le contexte ne soit absolument clair, il vaut mieux être
explicite pour éviter de telles ambiguïtés. C'est pourquoi on dénote
souvent explicitement la base; par exemple, (11)2 pour le nombre
trois en binaire qui pourra être distingué de (11)10, le nombre onze
en décimal.


## Représentations compactes de nombres binaires

En comparant un nombre décimal et sa représentation binaire, comme par
exemple ici 37 et 100101, on voit bien que la représentation binaire
est nettement plus encombrante. On utilise souvent des notations plus
compactes mais qui conservent un lien direct avec la représentation
binaire: la représentation **octale** et la représentation
**hexadécimale**.


### Représentation octale

La représentation octale consiste à utiliser la base 8, avec les
chiffres $0, 1, \ldots, 7$. On voit la correspondance entre les
nombres en binaire et les chiffres de la représentation octale dans le
tableau [72](#org236ae00).

<table id="orgf3c0f1e" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 3 :</span> Représentation octale</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">Binaire</th>
<th scope="col" class="org-right">Octal</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">000</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">001</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">010</td>
<td class="org-right">2</td>
</tr>


<tr>
<td class="org-right">011</td>
<td class="org-right">3</td>
</tr>


<tr>
<td class="org-right">100</td>
<td class="org-right">4</td>
</tr>


<tr>
<td class="org-right">101</td>
<td class="org-right">5</td>
</tr>


<tr>
<td class="org-right">110</td>
<td class="org-right">6</td>
</tr>


<tr>
<td class="org-right">111</td>
<td class="org-right">7</td>
</tr>
</tbody>
</table>

Pour convertir un nombre binaire en nombre octal, il suffit de
regrouper les bits par groupes de trois bits, en partant de la droite
(bit le moins significatif), et de remplacer chaque groupe par le
chiffre en base 8 correspondant.

Par exemple, pour (1010011110001)2, on aura le découpage du tableau
[4](#org1b5303f).

<table id="org1b5303f" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 4 :</span> Regroupement pour conversion en octal</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Binaire</td>
<td class="org-right">1</td>
<td class="org-right">010</td>
<td class="org-right">011</td>
<td class="org-right">110</td>
<td class="org-right">001</td>
</tr>


<tr>
<td class="org-left">Octal</td>
<td class="org-right">1</td>
<td class="org-right">2</td>
<td class="org-right">3</td>
<td class="org-right">6</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

On obtient le nombre octal (12361)8.


### Représentation hexadécimale

La représentation hexadécimale consiste à utiliser la base 16, avec
les chiffres $0, 1, \ldots, 9$, auxquels on ajoute les lettres A, B,
C, D, E et F pour représenter les valeurs de dix à quinze
respectivement<sup><a id="fnr.1" class="footref" href="#fn.1" role="doc-backlink">1</a></sup>. On voit la correspondance entre les nombres en binaire et les chiffres de la représentation hexadécimale dans le tableau [5](#orgc5187c4).

<table id="orgc5187c4" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 5 :</span> Représentation hexadécimale</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">Binaire</th>
<th scope="col" class="org-right">Hexadécimal</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0000</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0001</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0010</td>
<td class="org-right">2</td>
</tr>


<tr>
<td class="org-right">0011</td>
<td class="org-right">3</td>
</tr>


<tr>
<td class="org-right">0100</td>
<td class="org-right">4</td>
</tr>


<tr>
<td class="org-right">0101</td>
<td class="org-right">5</td>
</tr>


<tr>
<td class="org-right">0110</td>
<td class="org-right">6</td>
</tr>


<tr>
<td class="org-right">0111</td>
<td class="org-right">7</td>
</tr>


<tr>
<td class="org-right">1000</td>
<td class="org-right">8</td>
</tr>


<tr>
<td class="org-right">1001</td>
<td class="org-right">9</td>
</tr>


<tr>
<td class="org-right">1010</td>
<td class="org-right">A</td>
</tr>


<tr>
<td class="org-right">1011</td>
<td class="org-right">B</td>
</tr>


<tr>
<td class="org-right">1100</td>
<td class="org-right">C</td>
</tr>


<tr>
<td class="org-right">1101</td>
<td class="org-right">D</td>
</tr>


<tr>
<td class="org-right">1110</td>
<td class="org-right">E</td>
</tr>


<tr>
<td class="org-right">1111</td>
<td class="org-right">F</td>
</tr>
</tbody>
</table>

Pour convertir un nombre binaire en nombre hexadécimal, il suffit de
regrouper les bits par groupes de quatre bits, en partant de la droite
(bit le moins significatif), et de remplacer chaque groupe par le
chiffre en base 16 correspondant.

Par exemple, pour (1010011110001)2, on aura le découpage du tableau
[6](#orga58273b).

<table id="orga58273b" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 6 :</span> Regroupement pour conversion en hexadécimal</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
<th scope="col" class="org-right">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Binaire</td>
<td class="org-right">1</td>
<td class="org-right">0100</td>
<td class="org-right">1111</td>
<td class="org-right">0001</td>
</tr>


<tr>
<td class="org-left">Hexa</td>
<td class="org-right">1</td>
<td class="org-right">4</td>
<td class="org-right">F</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

On obtient le nombre hexadécimal (14F1)16.


### Conversion en sens inverse

La conversion de octal (respectivement, hexadécimal) à binaire se fait
simplement en remplaçant chaque chiffre octal (resp., hexadécimal) par
le groupe de trois (resp., quatre) bits correspondant, en partant du
moins significatif.


## Nombres binaires fractionnaires

Il est aussi possible de représenter des nombres fractionnaires en
base 2. En gardant à l'esprit que la position d'un bit détermine sa
valeur, il suffit d'étendre le principe déjà établi aux bits qui
seront placés après la virgule qui sépare la partie entière de la
partie fractionnaire. Les indices des positions à droite de la virgule
seront négatifs.

Le tableau [7](#orgcf4abd3) donne en exemple le détail de l'évaluation
de la valeur du nombre fractionnaire (101,11)2. On obtient comme
valeur $1 \times 4 + 0 \times 2 + 1 \times 1 + 1 \times 1/2 + 1
\times 1/4 = 5,75$.

<table id="orgcf4abd3" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 7 :</span> Évaluation de la valeur du nombre fractionnaire (101,11)2</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Position</th>
<th scope="col" class="org-right">2</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">-1</th>
<th scope="col" class="org-right">-2</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Valeur</td>
<td class="org-right">\(2^2\)</td>
<td class="org-right">\(2^1\)</td>
<td class="org-right">\(2^0\)</td>
<td class="org-right">\(2^{-1}\)</td>
<td class="org-right">\(2^{-2}\)</td>
</tr>


<tr>
<td class="org-left">Valeur déc.</td>
<td class="org-right">4</td>
<td class="org-right">2</td>
<td class="org-right">1</td>
<td class="org-right">1/2</td>
<td class="org-right">1/4</td>
</tr>


<tr>
<td class="org-left">Bit</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>


## Opérations arithmétiques binaires

Il est possible de transposer les opérations arithmétiques habituelles
pour effectuer différentes opérations arithmétiques: addition,
soustraction, multiplication, division, avec des nombres
binaires. Nous verrons plus loin comment ces opérations s'exécutent
lorsque nous aurons établi les formes d'encodages binaires qui seront
utilisés pour les nombres, notamment la représentation des nombres
signés.


### Multiplication et division par deux

Pour multiplier un nombre binaire non signé par deux, il suffit de
décaler tous ses bits d'une position vers la gauche. Si le nombre est
entier, on devra insérer un zéro à la position zéro. Si le nombre est
fractionnaire, le bit le plus significatif de la partie fractionnaire se
retrouvera à la position zéro.

$$ (10011)2 \times 2 = (100110)2 $$

$$ (100,11)2 \times 2 = (1001,1)2 $$

Pour diviser un nombre binaire par deux, il suffit de décaler tous ses
bits d'une position vers la droite. Une division fractionnaire
produira possiblement un nombre fractionnaire, comme dans l'exemple
suivant.

1.  Division fractionnaire

    $$ (10011)2 \div 2 = (1001,1)2 $$

2.  Division entière

    Pour une division entière (sans fraction), on éliminera le bit qui
    aurait été placé après la virgule.
    
    $$ (10011)2 \div 2 = (1001)2 $$
    
    Il est évident de généraliser ces opérations pour les multiplications
    ou divisions par des puissances de 2: par 4, 8, 16, etc.


## Compléments de nombres

Les compléments de nombres jouent un rôle dans la simplification de
certaines opérations mathématiques et logiques. Dans un système de
numération de base $b$, on considère deux types de compléments: le
complément à $b$ et le complément à $b-1$. Pour la base 10, nous
aurons donc le complément à dix et le complément à neuf. Pour les
nombres binaires (base 2), nous aurons le complément à deux et le
complément à un.  Pour évaluer les compléments d'un nombre, on doit
tenir compte du nombre de chiffres que comporte ce nombre.


### Complément à neuf et complément à un

Soit un nombre entier $N$ en base $b$ constitué de $n$ chiffres. Le
complément à $b-1$ de $N$ est $(b^n-1)-N$.

Par exemple, en base $b=10$, le complément à neuf pour le nombre décimal
$N = 4576$ formé de $n=4$ chiffres sera $(b^n-1)-N = (10^4 -1) -
4576 = 5424$.

En base $b=2$, le complément à un pour le nombre binaire $N =
(10011)2 = (19)10$ formé de $n=5$ bits sera $(b^n-1)-N = (2^5
-1) - 19 = 12$ ce qui donne en binaire: $(12)10 = (1100)2$.

On peut vérifier qu'il est très facile, en binaire, de déterminer le
complément à un, sans effectuer de calculs, en inversant simplement
chacun des bits de la représentation binaire du nombre à
complémenter. Ainsi, avec notre exemple, on trouve:

$$ 10011 $$

$$ 01100 $$

Remarquons ici un zéro non significatif comme premier bit à gauche.


### Complément à dix et complément à deux

Le complément à $b$ de l'entier $N$ s'évalue comme
$(b^n)-N$. Cela correspond à ajouter 1 au complément à $b-1$.

Ainsi, pour notre exemple précédent en base $b=10$, le complément à
dix pour le nombre décimal $N = 4576$ formé de $n=4$ chiffres sera
$(b^n)-N = (10^4) - 4576 = 5425$.

Pour notre autre exemple, en base $b=2$, le complément à deux pour
le nombre binaire $N = (10011)2 = (19)10$ formé de $n=5$ bits
sera $(b^n)-N = (2^5) - 19 = 13$ ce qui donne en binaire:
$(13)10 = (1101)2$.

L'évaluation directe à la main, sans calculs, du complément à deux est
également possible en suivant la démarche suivante:

1.  On parcourt le nombre binaire initial à partir (à droite) du bit le moins
    significatif, en retranscrivant les bits rencontrés jusqu'à
    atteindre un premier bit 1, que l'on retranscrit également.
2.  On continue la retranscription vers la gauche, en inversant cette
    fois les bits subséquents.

Par exemple, pour (10110)2, on aura la démarche détaillée dans le
tableau [8](#org1807761). Les étapes sont numérotées selon la position
considérée, à partir de la droite.

<table id="org1807761" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 8 :</span> Étapes pour complément à deux</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Nombre</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Étape 0</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">Retranscrit</td>
</tr>


<tr>
<td class="org-left">Étape 1</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">Retranscrit</td>
</tr>


<tr>
<td class="org-left">Étape 2</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">Inversé</td>
</tr>


<tr>
<td class="org-left">Étape 3</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">Inversé</td>
</tr>


<tr>
<td class="org-left">Étape 4</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">Inversé</td>
</tr>
</tbody>
</table>

Pour une évaluation par un circuit, on commencera par déterminer le
complément à un par inversion et on lui additionnera 1 pour obtenir le
complément à deux.


## Nombres signés et codage

Représenter des nombres $\geq 0$ en binaire est donc relativement
naturel. Dans l'optique où on voudra stocker ces nombres dans une
mémoire binaire numérique, il n'y a qu'à prévoir une taille suffisante
(en nombre de bits) pour pouvoir accommoder des nombres assez grands
pour l'application considérée. Avec $n$ bits, il est possible de
représenter des entiers de $0$ à $2^n-1$ avec cette représentation
«naturelle».

Mais on peut se demander comment représenter des nombres négatifs,
c'est-à-dire $< 0$. Une première observation est le fait que si on
considère des nombres positifs **et** négatifs, on double en quelque
sorte la quantité de valeurs à représenter. Par exemple, il y a 21
nombres à représenter si on veut pouvoir utiliser les valeurs
comprises entre $-10$ et $+10$, comme on peut le voir dans le
tableau [9](#org1322a2b).

<table id="org1322a2b" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 9 :</span> Nombre de valeurs à représenter entre \(-10\) et \(+10\)</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Gamme</th>
<th scope="col" class="org-right">N. de valeurs</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">de -10 à -1</td>
<td class="org-right">10</td>
</tr>


<tr>
<td class="org-left">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">de 1 à 10</td>
<td class="org-right">10</td>
</tr>
</tbody>

<tbody>
<tr>
<td class="org-left">Total</td>
<td class="org-right">21</td>
</tr>
</tbody>
</table>

Nous devons donc nous assurer d'avoir autant de combinaisons de bits
qu'il sera nécessaire. La deuxième observation est qu'il faudra un
moyen de distinguer les nombres positifs des nombres négatifs. Si on
veut que cette distinction puisse se faire non seulement sur papier,
mais surtout lorsque les nombres seront stockés et manipulés dans un
système électronique, il faut définir un format binaire «tout compris»
qui permette de le faire.

Nous devons donc établir un **code**, c'est-à-dire une **convention** qui
permettra de donner un sens à un groupe de bits. Le choix de la
convention devrait être guidé par les usages qui seront ultimement
faits des nombres qui seront représentés.

En fait, lorsque nous avons convenu (implicitement) de représenter des
nombres entiers en utilisant directement la conversion en base 2 des
nombres décimaux, nous avons établi un code de représentation qui,
bien que naturel, n'en est pas moins une convention. Ici, nous devrons
formuler plus explicitement la convention qui sera utilisée pour
représenter les entiers signés.

Une convention de représentation peut être établie totalement
arbitrairement, mais elle sera sans doute plus utile si elle peut
contribuer à faciliter des opérations courantes réalisées avec les
éléments à représenter. Puisqu'il est question ici de nombres entiers
signés, l'opération à considérer en priorité est l'addition. Nous devrions 
aussi considérer les trois points suivants dans notre choix de
convention pour attribuer des codes binaires aux valeurs. (Pour
illustrer notre réflexion, nous allons considérer des nombres pouvant
être représentés par des codes binaires de 4 bits, ce qui permet
en théorie de représenter un total de 16 valeurs.)

1.  Puisqu'il faudra partager notre ensemble de codes binaires en deux,
    il serait logique de placer la représentation pour zéro au centre
    de ce découpage.

2.  Les codes binaires utilisés pour un nombre et pour son inverse
    additif devraient être disposés symétriquement autour du code
    utilisé pour représenter le zéro. Il est naturel de représenter la
    valeur zéro avec le code 0000.

3.  L'ordre des codes devrait correspondre à l'ordre des nombres. On
    sait bien comment ordonner les nombres entiers, en passant des
    nombres négatifs aux nombres positifs.

Quel ordre serait approprié pour les représentations (codes binaires)?
L'ordre naturel, du moins pour les nombres entiers positifs, serait de
passer de 0000 à 0001 à 0010, etc. Il faudra cependant limiter le
nombre de valeurs positives, car il faut réserver des codes pour les
valeurs négatives, et nous avons déjà utilisé un code pour le
zéro. Quel code binaire devrait-on placer juste avant le zéro, pour
représenter -1? Si on dispose l'ensemble des codes binaires entre 0000
et 1111 selon un cycle, comme illustré sur la figure
[106](#orgdd9b79d), alors le code approprié pour -1 sera 1111. Et le
code pour -2 sera 1110. Un avantage de cette disposition est que, en
ajoutant 1 pour passer de -2 à -1, on parcourt le cycle dans le même
sens qu'en ajoutant 1 pour passer de 1 à 2.

![img](Sources_images_logiques/images/cycle.png "Relations entre les codes dans l'assignation en complément à deux")

En suivant cette logique, on pourra, comme indiqué sur la figure,
assigner les codes dans les boîtes en ellipses, en jaune, à des
valeurs positives et les codes dans les boîtes en hexagones, en vert,
à des valeurs négatives. Si on assigne autant de valeurs positives que
de valeurs négatives, un seul code binaire ne sera pas utilisable, le
code 1000, dans la boîte en losange. Tout mouvement selon le sens des
flèches (horaire) sur l'illustration correspond à une addition;
tout mouvement en sens inverse correspond à une soustraction. Les nombres
binaires seront ainsi symétriques par rapport à notre zéro.

Nous obtenons ainsi l'assignation du tableau [10](#orga222972).

<table id="orga222972" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 10 :</span> Assignation de codes aux nombres de 4 bits</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">Code</th>
<th scope="col" class="org-right">Nombre</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">1001</td>
<td class="org-right">-7</td>
</tr>


<tr>
<td class="org-right">1010</td>
<td class="org-right">-6</td>
</tr>


<tr>
<td class="org-right">1011</td>
<td class="org-right">-5</td>
</tr>


<tr>
<td class="org-right">1100</td>
<td class="org-right">-4</td>
</tr>


<tr>
<td class="org-right">1101</td>
<td class="org-right">-3</td>
</tr>


<tr>
<td class="org-right">1110</td>
<td class="org-right">-2</td>
</tr>


<tr>
<td class="org-right">1111</td>
<td class="org-right">-1</td>
</tr>


<tr>
<td class="org-right">0000</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0001</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0010</td>
<td class="org-right">2</td>
</tr>


<tr>
<td class="org-right">0011</td>
<td class="org-right">3</td>
</tr>


<tr>
<td class="org-right">0100</td>
<td class="org-right">4</td>
</tr>


<tr>
<td class="org-right">0101</td>
<td class="org-right">5</td>
</tr>


<tr>
<td class="org-right">0110</td>
<td class="org-right">6</td>
</tr>


<tr>
<td class="org-right">0111</td>
<td class="org-right">7</td>
</tr>


<tr>
<td class="org-right">1000</td>
<td class="org-right">aucun</td>
</tr>
</tbody>
</table>

Voici quelques observations importantes sur cette représentation.

1.  Tous les codes des nombres négatifs ont le premier bit à gauche
    (qui serait le bit le plus significatif) à la valeur 1, alors que
    les autres codes ont la valeur 0. Ce bit peut ainsi servir
    d'indicateur de signe, avec la convention habituelle qu'on ne met
    pas de signe au zéro. On parlera ainsi de **bit de signe** pour
    dénoter ce bit, qui ne contribue pas à la grandeur (en valeur
    absolue) du nombre.

2.  L'inverse additif d'un nombre $n$, c'est-à-dire $-n$, est
    représenté par le **complément à deux** du nombre. Ceci signifie que
    pour trouver l'inverse additif d'un nombre, il suffit de calculer
    son complément à deux. Le complément à deux du complément à deux nous
    redonnera le nombre initial, conformément à la double négation
    $--n = n$.

Il existe d'autres conventions pour la représentation de nombres
signés, comme la représentation signe+magnitude, mais la
représentation en complément à deux est de loin la plus utilisée.


## Opérations arithmétiques binaires


### Addition de nombres non signés

En transposant les opérations classiques pour effectuer à la main des
additions ou des soustractions, il est possible d'effectuer des
calculs avec des nombres binaires. Additionner des nombres entiers non
signés ne pose pas de difficultés particulières.

On suppose deux nombres entiers binaires non signés $A$ et $B$
représentés en utilisant le même nombre de bits (si un nombre est plus
petit, on ajoutera des 0 non significatifs à gauche pour compléter la
représentation). Lorsqu'on effectue l'opération bit par bit, en
partant de la position la moins significative, on peut utiliser la
table d'addition suivante. À la position $i$, on a trois entrées à
prendre en considération: $A_{i}$ et $B_{i}$, les bits des nombres
à additionner, et $R_{i-1}$, la retenue provenant de la position
$i-1$. En sortie, on a la somme $S_{i}$ et la retenue $R_{i}$.
On obtient le tableau de vérité suivant ([11](#org399589e)).

<table id="org399589e" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 11 :</span> Tableau de vérité pour l'additionneur binaire</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(A_{i}\)</th>
<th scope="col" class="org-right">\(B_{i}\)</th>
<th scope="col" class="org-right">\(R_{i-1}\)</th>
<th scope="col" class="org-right">\(R_{i}\)</th>
<th scope="col" class="org-right">\(S_{i}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Exemple:

A: 101110001
B: 001111001
S: 111101010
R: 001110001

S'il y a une retenue non nulle à la suite de l'addition à la position
la plus significative, il y a un **débordement**, car le résultat est trop
grand pour être représenté avec le nombre de bits initial.


### Addition de nombres signés

L'addition de nombres signés codés avec la représentation en complément
à deux est nettement avantageuse. Il suffit d'additionner les deux
nombres comme s'il s'agissait de nombres non signés, en incluant les
bits de signe dans le calcul. La retenue qui émane de la position la
plus significative ne doit pas être prise en compte. 

Exemple 1:

Additionnons $A=-2$ et $B=4$, représentés respectivement (1110)2 et (0100)2.

A: 1110
B: 0100
S: 0010
R: 1100

qui nous donne bien le résultat escompté: S = (0010)2 = (2)10.

Exemple 2:

Additionnons $A=3$ et $B=-5$, représentés respectivement (0011)2 et (1011)2.

A: 0011
B: 1011
S: 1110
R: 0011

qui nous donne bien le résultat escompté: S = (1110)2 = (-2)10.

On peut vérifier facilement qu'additionner un nombre avec son
complément à deux donne toujours zéro, ce qui revient à faire $-n + n
= 0$.

Comme avec l'addition de nombres entiers non signés, il faudra se
préoccuper des débordements qui peuvent survenir parce que la capacité
de représentation est limitée par la taille (en nombre de bits) des
codes binaires utilisés.


### Soustraction de nombres signés

La soustraction s'effectue en faisant $A - B = A + (-B)$, comme suit:

1.  On détermine le complément à deux du nombre à soustraire (ici, $B$).
2.  On additionne ce complément à deux au nombre duquel on soustrait  (ici, $A$). La
    retenue qui émane de la position la plus significative ne doit pas
    être prise en compte.

Le résultat s'interprétera comme un nombre signé en complément à deux. 


### Extension de signe

Dans la représentation des nombres signés en complément à deux, le bit
de signe (bit le plus à gauche) est une indication directe du signe
d'un nombre. Si on change la taille des nombres, c'est-à-dire, le nombre
de bits utilisés au total pour la représentation, il faut une
opération spécifique pour préserver l'encodage en complément à deux. 

Considérons par exemple le nombre 5, représenté d'abord sur quatre
bits et ensuite sur huit bits. On a pour 5 

$$ 0101 $$

ou encore 

$$ 00000101 $$

Quand on compare ces deux représentations, on observe: 

-   qu'elles se terminent de la même façon, avec les trois bits 101 qui
    représentent la grandeur du nombre;
-   que le bit le plus à gauche est 0 dans les deux cas (même signe);
-   que dans la représentation sur huit bits, il y a des bits 0 entre le bit
    de signe et les trois derniers bits.

Considérons maintenant un nombre négatif, le nombre -5, représenté
d'abord sur quatre bits et ensuite sur huit bits. Le complément à deux
de 5 = (0101)2 est

$$ 1011 $$

alors que le complément à deux de 5 = (00000101)2 est

$$ 11111011 $$

Quand on compare ces deux représentations, on observe: 

-   qu'elles se terminent de la même façon, avec les trois bits 011;
-   que le bit le plus à gauche est 1 dans les deux cas (même signe);
-   que dans la représentation sur huit bits, il y a des bits 1 entre le bit
    de signe et les trois derniers bits.

Ces constatations nous amènent à conclure que lorsqu'on augmente la
taille de représentation d'un nombre signé, il faut faire une
**extension de signe** pour intercaler les bonnes valeurs binaires entre
le bit de signe et les bits qui représentent la grandeur du
nombre. Pour un nombre positif, on doit intercaler des bits 0, alors
que pour un nombre négatif, on intercale des bits 1. On peut donc
énoncer la règle comme *on doit intercaler des bits dont la valeur est
la même que le bit de signe.*

Si, à l'inverse, on réduit la taille des nombres signés, on n'aura
qu'à supprimer des bits, tous égaux au bit de signe, entre le bit de
signe et ceux qui représentent la grandeur du nombre. Si les bits à
supprimer ne sont pas tous égaux au bit de signe, c'est une indication
que la réduction de taille n'est pas possible: la nouvelle taille est
insuffisante pour représenter les nombres correctement.


## Codes binaires

Il n'y a pas que des nombres que l'on voudra représenter en
binaire. Il est maintenant le temps de définir ce qu'on appelle un
**code binaire**, car cette notion est au centre de tous les encodages
que nous aurons à utiliser.

Un code binaire sur $n$ bits est typiquement une association entre,
d'une part, les éléments d'un ensemble que l'on cherche à représenter
et d'autre part, les différents groupes ou patrons possibles avec
$n$ bits. On appelle parfois ces patrons des mots du code (ou par abus
de langage, des codes). Comme il y a $2^n$ patrons de bits
différents, il est possible d'associer jusqu'à ce nombre
d'éléments.

Une règle, souvent implicite mais essentielle, stipule qu'**on
ne devrait associer qu'un seul élément à un patron de bits donné.**
Sinon, l'interprétation du code (le décodage) devient ambiguë. Selon
l'application, il n'est pas toujours nécessaire d'associer tous les
patrons de bits à des éléments. Par exemple, si on veut représenter
les chiffres décimaux, il est nécessaire de disposer d'au moins 10
patrons de bits, ce qui est possible avec $n=4$. Puisque $2^4 =
16$, il y aura $16 - 10 = 6$ patrons de bits inutilisés.

La règle spécifique d'association peut être établie arbitrairement,
mais elle est souvent conçue en vue de respecter certaines propriétés
liées aux éléments à représenter ou à la configuration du code
lui-même. C'est ce qu'on a fait, par exemple, pour définir la
convention d'encodage des entiers par complément à deux.


### Code Gray

Lorsqu'on utilise un code binaire pour représenter des valeurs
associées à des phénomènes physiques, il peut être opportun d'utiliser
un encodage dans lequel le nombre de changements de bits est minimal
lorsqu'on passe d'un patron de bits au suivant dans la séquence des
codes. Par exemple, si on cherche à encoder des positions d'un
interrupteur rotatif (comme pour encoder des angles), il est
préférable que lorsqu'on passe d'une position à la suivante en tournant
le commutateur, un seul bit ne change dans la sortie. Ainsi, une
erreur sur un bit n'introduit pas un gros changement dans
l'interprétation de la valeur encodée. Un code Gray permet d'atteindre
cet objectif.

Avec le code Gray du tableau [12](#org3c45950), on peut voir par exemple que la
transition entre les codes pour 7 et 8 n'entraîne qu'un changement sur
un bit, de 0110 à 1100. Avec un encodage classique basé sur les
entiers binaires, on aurait observé pour ce cas une transition entre
0111 et 1000, qui comporte quatre changements de valeurs de bits.

<table id="org3c45950" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 12 :</span> Code Gray à quatre bits</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">Code Gray</th>
<th scope="col" class="org-right">Valeur</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0000</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0001</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0011</td>
<td class="org-right">2</td>
</tr>


<tr>
<td class="org-right">0010</td>
<td class="org-right">3</td>
</tr>


<tr>
<td class="org-right">0110</td>
<td class="org-right">4</td>
</tr>


<tr>
<td class="org-right">0111</td>
<td class="org-right">5</td>
</tr>


<tr>
<td class="org-right">0101</td>
<td class="org-right">6</td>
</tr>


<tr>
<td class="org-right">0100</td>
<td class="org-right">7</td>
</tr>


<tr>
<td class="org-right">1100</td>
<td class="org-right">8</td>
</tr>


<tr>
<td class="org-right">1101</td>
<td class="org-right">9</td>
</tr>


<tr>
<td class="org-right">1111</td>
<td class="org-right">10</td>
</tr>


<tr>
<td class="org-right">1110</td>
<td class="org-right">11</td>
</tr>


<tr>
<td class="org-right">1010</td>
<td class="org-right">12</td>
</tr>


<tr>
<td class="org-right">1011</td>
<td class="org-right">13</td>
</tr>


<tr>
<td class="org-right">1001</td>
<td class="org-right">14</td>
</tr>


<tr>
<td class="org-right">1000</td>
<td class="org-right">15</td>
</tr>
</tbody>
</table>


### Codes alphanumériques et autres

Vous rencontrerez sans doute plusieurs autres encodages courants,
par exemple pour encoder des caractères (code ASCII, codes UTF)
ou pour encoder uniquement des chiffres décimaux (code BCD). Une fois
qu'on a bien compris la règle d'encodage, il n'y a généralement pas de
difficultés à les utiliser.

Certains codes sont construits de manière à permettre d'identifier et
même, dans certains cas, de corriger des erreurs dans le stockage ou
la transmission des données encodées. Ces codes sont construits en
fonction de règles d'encodage, qui, lorsqu'elles ne sont pas
respectées, permettent de constater la présence d'erreurs.


# Logique binaire, fonctions logiques et algèbre de Boole


## Objectifs

-   Situer les opérations de la logique binaire dans leur contexte algébrique
-   Se familiariser avec les postulats de l'algèbre de Boole, et les
    principaux théorèmes
-   Exprimer une fonction logique par un tableau de vérité
-   Formuler une expression logique à partir d'un tableau de vérité
-   Exprimer une fonction logique en *somme de produits*, ou en
    *produit de sommes*, et convertir d'une forme à l'autre


## Logique binaire

La logique binaire associe une valeur de vérité à des variables, selon
une convention préétablie. Ces valeurs de vérité sont binaires, à
savoir **vrai** ou **faux**. Pour représenter ces valeurs de vérité, on
peut utiliser un encodage binaire, par exemple:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Valeur de vérité</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">Valeur binaire</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Vrai</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">Faux</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>


### Variable binaire

Une variable binaire, dénotée par une lettre, permet de désigner une
valeur binaire pouvant assumer une des deux valeurs possible, 0
ou 1. La variable est typiquement associée à une proposition, à l'état
d'un élément ou à toute autre condition pouvant admettre deux états
distincts. En assignant une valeur binaire à la variable, on définit
une valeur de vérité associée à cette variable, et ainsi à la
condition qu'elle représente. Par exemple, soit $S$ une variable
binaire qui représente la proposition «le soleil est visible». Alors,
$S=0$ peut s'interpréter comme «le soleil est visible est faux» ou
«le soleil n'est pas visible».


### Opérations logiques

Trois opérations logiques de base permettent d'agir sur des variables
binaires, de les combiner et de formuler des expressions logiques à
partir d'elles.

1.  ET: cette opération est représentée (comme la multiplication) par
    un point central ou par l'absence de signe d'opérateur entre les
    arguments. Par exemple, $x \cdot y$ ou $x y$. La valeur de
    l'expression est 1 si et seulement si toutes les variables ont la
    valeur 1. Sinon, la valeur est 0.
2.  OU: cette opération est représentée (comme l'addition) par un signe
    +. Par exemple, $x + y$. La valeur de l'expression est 1 si au
    moins une des variables a la valeur 1. Si aucune des variables ne
    vaut 1, la valeur de l'expression est 0.
3.  NON: cette opération est représentée par un prime, par
    exemple $x^\prime$, ou par une barre au-dessus de la variable,
    $\overline{x}$.  L'opération NON renverse la valeur binaire de
    son argument: si $x =0$ alors $x^ \prime = 1$; si $x =1$
    alors $x^ \prime = 0$. Cette opération de négation, est aussi
    appelée complément, car complémenter une valeur binaire revient à
    faire basculer sa valeur.


### Expression logique

Une expression logique combine des variables logiques et des
opérations et peut donc assumer une valeur binaire logique. Cette
valeur logique peut être assignée à une autre variable, en créant
ainsi une équation logique. Par exemple, $z = x \cdot y$ signifie
que $z$ assume la valeur de l'expression $x \cdot y$. À partir des
valeurs logiques des variables (entrées) $x$ et $y$, on peut donc
déterminer la valeur logique de la sortie $z$.


### Tableaux de vérité

On peut décrire la valeur logique d'une variable de sortie en
fonction des valeurs possibles des variables d'entrée au moyen
d'un tableau de vérité. Dans un tel tableau, il y a une ligne pour
chaque combinaison possible des valeurs d'entrée et, sur chaque ligne,
on indique la valeur de sortie correspondante. C'est en quelque sorte
une description en extension de la valeur de l'expression de sortie.

Voici par exemple les tableaux de vérité pour les opérations de base.

Opération ET:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x \cdot y\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Opération OU:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x + y\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Opération complément:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x^{\prime}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>


## Formalisme mathématique

Un formalisme mathématique, élaboré bien avant l'avènement des
circuits électroniques numériques, permet de formuler, analyser et
simplifier les expressions de la logique binaire. Il s'agit de
l'algèbre de Boole. 


### Définitions

Une algèbre est un système mathématique, défini pour un ensemble
d'éléments auxquels sont associés un ensemble d'opérateurs et qui
respecte un jeu d'axiomes ou postulats. Une algèbre nécessite donc:

1.  Un ensemble $S$ d'éléments

2.  Des opérateurs: $\cdot$, $\star$, $+$

3.  L'application des opérateurs aux différents éléments doit respecter
    un certain nombre de propriétés appelées postulats, comme:
    -   Fermeture
    
    -   Associativité
    
    -   Commutativité
    
    -   Existence d'élément identité
    
    -   Existence d'élément inverse
    
    -   Distributivité

Selon le choix des postulats, on arrive à définir différents types de
systèmes algébriques. Par exemple, les nombres réels qui nous sont
familiers constituent un système algébrique d'un type appelé **corps**.


## Algèbre de Boole

Une algèbre de Boole est un type de système algébrique défini sur un
ensemble $B$, muni de deux opérateurs dénotés $+$ et $\cdot$, et qui
respecte les postulats suivants<sup><a id="fnr.2" class="footref" href="#fn.2" role="doc-backlink">2</a></sup> (postulats de Huntington):

1.  Fermeture: tout résultat d'une opération sur un élément de
    l'ensemble donne un élément de l'ensemble.
    1.  &spades; Fermeture par rapport à $+$.
    
    2.  &hearts; Fermeture par rapport à $\cdot$.

2.  Éléments identité
    1.  &spades; Élément identité de $+$, noté 0: on a $x + 0 = 0 + x = x$.
    
    2.  &hearts; Élément identité de $\cdot$, noté 1: on a $x \cdot 1 = 1 \cdot x = x$.

3.  Commutativité
    1.  &spades; Commutativité par rapport à $+$: on a $x + y = y + x$.
    
    2.  &hearts; Commutativité par rapport à $\cdot$: on a $x \cdot y = y
                \cdot x$.

4.  Distributivité
    1.  &spades; $\cdot$ est distributif sur $+$: on a $x \cdot (y + z)= (x \cdot y) +
                (x \cdot z)$.
    
    2.  &hearts; $+$ est distributif sur $\cdot$: on a $x + (y \cdot z)= (x + y) \cdot
                (x + z)$.

5.  Pour chaque élément $x \in B$, il existe un élément
    $x^{\prime} \in B$ (appelé complément de $x$) tel que
    1.  &spades; $x + x^{\prime} = 1$.
    
    2.  &hearts; $x \cdot x^{\prime} = 0$.

6.  Il existe au moins deux éléments $x, y \in B$ tels que $x \neq y$.

Observons des différences entre une algèbre de Boole et le corps des réels:

1.  Il n'y a pas de loi d'associativité dans les postulats. On peut en
    démontrer une, cependant.

2.  L'opération $+$ est distributive sur $\cdot$.

3.  Il n'y a pas d'inverse multiplicatif ni d'inverse additif, on ne
    peut donc pas faire de soustraction ou de division.

4.  Il y a un concept de complément.

5.  L'ensemble d'éléments est différent. Nous utiliserons pour notre
    part l'ensemble $B: \{0, 1 \}$ pour notre algèbre de Boole.


## Algèbre de Boole à deux valeurs

L'ensemble de définition: $B : \{0, 1 \}$.

Opérateur $\cdot$

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x \cdot y\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Opérateur $+$

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x + y\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Règle de complémentation

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x^{\prime}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>


## Vérification des postulats

1.  La fermeture est évidente (en regardant les tableaux des opérations).

2.  En observant les tableaux de vérité, on constate que
    
    1.  $0 + 0 = 0$, $0 + 1 = 1 + 0 = 1$
    
    2.  $1 \cdot 1 = 1$, $0 \cdot 1 = 1 \cdot 0 = 0$
    
    ce qui définit les deux éléments identité: 0 pour $+$ et 1 pour  $\cdot$.

3.  La commutativité des lois est évidente: les tableaux sont
    symétriques.

4.  Les lois de distributivité se démontrent aisément en établissant des
    tableaux de vérité pour les différentes valeurs de $x, y$ et $z$.

5.  Par le tableau de complément, on vérifie que
    1.  $x + x^{\prime} = 1$, car $0 + 0^{\prime} = 0 + 1 = 1$ et $1 +
                1^{\prime} = 1+ 0 = 1$
    
    2.  $x \cdot x^{\prime} = 0$ car $0 \cdot 0^{\prime} = 0 \cdot 1 =
                0$ et $1 \cdot 1^{\prime} = 1 \cdot 0 = 0$.

6.  Le postulat 6 est vérifié car il y a deux éléments distincts: 0 et 1.


# Théorèmes et propriétés


## Objectifs

-   Bien saisir les relations de dualité entre les opérations
-   Connaître les principaux théorèmes de l'algèbre de Boole et
    les appliquer correctement
-   Appliquer les théorèmes de DeMorgan
-   Passer d'une version d'un théorème à sa version duale
-   Connaître les autres fonctions logiques importantes
-   Construire un tableau de vérité


## Dualité

Les postulats ont été formulés en paires, identifiés par &spades; et
&hearts;. En interchangeant les opérateurs et les éléments identité, on
transforme un postulat de forme &spades; en un postulat de forme
&hearts;. C'est le principe de **dualité**. Ainsi, n'importe quelle
expression algébrique demeurera valide si les opérateurs et les
valeurs d'éléments identité sont interchangés.

Puisque notre algèbre ne comporte que deux éléments, les deux éléments
identité sont en fait les deux seuls éléments, 0 et 1. On obtient donc
le dual d'une expression en changeant les 0 pour des 1, les 1 pour des
0 et les ET pour des OU, les OU pour des ET.


## Théorèmes de base

Le tableau [20](#org63be87f) résume les postulats et théorèmes de base de
notre algèbre. On présente en parallèle chaque version et sa version
duale.

<table id="org63be87f" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 13 :</span> Théorèmes de l'algèbre de Boole</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">Version  &spades;</th>
<th scope="col" class="org-left">Version  &hearts;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Postulat 2</td>
<td class="org-left">\(x+0=x\)</td>
<td class="org-left">\(x \cdot 1 = x\)</td>
</tr>


<tr>
<td class="org-left">Postulat 5</td>
<td class="org-left">\(x+x^{\prime} = 1\)</td>
<td class="org-left">\(x \cdot x^{\prime} = 0\)</td>
</tr>


<tr>
<td class="org-left">Théorème 1</td>
<td class="org-left">\(x + x = x\)</td>
<td class="org-left">\(x \cdot x = x\)</td>
</tr>


<tr>
<td class="org-left">Théorème 2</td>
<td class="org-left">\(x + 1 = 1\)</td>
<td class="org-left">\(x \cdot 0 = 0\)</td>
</tr>


<tr>
<td class="org-left">Théorème 3</td>
<td class="org-left">\((x^{\prime})^{\prime} = x\)</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">Postulat 3</td>
<td class="org-left">\(x + y = y + x\)</td>
<td class="org-left">\(xy = yx\)</td>
</tr>


<tr>
<td class="org-left">Théorème 4</td>
<td class="org-left">\(x + (y + z) = (x + y ) + z\)</td>
<td class="org-left">\(x(yz) = (xy)z\)</td>
</tr>


<tr>
<td class="org-left">Postulat 4</td>
<td class="org-left">\(x(y+z) = xy + xz\)</td>
<td class="org-left">\(x + yz = (x+y)(x+z)\)</td>
</tr>


<tr>
<td class="org-left">Théorème 5</td>
<td class="org-left">\((x + y)^{\prime} = x^{\prime} y^{\prime}\)</td>
<td class="org-left">\((xy)^{\prime} = x^{\prime} + y^{\prime}\)</td>
</tr>


<tr>
<td class="org-left">Théorème 6</td>
<td class="org-left">\(x + xy = x\)</td>
<td class="org-left">\(x(x+y) = x\)</td>
</tr>
</tbody>
</table>


### Autres fonctions logiques

Nous avons vu que les opérateurs logiques ET, OU et NON, qu'on peut
aussi appeler fonctions logiques, sont à la base même de la définition
de notre algèbre de Boole. Il est possible de concevoir d'autres
fonctions logiques qui vont s'avérer utiles pour la formulation, la
conception et la réalisation de systèmes logiques. Voici quelques-unes
des plus souvent utilisées.

1.  Fonction NON-ET (NAND)

    La fonction NON-ET, souvent désignée NAND, est obtenue en
    complémentant la sortie d'une fonction ET: $(x \cdot y)^\prime$.
    
    <table id="orgaa4d036" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    <caption class="t-above"><span class="table-number">Tableau 14 :</span> Tableau de vérité de la fonction NON-ET</caption>
    
    <colgroup>
    <col  class="org-right" />
    
    <col  class="org-right" />
    
    <col  class="org-left" />
    
    <col  class="org-right" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-right">\(x\)</th>
    <th scope="col" class="org-right">\(y\)</th>
    <th scope="col" class="org-left">&#xa0;</th>
    <th scope="col" class="org-right">\((x \cdot y)^\prime\)</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    </tr>
    
    
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    </tr>
    </tbody>
    </table>

2.  Fonction NON-OU (NOR)

    La fonction NON-OU, souvent désignée NOR, est obtenue en complémentant
    la sortie d'une fonction OU: $(x + y)^\prime$.
    
    <table id="org688a466" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    <caption class="t-above"><span class="table-number">Tableau 15 :</span> Tableau de vérité de la fonction NON-OU</caption>
    
    <colgroup>
    <col  class="org-right" />
    
    <col  class="org-right" />
    
    <col  class="org-left" />
    
    <col  class="org-right" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-right">\(x\)</th>
    <th scope="col" class="org-right">\(y\)</th>
    <th scope="col" class="org-left">&#xa0;</th>
    <th scope="col" class="org-right">\((x + y)^\prime\)</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    </tr>
    
    
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    </tr>
    </tbody>
    </table>

3.  Fonction OU-exclusif (XOR)

    La fonction OU-exclusif, souvent désignée XOR, est obtenue en évaluant
    $x \cdot y^\prime + x^\prime \cdot y$. La sortie est 1 seulement si
    une seule des entrées est 1. On verra plus loin que cette fonction
    joue un rôle important dans la formulation d'un additionneur.
    
    <table id="orgdc5f32e" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    <caption class="t-above"><span class="table-number">Tableau 16 :</span> Tableau de vérité de la fonction OU-exclusif</caption>
    
    <colgroup>
    <col  class="org-right" />
    
    <col  class="org-right" />
    
    <col  class="org-left" />
    
    <col  class="org-right" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-right">\(x\)</th>
    <th scope="col" class="org-right">\(y\)</th>
    <th scope="col" class="org-left">&#xa0;</th>
    <th scope="col" class="org-right">\((x \cdot y^\prime + x^\prime \cdot y)\)</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    </tr>
    </tbody>
    </table>


### Fonctions de plusieurs entrées

La plupart des fonctions logiques simples peuvent naturellement se
formuler en fonction de plus de deux entrées. Par exemple, $a \cdot b
\cdot c$ nous donne une fonction ET à trois entrées, et on peut
facilement imaginer des fonctions ET ou des fonctions OU avec encore
plus d'entrées.


### Expressions et fonctions binaires

Une fonction binaire peut être décrite par une expression algébrique
booléenne. Selon les valeurs des variables, la valeur de l'expression
booléenne détermine la valeur de la fonction. Par exemple, $F_1$ est
une fonction de trois entrées $a$, $b$ et $c$ définie par
l'expression

$$ F_1 = a + b \cdot c^\prime $$

La priorité des opération dans les expressions algébriques est (1)
parenthèses, (2) NON, (3) ET, (4) OU.

Il est possible de construire le tableau de vérité pour $F_1$ en
évaluant la fonction pour les $2^3 = 8$ combinaisons d'entrées
possibles, comme dans le tableau [24](#org141e6e6).

<table id="org141e6e6" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 17 :</span> Fonction de trois variables</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(a\)</th>
<th scope="col" class="org-right">\(b\)</th>
<th scope="col" class="org-right">\(c\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(F_1\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

En général, pour une fonction à $n$ entrées, le tableau de vérité
comportera $2^n$ lignes.


## Théorèmes de DeMorgan

Le complément d'une fonction $F$, $F^\prime$, s'obtient en
remplaçant tous les 0 par des 1 et tous les 1 par des 0 dans les
valeurs de la fonction. Par exemple, en complémentant ainsi les
valeurs dans le tableau de vérité, on effectue ce changement.

On peut aussi effectuer ce changement en appliquant les théorèmes de
DeMorgan (Théorème 5 &spades; et &hearts; du tableau [20](#org63be87f)) qui
peuvent se généraliser à plus de deux variables.


# Portes logiques


## Objectifs

-   Se familiariser avec les symboles usuels des portes logiques
-   Se familiariser avec les conventions et règles de dessin de schémas
    logiques
-   Faire la différence entre niveau de signal et valeur logique
-   Expliquer les différences entre le fonctionnement idéalisé
    et la réalité physique des portes logiques


## Niveaux logiques

Une porte logique est un dispositif électronique qui implémente une
fonction logique en agissant sur des signaux électriques selon une
convention préétablie. En général, on établit des valeurs binaires en
se basant sur la tension des signaux, en définissant une
correspondance entre des gammes de tensions et les valeurs logiques 0
et 1. Par exemple, pour une tension d'alimentation $V_{DD}$, on
pourrait avoir les correspondances suivantes:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Gamme de tensions</th>
<th scope="col" class="org-left">Niveau</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">de 0 à  \(V_{DD}/3\)</td>
<td class="org-left">Niveau bas</td>
</tr>


<tr>
<td class="org-left">de \(2V_{DD}/3\) à  \(V_{DD}\)</td>
<td class="org-left">Niveau haut</td>
</tr>
</tbody>
</table>

Les portes logiques sont manufacturées selon différents standards
technologiques qu'on appelle communément des **familles logiques**. Au
sein d'une même famille, les portes respectent les mêmes références de
niveaux pour pouvoir fonctionner ensemble adéquatement. Une porte peut
comporter une ou plusieurs entrées et agit généralement sur une seule
sortie.


## Logique négative ou positive

On associe ensuite une valeur binaire à chacun des niveaux selon une
certaine convention, par exemple:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Niveau</th>
<th scope="col" class="org-right">Valeur logique</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Niveau bas</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">Niveau haut</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

qui correspond à une logique positive. La convention inverse nous
donne la logique négative.

Certains signaux seront considérés comme actifs lorsque leur niveau
logique sera 0. On parlera alors de signaux **actifs bas**. La
convention implicite est généralement que les signaux sont **actifs
haut**.


## Symboles

On a défini des symboles pour représenter graphiquement les portes
logiques courantes. Dans un schéma logique, les portes sont
interconnectées au moyen de symboles de conducteurs
(fils) qui permettent d'acheminer les valeurs logiques d'une porte à
l'autre.


### Porte ET

À deux entrées $S =  A \cdot B$

![img](Sources_images_logiques/images/and_logique.svg "Porte ET à deux entrées")

Les portes qui réalisent des fonctions qui sont associatives et
commutatives peuvent aussi se définir avec plus de deux entrées. C'est
le cas avec les fonctions ET et OU.

À trois entrées $S =  A \cdot B \cdot C$

![img](Sources_images_logiques/images/and3_logique.svg "Porte ET à trois entrées")


### Porte OU

À deux entrées $S =  A + B$

![img](Sources_images_logiques/images/or_logique.svg "Porte OU à deux entrées")


### Porte inverseur

L'opération NON qui consiste à complémenter une valeur binaire
s'effectue avec une porte appelée **inverseur**.  Il n'y a toujours
qu'une entrée. $B = A^\prime$

![img](Sources_images_logiques/images/not_logique.svg "Porte inverseur") 


### Porte NON-OU (NOR)

![img](Sources_images_logiques/images/nor_logique.svg "Porte NOR à deux entrées")


### Porte NON-ET (NAND) et NON-OU (NOR)

Les fonctions NAND et NOR ne sont pas associatives. Par exemple,

$$
(x \operatorname{Nor} y) \operatorname{Nor} z \neq x \operatorname{Nor} (y \operatorname{Nor} z) 
$$

On peut néanmoins définir des versions à plusieurs entrées de ces
fonctions en ajustant la priorité d'évaluation. Pour une porte NAND à
trois entrées, on fera $S = (A \cdot B \cdot C)^\prime$.

Pour une porte NOR à trois entrées, on fera $(A + B + C)^\prime$.

![img](Sources_images_logiques/images/nand3_logique.svg "Porte NAND à trois entrées")


### Entrées inversées

On utilise souvent l'élément symbolique qui est placé à la sortie de
l'inverseur (un petit cercle) pour indiquer l'inversion d'une entrée
ou d'une sortie d'une porte. C'est le cas à la sortie des portes NAND
et NOR comme on vient de le voir. Un autre exemple est la porte NAND
de la figure [274](#orgf167942), où une des entrées est également
inversée. La porte évalue donc $S =  (A^\prime \cdot B  \cdot C)^\prime$

![img](Sources_images_logiques/images/nand3_logique_invin1.svg "Porte NAND à trois entrées dont une inversée") 


### NAND et NOR, représentations équivalentes

En vertu du théorème de DeMorgan, on sait que $(x + y)^{\prime} =
x^{\prime} y^{\prime}$ et que $(xy)^{\prime} = x^{\prime} +
y^{\prime}$. On peut donc représenter les portes NAND et NOR de deux
façons équivalentes.

![img](Sources_images_logiques/images/NANDequiv.svg "Deux représentations équivalentes pour une porte NAND")

![img](Sources_images_logiques/images/NORequiv.svg "Deux représentations équivalentes pour une porte NOR")


### Porte OU-exclusif (XOR)

La porte XOR à deux entrées donne une sortie 1 seulement lorsque ses
deux entrées sont différentes. Il est possible de définir des portes
XOR à plus de deux entrées, mais il y a différentes interprétations de
ce qu'une telle porte devrait avoir comme comportement. De plus, comme
la réalisation pratique de cette fonction n'est pas aussi simple que
pour les autres fonctions, on se retrouve la plupart du temps à devoir
mettre des portes à deux entrées en cascade pour augmenter le nombre
d'entrées, ce qui rend moins intéressantes les portes XOR avec entrées
nombreuses.

$$ S= A \cdot B^\prime + A^\prime \cdot B $$  

![img](Sources_images_logiques/images/exor_logique.svg "Porte XOR à deux entrées")


### Porte NON-OU-exclusif ou Équivalence (XNOR)

La porte **Équivalence** produit une sortie 1 lorsque ses entrées ont la
même valeur (et sont donc équivalentes). Comme pour les portes XOR,
les portes XNOR à plus de trois entrées peuvent s'interpréter de
différentes façons.

![img](Sources_images_logiques/images/xnor_logique.svg "Porte XNOR")


## Universalité des NAND et NOR

En faisant appel uniquement à des portes de type NAND ou NOR, il est
possible de réaliser n'importe quelle fonction logique, puisqu'il est
possible de réaliser les trois opérateurs de base.

1.  Pour réaliser un inverseur, on utilise une porte NAND à une seule
    entrée (ou dont toutes les entrées sont reliées ensemble).
2.  Pour réaliser une porte ET, on fait suivre une porte NAND d'un
    inverseur.
3.  Pour réaliser une porte OU, on place un inverseur devant chaque
    entrée d'une porte NAND.

Nous verrons plus loin qu'il est aussi possible de réaliser
avantageusement des fonctions quelconques avec des portes NAND en
exploitant la forme *somme de produits*.


## Limites physiques

Les portes logiques qu'on utilisera en pratique sont des dispositifs
électroniques dont le fonctionnement correspond, dans les grandes
lignes, aux comportements idéalisés des modèles abstraits de l'algèbre
de Boole. Mais il faut toujours garder à l'esprit que la
correspondance entre modèle et réalité physique n'est jamais
parfaite. En raffinant nos modèles pour y incorporer des
caractéristiques, limites ou contraintes appropriées, il sera possible
de mieux tenir compte de la réalité physique.


### Sortance (*Fan-out*)

La sortance (*fan-out*) d'une porte logique mesure sa capacité à commander
d'autres portes reliées à sa sortie. Puisque les portes sont des
dispositifs électroniques qui doivent faire circuler un certain
courant électrique pour concrétiser les niveaux de tensions qui
définissent leurs valeurs d'entrée et de sortie, il y a une limite
pratique à la capacité d'une porte de fournir le courant nécessaire
pour faire réagir la sortie des portes qu'elle devrait commander. La sortance 
mesure cette limite, en nombre de portes à commander. Si on
connecte plus d'entrées à une sortie que sa valeur de sortance, cette
sortie ne pourra pas atteindre le niveau de tension adéquat, et les
opérations logiques seront faussées.


### Modèles de délai

Dans la mesure où on respecte ses contraintes d'utilisation, notamment
de sortance, une porte logique se comporte globalement de la façon
attendue, étant donné sa fonction et les conventions de niveaux de
signal établies. Par exemple, le niveau signal à la sortie d'un
inverseur correspondra au niveau de signal attendu pour le complément
de la valeur logique à son entrée. Mais il faut garder à l'esprit que
les portes sont des dispositifs électroniques, et donc physiques,
sujets à des «imperfections» qui diffèrent du comportement idéalisé.

Une de ces «imperfections» dont on doit impérativement tenir compte
est le **délai de propagation** qui se manifeste comme un retard entre
le moment où le signal à l'entrée de la porte assume (se stabilise à)
son niveau de signal et le moment où la sortie de la porte atteint
son niveau de signal attendu. C'est en quelque sorte le délai entre
une action à l'entrée et son effet sur la sortie. Ce délai limite la
vitesse à laquelle on peut utiliser notre circuit logique. Si on
essaie d'effectuer des transitions plus rapides que le délai, le
comportement ne sera plus conforme aux attentes de conception. On doit
donc respecter une vitesse de commutation maximale imposée par les
délais de propagation.

Le délai de propagation peut dépendre de plusieurs facteurs: la
famille logique, le type de porte, le sens de la transition, la
sortance effective, les caractéristiques d'interconnexions, etc. Pour
faciliter l'analyse, on fait appel à des modèles de délais plus ou
moins sophistiqués. Un modèle très simple consiste à supposer un délai
de propagation moyen, constant pour toutes les portes d'une famille
donnée. Un modèle un peu plus subtil pourrait prendre en compte des
délais de propagation moyens différents par types de portes. Le délai
de propagation moyen est une caractéristique clé qui différencie les
différentes familles logiques. Les délais sont typiquement de l'ordre
de nanosecondes, permettant des vitesses de commutation dans les
dizaines, centaines, voire des milliers de MHz.

Lorsqu'un signal doit se propager à travers plusieurs portes, les
délais de propagation s'accumulent, limitant encore davantage la
vitesse de commutation de l'ensemble du circuit. La vitesse qui pourra
être atteinte pour l'ensemble d'un circuit sera typiquement déterminée
par le plus lent chemin (c'est-à-dire celui qui cumule le plus long
temps de propagation).

1.  Modèles simples

    À titre d'exemple, considérons une porte ET à deux entrées $S = A B$. 
    Le modèle le plus simple suppose une porte idéale, sans aucun délai:
    le chronogramme suivant montre la sortie qui commute immédiatement
    lorsque les conditions d'entrée changent.
    
    ![img](Sources_images_logiques/images/chronopasdelais.svg "Porte ET sans délai")
    
    1.  Modèle avec délai en sortie
    
        Le modèle avec délai en sortie consiste à considérer un délai fixe,
        qui affecte la sortie de la porte: la commutation prend effet en
        sortie après un délai $t_p$.
        
        ![img](Sources_images_logiques/images/chrononodelaisortie.svg "Porte ET avec délai en sortie")
    
    2.  Modèle avec délai en entrée
    
        Le modèle avec délai en entrée est plus nuancé, car il permet de
        spécifier un délai différent selon l'entrée qui entraîne le changement
        à la sortie.
        
        ![img](Sources_images_logiques/images/chrononodelaientree.svg "Porte ET avec délai aux entrées")
    
    3.  Modèle combiné
    
        Le modèle combiné consiste à considérer des délais différents par
        entrée et, en plus, un délai global en sortie.

2.  Condition de course et aléas

    Un autre effet néfaste potentiel des délais à considérer est ce qu'on
    appelle une **condition de course**. Considérons le circuit de la figure
    [302](#orge0a472e).  La sortie de la porte est $s = a \cdot a^\prime$ qui
    devrait normalement donner systématiquement 0. Mais le chemin menant
    de l'entrée $a$ à l'entrée du haut de la porte ET est plus court (en
    termes de délais) que le chemin qui mène à l'entrée du bas. En effet,
    le signal $a^\prime$ est retardé d'un délai de propagation
    $t_{p1}$ par rapport à $a$.
    
    ![img](Sources_images_logiques/images/course.svg "Cas à risque de condition de course")
    
    En pratique, on pourrait observer un chronogramme qui s'apparente à
    celui de la figure suivante (figure [304](#org1004eb1)), où on voit
    que les deux signaux à l'entrée de la porte ET sont simultanément
    égaux à 1 pendant une courte période. Une courte impulsion 1 sera donc
    générée sur le signal $s$ en sortie de la porte ET, après le délai
    de propagation $t_{p2}$ de celle-ci. Cette impulsion, qui ne
    correspond à rien selon la logique du circuit est appelée un **aléa** (ou
    en anglais, *glitch*).
    
    ![img](Sources_images_logiques/images/chronocourse.svg "Chronogramme montrant une condition de course")
    
    Ces aléas peuvent être la source de problèmes et de dysfonctionnements
    qui sont parfois difficiles à diagnostiquer, et il faut vraiment s'en
    méfier. Une telle impulsion, quasi imperceptible, pourrait par exemple
    déclencher le basculement de la valeur d'une cellule mémoire plus loin
    dans le circuit.


### Porte tampon

La valeur binaire à la sortie d'une porte tampon est la même qu'à
l'entrée. La porte n'agit pas sur la valeur logique mais permet de
reconditionner le signal à son entrée pour le rendre, en sortie,
davantage conforme aux niveaux électriques de référence. Une porte
tampon est essentiellement utilisée pour renforcer et stabiliser le
niveau du signal. Une façon pratique de réaliser une porte tampon est
de placer deux inverseurs l'un à la suite de l'autre. L'utilisation de
portes tampons est un des moyens de s'assurer de respecter les
conditions de sortance.


# Simplification logique


## Objectifs

-   Formuler une expression logique en forme canonique *Produit
    de sommes* ou *Somme de produits*, et convertir entre les deux formes
-   Simplifier une expression au moyen d'un diagramme de
    Karnaugh
-   Simplifier une expression par la méthode Quine-McCluskey
-   Se familiariser avec les approches d'implémentation des fonctions
    simplifiées


## Expressions équivalentes

Un des aspects ennuyeux des expressions logiques est que la
correspondance entre expression et fonction logique n'est pas
biunivoque: plusieurs expressions différentes peuvent correspondre à
une seule et même fonction. De plus, certaines des expressions
équivalentes peuvent être plus complexes que d'autres. Lorsque vient
le temps d'implémenter avec des portes une fonction logique, il est la
plupart du temps plus efficace d'implémenter selon une expression plus
simple, voire minimale. On doit donc considérer des approches
systématiques et efficaces pour simplifier les expressions logiques.

Quand une expression booléenne est implémentée avec des portes
logiques, chaque terme nécessite une porte et chaque variable au sein
d'un terme correspond à une entrée de la porte. On appelle **littéral**
une variable qui apparaît dans un terme, sous forme complémentée ou
non. Par exemple, l'expression $F = x^\prime y^\prime z + xz +
xy^\prime z$ compte huit littéraux. Si on réduit le nombre de
termes, le nombre de littéraux, ou les deux, on obtiendra une
expression qui sera plus simple à implémenter avec des portes.


## Formes canoniques


### Minterms et maxterms

Dans une expression, une variable $x$ peut apparaître telle quelle
$x$ ou complémentée $x^\prime$. Si on considère les combinaisons
possibles de deux variables via un opérateur ET, on a alors quatre
possibilités: $x^\prime y^\prime, x^\prime y, x y^\prime,x
y$. Chacun de ces quatre termes s'appelle un **minterm**.

De façon équivalente (duale, en vérité), $n$ variables reliées par
une fonction OU peuvent donner lieu à $2^n$ termes distincts,
appelés **maxterms**. 

De façon générale, pour $n$ variables, on aura $2^n$ minterms ou
$2^n$ maxterms différents possibles.

Pour étiqueter les différents minterms ou maxterms, on a établi une
convention de numérotation. Le numéro d'étiquette d'un minterm est
construit de la façon suivante. Une variable complémentée amène un bit
d'étiquette 0, une variable telle quelle amène un bit d'étiquette 1.
En ordonnant les bits selon l'ordre alphabétique des variables, on
obtient un vecteur de bits qui donnera le numéro à assigner au
minterm.  Par exemple, le minterm $x y^\prime z$ donnera l'étiquette
101, donc le numéro de minterm (en équivalent décimal) 5.

La règle pour les maxterms est duale: une étiquette 0 pour une
variable telle quelle, et une étiquette 1 pour une variable
complémentée. Chaque maxterm est le complément du minterm
correspondant (de même numéro), et *vice versa*.

Dans le tableau [27](#org59a2ca5), on montre les symboles de la forme
$m_j$ pour les minterms et $M_j$ pour les maxterms, avec $j$ qui
est l'équivalent décimal de la combinaison de bits correspondante.

<table id="org59a2ca5" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 18 :</span> Minterms et maxterms pour trois variables</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-right">\(z\)</th>
<th scope="col" class="org-left">Minterm</th>
<th scope="col" class="org-left">Symb.</th>
<th scope="col" class="org-left">Maxterm</th>
<th scope="col" class="org-left">Symb.</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">\(x^\prime y^\prime z^\prime\)</td>
<td class="org-left">\(m_0\)</td>
<td class="org-left">\(x+ y+ z\)</td>
<td class="org-left">\(M_0\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">\(x^\prime y^\prime z\)</td>
<td class="org-left">\(m_1\)</td>
<td class="org-left">\(x+ y+ z^\prime\)</td>
<td class="org-left">\(M_1\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">\(x^\prime y z^\prime\)</td>
<td class="org-left">\(m_2\)</td>
<td class="org-left">\(x+ y^\prime+ z\)</td>
<td class="org-left">\(M_2\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">\(x^\prime y z\)</td>
<td class="org-left">\(m_3\)</td>
<td class="org-left">\(x+ y^\prime+ z^\prime\)</td>
<td class="org-left">\(M_3\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">\(x y^\prime z^\prime\)</td>
<td class="org-left">\(m_4\)</td>
<td class="org-left">\(x^\prime+ y+ z\)</td>
<td class="org-left">\(M_4\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">\(x y^\prime z\)</td>
<td class="org-left">\(m_5\)</td>
<td class="org-left">\(x^\prime+ y+ z^\prime\)</td>
<td class="org-left">\(M_5\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">\(x y z^\prime\)</td>
<td class="org-left">\(m_6\)</td>
<td class="org-left">\(x^\prime+ y^\prime+ z\)</td>
<td class="org-left">\(M_6\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">\(x y z\)</td>
<td class="org-left">\(m_7\)</td>
<td class="org-left">\(x^\prime + y^\prime+ z^\prime\)</td>
<td class="org-left">\(M_7\)</td>
</tr>
</tbody>
</table>

Pour la fonction $F_1$ dont le tableau de vérité est le suivant: 

<table id="org701fb63" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 19 :</span> Fonction de trois variables</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-right">\(z\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(F_1\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

on peut donc écrire

$$ F_1 = x^\prime y
z^\prime + x y^\prime z^\prime + x y^\prime z + x y z^\prime + x y z =
m_2 + m_4 + m_5 + m_6 + m_7 $$

puisque ce sont les termes pour lesquels la fonction vaut 1. Cette
forme d'expression est une forme canonique appelée *somme de
produits*.

Pour simplifier la notation, on peut écrire de façon plus compacte  

$$F_1 = \sum (2, 4, 5, 6, 7)$$

où on ne met que les numéros des minterms participant à la somme.

Si on veut exprimer le complément d'une fonction, on peut lire dans le
tableau de vérité les combinaisons pour lesquelles la fonction
vaut 0. En prenant un minterm pour chaque combinaison où la fonction
vaut 0 et en faisant un OU de ces termes, on obtient une expression en
*somme de produits* pour le complément de la fonction. Ainsi, pour la
fonction $F_1^\prime$, on a

$$ F_1^\prime = m_0 + m_1 + m_3 = x^\prime y^\prime z^\prime +
x^\prime y^\prime z + x^\prime y z $$

Si on complémente $F_1^\prime$, on obtiendra naturellement
$F_1$. En appliquant le théorème de DeMorgan à chaque terme, on
trouve

$F_1 = (x+ y+ z)(x + y + z^\prime)(x + y^\prime + z^\prime) = M_0
\cdot M_1 \cdot M_3$

Cette forme d'expression est aussi une forme canonique appelée
*produit de sommes*.

Pour simplifier la notation, on peut écrire de façon plus compacte  

$F_1 = \prod (0,1,3)$

où on ne met cette fois que les numéros des maxterms participant au
produit.


### Somme de produits

Pour $n$ variables binaires, on a $2^n$ minterms différents
possibles. Les minterms qui participent à la somme dans l'expression
en forme canonique *somme de produits* sont ceux qui produisent un 1
dans le tableau de vérité de la fonction. Puisque la fonction peut
valoir 0 ou 1 pour chaque minterm, le nombre total de fonctions
différentes qui peuvent être définies avec $n$ variables est de
$2^{2^n}$.

Si on veut convertir en forme canonique *somme de produits* l'expression
pour une fonction qui ne serait pas sous cette forme, on commence par
faire l'expansion de l'expression en forme *somme de produits*. Ensuite,
on vérifie chaque terme pour voir si toutes les variables en font
partie. S'il manque une ou des variables, on peut faire un ET du
terme avec une expression du type $x + x^\prime$ dans laquelle $x$
est une variable manquante. Ce ET ne change pas la valeur de la
fonction puisque $x + x^\prime = 1$.

Évidemment, on peut toujours trouver la formulation en forme canonique
en se basant sur le tableau de vérité.


### Produit de sommes

Si on veut convertir en forme canonique *produit de sommes*
l'expression pour une fonction qui ne serait pas sous cette forme, on
commence par faire l'expansion de l'expression en forme *produit de
sommes*. Pour ce faire, on peut avantageusement faire appel à la
distributivité de $+$ sur $\cdot$. Ensuite, on vérifie chaque
terme pour voir si toutes les variables en font partie. S'il manque
une ou des variables, on peut faire un OU du terme avec une expression
du type $x \cdot x^\prime$ dans laquelle $x$ est une variable
manquante. Ce OU ne change pas la valeur de la fonction puisque $x
\cdot x^\prime = 0$.


### Conversion entre formes canoniques

Prenons notre exemple précédent $F_1 = \sum (2, 4, 5, 6, 7)$. On
sait que $F_1^\prime = \sum (0,1,3)$. Si on prend le complément de
$F_1^\prime$ par le théorème de DeMorgan, on obtient $F_1 = (m_0 +
m_1 + m_3)^\prime = m_0^\prime \cdot m_1^\prime \cdot m_3^\prime = M_0
\cdot M_1 \cdot M_3 = \prod (0,1,3)$.

En effet, de minterm à maxterm, on a $m_j^\prime = M_j$. Le maxterm
d'indice $j$ est le complément du minterm de même indice $j$, et
*vice versa*.


### Formes standard

Les expressions canoniques en *somme de produits* et en *produit de
sommes* ne sont généralement pas simples, car toutes les variables
doivent être présentes. Pour l'implémentation, on cherchera des
expressions en formes *somme de produits* ou *produit de sommes* dans
lesquelles les termes pourront être simplifiés. C'est-à-dire que les
termes pourront comporter une, deux, trois, etc. variables plutôt
qu'obligatoirement **toutes** les variables. Toujours pour notre
fonction exemple, on peut écrire

$F_1 = x + y z^\prime$

Lorsqu'on implémente une telle fonction avec des portes logiques, il
faut une porte ET pour chaque terme produit (qui comporte plus d'une
variable) et une porte OU pour faire la somme finale. On obtient une
implémentation à deux niveaux.

De façon duale, on peut également obtenir une formulation en *produit
de sommes* qui aboutira à une implémentation à deux niveaux avec une
porte OU par terme et une porte ET pour le produit final.


## Objectifs de minimisation

Étant donné une fonction logique de $n$ variables $z(x_1, x_2, \ldots,
x_n)$, on veut déterminer une expression pour cette fonction sous la
forme *somme de produits* (S de P) ou *produit de sommes* (P de S) qui

1.  comporte un nombre minimum de termes produits (pour la forme S de P)
    ou de termes sommes (pour la forme P de S);

2.  est telle qu'aucune expression pour $z$ comportant le même nombre
    de termes n'utilise moins de littéraux.


## Diagrammes de Karnaugh

Une méthode visuelle permet de simplifier l'expression logique d'une
fonction en systématisant une procédure faisant appel à un diagramme
qui fait ressortir les simplifications possibles.

Un diagramme de Karnaugh (diag-K) est constitué d'un regroupement de
cellules carrées, chaque cellule correspondant à un minterm
possible. Les cellules sont organisées de façon à ce que lorsqu'on
passe d'une cellule à une cellule adjacente (horizontalement ou
verticalement), un seul bit du minterm change, ce qui revient à dire
qu'une seule variable passe de telle quelle à complémentée.

Cela fait en sorte que si la fonction est 1 pour deux minterms
adjacents, la somme des deux minterms pourra être simplifiée en un
seul terme dans lequel la variable correspondant au bit qui change est
absente. Par exemple, on pourrait avoir pour deux minterms adjacents
$m_5 + m_7 = xy^\prime z + xyz = xz(y^\prime + y) = xz$. Ici, les
deux minterms adjacents diffèrent par la variable $y$, qui sera donc
supprimée du terme produit résultant.

![img](Sources_images_logiques/images/kmap2.svg "Diag-K à deux variables")

![img](Sources_images_logiques/images/kmap3minterms.svg "Diag-K à trois variables, avec minterms")

Sur un diag-K à trois variables, on voit que les bits $AB$ sont
ordonnés selon un code Gray, de façon à ce qu'un seul des bits change
lorsqu'on passe d'une cellule à la suivante
horizontalement. L'adjacence se poursuit en bout de diagramme: par
exemple, la cellule 100 ($m_4$) est adjacente horizontalement à la
cellule 000 ($m_0$). On peut imaginer le diagramme comme replié sur
lui-même pour visualiser cette adjacence.

![img](Sources_images_logiques/images/kmap3_repli.svg "Diag-K avec adjacence horizontale")

Sur un diag-K à quatre variables, l'adjacence repliée est aussi bien horizontale
que verticale.

Pour plus de quatre variables, il devient difficile d'utiliser cette
méthode: les diagrammes sont de grande taille et, surtout, les règles
d'adjacence ne sont plus aussi facilement observables. Les risques
d'erreurs sont plus grands.

![img](Sources_images_logiques/images/kmap4.svg "Diag-K à quatre variables")


### Procédure de simplification

Pour utiliser un diag-K pour minimiser une fonction logique, 

1.  Les minterms de la fonction à minimiser sont identifiés en insérant
    un 1 dans la cellule correspondant à chaque minterm.
2.  On cherche dans le diagramme pour trouver des regroupements de deux
    cellules adjacentes qui sont marquées d'un 1.
3.  Chaque groupe de deux cellules 1 adjacentes est marqué comme
    groupe. Un même minterm peut être incorporé à plus d'un groupe.
4.  Il est aussi possible de regrouper les groupes: deux groupes de 2
    qui sont adjacents peuvent ainsi se regrouper en un groupe
    de 4. Les tailles de groupes doivent être des puissances de 2. Il
    est ainsi possible de créer des groupes de 2, 4, 8 ou 16 minterms.
5.  Une fois tous les regroupements identifiés, il est possible de lire
    l'expression de la fonction en *somme de produits*. Chaque groupement
    correspond à un terme produit, et la ou les variables dont le bit ne
    change pas dans le groupe sont conservées; les autres sont
    éliminées.

Considérons par exemple la fonction $F(A,B,C) = \sum (0, 4, 6,
7)$. Après la première étape, on obtient

![img](Sources_images_logiques/images/kmap3fonct.svg)

Après les regroupements, on obtient un diag-K comportant trois regroupements

![img](Sources_images_logiques/images/kmap3fonctsimp.svg "Diagramme après les regroupements")

Le groupe en rouge correspond au produit $B^\prime C^\prime$, celui
en bleu correspond à $A B$ et celui en vert correspond à $A
C^\prime$. L'expression finale en *somme de produits* est donc $F =
B^\prime C^\prime + A B + A C^\prime$.


### Cas facultatifs

Certaines fonctions sont incomplètement définies, dans le sens où
certaines combinaisons d'entrées ne se produiront jamais ou seront
sans conséquences si elles se produisent. On parle de **cas
indifférents** ou **facultatifs** (en anglais, *don't care*). Pour la
simplification, ces cas pourront être traités tantôt comme des 0,
tantôt comme des 1, selon ce qui sera le plus avantageux.

Pour tenir compte de ces cas, les minterms seront notés avec un X dans
le diagramme de Karnaugh. Dans l'exemple à quatre variables suivant,
sur deux cas facultatifs, un seul, celui correspondant à $m_{7}$, a
été traité comme un 1, ce qui a permis de créer le regroupement en
bleu. L'autre cas facultatif, correspondant à $m_{2}$, n'a pas servi
dans un regroupement, ce qui signifie qu'il a été traité comme
un 0. La fonction résultante est donc $A C^\prime D^\prime + BD + AB
$.

![img](Sources_images_logiques/images/kmap4fonct.svg "Diag-K avec cas facultatifs")


### Impliquants

Le choix des regroupements à utiliser doit toujours viser à s'assurer que:

1.  Tous les minterms de la fonction sont couverts par les regroupements choisis.
2.  Le nombre de termes retenus pour l'expression est minimal.
3.  Il n'y a pas de termes redondants, c'est-à-dire qui couvrent
    uniquement des minterms déjà couverts.

Il y a parfois plus d'une expression qui satisfait ces
critères. Il est possible de systématiser le choix des termes en
prenant en compte le caractère essentiel des termes.

Soit $p(X)$ un terme produit de littéraux tirés de l'ensemble de
variables $X$. Si, pour une fonction logique $z(X)$ définie pour le
même ensemble de variables, la relation

> pour tout $A$ tel que $p(A)=1$, $z(A)=1$

tient, alors $p$ est un **impliquant** de $z$. Cela signifie que la
vérité du terme produit $p$ implique celle de $z$. *Tout minterm de
$p$ est aussi un minterm de $z$.*

Exemple:

$$z_1 = ab + bc + a b^{\prime} c$$ 

$a b$, $b c$, $a b^{\prime} c$ sont des impliquants évidents de $z_1$.

$a^{\prime} b c$, $a b c^{\prime}$, $a b c$, $a c$ sont aussi des
impliquants de $z_1$.

![img](Sources_images_logiques/images/kmap3fonctimp.svg "Diag-K pour l'exemple des impliquants")


### Impliquant premier

Un impliquant $p$ de la fonction $z$ est **premier** si n'importe quel
terme produit obtenu de $p$ en supprimant un littéral n'est pas un
impliquant de $z$.

Ici, $a b$ est un impliquant premier de $z_1$, car ni $a$ ni $b$ ne
sont des impliquants de $z_1$. Mais $a b^{\prime} c$ n'est pas un
impliquant premier de $z_1$, car $a c$ est un impliquant de $z_1$.
Sur un diagramme de Karnaugh, un impliquant premier (i.p.) est un
groupe qui n'est contenu dans aucun autre groupe plus grand.


### Couverture d'une fonction

Un sous-ensemble d'i.p. qui contient tous les minterms d'une fonction
**couvre** la fonction.

Une **couverture minimale** est une couverture avec

1.  le nombre minimal d'impliquants premiers,

2.  le moins de littéraux parmi les couvertures avec nombre minimum
    d'impliquants.


### Impliquant premier essentiel

Un i.p. est **essentiel** si et seulement s'il couvre un minterm de la
fonction qui ne peut être couvert par un autre i.p. de la fonction.
Une couverture de la fonction **doit** contenir tous les impliquants
premiers essentiels (i.p.e.).

Un **impliquant premier absolument inessentiel** est un i.p. qui couvre
des minterms qui sont tous couverts par les i.p.e. de la fonction.


### Sélection des impliquants

Règles de sélection des impliquants

1.  Mettre de côté tous les i.p.e. Ils seront utilisés dans la solution
    finale.

2.  Éliminer tous les i.p. absolument inessentiels.

3.  Il reste à choisir parmi les i.p. inessentiels pour obtenir une
    couverture minimale.

Lorsque le problème est de taille réduite, on peut faire une recherche
exhaustive de toutes les solutions possibles pour choisir la solution
minimale.


### Minimisation avec cas facultatifs

1.  Lorsqu'on détermine les i.p., on doit considérer les X comme des
    1, de façon à pouvoir utiliser les i.p. rendus possibles par les
    cas facultatifs.

2.  Lors de la sélection des i.p. pour obtenir une couverture
    minimale, on ne doit pas essayer de couvrir les X.


### Minimisation avec plusieurs fonctions

Si deux fonctions $z_i$ et$z_j$ ont des expressions minimales qui
comportent un terme commun, une seule porte suffira pour générer ce
terme au profit des deux fonctions.

Exemple:

$$z_1 = a c + a^{\prime} b c^{\prime} + a^{\prime} c^{\prime} d$$

$$z_2 = a c + a^{\prime}  b c^{\prime} d^{\prime} +
a^{\prime} b^{\prime} c^{\prime} d$$

![img](Sources_images_logiques/images/kmap4z1.svg "Fonction $z_1$")

![img](Sources_images_logiques/images/kmap4z2.svg "Fonction $z_2$")

Il est alors préférable de réutiliser les termes communs et de générer
seulement les termes manquants pour la seconde fonction. Dans cet
exemple, le terme $a c$ sera calculé une seule fois. Les termes
$a^{\prime} b c^{\prime} d^{\prime}$ et $a^{\prime} b^{\prime}
c^{\prime} d$ sont nécessaires pour $z_2$. Alors, pour $z_1$, on
fera

$$ z_1 =  a c + a^{\prime}  b c^{\prime} d^{\prime} +
a^{\prime} b^{\prime} c^{\prime} d +
a^{\prime} b c^{\prime} d $$

qui ne nous coûtera que le dernier terme produit et une somme de
quatre termes.


## Tableau de couverture Quine-McCluskey

La méthode de Quine-McCluskey systématise la sélection des impliquants
en se basant sur des relations qui s'expriment en fonction d'un
tableau de couverture.

Un **tableau de couverture** comporte une ligne pour chaque i.p. et une
colonne pour chaque minterm de la fonction à minimiser $z$. Un &check; est
inscrit à l'intersection de la ligne $i$ et de la colonne  $j$ si
l'i.p.  $P_i$ de la ligne  $i$ couvre le minterm  $m_j$ de la colonne
 $j$.

Le problème de minimisation devient alors: trouver une couverture pour
la fonction $z$ qui

1.  contient le nombre minimum de lignes

2.  est telle qu'aucune autre couverture à nombre de lignes minimum
    comprend moins d'entrées 1 et 0 dans ses codes d'impliquants de
    ligne.

Dans le tableau de couverture, on identifie facilement les i.p.e. par
les colonnes qui ne contiennent qu'un &check;. L'i.p. qui couvre une colonne
qui ne contient qu'un &check; est un i.p.e.

Puisque les i.p.e. doivent faire partie de la solution finale, toutes
les colonnes couvertes par des i.p.e. seront couvertes dans n'importe
quelle solution. On peut donc éliminer ces colonnes de la suite de la
recherche de la solution, de même que les lignes correspondant aux
i.p.e. On obtient ainsi un tableau de couverture **réduit**.

**Il ne faut cependant pas oublier de mettre les i.p.e. dans la solution
finale.**


### Tableau de couverture réduit

Le tableau de couverture réduit permet de se concentrer sur la
sélection des i.p. dont la sélection n'est pas évidente *a
priori*. Pour illustrer la discussion, considérons le tableau de
couverture réduit suivant. $m_c$ est sans doute couvert par un
i.p.e. qui n'est pas montré ici.

<table id="orgad47aac" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 20 :</span> Tableau réduit</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(m_a\)</th>
<th scope="col" class="org-left">\(m_b\)</th>
<th scope="col" class="org-left">\(m_c\)</th>
<th scope="col" class="org-left">\(m_d\)</th>
<th scope="col" class="org-left">\(m_e\)</th>
<th scope="col" class="org-left">\(m_f\)</th>
<th scope="col" class="org-left">\(m_g\)</th>
<th scope="col" class="org-left">\(m_h\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">\(P_A\)</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
</tr>


<tr>
<td class="org-left">\(P_B\)</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
</tr>


<tr>
<td class="org-left">\(P_C\)</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
</tr>


<tr>
<td class="org-left">\(P_D\)</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
</tr>


<tr>
<td class="org-left">\(P_E\)</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
<td class="org-left">&check;</td>
</tr>
</tbody>
</table>


### Dominance de lignes

Une ligne $P_i$ domine une ligne $P_j$ (ce qui est noté $P_i \supseteq
P_j$) si la ligne $P_i$ contient un &check; dans toutes les colonnes où
la ligne $P_j$ contient un &check;. Ici, on a $P_B \supseteq P_D$ mais
$P_B$ ne domine pas $P_A$. On peut voir aussi que $P_E$ domine
plusieurs lignes.

En général, une $P_i$ dominante contient plus de &check; que $P_j$. Si
elles ont le même nombre de &check; (dans les mêmes colonnes), on a $P_i =
P_j$. Il n'y a pas de cas d'égalité ici.

Une ligne **dominée** par une autre peut être éliminée du tableau de
couverture à condition que son nombre de littéraux soit supérieur ou
égal à celui de la ligne dominante.


### Dominance de colonnes

Une colonne $m_i$ domine une colonne $m_j$ (ce qui est noté $m_i \supseteq
m_j$) si la colonne $m_i$ contient un &check; dans toutes les lignes où
la colonne $m_j$ contient un &check;. Ici, la colonne $m_h \supseteq
m_g$ mais $m_b$ ne domine pas $m_a$. 

Une colonne **dominant** une autre colonne peut être éliminée du tableau de
couverture, car le fait que la solution finale couvre la colonne
dominée assure que la colonne dominante sera couverte aussi. Donc ici,
la colonne $m_h$ peut être éliminée.

En cas d'égalité, comme on a ici pour $m_e = m_g$, on peut librement
choisir quelle colonne éliminer.


## Implémentation des fonctions simplifiées

Les circuits logiques simplifiés en forme *produit de sommes* ou
*somme de produits* sont souvent mis en oeuvre au moyen de portes NAND
ou NOR plutôt qu'avec des portes ET et OU. La raison en est qu'il est
plus simple en pratique de réaliser ces portes.


### Implémentation à deux niveaux

Une fonction en forme *somme de produits* s'implémente évidemment avec
des portes ET pour les produits et une porte OU pour la somme
finale. Considérons par exemple $F = AB + CD$.

![img](Sources_images_logiques/images/somme_produits.svg "*Somme de produits* pour $F = AB + CD$") 

La fonction peut aussi s'implémenter tout naturellement en faisant
appel uniquement à des portes NAND. On peut vérifier facilement que le
circuit suivant implémente la même fonction $F = ((AB)^\prime \cdot
(CD)^\prime)^\prime = AB + CD$

![img](Sources_images_logiques/images/somme_produitsNAND2.svg "*Somme de produits* NAND") 

Cette configuration s'interprète plus facilement en représentant la
porte de sortie comme une porte NOR avec les entrées complémentées
(version équivalente de la porte NAND). En effet, la complémentation
de chaque sortie de somme est compensée par la complémentation à
l'entrée de la porte de sortie.

![img](Sources_images_logiques/images/somme_produitsNAND.svg "*Somme de produits* NAND plus évidente")


# Circuits combinatoires typiques


## Objectifs

-   Analyser un circuit combinatoire à partir de son schéma
-   Concevoir un circuit combinatoire à partir d'une spécification
-   Connaître différentes approches de réalisation
-   Se familiariser avec les principaux circuits combinatoires courants et
    leurs fonctions: additionneur, décodeur, multiplexeur, encodeur,
    comparateur
-   Comprendre le fonctionnement d'une chaîne d'addition binaire et les
    mécanismes de propagation et d'anticipation de retenue


## Circuit combinatoire

Un circuit logique combinatoire est une combinaison de portes logiques
dont la sortie à un instant donné ne dépend que des valeurs des
entrées à cet instant. Un circuit combinatoire à $n$ entrées et
$m$ sorties peut être représenté par un schéma-bloc, dans lequel on
place généralement les entrées à gauche et les sorties à droite.

![img](Sources_images_logiques/images/circuit_comb.png "Circuit combinatoire")

Avec $n$ entrées, il est possible de créer $2^n$ combinaisons
différentes des entrées binaires. Pour chaque combinaison, le circuit
peut donner une sortie 0 ou 1. On peut donc préciser la fonction
réalisée par le circuit au moyen d'un tableau de vérité comportant $2^n$
lignes. Comme nous avons $m$ sorties différentes, il y aura $m$
colonnes dans le tableau de vérité pour les fonctions de
sortie. Traditionnellement, on présente les entrées en ordre croissant
de combinaisons binaires.


## Analyse d'un circuit logique combinatoire

Si on se trouve devant le schéma d'un circuit logique dont on ne
connaît pas la fonction, on doit en faire l'analyse. La première étape
consiste à vérifier qu'il s'agit bien d'un circuit combinatoire. Si le
schéma ne comporte pas de cellules de mémoire ou de boucles de
rétroaction, on peut conclure que le circuit est combinatoire. Une
boucle de rétroaction consiste en un chemin du circuit par
lequel une valeur d'entrée d'une porte provient, directement ou
indirectement (par l'intermédiaire d'autres portes), de la sortie de
la même porte. La présence de rétroaction est une caractéristique des
circuits logiques séquentiels, que nous étudierons plus loin.

Pour interpréter le comportement du circuit, nous devons déterminer
les expressions logiques qu'il met en oeuvre ou établir son tableau de
vérité.

Pour déterminer l'expression logique, on procède ainsi:

1.  Étiqueter toutes les sorties des portes qui sont alimentées par les
    variables d'entrée du système. Les noms de variables seront
    arbitraires, mais devraient être choisis de façon à faciliter
    l'interprétation par la suite. Déterminer les fonctions logiques
    pour ces variables.
2.  Étiqueter les sorties des portes qui sont alimentées par les
    variables d'entrée et par les sorties étiquetées à l'étape
    précédente. Déterminer les fonctions logiques pour ces nouvelles
    variables.
3.  Répéter l'étape 2 jusqu'à arriver aux variables de sortie du système.
4.  En substituant les expressions logiques des fonctions identifiées,
    déterminer l'expression logique pour les sorties du système en
    fonction des entrées du système.


### Exemple

Analysons le circuit combinatoire illustré à la figure
suivante.

![img](Sources_images_logiques/images/circuit_logique_inconnu.svg "Circuit combinatoire à analyser")

1.  Il n'est pas la peine d'étiqueter la sortie de la porte
    inverseur. Comme variables intermédiaire, on considère $I_1$ en
    sortie de la porte ET à trois entrées et $I_2$ en sortie de la
    porte NOR. On trouve que $I_1 = A^\prime \cdot B \cdot C$ et que
    $I_2 = (A + D)^\prime = A^\prime \cdot D^\prime$.

2.  On aura donc $F_1 = I_1 \cdot I_2$.

3.  En substituant, $F_1 = ( A^\prime \cdot B \cdot C ) \cdot (
       A^\prime \cdot D^\prime) = A^\prime \cdot B \cdot C \cdot
       D^\prime$.

4.  En simplifiant, on obtient finalement $F_1 = A^\prime \cdot B
       \cdot C \cdot D^\prime$.

<table id="org586d7b5" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 21 :</span> Tableaux de vérité des fonctions intermédiaires et de la sortie</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(A\)</th>
<th scope="col" class="org-right">\(C\)</th>
<th scope="col" class="org-right">\(B\)</th>
<th scope="col" class="org-right">\(D\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(I_1\)</th>
<th scope="col" class="org-right">\(I_2\)</th>
<th scope="col" class="org-right">\(F_1\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>


## Conception d'un circuit combinatoire

Concevoir un circuit logique commence avec la formulation de la ou des
fonctions du système et se termine avec une implémentation en portes
logiques des fonctions logiques correspondantes. Voici les étapes à
suivre.

1.  À partir de l'expression du besoin ou des spécifications du
    système, déterminer combien d'entrées et de sorties sont
    requises, puis leur assigner des noms de variables. Le choix des noms
    devrait faciliter leur interprétation en lien avec leur fonction.

2.  Formuler le tableau de vérité qui décrit les valeurs logiques que
    doivent assumer les sorties en fonction des différentes
    combinaisons d'entrées.

3.  Simplifier les expressions logiques pour les différentes fonctions,
    en tenant éventuellement compte des partages possibles d'éléments
    intermédiaires.

4.  Tracer le circuit logique résultant et le valider (à la main ou
    mieux, par simulation).

L'étape 2 est cruciale, car ce qui sera implémenté (s'il n'y a pas
d'erreurs) est exactement ce que le tableau de vérité stipule. On
doit donc s'assurer que le tableau est correctement rempli et
représente véritablement les besoins identifiés. Si des hypothèses ou
des choix doivent être faits, notamment dans le cas où l'expression
informelle des besoins est incomplète ou ambiguë, ces choix doivent
être clairement identifiés et documentés, permettant le cas échéant de
les modifier lorsque le système est mis à l'épreuve en fonctionnement.

N'importe quelle méthode de simplification peut être utilisée pour
l'étape 3, mais il faut aussi prendre en compte le type de portes
disponibles pour l'implémentation, les délais de propagation à
travers les portes, le nombre d'interconnexions entre sorties et
entrées de portes, et tout autre facteur pratique susceptible
d'orienter les décisions.


## Alternatives d'implémentation

Considérons la fonction logique $Y$ correspondant au diag-K de la
figure suivante.

![img](Sources_images_logiques/images/kmap3altern.svg "Diag-K d'une fonction combinatoire $Y$ à réaliser") 


### Implémentations via la fonction directe

1.  Implémentation en *somme de produits*

    En *somme de produits*, on a $Y = bc + a^\prime b + a b^\prime
    c^\prime$ pour la fonction et $Y^\prime = a^\prime b^\prime +
    b^\prime c + a b c^\prime$ pour son complément. Les implémentations
    possibles pour la fonction directe sont illustrées ci-dessous.
    
    ![img](Sources_images_logiques/images/circ_altern_1.svg "Implémentation de $Y$ en *somme de produits*") 
    
    ![img](Sources_images_logiques/images/circ_altern_2.svg "Implémentation (en NAND) de $Y$ en *somme de produits*") 

2.  Implémentation en *produit de sommes*

    En *produit de sommes*, on a $Y =(a + b ) (b + c^\prime ) (a^\prime +
    ba^\prime + c)$ pour la fonction et $Y^\prime = (b^\prime +c^\prime
    )(a+b^\prime )(a^\prime +b+c)$ pour son complément.  Les implémentations
    possibles pour la fonction directe sont illustrées ci-dessous.
    
    ![img](Sources_images_logiques/images/circ_altern_ps1.svg "Implémentation de $Y$ en *produit de sommes*") 
    
    ![img](Sources_images_logiques/images/circ_altern_ps2.svg "Implémentation (en NOR) de $Y$ en *produit de sommes*") 


### Implémentations via la fonction complémentaire

On peut aussi implémenter la fonction à partir de la fonction
complémentaire $Y^\prime$, en se basant sur le complément $Y^\prime
= (b^\prime +c^\prime )(a+b^\prime )(a^\prime +b+c)$ et en inversant
la sortie. Voici les implémentations que l'on obtient alors.

1.  Implémentation en *somme de produits*

    En *somme de produits*, on a utilisé une porte NOR en sortie pour
    obtenir finalement $Y$.
    
    ![img](Sources_images_logiques/images/circ_altern_comp_sp1.svg "Implémentation via $Y^\prime$ en *somme de produits*") 
    
    Une autre forme fait appel à des portes NAND au premier niveau.
    
    ![img](Sources_images_logiques/images/circ_altern_comp_sp2.svg "Implémentation via $Y^\prime$ en *somme de produits*") 

2.  Implémentation en *produit de sommes*

    En *produit de sommes*, en se basant sur le complément $Y^\prime =
    (b^\prime +c^\prime )(a+b^\prime )(a^\prime +b+c)$. On a encore ici
    deux variantes selon le type de portes utilisées.
    
    ![img](Sources_images_logiques/images/circ_altern_comp_ps1.svg "Implémentation via $Y^\prime$ en *produit de sommes*") 
    
    ![img](Sources_images_logiques/images/circ_altern_comp_ps2.svg "Implémentation via $Y^\prime$ en *produit de sommes*") 


## Circuits logiques combinatoires classiques

Nous allons maintenant nous intéresser à un certain nombre de
fonctions typiques que l'on rencontre fréquemment en circuits
logiques. Ce sera aussi l'occasion de mettre en pratique les approches
de conception que nous avons vues.


## Additionneur binaire

Une des opérations binaires les plus utilisées est l'addition (et la
soustraction). Nous avons présenté à la section [1.11.1](#org1961250) le tableau de vérité pour un additionneur binaire dont les
entrées sont $a_{i}$ et $b_{i}$, les bits des nombres à
additionner, et aussi $r_{i-1}$, la retenue provenant de la position
$i-1$. En sortie, on aura la somme $S_{i}$ et la retenue
$R_{i}$. Notez que pour bien distinguer la retenue d'entrée de la
retenue de sortie, nous utilisons un symbole minuscule, $r_{i-1}$,
pour l'entrée et un symbole majuscule, $R_{i}$, pour la sortie. 

![img](Sources_images_logiques/images/additionneur.png "Schéma-bloc d'un additionneur complet")

<table id="orge022a7f" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 22 :</span> Tableau de vérité pour l'additionneur binaire</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(a_{i}\)</th>
<th scope="col" class="org-right">\(b_{i}\)</th>
<th scope="col" class="org-right">\(r_{i-1}\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(R_{i}\)</th>
<th scope="col" class="org-right">\(S_{i}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>


### Demi-additionneur

Un circuit logique qui effectue l'addition de deux bits est appelé un
demi-additionneur. Mais ce qu'il nous faut vraiment, c'est un
**additionneur complet**, c'est-à-dire un circuit de trois entrées qui
fait l'addition de trois bits, puisqu'il faudra pouvoir tenir compte
de la retenue du niveau précédent pour effectuer l'addition sur un
niveau. Il est possible d'implémenter l'additionneur complet avec deux
demi-additionneurs.

<table id="org9d301dd" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 23 :</span> Tableau de vérité pour un demi-additionneur</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(a_{i}\)</th>
<th scope="col" class="org-right">\(b_{i}\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(R_{i}\)</th>
<th scope="col" class="org-right">\(S_{i}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

À partir du tableau de vérité, on peut trouver que pour un
demi-additionneur, $S_{i} = a_i b_i^\prime + a_i^\prime b_i = a_i
\operatorname{Xor} b_i$ et $R_{i} = a_i b_i$.

![img](Sources_images_logiques/images/demi_add2.svg "Circuit demi-additionneur (en S de P)")

![img](Sources_images_logiques/images/demi_add.svg "Circuit demi-additionneur avec porte XOR")


### Additionneur complet

Une addition binaire complète de deux arguments constitués de $n$
bits procède du bit le moins significatif vers le bit le plus
significatif, en additionnant à chaque étape trois bits: $a_{i}$,
$b_{i}$ et $r_{i-1}$ et en produisant une somme $S_{i}$ et une
retenue $R_{i}$.

![img](Sources_images_logiques/images/kmapSi_fulladder.svg "Diag-K pour $S_i$, additionneur complet")

![img](Sources_images_logiques/images/kmap3fulladderR.svg "Diag-K pour $R_i$, additionneur complet")

Les expressions simplifiées sont 

$$ S_{i} = a_i^\prime b_i^\prime r_{i-1} + a_i^\prime b_i
r_{i-1}^\prime + a_i b_i^\prime r_{i-1}^\prime + a_i b_i r_{i-1} $$

$$ R_{i} = a_i b_i + a_i r_{i-1} + b_i r_{i-1} $$

![img](Sources_images_logiques/images/fulladderS.svg "Circuit additionneur complet pour $S_i$")

![img](Sources_images_logiques/images/fulladderR.svg "Circuit additionneur complet pour $R_i$")

Comme nous le disions précédemment, il est possible de combiner deux
demi-additionneurs pour réaliser un additionneur complet, comme on
peut le voir ici.

![img](Sources_images_logiques/images/fulladderxor.svg "Circuit additionneur complet comportant deux demi-additionneurs et une porte OU")


### Additionneur binaire pour $n$ bits

Un additionneur binaire est un circuit logique qui permet d'évaluer la
somme arithmétique de deux nombres binaires de $n$ bits. Il peut
être conçu en combinant des additionneurs complets en cascade, en
reliant la retenue de sortie provenant de la position 0 (la moins
significative) à l'entrée de retenue de la position 1, la retenue de
sortie provenant de la position 1 à l'entrée de retenue de la position
2, &#x2026;, la retenue de sortie provenant de la position $i-1$ à l'entrée
de retenue de la position $i$, etc. (figure [493](#org4637d39)).

Pour en faire un circuit général pouvant également se combiner en
chaîne, on prévoit une entrée pour une retenue au niveau 0, $r_0$ et
une sortie pour une retenue du dernier niveau $n-1$, $R_{n-1}$. On
doit donc, pour le chaînage, acheminer la sortie retenue du niveau
courant à l'entrée de retenue du niveau suivant.

![img](Sources_images_logiques/images/additionneur_cascade.png "Chaîne d'addition")

Cette réalisation en forme de chaîne, en réutilisant de façon
systématique un bloc élémentaire, est avantageuse du point de vue de
la complexité et de la flexibilité. Imaginons par exemple le défi de
concevoir un additionneur binaire pour des nombres de quatre bits avec
la méthode classique. Comme il faudrait considérer neuf entrées, le
tableau de vérité comporterait $2^9= 512$ lignes!


### Propagation de retenue

L'approche en cascade ne comporte pas que des avantages. Lorsqu'on
effectue l'addition de deux nombres, les bits d'entrée des deux
arguments et la retenue d'entrée sont présentés en même temps à
l'additionneur.  Comme dans tout circuit combinatoire, il faut un
certain délai avant que les sorties n'atteignent leur niveau de sortie
final.  Ce délai de propagation dépend de la profondeur du circuit, en
nombre de portes élémentaires à franchir de l'entrée vers la
sortie.  Et c'est évidemment le chemin le plus long qui détermine le
délai de propagation global.  

Dans le cas de l'additionneur, le chemin de propagation le plus long
est celui qui mène à la dernière retenue finale $R_{n-1}$.  En
effet, pour pouvoir calculer $R_{n-1}$, bien que les valeurs de
$a_{n-1}$ et $b_{n-1}$ soient déjà disponibles, il faut attendre
que la valeur de $r_{n-1} = R_{n-2}$ soit stabilisée avant que le
calcul puisse s'effectuer avec les bonnes valeurs. Il en est de même
avec le bloc précédent et ainsi, en remontant la chaîne vers $r_0$,
on trouve le chemin de propagation de retenue comme chemin le plus
long.

Pour déterminer le nombre de portes à franchir pour le chemin de
propagation de retenue, nous avons ajouté deux sorties intermédiaires
à notre circuit d'additionneur complet, $P_i$ et $G_i$, permettant
de récrire la sortie comme $S_i = P_i  \operatorname{Xor} r_i$ et la retenue de
sortie comme $R_i = P_i r_i + G_i$. Les signaux $P_i$ et $G_i$
ne dépendent que des entrées et sont donc disponibles après le délai
des portes ET et XOR. Le chemin de $r_i$ à $R_i$ passe par une
porte ET et une porte OU. Pour un additionneur de $n$ bits
comprenant $n$ additionneurs complets, on aura une profondeur de
retenue totale de $2n$ portes.

![img](Sources_images_logiques/images/fulladderxorPG.svg "Circuit additionneur complet montrant les signaux intermédiaires $P_i$ et $G_i$")


### Anticipation de retenue

Les valeurs calculées par le circuit complet en chaîne ne seront
valides et ne devront être prises en compte que lorsque le délai
maximal se sera écoulé. Entre-temps, les valeurs binaires présentes
aux différentes sorties assumeront typiquement des valeurs changeantes
jusqu'à la stabilisation finale. Le délai de propagation de retenue est
un facteur qui limite la vitesse à laquelle on pourra calculer la
somme de deux nombres. Et comme l'addition est une opération 
souvent utilisée, parfois à répétition, pour réaliser d'autres
opérations arithmétiques, cette limitation est problématique. 

Il serait en théorie possible de ramener à un minimum le délai de
calcul de la retenue finale en réalisant cette fonction en deux
niveaux, par exemple avec un *produit de sommes*. Cette option n'est pas
réaliste, car le nombre d'entrées à considérer en parallèle est prohibitif.

Comme solutions de compromis intermédiaires, un certain nombre de
mécanismes ont été élaborés, dont l'approche par anticipation de
retenue, que nous allons explorer ici. On fait appel aux deux signaux
$P_i = a_i \operatorname{Xor} b_i$ et $G_i = a_i b_i$, qui donnent
respectivement pour la sortie et la retenue de sortie

$$ S_i = P_i \operatorname{Xor} r_{i-1} $$
$$ R_i = P_i r_{i-1} + G_i $$

$G_i$ est le signal qui indique la **génération** de retenue,
produisant une retenue lorsque $a_i$ et $b_i$ sont tous deux à 1,
sans égard à la valeur de la retenue d'entrée $r_{i-1}$. Le signal
$P_i$ est l'indicateur de **propagation** de retenue, parce qu'il
détermine si la retenue du niveau précédent $r_{i-1}$ sera propagée
à $R_i$.

En partant du niveau 0, voici les expressions pour les différentes retenues:

$$ R_0 = r_0 = \operatorname{in}$$
$$ R_1 = G_0 + P_0 R_0 $$
$$ R_2 = G_1 + P_1 R_1 = G_1 + P_1 (G_0 + P_0 R_0) = G_1 + P_1 G_0 + P_1 P_0 R_0 $$
$$ R_3 = G_2 + P_2 R_2 = G_2 + P_2 G_1 + P_2 P_1 G_0 + P_2 P_1 P_0 R_0 $$
etc.

Les expressions pour les retenues successives sont en forme *somme de
produits*, ce qui mène à une implémentation à deux niveaux pour
calculer les retenues rapidement. Contrairement à l'approche de
propagation de retenue, toutes les retenues sont obtenues après un
même délai équivalent à une profondeur de deux portes.  En calculant
d'abord les différentes valeurs de $P_i$ et $G_i$ pour chaque
niveau et en utilisant ces résultats intermédiaires pour, d'une part,
alimenter le circuit d'anticipateur de retenue et, d'autre part,
effectuer $S_i = P_i  \operatorname{Xor} r_i$, on obtient un additionneur parallèle
plus rapide que la configuration en cascade.

![img](Sources_images_logiques/images/lookahead1.svg "Circuit d'anticipateur de retenue pour $n= 4$")


### Soustraction

Pour effectuer une soustraction $A - B$, il faut effectuer $A +
(-B)$, c'est-à-dire additionner le complément à deux de $B$ à
$A$. On détermine le complément à deux en obtenant d'abord le
complément à un en complémentant chaque bit et en additionnant ensuite
1 à cette valeur par le biais de l'entrée de retenue de l'additionneur. Il
est ainsi possible de concevoir un additionneur/soustracteur commandé
par un signal de contrôle $O$. Si $O=0$, le circuit calcule $A +
(B)$ et si $O=1$, le circuit calcule $A + (-B)$.

La complémentation de $B$ se fait au moyen de portes XOR qui
calculent $O \operatorname{Xor} b_i$ et dont la sortie est acheminée
à l'entrée $B$ de l'additionneur. Lorsque $O=1$, leur sortie vaut
$b_i^\prime$.

![img](Sources_images_logiques/images/add_sous.svg "Circuit additionneur/ soustracteur 4 bits")


### Débordements

Un additionneur ou un soustracteur est conçu en fonction d'une
taille de nombres $n$. Lorsque le résultat de l'opération dépasse la
limite pouvant être représentée, on doit détecter cette condition et
la signaler par un signal binaire.

Le cas de l'addition de nombres non signés est le plus simple. Il
suffit de surveiller la retenue du niveau le plus significatif. Une
retenue de 1 signifie un débordement de l'addition.

Les calculs avec des nombres signés en complément à deux peuvent aussi
occasionner des débordements, mais la détection doit tenir compte des
bits qui indiquent le signe des nombres.

L'addition de deux nombres de signes différents ne peut pas
occasionner de débordement, puisque la valeur absolue du résultat sera
nécessairement moindre que celle du plus grand des nombres
initiaux. Un débordement ne peut donc se produire que si les deux
nombres additionnés sont de même signe, deux positifs ou deux
négatifs.

Prenons le cas de nombres représentés sur huit bits en complément à
deux. La gamme représentable va de -128 à +127 avec un bit qui
représente le signe. Si on additionne (+50)10 = (00110010)2 avec
(+100)10 = (01100100)2, on aura un débordement, car $150 > 127$. On
voit dans le tableau suivant les bits qui seront produits par
l'addition, avec en évidence les retenues des deux derniers
niveaux. Le bit de signe a été séparé des autres.

<table id="org6a5c8b2" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 24 :</span> Addition de (+50)10 + (+100)10 = (00110010)2 + (01100100)2</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Retenues</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">011 0010</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">110 0100</td>
</tr>
</tbody>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-left">001 0110</td>
</tr>
</tbody>
</table>

Refaisons le même exercice avec deux nombres négatifs: on additionne
(-50)10 = (1100 1110)2 avec (-100)10 = (1001 1100)2, qui créera aussi un
débordement.

<table id="org7035dfb" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 25 :</span> Addition de (-50)10 + (-100)10 = (1100 1110)2 + (1001 1100)2</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Retenues</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-left">100 1110</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-left">001 1100</td>
</tr>
</tbody>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">110 1010</td>
</tr>
</tbody>
</table>

On peut dans les deux cas détecter le débordement en observant que la
retenue du dernier niveau et la retenue de l'avant-dernier niveau sont
différentes. On peut vérifier facilement que les autres cas sans
débordement donnent des retenues égales. Donc, si on fait un
OU-exclusif entre ces deux retenues, un résultat 1 indiquera un
débordement. Ce mécanisme de détection de débordement a été ajouté au
circuit additionneur/soustracteur 4 bits dans la figure suivante pour
générer le signal $D$ qui indique un débordement.

![img](Sources_images_logiques/images/add_sous_deb.svg "Circuit additionneur/soustracteur 4 bits avec débordement")


## Multiplexeur

Un multiplexeur est un circuit combinatoire qui sélectionne le signal
qui provient d'une de ses entrées, et fait que sa sortie est égale à
l'entrée sélectionnée. Les signaux de sélection fonctionnent
typiquement selon un encodage binaire, ce qui suppose un nombre
d'entrées de la forme $2^n$. On désigne le multiplexeur par le
nombre de signaux d'entrées à sélectionner.


### Multiplexeur deux-vers-un

Le multiplexeur le plus simple utilise un seul signal de sélection
$S$ qui permet de choisir une de deux entrées $I_0$ ou $I_1$
pour agir sur la sortie $Y$.

![img](Sources_images_logiques/images/mux2b.svg "Circuit du multiplexeur deux-vers-un")

![img](Sources_images_logiques/images/mux2symb.svg "Symbole du multiplexeur deux-vers-un")


### Multiplexeur quatre-vers-un

Un multiplexeur quatre-vers-un permet de choisir une de quatre entrées
en utilisant deux signaux de sélection. Pour simplifier la
représentation symbolique, les deux signaux de sélection sont
représentés comme un seul fil, qui correspond en fait à une paire de
signaux $S_0$ et $S_1$. Pour un multiplexeur à $2^n$ entrées, on
aurait un vecteur de $n$ signaux de sélection.

![img](Sources_images_logiques/images/mux4.svg "Circuit du multiplexeur quatre-vers-un")

![img](Sources_images_logiques/images/mux4symb.svg "Symbole du multiplexeur quatre-vers-un")

<table id="org4cd9775" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 26 :</span> Tableau de vérité du multiplexeur quatre-vers-un</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(S_1\)</th>
<th scope="col" class="org-right">\(S_0\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(Y\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_0\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_1\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_2\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_3\)</td>
</tr>
</tbody>
</table>


## Décodeur

Un décodeur est un circuit combinatoire qui sert à interpréter des
données encodées, le plus souvent en binaire. Il prend un groupe
(vecteur) de $n$ bits en entrée, et active une sortie parmi jusqu'à
$2^n$ sorties différentes. Dans le cas où certaines combinaisons
d'entrées ne sont pas utilisées, moins de $2^n$ sorties peuvent être
produites.

Dans un décodeur générique, chaque combinaison binaire distincte
activera une seule sortie. Il y a une correspondance directe entre
chaque sortie possible et un minterm d'entrée.

![img](Sources_images_logiques/images/decod3_8.svg "Circuit du décodeur trois-vers-huit")

<table id="org651d0d5" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 27 :</span> Tableau de vérité du décodeur trois-vers-huit</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-right">\(z\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(D_0\)</th>
<th scope="col" class="org-right">\(D_1\)</th>
<th scope="col" class="org-right">\(D_2\)</th>
<th scope="col" class="org-right">\(D_3\)</th>
<th scope="col" class="org-right">\(D_4\)</th>
<th scope="col" class="org-right">\(D_5\)</th>
<th scope="col" class="org-right">\(D_6\)</th>
<th scope="col" class="org-right">\(D_7\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>


### Décodeur avec sortie active basse et signal de contrôle

On peut aussi concevoir des décodeurs basés sur des portes NAND et
dont la sortie sélectionnée est active au niveau bas. Une autre
fonction utile est un signal de contrôle $E$ qui n'active une sortie
que lorsqu'il est activé.

Le décodeur deux-vers-quatre, dont le circuit est présenté ci-dessous,
comporte ces deux caractéristiques. Comme on peut voir dans le tableau
de vérité, tant que le signal de contrôle est inactif ( $E = 1$
puisque ce signal est également actif bas), les sorties sont inactives
(au niveau 1) quelles que soient les entrées $x$ et $y$. Lorsque
$E = 0$, une seule sortie passe à 0, selon le code binaire présent
aux entrées $x$ et $y$. Notez que ce décodeur a été conçu et
étiqueté en fonction d'entrées $x$ et $y$ qui sont actives haut.

![img](Sources_images_logiques/images/decode2_4_enable.svg "Décodeur à sortie active basse")

<table id="org6289f91" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 28 :</span> Tableau de vérité, décodeur 2 vers 4 avec sortie active basse</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(E\)</th>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(D_0\)</th>
<th scope="col" class="org-right">\(D_1\)</th>
<th scope="col" class="org-right">\(D_2\)</th>
<th scope="col" class="org-right">\(D_3\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>


### Implémentation de fonctions arbitraires au moyen d'un décodeur

Puisqu'un décodeur active sélectivement les $2^n$ minterms possibles
à partir de ses $n$ entrées, il est possible d'implémenter, en *somme
de produits*, une fonction quelconque en acheminant les minterms de la
fonction à une porte OU. Il est même possible d'implémenter plusieurs
fonctions différentes, en leur consacrant chacune une porte OU de
sortie.

Voici par exemple une fonction réalisée à partir d'un décodeur
trois-vers-huit. L'entrée $I$ correspond à un vecteur de trois bits. Le
tableau de vérité correspondant est donné. On peut voir que les
minterms choisis permettent d'implémenter

$$ Y = \sum(0,2,5,6)$$

![img](Sources_images_logiques/images/fonct_arbit_decod.svg "Fonction arbitraire réalisée au moyen d'un décodeur")

<table id="org744ee62" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 29 :</span> Tableau de vérité pour la fonction arbitraire</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(I_2\)</th>
<th scope="col" class="org-right">\(I_1\)</th>
<th scope="col" class="org-right">\(I_0\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(Y\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

Une fonction qui comporte de nombreux minterms exige l'utilisation
d'une porte OU avec un grand nombre d'entrées. Si la fonction à
réaliser exige plus de $2^n/2$ minterms, il est alors plus
avantageux d'implémenter le complément de la fonction, qui nécessitera
moins de $2^n/2$ minterms, et d'inverser ensuite la sortie pour
obtenir la fonction.


## Encodeur

Un encodeur effectue le travail inverse du décodeur: lorsqu'une de ses
$2^n$ (ou moins) entrées est activée, il donne le code binaire
correspondant sur ses $n$ sorties vues comme un vecteur binaire. Le
circuit ne nécessite pas vraiment d'entrée pour $D_0$.

![img](Sources_images_logiques/images/encode1.svg "Encodeur 3 bits")

<table id="orgd63b607" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 30 :</span> Tableau de vérité pour l'encodeur 3 bits</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(D_0\)</th>
<th scope="col" class="org-right">\(D_1\)</th>
<th scope="col" class="org-right">\(D_2\)</th>
<th scope="col" class="org-right">\(D_3\)</th>
<th scope="col" class="org-right">\(D_4\)</th>
<th scope="col" class="org-right">\(D_5\)</th>
<th scope="col" class="org-right">\(D_6\)</th>
<th scope="col" class="org-right">\(D_7\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-right">\(z\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Cette configuration d'encodeur exige qu'une seule entrée soit
activée à la fois. Activer plus d'une entrée ne correspond en effet à
rien de valide: comment donner un sens à une telle combinaison au
moyen d'un vecteur de $n$ bits? Les sorties produites alors seront
des vecteurs binaires sans signification.


### Encodeur à priorité

Un encodeur à priorité met en oeuvre une priorité entre les
entrées. S'il y a plus d'une entrée 1 en même temps, la sortie sera
celle qui correspond à l'entrée active qui a la plus grande
priorité. Voici le tableau de vérité pour un encodeur 2 bits à priorité,
dans lequel on a ajouté une sortie $V$ qui indique la validité des
sorties. Si aucune entrée n'est active, $V=0$ et les sorties $x$
et $y$ ne doivent pas être prises en compte.

Lorsque des entrées sont activées, c'est celle qui a le plus grand
indice qui est prioritaire.

<table id="org4fdc552" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 31 :</span> Tableau de vérité pour encodeur 2 bits à priorité</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">\(D_0\)</th>
<th scope="col" class="org-right">\(D_1\)</th>
<th scope="col" class="org-right">\(D_2\)</th>
<th scope="col" class="org-right">\(D_3\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-right">\(y\)</th>
<th scope="col" class="org-right">\(V\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">X</td>
<td class="org-right">X</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">X</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">X</td>
<td class="org-right">X</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">X</td>
<td class="org-right">X</td>
<td class="org-right">X</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

![img](Sources_images_logiques/images/kmap4foncencode_pri_x.svg "Diag-K pour $x$ de l'encodeur à priorité")

![img](Sources_images_logiques/images/kmap4foncencode_pri_y.svg "Diag-K pour $y$ de l'encodeur à priorité")

En simplifiant, on trouve les expressions suivantes:

$$ x = D_2 + D_3 $$

$$ y = (D_1 D_2^\prime) + D_3 $$

$$ V = D_0 + D_1 + D_2 + D_3 $$

![img](Sources_images_logiques/images/encode_pri.svg "Encodeur 2 bits à priorité, en P de S")

Puisque le terme $x = D_2 + D_3$ est déjà calculé pour $x$, on
peut le réutiliser pour construire le terme pour $V$, tel
qu'illustré ci-dessous, ce qui évite d'utiliser une porte OU à quatre
entrées.

![img](Sources_images_logiques/images/encode_pri2.svg "Encodeur 2 bits à priorité avec ré-utilisation d'un des termes")


## Comparateur de magnitude

Comparer la magnitude de deux nombres binaires est une opération qui
peut se systématiser, comme on l'a fait pour l'addition. Considérons
deux nombres binaires non signés, $A$ et $B$ de même taille $n$,
avec leurs bits respectifs $a_i$ et $b_i$. Nous voulons que notre
comparateur active une des trois sorties, selon le cas: $A < B$, $A
= B$ ou $A > B$. Pour illustrer, nous considérerons $n = 4$.

$$ a_3 a_2 a_1 a_0 $$

$$ b_3 b_2 b_1 b_0 $$

Nous aurons besoin d'une fonction qui permet de déterminer si deux
bits sont égaux. Cette fonction correspond à la fonction **Équivalence**
ou NOR-exclusif $a_i b_i + a_i^\prime b_i^\prime$.  Si les bits
diffèrent en position $i$, $a_i = 1$ nous permet de conclure que
$A > B$ et, à l'inverse, $a_i = 0$ nous indique que $A < B$. Nous avons ainsi
les éléments qui permettent d'effectuer une comparaison pour un bit,
comme on peut en voir l'implémentation sur la figure suivante.

![img](Sources_images_logiques/images/comparateur.svg "Comparateur de magnitude")

Notre démarche de conception pour $n$ bits sera calquée sur la
procédure que nous utilisons intuitivement pour faire une telle
comparaison. La comparaison commence au niveau du bit le plus
significatif. Si ces bits sont égaux, on considère la position
suivante, jusqu'à atteindre une position $i$ où les bits diffèrent
ou jusqu'à atteindre la fin des nombres (c'est-à-dire $i=0$). Si les
bits diffèrent en position $i$, $a_i = 1$ nous permet de conclure
que $A > B$, alors que $a_i = 0$ nous indique que $A < B$.

Les signaux intermédiaires $x_i = a_i b_i + a_i^\prime b_i^\prime$
qui indiquent si deux bits d'une position sont égaux seront mis à
profit pour alimenter un réseau de conditions en forme *somme de
produits* qui mettront en application les règles énoncées. Les signaux
de sortie binaires sont $(A = B), (A < B), (A > B)$.  D'une part,
la régularité des opérations simplifie la conception et, d'autre part,
l'implémentation sera simplifiée du fait que certains des termes
nécessaires peuvent être réutilisés.

$$ (A = B) = x_3 x_2 x_1 x_0 $$ 

$$ (A < B) = a_3^\prime b_3 + x_3  a_2^\prime b_2  +  x_3 x_2  a_1^\prime b_1 +  x_3 x_2 x_1  a_0^\prime b_0 $$

$$ (A > B) = a_3 b_3^\prime + x_3  a_2 b_2^\prime  +  x_3 x_2  a_1 b_1^\prime +  x_3 x_2 x_1  a_0 b_0^\prime $$

On obtient ainsi un comparateur pour des nombres de quatre bits, tel qu'illustré.

![img](Sources_images_logiques/images/comparateur_4b.svg "Comparateur de magnitude 4 bits")


## Démultiplexeur

Un démultiplexeur achemine la valeur logique de son entrée à une
sortie (parmi $2^n$ sorties) sélectionnée par un code binaire de
sélection. Le démultiplexeur de la figure suivante comporte trois bits
de sélection et permet donc d'acheminer la valeur de l'entrée $I$
vers une des huit sorties $O_i, i = 0, \ldots, 7$. On peut aussi
interpréter ce circuit comme un décodeur trois-vers-huit avec une
entrée signal de contrôle (*enable*) $I$.

![img](Sources_images_logiques/images/demux8.svg "Démultiplexeur un-vers-huit")


## Encodeurs divers

Il est possible de concevoir des encodeurs pour des fonctions
spécialisées, comme des encodeurs pour commander des affichages. La
démarche de conception s'apparente largement à celles que nous avons
vues dans les exemples précédents.


## Portes à trois états et tampon de bus

Les portes à trois états ajoutent un troisième état de fonctionnement
aux sorties: en plus des niveaux logiques bas et haut conventionnels,
un troisième état appelé **haute impédance** fait en sorte que la sortie
se comporte comme si elle n'était plus connectée au circuit. La sortie
n'agit pas sur le reste du circuit, les autres portes dont les entrées
sont alimentées par la porte en haute impédance ne sont aucunement
affectées par celle-ci. Pour activer cet état de sortie
haute impédance, une entrée de contrôle est ajoutée.

Le figure ci-dessous montre une porte tampon à trois états. Avec
`Contrôle` = 0, la sortie est en haute impédance; avec  `Contrôle` = 1,
la sortie est égale à l'entrée.

![img](Sources_images_logiques/images/buf_3s.svg "Porte tampon à trois états")

En plaçant des tampons à trois états à chaque sortie d'un décodeur, on
peut réaliser un multiplexeur $n$-vers-un en reliant les sorties des
tampons à une sortie unique. Ainsi, lorsqu'une entrée est
sélectionnée au moyen des entrées de sélection, c'est sa valeur qui se
retrouve à la sortie du dispositif. La valeur Z représente l'état
haute impédance.  Lorsque l'entrée de contrôle $E = 0$, la sortie est
en haute impédance.

<table id="org1614755" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 32 :</span> Tableau de vérité pour un  multiplexeur quatre-vers-un trois états</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(s_1\)</th>
<th scope="col" class="org-right">\(S_0\)</th>
<th scope="col" class="org-right">\(E\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(I_0\)</th>
<th scope="col" class="org-left">\(I_1\)</th>
<th scope="col" class="org-left">\(I_2\)</th>
<th scope="col" class="org-left">\(I_3\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(Y\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">X</td>
<td class="org-right">X</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">Z</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_0\)</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_0\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">X</td>
<td class="org-left">\(I_1\)</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_1\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">\(I_2\)</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_2\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">\(I_3\)</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(I_3\)</td>
</tr>
</tbody>
</table>

![img](Sources_images_logiques/images/mux_4_1_3s.svg "Multiplexeur quatre-vers-un trois états")

La fonctionnalité trois-états permet aussi de concevoir un
émetteur-récepteur de bus. Ce dispositif, illustré à la figure
suivante ([572](#orgf3d7676)), permet d'établir une connexion
bidirectionnelle entre `I/O` et `O/I`. Lorsque l'entrée de contrôle
$E = 0$, c'est le tampon du haut de la figure qui est actif, et
`O/I` détermine la valeur de `I/O`. Lorsque $E = 1$, c'est le tampon
du bas qui est actif, et `I/O` détermine la valeur de `O/I`.

![img](Sources_images_logiques/images/bus_trans.svg "Émetteur-récepteur de bus")


# Circuits séquentiels


## Objectifs

-   Identifier un circuit logique séquentiel
-   Faire la distinction entre les circuits séquentiels synchrones et asynchrones
-   Se familiariser avec les principaux types de loquets, en expliquer
    le fonctionnement
-   Se familiariser avec les principaux types de bascules, en expliquer
    le fonctionnement


## Modèle d'un circuit séquentiel

Les circuits logiques séquentiels sont ceux qui comportent de la
mémoire. Le modèle général d'un circuit séquentiel est illustré sur la
figure [579](#org1a05bbe). On y voit qu'il y a une boucle de rétroaction,
qui fait que les valeurs binaires stockées dans les éléments de
mémoire contribuent au calcul des sorties. Les sorties du circuit à un
instant donné ne dépendent donc pas seulement des entrées présentes à
ce moment, mais aussi de ces valeurs qui sont mémorisées dans le
système. Pour décrire cette situation dans laquelle se trouvent les
valeurs stockées en mémoire, on parle de l'**état** du système. Selon
les entrées et l'état à un instant donné, le système pourra changer
d'état selon les changements qui seront apportés par la portion
combinatoire aux valeurs mémorisées.

On verra donc le système évoluer au fil du temps, passant d'un état à
un autre, et générant des sorties en fonction des entrées et de l'état
du moment. Intuitivement, on peut penser que le nombre d'états
distincts sera fonction du nombre de valeurs binaires qui seront
mémorisées. Le comportement d'un système séquentiel est donc
caractérisé par une séquence temporelle d'entrées, de sorties et de
valeurs internes d'état.

![img](Sources_images_logiques/images/circuit_seq.png "Modèle de circuit séquentiel")

On peut distinguer les circuits séquentiels selon la relation de
synchronisation qui existe entre les différents signaux du
système. Dans un circuit séquentiel **synchrone**, le comportement du
système peut se définir en fonction des valeurs de ses signaux à des
instants discrets prédéterminés. 

Le comportement d'un circuit séquentiel **asynchrone** dépend à tout
moment des signaux d'entrée et de l'ordre dans lequel ces signaux
changent.

Un circuit séquentiel synchrone fait appel à un signal spécial appelé
**horloge** qui rythme les changements d'état et de sorties afin qu'ils se
produisent à des instants discrets. Les éléments de mémoire qui
stockent les valeurs binaires sont appelés **bascules** (*flip-flops* en
anglais). Il existe différents types de bascules. Nous les étudierons
en détail, car elles sont à la base des circuits séquentiels les plus
utilisés. La figure [583](#orgef65b0c) présente le modèle général d'un
circuit séquentiel synchrone.

![img](Sources_images_logiques/images/circuit_seq_sync.png "Modèle de circuit séquentiel synchrone")

Le signal d'horloge est typiquement une onde carrée, comme illustré
sur la figure [585](#orgc4bb4be).

![img](Sources_images_logiques/images/horloge.svg "Signal d'horloge")


## Éléments de mémoire

Un élément de mémoire peut maintenir son état binaire indéfiniment (à
condition, évidemment, qu'il soit alimenté). Son état est observable
par l'intermédiaire de ses sorties. On doit agir via la ou les entrées
de l'élément pour le faire changer d'état. Les différents types
d'éléments de mémoire sont caractérisés par le nombre et le type
d'entrées.

Les éléments de mémoire qui sont contrôlés par les niveaux de leurs
entrées sont appelés des **loquets** (*latches* en anglais). Les
éléments contrôlés par des changements ou **transitions** de niveaux
sont appelés des bascules. Les transitions sont appliquées à une
entrée spéciale d'horloge qui sert à déclencher les changements d'état
à des instants précis. Les loquets sont des ingrédients de base dans
la conception des bascules. Nous les étudierons en premier.


## Loquets


### Loquet SR

Le loquet SR est formé de deux portes NOR interconnectées et comporte
deux entrées: $S$ pour `Set`, qui permet de mémoriser une valeur 1,
et $R$ pour `Reset`, qui permet de mémoriser une valeur 0. Le schéma
classique du loquet SR montré sur la figure [589](#org6dfdd56) ne fait pas
ressortir la boucle de rétroaction, mais si on déplace un peu les
éléments sans changer les connexions, on voit mieux le lien de retour
caractéristique de la boucle. Sur la figure [590](#orgdcb5274), la porte reliée
à $S$ a été placée devant, mais nous aurions pu tout aussi bien
mettre l'autre porte en avant. Aucune des deux n'est vraiment devant
l'autre, puisqu'il s'agit d'une boucle n'ayant ni début ni fin.

![img](Sources_images_logiques/images/SRlatch.svg "Schéma du loquet SR avec portes NOR")

![img](Sources_images_logiques/images/SRlatch_bouc.svg "Schéma du loquet SR NOR mettant la boucle en évidence")

Quand les sorties sont $Q=1, Q^\prime=0$, on dit que le loquet est
dans l'état activé (`set`). Lorsque $Q=0, Q^\prime=1$, le loquet
est désactivé (`reset`). Les sorties $Q$ et $Q^\prime$ sont
normalement complémentaires. Si on active la condition d'entrée $S=1,
R=1$, les deux sorties seront à 0, mais lorsqu'on relâchera les
entrées, le loquet passera à un état imprévisible, voire
instable. Dans une application normale, on voudra éviter le cas
d'entrée $S=1, R=1$. 

En fonctionnement normal, à moins de vouloir changer l'état, on garde
les deux entrées à $S=0, R=0$ et l'état du loquet se maintient. En
appliquant le niveau 1 pendant un certain temps à $S$ seulement, le
loquet s'active, peu importe l'état dans lequel il se trouvait
auparavant. On doit s'assurer de ramener l'entrée $S$ à 0 avant
d'apporter d'autres changements aux entrées, pour éviter le cas
interdit $S=1, R=1$.

De même, en appliquant le niveau 1 pendant un certain
temps à $R$ seulement, le loquet se désactive, peu importe l'état
dans lequel il se trouvait auparavant.

<table id="org2e09daa" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 33 :</span> Loquet SR NOR: tableau de fonctionnement</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(S\)</th>
<th scope="col" class="org-right">\(R\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(Q\)</th>
<th scope="col" class="org-right">\(Q^\prime\)</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">après \(s=1, R=0\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">après \(s=0, R=1\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">interdit</td>
</tr>
</tbody>
</table>

On peut aussi concevoir un loquet avec des portes NAND, comme sur la
figure [595](#org4f32f0c). Le fonctionnement est sensiblement le même,
si ce n'est que les niveaux sont inversés par rapport au loquet NOR
comme on peut le voir sur le tableau de fonctionnement (tableau
[43](#orgf25d127)). Par exemple, on garde les deux entrées à $S=1, R=1$
pour maintenir l'état du loquet.

![img](Sources_images_logiques/images/SRlatch_nand.svg "Loquet SR en portes NAND")

<table id="orgf25d127" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 34 :</span> Loquet SR NAND: tableau de fonctionnement</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(S\)</th>
<th scope="col" class="org-right">\(R\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(Q\)</th>
<th scope="col" class="org-right">\(Q^\prime\)</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">après \(s=1, R=0\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">après \(s=0, R=1\)</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">interdit</td>
</tr>
</tbody>
</table>

On peut ajouter un signal de contrôle d'entrée $E$ (*enable*) pour
contrôler **quand** le loquet pourra être affecté par les signaux
d'entrée. Le circuit est représenté à la figure [598](#orgb34c7e3). Comme
on peut voir dans le tableau [44](#org0c71af5), les sorties des portes
NAND d'entrée demeurent à 1 tant que $E = 0$, et le loquet ne peut
pas être affecté par les entrées $S$ et $R$. Quand on active $E
= 1$, le circuit peut être actionné par les entrées $S$ et $R
$. La condition pour activer est $S=1, R=0$; pour désactiver,
c'est $S=0, R=1$. Lorsque $E = 1$, on ne doit pas faire $S=1,
R=1$, car on mettrait le loquet dans un état indéterminé.

Le loquet SR avec contrôle est surtout important comme
ingrédient de base pour la conception de bascules.

![img](Sources_images_logiques/images/SRlatch_nand_en.svg "Loquet SR NAND avec signal de contrôle")

<table id="org0c71af5" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 35 :</span> Loquet SR avec signal de contrôle: tableau de fonctionnement</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(E\)</th>
<th scope="col" class="org-right">\(S\)</th>
<th scope="col" class="org-right">\(R\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">Prochain \(Q\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">X</td>
<td class="org-right">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">inchangé</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">inchangé</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q = 0\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q = 1\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">indéterminé</td>
</tr>
</tbody>
</table>


### Loquet D

Une option pour éliminer la condition qui fait apparaître un état
indéterminé est de s'assurer de toujours commander $S$ et $R$
avec des signaux complémentaires. C'est ainsi qu'on arrive au loquet
D, illustré sur la figure [600](#org2df9778), qui ne comporte qu'une entrée de
donnée $D$ et une entrée de contrôle $E$. La valeur de $D$ est
reflétée à $Q$ lorsque $E=1$ et se maintient après que $E$ passe
à 0 (tableau [45](#orge5a0743)).

![img](Sources_images_logiques/images/Dlatch.svg "Schéma du loquet D")

<table id="orge5a0743" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 36 :</span> Loquet D: tableau de fonctionnement</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(E\)</th>
<th scope="col" class="org-right">\(D\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">Prochain \(Q\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">inchangé</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q = 0\)</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q = 1\)</td>
</tr>
</tbody>
</table>

Le symbole graphique d'un loquet D est illustré à la figure [602](#orgb59f840).

![img](Sources_images_logiques/images/schema_latchD.svg "Symbole du loquet D")


## Application: rebonds d'interrupteurs

Lorsqu'on utilise un interrupteur pour commuter un signal entre les
niveaux qui correspondent aux valeurs logiques 0 et 1, le contact ne
se fait pas de façon franche sans hésitations, et le signal observé
rebondit plusieurs fois avant de se stabiliser à sa valeur, comme on
peut le voir sur la partie de gauche de la figure [604](#orgc880352). Ces
rapides allers-retours entre les niveaux peuvent bien souvent
déclencher un circuit logique et le mettre dans un état
imprévisible. Pour éviter ce problème, on peut faire appel à un loquet
selon la configuration de la partie droite de la figure. Le loquet
réagit dès que l'entrée B passe à 0. Même si cette entrée remonte à 1,
la valeur $Q$ est maintenue. On obtient donc une transition franche sur
$Q$.

![img](Sources_images_logiques/images/debounce.svg "Contacts et rebonds")


## Bascules (Flip-flops)

Les loquets peuvent remplir le rôle de mémoriser des valeurs binaires,
mais le fait que les changements d'état soient activés par un **niveau**
pose des difficultés. En effet, si les valeurs à l'entrée changent
pendant que le signal de contrôle est actif, la valeur qui sera
mémorisée par la rétroaction sera la dernière qui aura eu le temps de
s'y établir, qui ne sera pas nécessairement la valeur souhaitée. Si la
sortie du loquet est acheminée, directement ou à travers un circuit
combinatoire, vers ses entrées ou les entrées d'autres loquets
(activés par le même signal de contrôle) dans une boucle du circuit
séquentiel, il se peut que les délais de propagation et de prise en
compte des entrées fassent que la sortie globale du circuit séquentiel
soit imprévisible.

La conception des bascules vise à corriger ce problème, en établissant
un instant précis et prévisible de déclenchement où les valeurs
d'entrée seront prises en compte systématiquement. Le concept
essentiel est que l'état d'une bascule est modifié uniquement au
moment où il y a un changement dans son signal de contrôle. Ce
changement momentané est appelé **transition** et on dit que c'est la
transition qui provoque le changement d'état qui **déclenche** la
bascule.

On parlera de déclenchement sur le **front montant** lorsque la
transition qui provoque le déclenchement passe d'un niveau bas vers un
niveau élevé, et de déclenchement sur le **front descendant** dans le
cas d'une transition du haut vers le bas.  On illustre parfois le
front de déclenchement au moyen d'une flèche, comme on peut le voir
sur la figure [608](#org5bbae8c).

![img](Sources_images_logiques/images/horlogeP.svg "Signaux d'horloge avec fronts de déclenchement")


### Bascule D

Le secret pour isoler la valeur mémorisée par l'élément de mémoire des
changements qui pourraient survenir sur les entrées consiste à
utiliser un mécanisme semblable à celui d'un sas. Selon le *Larousse*, la
définition d'un sas est

> Enceinte ou passage clos, muni de deux portes ou systèmes de fermeture
> dont on ne peut ouvrir l'un que si l'autre est fermé et qui permet de
> passer ou de faire passer d'un milieu à un autre en maintenant ceux-ci
> isolés l'un de l'autre.

Dans notre contexte, nous utiliserons deux loquets en série, avec la
sortie du premier, appelé **maître**, reliée à l'entrée du second,
appelé **esclave**. Le loquet maître sera activé par le signal d'horloge,
alors que le loquet esclave sera activé par le complément du signal
d'horloge. De cette façon, un seul des loquets sera actif à la fois,
comme dans un sas. La figure [612](#org8b8d79f) illustre la
configuration pour réaliser une bascule D maître-esclave.

![img](Sources_images_logiques/images/D_mast_slave_sanst.svg "Bascule D maître-esclave")

Lorsque le signal d'horloge est au niveau haut, seul le loquet maître
pourra réagir au signal d'entrée. Puis, lorsque le signal d'horloge
sera au niveau bas, ce premier loquet sera désactivé, sa sortie sera
maintenue, et le deuxième loquet sera activé. Comme l'entrée du loquet
esclave est alimentée par le loquet maître dont la sortie est
maintenue, c'est la valeur mémorisée par le maître qui sera mémorisée
dans l'esclave et qui apparaîtra donc en sortie de l'ensemble.

La valeur qui sera ultimement mémorisée est celle qui se trouvait tout
juste avant la transition de l'horloge passant du niveau haut vers le
niveau bas. Nous avons donc créé une bascule sensible au front
descendant.

En résumé:

1.  La sortie $Q$ ne changera qu'une fois par cycle d'horloge.
2.  Un changement de valeur sera causé par la valeur d'entrée présente
    juste avant le front descendant de l'horloge.
3.  La valeur de sortie changera effectivement (s'il y a lieu) pendant
    la demi-période basse de l'horloge.

D'autres configurations permettent de réaliser ce comportement de
sas. Par exemple, le circuit de la figure [620](#org5c3b2fb) utilise
trois éléments en loquet SR NAND: les deux premiers sont activés par
le signal de donnée $D$ et l'horloge, et le dernier mémorise et
fournit le signal de sortie $Q$. Cette configuration réalise une
bascule D à déclenchement sur front montant.

![img](Sources_images_logiques/images/D_front_montant.svg "Bascule D à déclenchement sur front montant")

Pour bien comprendre le comportement du circuit, la série de figures
suivantes permet d'en suivre le fonctionnement. Sur les figures,
les valeurs binaires sont indiquées par des couleurs: un signal en
vert sombre dénote la valeur 0 et un signal en vert clair représente
la valeur 1.

Comme on peut le voir sur la figure [623](#orgca9b97f), lorsque $clk = 0$, les
entrées intermédiaires $S$ et $R$ sont maintenues au niveau 1,
quelle que soit la valeur de l'entrée $D$, ce qui assure de
maintenir la valeur de sortie en $Q$.

![img](Sources_images_logiques/images/D_c0_d0.svg "Bascule au repos  $clk = 0, D=0$")

Même lorsque l'entrée de donnée $D$ change, la valeur de sortie est
maintenue, comme on le voit sur la figure [625](#orgb5b9648).

![img](Sources_images_logiques/images/D_c0_d1.svg "Bascule au repos  $clk = 0, D \rightarrow 1$")

Si l'entrée de donnée $D = 0$ lorsque $clk$ passe à 1, $R$
devient 0, ce qui met $Q$ à 0 (opération *reset*) (figure
[627](#orgc38ce1f)).

![img](Sources_images_logiques/images/D_c1_d0.svg "Bascule  *reset* $clk \rightarrow 1, D=0$")

Si l'entrée de donnée $D$ change pendant que $clk = 1$, comme sur
la figure [629](#orgc4965ce), $R$ reste à 0, parce que la porte NAND à
trois entrées a ses trois entrées à 1: par le signal $clk = 1$, par
la rétroaction du signal $S$ et par le signal de sortie de la porte
NAND du bas.

![img](Sources_images_logiques/images/D_c1_dchange.svg "Bascule   $clk = 1, D \rightarrow 1$")

Quand $clk$ revient à 0, on a $S=1, R=1$ et la sortie $Q$ ne
peut plus changer.

La figure [632](#org96ca0c0) présente la bascule dans l'état $Q=0$
avec l'entrée de donnée $D = 1$, juste avant que $clk$ passe
à 1. On voit que les deux portes NAND du haut sont prêtes à provoquer
un changement d'état de $S$ lorsque l'horloge passera à 1.

![img](Sources_images_logiques/images/D_c0_d1_avant.svg "Bascule   $clk =0, D = 1$")

Si l'entrée de donnée $D = 1$ lorsque $clk$ passe à 1, on voit
que $S$ est devenu 1, ce qui a amené $Q$ à 1 (opération *set*)
(figure [634](#org9cb48af)).

![img](Sources_images_logiques/images/D_c1_d1.svg "Bascule  *set* $clk \rightarrow 1, D=1$")

La figure [636](#orga6e6cf8) présente un chronogramme qui montre la bascule
qui passe de l'état 0 à l'état 1 et retourne, au cycle suivant, à
l'état 0.

![img](Sources_images_logiques/images/chron_D.svg "Chronogramme pour une bascule D")


### Délais et réponse temporelle

Comme dans tout circuit logique, les changements de valeurs logiques
dans les différentes portes qui constituent une bascule ne sont pas
instantanés. Il faut donc laisser le temps nécessaire pour que les
changements puissent se propager, être pris en compte et se stabiliser.

Sur la figure [641](#org44d73c5), on indique le délai $t_{setup}$ entre le
moment où la valeur à l'entrée de donnée D est modifiée et la
prochaine transition de déclenchement de l'horloge. Pour assurer un
fonctionnement adéquat de la bascule, on doit respecter un temps de
**mise en place** (*setup*) minimum pendant lequel la valeur à l'entrée
de donnée D doit être maintenue **avant** la transition de
déclenchement.

On montre aussi sur la figure le délai $t_{hold}$ entre le moment de
déclenchement et un prochain changement de valeur à l'entrée de
donnée D. Pour un fonctionnement adéquat, on doit également respecter
un temps de **maintien** (*hold*) minimum pendant lequel la valeur à
l'entrée de donnée D doit être maintenue **après** la transition de
déclenchement de l'horloge.

Enfin, la figure montre le délai de propagation à la sortie de la
bascule $t_{prop}$, qui se mesure entre le moment du déclenchement et
le moment où la sortie se stabilise à sa nouvelle valeur.

![img](Sources_images_logiques/images/D_setup.svg "Chronogramme avec temps et délais")

Le symbole graphique d'une bascule D comporte un petit triangle à
l'entrée d'horloge pour indiquer que le déclenchement se fait sur une
transition. Un déclenchement sur front descendant est indiqué par un
petit cercle d'inversion à l'entrée d'horloge.

![img](Sources_images_logiques/images/schema_bascules.svg "Symboles de bascules")


### Autres bascules

Il y a essentiellement trois opérations possibles pour une bascule:
mettre sa sortie à 1 (*set*), mettre sa sortie à 0 (*reset*) ou faire
basculer son état de sortie (*toggle*).


### Bascule JK

Une bascule JK comporte deux entrées, ce qui permet de lui faire
exécuter les trois opérations. Activer seulement l'entrée $J$ fait
un *set*, activer seulement l'entrée $K$ fait un *reset* et activer
les deux entrées fait un *toggle*. On peut réaliser une bascule JK
comme sur la figure [1023](#org98bc27f).

![img](Sources_images_logiques/images/bascule_JK.svg "Bascule JK")

La figure [648](#org1342860) montre le chronogramme de fonctionnement
d'une bascule JK. La bascule fait d'abord un *set*, puis un *reset* et
enfin trois *toggles* de suite.

![img](Sources_images_logiques/images/chron_JK.svg "Chronogramme de la bascule JK")


### Bascule T

La bascule T (T pour *toggle*) change d'état à chaque déclenchement
lorsque l'entrée $T$ est activée. On peut la réaliser à partir d'une
bascule D ou d'une bascule JK (figure [650](#orgc996a89)).

![img](Sources_images_logiques/images/basculeT.svg "Bascule T")


### Tableaux caractéristiques

On résume le fonctionnement des différentes bascules au moyen de
tableaux qui décrivent, selon les conditions d'entrée et l'état
présent, quel sera le prochain état après le déclenchement. $Q(t)$
représente l'état présent et $Q(t+1)$ l'état suivant.

<table id="orgbc68753" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 37 :</span> Bascule D</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(D\)</th>
<th scope="col" class="org-right">\(Q(t+1)\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left"><i>reset</i></td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left"><i>set</i></td>
</tr>
</tbody>
</table>

<table id="orgbfc3e5c" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 38 :</span> Bascule JK</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(J\)</th>
<th scope="col" class="org-right">\(K\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(Q(t+1)\)</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q(t)\)</td>
<td class="org-left">pas de changement</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">0</td>
<td class="org-left"><i>reset</i></td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">1</td>
<td class="org-left"><i>set</i></td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q^\prime(t)\)</td>
<td class="org-left">basculement</td>
</tr>
</tbody>
</table>

<table id="org38376fe" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 39 :</span> Bascule T</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(T\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(Q(t+1)\)</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q(t)\)</td>
<td class="org-left">pas de changement</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(Q^\prime(t)\)</td>
<td class="org-left">basculement</td>
</tr>
</tbody>
</table>


### Équations caractéristiques

On peut de même formuler des équations qui décrivent le comportement
des bascules. Pour une bascule D, on a

$$ Q(t+1) = D $$

Pour une bascule JK, on a

$$ Q(t+1) =J Q^\prime + K^\prime Q $$

Pour une bascule T, on a

$$ Q(t+1) = T \operatorname{Xor} Q = T Q^\prime + T^\prime Q $$


### Entrées asynchrones

Certaines bascules sont aussi munies d'entrées asynchrones, dont
l'effet n'est pas soumis à l'horloge. Ces entrées sont typiquement
utilisées pour faire un *reset* ou un *set* de la bascule, par exemple
pour une remise à zéro initiale d'un circuit séquentiel. Une
configuration typique est illustrée par la bascule de la figure
[659](#orgd5461f9) qui comporte une entrée `Reset'`, laquelle
permet de forcer l'état en agissant sur une porte NAND de chacune des
paires de portes. Cette entrée est active au niveau bas, c'est
pourquoi il y a une indication de complément dans son symbole.

![img](Sources_images_logiques/images/D_front_montant_setasyn.svg "Bascule D avec reset asynchrone")


# Analyse de circuits logiques séquentiels synchrones


## Objectifs

-   Analyser en détail le comportement d'un circuit séquentiel
    synchrone à partir de son schéma, selon différents types de bascules
    employés
-   Établir les équations de transition qui commandent les bascules
-   Se familiariser avec la notion de tableau d'excitation
-   Tracer un diagramme d'état
-   Interpréter le comportement du système à partir de son
    diagramme d'état
-   Faire la distinction entre les deux modèles de circuits séquentiels
    (Mealy et Moore)


## Démarche d'analyse

Analyser un circuit logique séquentiel a pour but de déterminer le
comportement qu'aura le circuit selon les séquences d'entrée qui lui
seront appliquées et l'état dans lequel il se trouve initialement. On
voudra aussi connaître quelles séquences de sortie seront produites.

Dans la mesure où un circuit comporte une ou des bascules (peu importe
le type) et un signal d'horloge, on peut considérer qu'il s'agit d'un
circuit séquentiel synchrone. Le type de bascule sera pris en compte
pour l'analyse, qui consistera à déterminer, pour un état présent
donné, quels seront les prochains états possibles selon les valeurs
d'entrée.

Les grandes lignes de la démarche sont les suivantes.

1.  Identification des éléments fonctionnels:
    1.  entrées externes
    
    2.  éléments de mémoire
    
    3.  décodeur de prochain état
    
    4.  sorties externes
    
    5.  décodeur de sortie
2.  Expressions logiques du décodeur de prochain état: établies pour
    chaque entrée des bascules, en fonction des entrées externes et des
    variables d'état
3.  Expressions logiques des sorties externes, établies en fonction des
    entrées externes et des variables d'état
4.  Construction du tableau d'excitation
5.  Diagramme d'état
6.  Interprétation du comportement du circuit séquentiel

Au centre de ce processus se trouve l'analyse des circuits
combinatoires qui déterminent ce que seront les entrées des
bascules. Nous chercherons à établir les **équations de transition** qui
précisent ce que sera le prochain état en fonction des entrées et de
l'état présent.


## Exemple d'analyse

Nous allons appliquer la démarche à un exemple qui nous permettra de
mieux expliquer chacune des étapes. Considérons le circuit de la
figure [682](#orge817236).

![img](Sources_images_logiques/images/exemple_seq1.svg "Circuit séquentiel synchrone à analyser")

1.  Identification des éléments fonctionnels:
    1.  Il y a une seule entrée externe $I$
    2.  Il y a deux éléments de mémoire, étiquetés $Z_0^n$ et  $Z_1^n$
    3.  On a un décodeur de prochain état pour deux bascules D
    4.  Il y a deux sorties externes: $S$ et $U$
    5.  Il y a un décodeur de sortie

2.  Expressions logiques pour le décodeur de prochain état:

$$ Z_0^{n+1} = I \cdot (Z_1^n)^\prime  + I \cdot Z_0^n $$

$$ Z_1^{n+1} = I \cdot Z_1^n +  Z_0^n  $$

1.  Expressions logiques des sorties externes:

$$ S =  Z_0^n \cdot (Z_1^{n})^\prime $$

$$ U =  Z_0^n \cdot Z_1^{n} $$

1.  Tableau d'excitation: chaque ligne du tableau d'excitation (tableau [49](#orgd46a7b9)) montre, à gauche,

un état présent (identifiable par les valeurs des bascules) et une
combinaison de valeurs d'entrée, et à droite, le prochain état et les
valeurs de sortie produites.

<table id="orgd46a7b9" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 40 :</span> Tableau d'excitation pour l'exemple</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(Z_1^n\)</th>
<th scope="col" class="org-right">\(Z_0^n\)</th>
<th scope="col" class="org-right">\(I\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(Z_1^{n+1}\)</th>
<th scope="col" class="org-right">\(Z_0^{n+1}\)</th>
<th scope="col" class="org-right">\(S\)</th>
<th scope="col" class="org-right">\(U\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

1.  Diagramme d'état: le diagramme d'état représente de façon schématique le comportement du

circuit séquentiel. Les cercles correspondent aux différents états
dans lesquels le système peut se trouver. On peut utiliser des
étiquettes à l'intérieur des cercles pour nommer les états. On peut
aussi y indiquer les numéros d'état (soit en vecteurs de bits, soit
avec des nombres binaires comme ici sur la figure). Les sorties
produites par le système sont aussi indiquées dans les cercles.  Les
transitions entre les états sont indiquées par des flèches. Une flèche
qui revient vers le même cercle signifie que l'état ne change pas.

Les conditions appliquées aux entrées pour déclencher les transitions
sont indiquées sur les flèches. Dans la figure, on voit aussi l'état
initial, identifié par une flèche partant d'un gros point noir.

Le diagramme d'état se construit aisément à partir du tableau
d'excitation.

![img](Sources_images_logiques/images/exemple_seq1_fsm.svg "Diagramme d'état")

1.  Interprétation du comportement du circuit séquentiel: le système est initialement à l'état *a*. Tant que l'entrée $I$ est 0,

il demeure dans cet état. Lorsque $I=1$, on passe à l'état *b*. Si
$I$ reste à 1, on passe à l'état *d* et on boucle sur l'état *d*. Si
$I$ revient à 0, de l'état *b* ou *d*, on passe à l'état *c*. De l'état *c*,
si $I = 1$, on reste dans l'état *c*. Sinon ($I = 0$), on retourne à
l'état *a*.

La figure [705](#org2dde65b) montre une trace des formes d'onde
observées en fonctionnement pour le système. Dans cet exemple, le
système boucle d'abord sur l'état *a* (valeur 0 sur la trace), puis
passe à l'état *b* (valeur 1) et ensuite à l'état *d* (valeur 3),
boucle sur l'état *d* et passe ensuite à l'état *c* (valeur 2) pour
finalement revenir à l'état *a*.

![img](Sources_images_logiques/images/exemple_seq1_run.svg "Exemple de fonctionnement")


## Analyse pour des bascules JK

Pour analyser un circuit séquentiel utilisant des bascules JK, on
détermine d'abord les expressions $J_A$ et $K_A$, $J_B$ et
$K_B$, etc., pour chacune des bascules. On doit ensuite se référer
au tableau caractéristique pour ce type de bascule (tableau
[47](#orgbfc3e5c)) pour déterminer quelles seront les prochaines valeurs
de sortie pour chacune des bascules. L'exemple suivant illustre la
procédure.


### Exemple avec bascules JK

Considérons le circuit séquentiel de la figure [708](#org37df33d).

![img](Sources_images_logiques/images/seq_JK.svg "Exemple de circuit séquentiel avec des bascules JK")

À partir des expressions des entrées $J$ et $K$ suivantes:

$$ J_0 = (q_1^{n})^\prime $$

$$ K_0 = q_0^{n} \cdot (q_1^{n})^\prime $$

$$ J_1 = q_0^{n} $$

$$ K_1 = (q_0^{n})^\prime \cdot q_1^{n} $$

on peut remplir le tableau d'excitation (tableau [50](#orgc94fa1c)).

<table id="orgc94fa1c" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 41 :</span> Tableau d'excitation circuit séquentiel JK</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(q_1^{n+1}\)</th>
<th scope="col" class="org-right">\(q_0^n\)</th>
<th scope="col" class="org-right">\(J_0\)</th>
<th scope="col" class="org-right">\(K_0\)</th>
<th scope="col" class="org-right">\(J_1\)</th>
<th scope="col" class="org-right">\(K_1\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(q_1^{n+1}\)</th>
<th scope="col" class="org-right">\(q_0^{n+1}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

À partir du tableau d'excitation, on peut tracer le diagramme d'état
(figure [716](#org4ffc548)).

![img](Sources_images_logiques/images/seq_JKb_FSM.svg "Diagramme d'état du circuit séquentiel avec bascules JK")


## Modèles de machines séquentielles

On appelle les modèles abstraits de systèmes séquentiels des
**automates finis** ou des **machines à état fini** (en anglais, *Finite
State Machines* (FSM)).  On distingue deux modèles de circuits
séquentiels, selon la façon dont les sorties sont obtenues. Dans le
modèle de Mealy, les sorties dépendent à la fois des entrées et des
variables d'état présent (figure [718](#org92ac7ea)). Dans le modèle de Moore,
les sorties ne dépendent que des variables d'état présent (figure
[719](#org577161f)).

![img](Sources_images_logiques/images/mealy.png "Machine de Mealy")

![img](Sources_images_logiques/images/moore.png "Machine de Moore")


# Conception de circuits logiques séquentiels


## Objectifs

-   Concevoir un circuit logique séquentiel synchrone à partir
    d'une spécification fonctionnelle
-   Construire un diagramme d'état en fonction d'un besoin
-   Construire un tableau d'état en fonction d'un diagramme d'état
-   Réduire le nombre d'états nécessaires
-   Assigner des codes binaires aux états et choisir une approche
-   Concevoir un décodeur de prochain état et un décodeur de sortie


## Conception d'un circuit séquentiel synchrone

Concevoir un circuit logique séquentiel permet de répondre à un besoin
pratique qui ne peut pas être satisfait par un circuit combinatoire.
Le point de départ est une description, la plus précise possible, du
besoin à satisfaire: quelles doivent être la ou les entrées, sorties
ou conditions qui font passer d'un état au suivant, etc. Pour un
besoin donné, une multitude de solutions fonctionnellement
équivalentes sont possibles; ainsi, il faudra établir des critères ou
identifier des contraintes qui permettront d'orienter la conception et
le choix final d'une solution. Deux systèmes peuvent avoir un même
comportement vu de l'extérieur, mais comporter des nombres d'états
internes différents.

Des considérations pratiques nous amèneront souvent à vouloir réduire
le nombre d'états nécessaires, et à simplifier les différents circuits
combinatoires utilisés. Réduire le nombre de bascules utilisées ne se
traduit pas toujours par un système plus simple, car les décodeurs
d'état et de sortie peuvent alors s'en trouver plus complexes.


## Spécification fonctionnelle

Comme dans tout problème de conception, la formulation en mots de la
spécification du système est cruciale. Appliquer parfaitement une
procédure de conception en se basant sur une spécification erronée ne
peut pas conduire à un système adéquat.

Il faudra un bon bagage d'expérience et d'intuition au concepteur ou à
la conceptrice pour pouvoir interpréter une description informelle,
très souvent incomplète, ambiguë et imprécise, et la traduire
correctement en un design concret qui répond à un besoin
maladroitement exprimé. Il revient à cette personne de s'assurer que
ce qu'elle a compris correspond bien à ce qui était demandé.

La première question à poser est: *Que doit faire le système?*
Suivront d'autres questions, amenant à définir davantage de détails:
*Doit-il y avoir des entrées? Si oui, combien? Combien de sorties sont
nécessaires?* Le comportement du système pourra être essentiellement
caractérisé en répondant à la question: *Quelle doit être la séquence
des sorties, pour une certaine séquence d'entrées?* Mais comme les
séquences d'entrées peuvent être en nombre infini, il faudra
identifier des patrons qui permettront de résumer le comportement du
système.


## Diagramme d'état

Un diagramme d'état préliminaire est un bon point de départ pour
définir et étudier le comportement du système. On identifiera les
différents états par des lettres pour les distinguer sans faire
référence à des variables binaires associées à des éléments de
mémoire. Il s'agit dans un premier temps d'un diagramme préliminaire,
parce que le diagramme final qui sera implémenté sera potentiellement
différent.

À partir du diagramme d'état, il est possible de vérifier quelle
séquence de sortie correspond à une séquence d'entrée donnée, et ainsi
de valider le comportement.


## Tableau d'état

Un tableau d'état comporte une ligne par état présent et combinaison
d'entrées. Selon les combinaisons d'entrées possibles, on donne le
prochain état et les valeurs de sortie.


## Réduction du nombre d'états

Deux états sont équivalents si, pour chaque combinaison d'entrées, ils
produisent la même sortie et amènent le système dans le même état ou
dans un état équivalent. Considérons le diagramme d'état de la figure
[735](#org8aa651a) et le tableau d'état correspondant (tableau 
[52](#org745e7de)). On peut voir qu'il s'agit ici d'une machine de
Mealy, car les valeurs de sortie sont associées aux transitions.

![img](Sources_images_logiques/images/exemp_simplif_net.svg "Diagramme d'état avant réduction")

<table id="orgaba9723" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 42 :</span> Tableau d'état initial</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État présent</th>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-right">\(S\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">a</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">f</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">e</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">e</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">e</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

En inspectant les différents états, on voit que les états *c* et *f*
sont équivalents. En remplaçant l'état *f* par l'état *c*, on obtient
le nouveau tableau d'état (tableau [52](#org745e7de)).

<table id="org745e7de" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 43 :</span> Tableau d'état après une simplification</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État présent</th>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-right">\(S\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">a</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">e</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">e</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

On voit maintenant que les états *a* et *d* sont équivalents. En
remplaçant l'état *d* par l'état *a*, on obtient le tableau d'état
simplifié (tableau [53](#org3df9d89)). Il n'y a plus de simplification
possible. Nous sommes passés de six états à quatre.

<table id="org3df9d89" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 44 :</span> Tableau d'état simplifié</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État présent</th>
<th scope="col" class="org-right">\(x\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-right">\(S\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">a</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">e</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">e</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Il faut bien s'assurer que le tableau d'état simplifié produit les
séquences de sortie désirées selon les séquences d'entrée appliquées.


### Tableau d'implication

La méthode du tableau d'implication facilite l'identification des
états redondants à éliminer. Considérons le tableau d'état suivant,
qui correspond cette fois-ci à une machine de Moore dont nous allons
réduire le nombre d'états.

<table id="orgf44390e" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 45 :</span> Tableau d'état (machine de Moore)</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État présent</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-right">\(S\)</th>
</tr>


<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(x=0\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(x=1\)</th>
<th scope="col" class="org-right">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-left">g</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-left">f</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">h</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-left">e</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">d</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-left">a</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-left">c</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-left">f</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">g</td>
<td class="org-left">a</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">h</td>
<td class="org-left">c</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">g</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Un tableau d'implication comporte une entrée pour chaque paire d'états
dans le tableau d'état. Avec $n$ états initialement (ici on a
$n=8$), on étiquettera les colonnes avec les $n-1$ premiers états,
et les lignes avec les $n-1$ derniers états. La première case vide,
en haut à gauche, sera notée [a;b] et la dernière en bas à droite sera
[g;h]. Voici le tableau avant d'être rempli (tableau
[55](#orgb3b380f)). Seules les cases qui ne comportent pas de \_
peuvent être remplies. Il n'y a par exemple rien d'utile à mettre dans
une case étiquetée [b;b], et on mettra l'information qui irait dans la
case [c;b] dans la case [b;c].

<table id="orgb3b380f" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 46 :</span> Tableau d'implication</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">b</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">c</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">d</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">e</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">f</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">g</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">h</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-left">b</td>
<td class="org-left">c</td>
<td class="org-left">d</td>
<td class="org-left">e</td>
<td class="org-left">f</td>
<td class="org-left">g</td>
</tr>
</tbody>
</table>

1.  On applique la procédure en considérant chaque case du tableau, ce
    qui permet de comparer chaque paire de lignes du tableau d'état.
    -   On vérifie dans un premier temps si les sorties sont
        différentes. Si c'est le cas, on met un &check; dans la
        case. Par exemple ici, *a* et *c*, *a* et *e*, *a* et *f*, *a* et
        *h* ont des sorties différentes, donc on place des &check;
        dans les cases [a;c], [a;e], [a;f] et [a;h].
    -   Si les sorties sont les mêmes, on place dans la case les paires
        d'états qu'une équivalence nécessiterait. Par exemple, pour la
        case [a;b], une équivalence entre *a* et *b* nécessiterait les
        équivalences g=f et c=h entre les états prochains. Pour la case
        [a;d], une équivalence entre *a* et *d* nécessiterait les
        équivalences g=a et c=c. Cette dernière, évidente, n'est pas
        inscrite dans le tableau. Pour [b;d], on trouve f=a et h=c.
    -   Si les sorties sont les mêmes et les paires d'états suivants sont
        identiques ou encore sont les états mêmes qu'on est en train de
        considérer, on met directement OUI dans le tableau. Par exemple,
        pour la case [a;g], on a les paires g=a et c=c, donc on met
        OUI. Pour la case [d;g], on a a=a et c=c, on met OUI
        également. On continue ainsi, de colonne en colonne, pour obtenir
        après ces étapes le résultat suivant (tableau [56](#org49e76e9)).

<table id="org49e76e9" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 47 :</span> Tableau d'implication, après étape 1</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">b</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">g=f c=h</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">c</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">d</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">g=a</th>
<th scope="col" class="org-left">f=a h=c</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">e</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">d=a</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">f</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">e=f d=b</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">c=f a=b</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">g</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">OUI</th>
<th scope="col" class="org-left">f=a h=c</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">OUI</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">h</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">e=c d=g</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">a=g</th>
<th scope="col" class="org-left">f=c b=g</th>
<th scope="col" class="org-left">&check;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-left">b</td>
<td class="org-left">c</td>
<td class="org-left">d</td>
<td class="org-left">e</td>
<td class="org-left">f</td>
<td class="org-left">g</td>
</tr>
</tbody>
</table>

2.  L'étape suivante consiste à considérer chaque case qui comporte
    une ou des paires d'états impliqués. On regarde la case
    correspondant à chaque paire, et s'il y a un &check; dans la
    case, alors l'implication ne fonctionne pas. Par exemple, la case
    [a;b] repose sur les équivalences g=f et c=h. Or si on regarde la
    case [f;g], on voit qu'il s'y trouve un &check;, ce qui veut
    dire que *f* et *g* ne peuvent pas être équivalents, ce qui
    implique que *a* et *b* ne pourront pas être équivalents. Ce n'est
    pas la peine de regarder la case [c;h].  On remplacera donc les
    paires de la case [a;b] par un &check;&check;, pour faire
    ressortir ces nouveaux échecs.
3.  Un &check;&check; dans le tableau peut faire échouer d'autres
    implications. Il faut donc revoir les cases avec des paires d'états
    impliqués pour voir s'il faut changer leur statut. On continue à
    revoir ainsi jusqu'à ce qu'il n'y ait plus d'ajouts de
    &check;&check;. On obtient finalement le tableau suivant
    (tableau [57](#orgc14cfe8)).

<table id="orgc14cfe8" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 48 :</span> Tableau d'implication, après étape 3</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">b</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">c</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">d</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">g=a</th>
<th scope="col" class="org-left">&check;&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">e</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">d=a</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">f</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;&check;</th>
<th scope="col" class="org-left">_</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">g</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">OUI</th>
<th scope="col" class="org-left">&check;&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">OUI</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">_</th>
</tr>


<tr>
<th scope="col" class="org-left">h</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">e=c d=g</th>
<th scope="col" class="org-left">&check;</th>
<th scope="col" class="org-left">a=g</th>
<th scope="col" class="org-left">&check;&check;</th>
<th scope="col" class="org-left">&check;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-left">b</td>
<td class="org-left">c</td>
<td class="org-left">d</td>
<td class="org-left">e</td>
<td class="org-left">f</td>
<td class="org-left">g</td>
</tr>
</tbody>
</table>

4.  Après cette étape, toutes les  cases qui contiennent OUI ou des
    paires d'implications indiquent des équivalences d'états. Ici, on a
    les équivalences suivantes: a=d, a=g, c=e, c=h, d=g, e=h. Les états
    uniques résultants sont *a*, *b*, *c* et *f*. On obtient le tableau
    d'état réduit suivant (tableau [58](#org6bd906a)).

<table id="org6bd906a" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 49 :</span> Tableau d'état réduit (machine de Moore)</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État présent</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-right">\(S\)</th>
</tr>


<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(x=0\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(x=1\)</th>
<th scope="col" class="org-right">&#xa0;</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-left">a</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-left">f</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">c</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-left">c</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">a</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-left">f</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>


## Codage des états

Une fois que le nombre d'états a été réduit, il faut assigner des
codes binaires aux états. Si on doit coder $m$ états, il faudra
$n$ bits, avec $2^n \geq m$. Si le nombre de combinaisons
binaires est plus grand que le nombre d'états nécessaires, les
combinaisons inutilisées seront considérées comme des cas facultatifs.

Le choix d'une assignation des codes aux états aura des répercussions
sur la complexité du décodeur de prochain état et sur le décodeur de
sortie. Plusieurs options peuvent être envisagées: assigner des codes
dans l'ordre naturel d'énumération binaire, assigner selon un code
Gray, ou encore choisir une assignation où il y a un seul bit 1 par
code binaire (approche dite *one-hot*). L'approche *one-hot* requiert
plus de bascules, mais permet souvent de simplifier les décodeurs de
prochain état et de sortie. Le tableau [59](#org2a584cd) montre
un exemple possible d'assignation pour chacune de ces approches.

<table id="org2a584cd" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 50 :</span> Possibilités d'assignation de codes d'états</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État</th>
<th scope="col" class="org-right">Binaire</th>
<th scope="col" class="org-right">Gray</th>
<th scope="col" class="org-right"><i>One-hot</i></th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-right">00</td>
<td class="org-right">00</td>
<td class="org-right">0001</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">01</td>
<td class="org-right">01</td>
<td class="org-right">0010</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">10</td>
<td class="org-right">11</td>
<td class="org-right">0100</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">11</td>
<td class="org-right">10</td>
<td class="org-right">1000</td>
</tr>
</tbody>
</table>


## Décodeur d'état

Après avoir décidé d'une assignation, on refait le tableau d'état
simplifié en remplaçant les étiquettes d'états symboliques par les
codes binaires correspondants. On obtient ainsi un **tableau de
transition**, qui permet d'élaborer les expressions logiques pour le
décodeur de prochain état. Le type de bascules à utiliser déterminera
les sorties nécessaires pour le décodeur d'état, en se basant sur les
tableaux caractéristiques de la section [7.6.6](#org5925d7e).


## Décodeur de sortie

Une fois que le codage d'état est établi, la conception du décodeur de
sortie est directe. Un tableau de vérité avec comme entrées les
valeurs binaires d'états et comme sorties les valeurs de sorties
externes permet de déterminer les fonctions combinatoires à
implémenter.


## Procédure de conception

La conception d'un circuit séquentiel suit une procédure bien
définie. Étant donnée la complexité de cette tâche, on limite la
conception manuelle à des circuits relativement petits. Pour des
besoins plus ambitieux, des outils de synthèse automatisés ont été
développés. Ces procédures automatisées supposent typiquement des
bascules D, car la correspondance entre l'entrée et la prochaine
sortie est directe. Voici les étapes à suivre:

1.  À partir de la description et des spécifications du comportement
    souhaité, concevoir un diagramme d'état
2.  Réduire le nombre d'états (si pertinent)
3.  Assigner des codes binaires aux états
4.  Remplir le tableau de transition
5.  Sélectionner un type de bascules à utiliser
6.  Déterminer les expressions simplifiées pour le décodeur de prochain
    état et le décodeur de sortie
7.  Tracer le schéma logique du circuit


## Exemple de conception

On doit concevoir un circuit séquentiel qui détecte la séquence
binaire 101 lorsqu'elle apparaît dans sa séquence d'entrée. Une fois
la séquence identifiée, le système produira une sortie 1 et demeurera
dans le même état en continuant de produire une sortie 1, jusqu'à une
remise à zéro.


### Bascules D

1.  Diagramme d'état

    Selon le diagramme d'état de la figure [762](#orgaab4fc0), le
    système démarre dans l'état *a* et demeure dans cet état tant que
    l'entrée $A=0$. Lorsque $A=1$, on passe à l'état *b*, début de la
    reconnaissance du patron 101. Ensuite, si $A=1$, on reste dans
    l'état *b* parce que ce pourrait être le début d'une autre
    séquence 101. De l'état *b*, si $A=0$, on passe à l'état *c*, car on
    a observé 10 en séquence. De l'état *c*, si on a $A=0$, la séquence
    observée est maintenant de 100 et on doit tout recommencer en
    retournant à l'état *a*.  De l'état *c*, si on a $A=1$, alors on a
    reconnu la séquence 101. On met la sortie $S=1$ et on reste dans cet
    état pour toutes les autres transitions, quelle que soit l'entrée. Il
    s'agit ici d'une machine de Moore, puisque la sortie $S=1$ est
    produite lorsqu'on est dans l'état *d*; on a $S=0$ dans les autres
    états.
    
    ![img](Sources_images_logiques/images/seq_101_sanscode.svg "Diagramme d'état pour détecter la séquence 101")

2.  Réduction d'états

    Il n'y a pas de réduction d'états possible ici.

3.  Assigner des codes binaires aux états

    Pour quatre états, il nous faudra deux bascules.  Le tableau
       [60](#orgfec0bbb) présente l'assignation d'états choisie.
    
    <table id="orgfec0bbb" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    <caption class="t-above"><span class="table-number">Tableau 51 :</span> Tableau d'assignation d'état</caption>
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-right" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-left">État</th>
    <th scope="col" class="org-right">Code</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-left">a</td>
    <td class="org-right">00</td>
    </tr>
    
    
    <tr>
    <td class="org-left">b</td>
    <td class="org-right">01</td>
    </tr>
    
    
    <tr>
    <td class="org-left">c</td>
    <td class="org-right">10</td>
    </tr>
    
    
    <tr>
    <td class="org-left">d</td>
    <td class="org-right">11</td>
    </tr>
    </tbody>
    </table>

4.  Remplir le tableau de transition

    Le tableau [61](#orgd358f36) donne les transitions d'états. 
    
    <table id="orgd358f36" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    <caption class="t-above"><span class="table-number">Tableau 52 :</span> Tableau de transition d'états</caption>
    
    <colgroup>
    <col  class="org-right" />
    
    <col  class="org-right" />
    
    <col  class="org-right" />
    
    <col  class="org-left" />
    
    <col  class="org-right" />
    
    <col  class="org-right" />
    
    <col  class="org-right" />
    </colgroup>
    <thead>
    <tr>
    <th scope="col" class="org-right">\(Z_1^n\)</th>
    <th scope="col" class="org-right">\(Z_0^n\)</th>
    <th scope="col" class="org-right">\(A\)</th>
    <th scope="col" class="org-left">&#xa0;</th>
    <th scope="col" class="org-right">\(Z_1^{n+1}\)</th>
    <th scope="col" class="org-right">\(Z_0^{n+1}\)</th>
    <th scope="col" class="org-right">\(S\)</th>
    </tr>
    </thead>
    
    <tbody>
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-right">0</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    </tr>
    
    
    <tr>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-left">&#xa0;</td>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    <td class="org-right">1</td>
    </tr>
    </tbody>
    </table>

5.  Sélectionner un type de bascules à utiliser

    On choisit des bascules D. 

6.  Déterminer les expressions simplifiées

    Les diagrammes de Karnaugh correspondants sont donnés pour
    $Z_0^{n+1}$ (figure [769](#org949fa37)), $Z_1^{n+1}$ (figure
    [770](#orgc7df451)) et $S$ (figure [771](#org1442ba6)).  
    
    Notons que la convention d'étiquetage des diagrammes est différente de
    ce que nous avons vu précédemment.  Au lieu d'étiqueter les lignes et
    les colonnes avec bits de minterms, on indique ici à l'extérieur du
    diagramme proprement dit les variables (telles quelles ou
    complémentées) et les régions du diagramme où on les retrouve. Par
    exemple, en dessous du diagramme de la figure [769](#org949fa37), on
    indique à partir de la gauche, une première région où la variable
    $A$ est complémentée (première colonne à gauche), puis une région
    correspondant à deux colonnes où la variable est telle quelle (deux
    colonnes du centre), et enfin une région où la variable est
    complémentée (colonne du centre).
    
    ![img](Sources_images_logiques/images/diag-k_z0.png "Diag-K pour $Z_0^{n+1}$")
    
    ![img](Sources_images_logiques/images/diag-k_z1.png "Diag-K pour $Z_1^{n+1}$")
    
    ![img](Sources_images_logiques/images/diag-k_S.png "Diag-K pour $S$")
    
    1.  Décodeur de prochain état
    
        Les expressions pour le décodeur de prochain état sont:
        
        $$ Z_1^{n+1} = (A^\prime \cdot Z_0^{n}) + (A \cdot  Z_1^{n}) $$
        
        $$ Z_0^{n+1} = A + (Z_0^{n} \cdot Z_1^{n}) $$
    
    2.  Décodeur de sortie
    
        L'expression pour le décodeur de sortie est:
        
        $$ S = Z_0^{n} \cdot Z_1^{n} $$

7.  Tracer le schéma logique du circuit

    Le circuit obtenu est représenté sur la figure
    [778](#orgb88cc61). On montre sur la figure
    [779](#orgeddd2c2) une trace d'exécution. Les premiers coups
    d'horloge, l'entrée $A=0$ et le système demeure dans l'état 0. Puis,
    lorsque $A=1$, on passe à l'état 1. Comme $A$ reste à 1, on
    demeure dans l'état 1 un certain temps. Puis, lorsque $A=0$, on
    passe à l'état 2. Avec $A=1$ de nouveau, on passe à l'état 3 en
    activant la sortie $S=1$. On ne quittera plus cet état par la
    suite. Une deuxième trace d'exécution (figure [780](#orga468eb9)
    ) montre un cas où le système retourne à l'état 0 après avoir reçu une
    séquence 100.
    
    ![img](Sources_images_logiques/images/exemp_seq101_circ.svg "Détecteur pour la séquence 101")
    
    ![img](Sources_images_logiques/images/exemp_seq101_trace1.svg "Trace d'exécution avec succès")
    
    ![img](Sources_images_logiques/images/exemp_seq101_trace2.svg "Trace d'exécution sans succès")


### Autres types de bascules

Les fonctions du décodeur de prochain état se formulent naturellement
en fonction de bascules D.  Pour faire l'implémentation avec des
bascules JK ou T, il faut pouvoir déterminer les entrées nécessaires
pour amener les changements d'état requis. Pour ce faire, on
utilisera des **tableaux d'excitation** qui listent les combinaisons
d'entrées pour passer d'un état présent $Q_n$ à un état prochain
$Q_{n+1}$. Le tableau d'excitation pour une bascule JK est donné
dans le tableau [62](#org52f58cf) et celui pour une bascule T est donné
dans le tableau [63](#org2dc5507).

<table id="org52f58cf" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 53 :</span> Tableau d'excitation, bascule JK</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(Q_n\)</th>
<th scope="col" class="org-right">\(Q_{n+1}\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(J\)</th>
<th scope="col" class="org-left">\(K\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">0</td>
<td class="org-left">X</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">1</td>
<td class="org-left">X</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">X</td>
<td class="org-left">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">X</td>
<td class="org-left">0</td>
</tr>
</tbody>
</table>

<table id="org2dc5507" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 54 :</span> Tableau d'excitation, bascule T</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(Q_n\)</th>
<th scope="col" class="org-right">\(Q_{n+1}\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(T\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

Reprenons le tableau de transition d'états pour notre exemple, tableau
[61](#orgd358f36), en ajoutant les signaux à générer pour des
bascules JK. On obtient alors le tableau [64](#org4d87612).

<table id="org4d87612" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 55 :</span> Tableau de transition d'états, avec bascules JK</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(Z_1^n\)</th>
<th scope="col" class="org-right">\(Z_0^n\)</th>
<th scope="col" class="org-right">\(A\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(Z_1^{n+1}\)</th>
<th scope="col" class="org-left">\(J\)</th>
<th scope="col" class="org-left">\(K\)</th>
<th scope="col" class="org-right">\(Z_0^{n+1}\)</th>
<th scope="col" class="org-left">\(J\)</th>
<th scope="col" class="org-left">\(K\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">0</td>
<td class="org-left">X</td>
<td class="org-right">0</td>
<td class="org-left">0</td>
<td class="org-left">X</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">0</td>
<td class="org-left">X</td>
<td class="org-right">1</td>
<td class="org-left">1</td>
<td class="org-left">X</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-left">1</td>
<td class="org-left">X</td>
<td class="org-right">0</td>
<td class="org-left">X</td>
<td class="org-left">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">0</td>
<td class="org-left">X</td>
<td class="org-right">1</td>
<td class="org-left">X</td>
<td class="org-left">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-left">X</td>
<td class="org-left">1</td>
<td class="org-right">0</td>
<td class="org-left">0</td>
<td class="org-left">X</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-left">X</td>
<td class="org-left">0</td>
<td class="org-right">1</td>
<td class="org-left">1</td>
<td class="org-left">X</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-left">X</td>
<td class="org-left">0</td>
<td class="org-right">1</td>
<td class="org-left">x</td>
<td class="org-left">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-left">X</td>
<td class="org-left">0</td>
<td class="org-right">1</td>
<td class="org-left">x</td>
<td class="org-left">0</td>
</tr>
</tbody>
</table>

On trouve les expressions simplifiées suivantes:

$$ J_{Z_1} = A^\prime \cdot Z_0^n $$

$$ K_{Z_1} = A^\prime \cdot (Z_0^n)^\prime $$

$$ J_{Z_0} = A $$ 

$$ K_{Z_0} = (A + Z_1^n)^\prime $$

Ce qui nous donne l'implémentation de la figure [789](#org4017f52).

![img](Sources_images_logiques/images/exemp_seq101_JK.svg "Détecteur pour la séquence 101, bascules JK")


## États interdits

Lorsque le nombre d'états nécessaires pour le fonctionnement de
l'automate fini est strictement inférieur au nombre total d'états
possibles avec les bascules utilisées, un certain nombre d'états
(physiques) ne seront pas utilisés dans le fonctionnement normal du
circuit séquentiel. On parlera alors d'**états interdits**.  Lors de la
formulation des tableaux de vérité pour le décodeur de prochain état,
ces états donneront lieu à des cas facultatifs, qui pourront permettre
la simplification du circuit combinatoire du décodeur.

Il faut toutefois se méfier de scénarios dans lesquels l'automate fini
pourrait se retrouver dans un tel état interdit en raison d'un
dysfonctionnement momentané ou lors de la mise en marche du
système. Considérons par exemple un circuit séquentiel dont le
diagramme d'état (tel qu'implémenté après conception) est illustré
ci-dessous (figure [792](#org3592a43)). En fonctionnement normal, le
système évolue entre les états *a*, *b* et *c*. Mais si pour une
raison quelconque, le système entre dans l'état *d*, il restera coincé
en bouclant sur cet état pour toujours (ou peut-être jusqu'à un
prochain dysfonctionnement).

![img](Sources_images_logiques/images/etat_interdit.svg "Diagramme d'état avec état interdit")

Une solution serait de modifier le décodeur de prochain état pour
s'assurer que, de l'état interdit, on revient toujours vers un état
normal, comme on peut le voir sur la figure suivante (figure
[794](#org362512e)), où de l'état *d*, on reviendra toujours
vers l'état *c*. 

![img](Sources_images_logiques/images/etat_interdit_revient.svg "Diagramme d'état qui assure le retour en fonctionnement normal")


## Exemple avec états *one-hot*

Dans l'exemple suivant, on explore l'assignation d'états *one-hot*
dans laquelle il n'y a qu'un bit 1 par code binaire.

Considérons le diagramme d'état suivant (figure [797](#org31d5cd6)).

![img](Sources_images_logiques/images/exemple_one-hot.svg "Diagramme d'état pour assignation *one-hot*")

Le tableau d'assignation d'état correspondant est donné dans le
tableau [65](#org9693241) ci-dessous.

<table id="org9693241" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 56 :</span> Assignation <i>one-hot</i></caption>

<colgroup>
<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État</th>
<th scope="col" class="org-right"><i>One-hot</i></th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-right">100</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">010</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">001</td>
</tr>
</tbody>
</table>

Chaque état aura sa propre bascule active, dont les sorties seront
dénotées $A$, $B$ et $C$. Le tableau de transition d'états qu'on
obtient comporte un grand nombre de cas facultatifs et d'états
inutilisés, que nous n'avons pas indiqués ici. Le tableau
[66](#org04991a9) ne montre que les six transitions spécifiées
dans le diagramme d'état.

<table id="org04991a9" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 57 :</span> Tableau de transition d'états <i>one-hot</i></caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(A^n\)</th>
<th scope="col" class="org-right">\(B^n\)</th>
<th scope="col" class="org-right">\(C^n\)</th>
<th scope="col" class="org-left">\(x\)</th>
<th scope="col" class="org-left">\(y\)</th>
<th scope="col" class="org-left">\(z\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(A^{n+1}\)</th>
<th scope="col" class="org-right">\(B^{n+1}\)</th>
<th scope="col" class="org-right">\(C^{n+1}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">0</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">1</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">X</td>
<td class="org-left">0</td>
<td class="org-left">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">X</td>
<td class="org-left">0</td>
<td class="org-left">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">X</td>
<td class="org-left">1</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">X</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Il est possible de formuler le décodeur de prochain état directement,
par inspection des transitions spécifiées.  Si on considère les
transitions qui entrent dans l'état *a*, il y a trois façons différentes
d'arriver en *a*:

-   à partir de *a*, sous la condition $x=0$
-   à partir de *b*, sous la condition $y=0, z=1$
-   à partir de *c*, sans conditions

L'équation de prochain état pour *a* sera ainsi 
$$
A^{n+1} = A^{n}x^\prime + B^n y^\prime z + C^n
$$

Le même raisonnement nous permet d'écrire pour les autres bascules:
$$
B^{n+1} = A^{n}x + B^n y^\prime z^\prime
$$
et 
$$
C^{n+1} = B^n y
$$

Le décodeur de prochain état est simplifié, car les bits d'état
offrent une indication directe de l'état dans lequel la machine se
trouve. Le fonctionnement de la machine entraîne peu de transitions,
ce qui se traduit par une consommation d'énergie réduite et moins de
risque d'aléas (*glitches*). La vitesse de commutation ne dépend pas du
nombre d'états. Il est possible d'ajouter ou retrancher un état sans avoir
à refaire entièrement la conception.  L'assignation *one-hot* est
particulièrement intéressante lorsqu'il y a moins de contraintes sur
le nombre de bascules que sur le nombre d'éléments combinatoires.

Le principal inconvénient de cette approche est la croissance du
nombre de bascules, qui est linéaire avec le nombre d'états plutôt que
logarithmique. Par exemple, pour 30 états, il faudra 30 bascules alors
qu'avec un encodage binaire, il n'en faudrait que cinq. Il faut aussi
considérer qu'il y a un grand nombre d'états interdits et prendre les
précautions qui s'imposent pour éviter les problèmes de fonctionnement
coincé.


# Circuit séquentiels: registres et compteurs


## Objectifs

-   Se familiariser avec les principaux circuits séquentiels classiques:
    registres, registres à décalage, compteurs
-   Savoir comment sont implémentées les différentes opérations:
    chargement, remise à zéro, comptage vers le haut/bas, décalage
-   Utiliser des compteurs pour générer des séquences de
    synchronisation
-   Faire la distinction entre compteur synchrone et compteur asynchrone


## Registres

Un registre est un groupe de bascules activées par un même signal
d'horloge. Chaque bascule permet de stocker un bit en
mémoire. Différentes configurations d'interconnexion entre les
bascules et éventuellement des composants combinatoires permettent de
concevoir des types de registres pouvant remplir des rôles variés.

La figure [814](#org949a323) montre un registre parallèle de quatre bits,
qui permet de stocker quatre valeurs binaires indépendantes. Le schéma
du bas est une représentation symbolique du registre, dans laquelle on
représente les entrées et sorties comme des vecteurs de quatre bits.

![img](Sources_images_logiques/images/regist_4.svg "Registre parallèle à quatre bits")


### Chargement parallèle

Si on veut concevoir un registre parallèle polyvalent, on doit le
munir de la possibilité de le charger à partir des entrées ou de
maintenir les valeurs déjà mémorisées. On ajoutera donc une entrée
*charge* au registre pour contrôler ces opérations.

Pour mettre en oeuvre ce chargement/maintien, il faut un peu de
réflexion. Il serait possible d'agir (à la façon d'un signal *enable*
via une porte ET, par exemple) sur l'entrée d'horloge des bascules pour
empêcher leur contenu d'être affecté par les entrées. Mais alors, on
briserait le principe de synchronisation qui veut que tous les
éléments d'un système soient commandés en même temps par une même
horloge.

La solution consiste à toujours mettre à jour le contenu des bascules: 

1.  Lorsque *charge* est inactif (fonction maintien), la sortie de
    chaque bascule, réacheminée à l'entrée, est sélectionnée pour
    récrire le même contenu.
2.  Lorsque *charge* est actif (fonction chargement), c'est l'entrée
    externe qui est sélectionnée pour écrire un nouveau contenu.

La sélection se fait au moyen d'un multiplexeur deux-vers-un à
l'entrée de chaque bascule. La figure [821](#orgffe4abb) montre le schéma
du registre chargeable.

![img](Sources_images_logiques/images/reg_4_paral.svg "Registre parallèle à quatre bits chargeable")


### Registres à décalage

Un registre à décalage consiste en une chaîne de bascules, la sortie
de l'une reliée à l'entrée de la suivante. La figure [823](#org49273e3) montre
un registre à décalage de quatre bits. À chaque coup d'horloge,
l'entrée est insérée dans la première bascule, à droite, et le contenu
du registre est décalé d'une position vers la gauche. La sortie
provient de la dernière bascule à droite.

![img](Sources_images_logiques/images/shift4.svg "Registre à décalage 4 bits")

En utilisant un multiplexeur quatre-vers-un pour sélectionner ce qui
sera inséré dans une bascule, il est possible de concevoir un registre
à décalage universel. Les différentes opérations sont le *maintien*, le
*décalage à droite* avec entrée $G$, le *décalage à gauche* avec entrée
$D$ et le *chargement parallèle*, avec les entrées $I_i, i=1, \ldots,
4$.

Les différentes opérations sont commandées par les deux signaux de
sélection, comme indiqué dans le tableau [67](#orgadd1d9a).

<table id="orgadd1d9a" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 58 :</span> Codes de sélection et opérations</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">Sél.</th>
<th scope="col" class="org-left">Action</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">00</td>
<td class="org-left">Maintien</td>
</tr>


<tr>
<td class="org-right">01</td>
<td class="org-left">Décalage à droite</td>
</tr>


<tr>
<td class="org-right">10</td>
<td class="org-left">Décalage à gauche</td>
</tr>


<tr>
<td class="org-right">11</td>
<td class="org-left">Chargement parallèle</td>
</tr>
</tbody>
</table>

![img](Sources_images_logiques/images/shift4_univ.svg "Registre à décalage universel") 

Les registres à décalage sont notamment utilisés pour convertir des
données parallèles en données sérielles et *vice versa*, des opérations
très utiles dans le contexte d'interfaces de communication. On peut
également s'en servir pour faire des multiplications ou divisions par
deux, comme on l'a vu à la section [1.8.1](#orga05f8d4).


## Compteurs

Un registre dont la séquence d'états est systématique est appelé un
**compteur**. Le comptage peut être contrôlé par une entrée spécifique
ou par l'entrée d'horloge. La séquence d'états est toujours la même
pour un type de compteur donné. Par exemple, les états d'un compteur
binaire à deux bits suivent la séquence $00 \rightarrow 01
\rightarrow 10 \rightarrow 11 \rightarrow 00 \ldots$ La sortie
correspond directement aux bits d'état. On distingue les compteurs
**asynchrones** et les compteurs **synchrones**. Quel que soit le type de
compteur, il y a toujours un retour vers l'état initial, car la
séquence d'états est un cycle.


### Compteur asynchrone

Dans un compteur binaire asynchrone, la sortie d'une bascule de poids
moins significatif est acheminée à l'entrée d'horloge de la bascule
suivante. C'est la transition de la sortie de la bascule de poids
moins significatif qui déclenche la bascule suivante. La figure
[830](#orgad74a2d) montre un compteur asynchrone construit à partir de
bascules T. La séquence de sortie est donnée dans le tableau
[68](#orga7b7603). On peut voir qu'après huit étapes, la séquence se
répète.

![img](Sources_images_logiques/images/rippleT3.svg "Compteur asynchrone")

<table id="orga7b7603" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 59 :</span> Séquence du compteur</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(A_2\)</th>
<th scope="col" class="org-right">\(A_1\)</th>
<th scope="col" class="org-right">\(A_0\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

Les compteurs asynchrones sont très simples, mais l'inconvénient est
que les transitions d'état ne sont pas synchrones. En particulier,
les bits d'état ne changent pas tous en même temps. Par exemple, si le
compteur passe de 0111 à 1000, la sortie peut passer par des états
intermédiaires parasites: 0111 $\rightarrow$ 0110 $\rightarrow$ 1100
$\rightarrow$ 1000.


### Compteur synchrone

Dans un compteur synchrone, toutes les bascules sont commandées par un
même signal d'horloge et les changements d'état sont
synchronisés. Les changements d'état sont contrôlés par les signaux
d'entrée appliqués aux bascules, comme dans le fonctionnement normal
d'un circuit séquentiel synchrone.

Le diagramme d'état d'un compteur trois bits (huit états) est un
cycle, comme on peut le voir sur la figure [834](#org4315aac). Le tableau
d'états correspondant est donné dans le tableau [69](#org5be6892).

![img](Sources_images_logiques/images/compt8_FSM.svg "Diagramme d'état d'un compteur")

<table id="org5be6892" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 60 :</span> Tableau d'état du compteur</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(Z_2^n\)</th>
<th scope="col" class="org-right">\(Z_1^n\)</th>
<th scope="col" class="org-right">\(Z_0^n\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(Z_2^{n+1}\)</th>
<th scope="col" class="org-right">\(Z_1^{n+1}\)</th>
<th scope="col" class="org-right">\(Z_0^{n+1}\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

Les expressions pour le décodeur de prochain état sont: 

$$  Z_2^{n+1} = Z_0^n \cdot Z_1^n \cdot (Z_2^{n})^\prime + (Z_0^{n})^\prime \cdot Z_2^n + (Z_1^{n})^\prime \cdot Z_2^n $$

$$  Z_1^{n+1} = Z_0^{n} \cdot (Z_1^{n})^\prime + (Z_0^{n})^\prime \cdot Z_1^n $$

$$  Z_0^{n+1} = (Z_0^{n})^\prime $$

Le schéma correspondant est donné à la figure [840](#org96419ba).

![img](Sources_images_logiques/images/compt8.svg "Schéma logique du compteur à 3 bits")

On peut ajouter aux compteurs des fonctions diverses: comptage vers le
haut, comptage vers le bas, préchargement parallèle, remise à zéro,
etc.

Le compteur de la figure [840](#org96419ba) a été conçu comme un circuit
séquentiel général, avec un décodeur de prochain état en forme *somme
de produits*. Il est également possible de concevoir un compteur
synchrone directement, sans passer par la méthodologie classique, en
suivant un raisonnement tout simple. La bascule du bit le moins
significatif $Z_0$ doit changer d'état à tous les coups
d'horloge. La bascule du bit suivant $Z_1$ doit changer d'état
seulement lorsque le bit précédent $Z_0$ vaut 1. La bascule du bit
suivant $Z_2$ doit changer d'état seulement lorsque les bits
précédents $Z_1, Z_0$ valent tous deux 1. Et on peut pousser le
raisonnement pour un compteur quelconque: 

> la bascule d'un bit $Z_i$
> doit changer d'état seulement lorsque les bits précédents
> $Z_{i-1},Z_{i-2},\ldots, Z_0$ valent tous 1.

Le compteur à quatre bits de la figure [845](#orge128976) a été conçu
selon cette approche, à partir de bascules JK.  L'utilisation d'une
porte ET par bascule permet de mettre en oeuvre les
conditions. L'entrée $E$ est un contrôle *enable* pour activer le
comptage. On a aussi prévu une sortie `Prochain` pour pouvoir
connecter en cascade d'autres compteurs.

![img](Sources_images_logiques/images/compt_4bits.svg "Schéma logique du compteur à 4 bits")

Si on réfléchit de la même façon pour le comptage vers le bas, on constate
que la règle devient:

> la bascule d'un bit $Z_i$ doit changer d'état
> seulement lorsque les bits précédents $Z_{i-1},Z_{i-2},\ldots, Z_0$
> valent tous 0.

Cette fois-ci, les conditions se baseront sur les sorties
complémentées des bascules précédentes.


### Compteur bidirectionnel

En combinant les deux conditions au moyen d'un multiplexeur
deux-vers-un, il est facile de concevoir un compteur haut/bas, comme
illustré sur la figure [850](#org9ef4724).

![img](Sources_images_logiques/images/compt_updown.svg "Schéma logique du compteur haut/bas à 4 bits")


### Compteur en anneau

Un compteur en anneau est un registre à décalage connecté en boucle où
une seule bascule est active à la fois. Il y a donc dans la sortie un
seul bit 1, qui se décale de façon cyclique: $0010 \rightarrow 0001
\rightarrow 1000 \rightarrow 0100 \rightarrow 0010, \ldots$ La
figure [853](#orgf00b600) illustre un compteur en anneau de quatre bits. Une
entrée `Init` permet d'injecter un bit 1 dans le registre au début. La
trace montre les formes d'onde obtenues.

On utilise fréquemment ce type de compteur pour générer des signaux de
synchronisation. En effet, chaque sortie devient active à son tour
dans le cycle, pendant une période d'horloge.

![img](Sources_images_logiques/images/ring4.svg "Compteur en anneau à 4 bits")


### Compteur Johnson

Un compteur Johnson permet de doubler le nombre d'états distincts par
rapport au compteur en anneau en injectant le complément du dernier
bit dans l'entrée du registre à décalage.  La figure [855](#org9c6c0ff)
illustre un compteur en anneau Johnson de quatre bits, de même que la
trace de fonctionnement. La séquence d'états est donnée dans le
tableau [70](#org71e7311).

![img](Sources_images_logiques/images/johnson4.svg "Compteur Johnson à 4 bits")

<table id="org71e7311" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 61 :</span> Séquence d'états du compteur Johnson</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">No</th>
<th scope="col" class="org-right">\(a\)</th>
<th scope="col" class="org-right">\(b\)</th>
<th scope="col" class="org-right">\(c\)</th>
<th scope="col" class="org-right">\(d\)</th>
<th scope="col" class="org-left">ET requis</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">\(a^\prime d^\prime\)</td>
</tr>


<tr>
<td class="org-right">2</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">\(a b^\prime\)</td>
</tr>


<tr>
<td class="org-right">3</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">\(b c^\prime\)</td>
</tr>


<tr>
<td class="org-right">4</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">\(c^\prime d^\prime\)</td>
</tr>


<tr>
<td class="org-right">5</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">\(a d^\prime\)</td>
</tr>


<tr>
<td class="org-right">6</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">\(a^\prime b\)</td>
</tr>


<tr>
<td class="org-right">7</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">\(b^\prime c\)</td>
</tr>


<tr>
<td class="org-right">8</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">\(c^\prime d\)</td>
</tr>
</tbody>
</table>

On peut construire des signaux de synchronisation distincts en
combinant deux par deux au moyen d'une porte ET des signaux de sortie
voisins (dans le cycle) ou leurs compléments. Le tableau [70](#org71e7311)
donne les paires de sorties à combiner pour ce faire avec le compteur
Johnson de quatre bits.

Nous avons appliqué ce principe à un compteur Johnson de deux bits,
présenté sur la figure [858](#org4e36bcf). La figure montre une trace
d'exécution avec les signaux de sortie. On y voit que chacun des
quatre signaux est activé à son tour.

![img](Sources_images_logiques/images/johnson2_quad_decode.svg "Compteur Johnson à 2 bits et circuit de décodage pour signaux de synchronisation")

Si on s'intéresse aux sorties des bascules de ce même compteur
Johnson, on peut voir sur la trace d'exécution de la figure
[860](#org34fbfe1) qu'on obtient des signaux en **quadrature**,
c'est-à-dire que les sorties sont déphasées de 90 degrés les unes par
rapport aux autres, comme le sont des fonctions $\sin(), \cos(),
-\sin(), -\cos()$.

![img](Sources_images_logiques/images/johnson2_quad.svg "Signaux en quadrature obtenus au moyen d'un compteur Johnson à 2 bits") 


### Diviseur de fréquence

Un compteur peut être utilisé pour diviser la fréquence d'un signal
périodique. Par exemple, la sortie d'un compteur à un bit change
d'état à tous les deux coups d'horloge, ce qui constitue une division
par deux de la fréquence d'horloge. Cette approche permet
naturellement des divisions par des puissances de deux.

On peut aussi utiliser un compteur Johnson, qui permettra alors, selon
le nombre d'étages du compteur, des divisions de fréquence par des
diviseurs, comme trois ou cinq, qui ne sont pas des puissances de deux.


### Compteur à chargement parallèle

Un compteur à chargement parallèle est illustré à la figure
[865](#org5a160b6). En activant l'entrée `Compte`, le comptage
se fait vers le haut. En activant l'entrée `Charge`, les entrées $
I_i, i=0, \ldots, 3$ sont insérées dans les bascules. Il y a aussi une
sortie `ov` qui indique lorsque le compteur atteint sa valeur
maximale. Cette sortie peut être utilisée pour activer un autre
compteur pour des bits de plus haut niveau.

La trace d'exécution de la figure [866](#orga70cff1)
montre le comptage de 4 jusqu'à 15 et retour à 0. On voit le signal
`ov` s'activer sur 15. 

![img](Sources_images_logiques/images/comptchargement.svg "Compteur à chargement parallèle")

![img](Sources_images_logiques/images/compt_chargement_tracecompte.svg "Trace d'exécution, de 0 à 15")

La trace de la figure suivante montre le compteur qui
passe de 0 à 5, puis un chargement parallèle de la valeur 12.

![img](Sources_images_logiques/images/compt_chargement_trace_charge.svg "Trace d'exécution, de 0 à 5 et chargement de 12")


### Compteur modulo

On peut réaliser aisément un compteur modulo dont le cycle est plus
court que le maximum possible, en utilisant un compteur avec
chargement parallèle.  Par exemple, pour réaliser un compteur qui
compte de 0 jusqu'à 12, il suffit de décoder au moyen d'une porte ET
l'état qui doit être le dernier du cycle, et d'utiliser le signal de
sortie obtenu pour charger la valeur 0 dans le compteur. On obtient
ainsi un compteur modulo-13, dont le cycle compte 13 états.  La figure
illustre le compteur modulo-13, de même qu'une trace d'exécution sur
laquelle on voit le passage de 12 à 0.

![img](Sources_images_logiques/images/compt_mod13.svg "Compteur modulo-13")

On pourrait aussi réaliser un compteur qui compte par exemple de 4 à
15, en utilisant cette fois la sortie `ov` pour activer le chargement
d'une valeur initiale 4.


# Mémoires


## Objectifs

-   Faire la distinction entre mémoire volatile et non-volatile
-   Faire la distinction entre mémoire volatile statique et dynamique
-   Connaître l'organisation typique d'une mémoire et le fonctionnement
    de l'adressage
-   Comprendre le fonctionnement d'un bus de données
-   Interpréter les cycles d'écriture et de lecture
-   Implémenter une fonction combinatoire arbitraire à l'aide d'une
    mémoire ROM
-   Utiliser un tableau de correspondance
-   Se familiariser avec les différents types de mémoires non-volatiles


## Mémoires

Une mémoire est utilisée pour stocker des valeurs binaires à plus ou
moins long terme. Généralement, l'information stockée dans la mémoire
sera lue et acheminée dans des registres pour être traitée par un
circuit logique de traitement. Les résultats du traitement seront
typiquement stockés de nouveau dans la mémoire. Constituée d'un grand
nombre de cellules permettant chacune de stocker un bit, la mémoire
est dotée de mécanismes permettant d'accéder aux cellules pour en
faire la lecture ou l'écriture.

On distingue les mémoires non volatiles (en anglais, *Read Only
Memories* (ROM)) et les mémoires volatiles (en anglais, *Random Access
Memories* (RAM)).


### Mémoires non-volatiles

Dans une mémoire ROM, les données sont stockées une fois pour
toutes. Elles y demeurent même après que la mémoire ait été mise hors
tension. Dans le cycle de vie des données, il y a donc **une** écriture
initiale, mais autant de lectures qu'on le souhaite. Il ne peut pas y
avoir de réécriture.

Une mémoire ROM est considérée comme un dispositif **programmable**,
dans le sens où le processus d'écriture initial demande une action
particulière, une procédure spécifique sur le plan matériel. Nous verrons
au chapitre [12](#orgd025945) d'autres dispositifs logiques
programmables. La programmation d'une ROM se fait en agissant sur des
connexions dites **fusibles**. Initialement, le fusible est comme un fil
qui permet au signal de passer. En le programmant, le fusible devient
un circuit ouvert qui ne laisse plus passer le signal.


### Mémoires volatiles

Une mémoire RAM stocke l'information de façon temporaire. En principe,
le contenu est conservé tant que la mémoire est maintenue sous
tension. Mais la réalité est un peu plus complexe, comme nous le verrons
plus loin.

L'opération d'**écriture** permet de stocker des valeurs et la
**lecture** permet d'extraire l'information de la mémoire.

Une mémoire RAM **statique** consiste en un ensemble de loquets qui
permettent de conserver des données binaires. L'information est
maintenue tant que la mémoire est alimentée. 

Les mémoires RAM **dynamiques** stockent l'information sous la forme
d'une charge capacitive au sein des transistors du circuit
intégré. Comme cette charge se disperse au fil du temps, la mémoire
doit être rafraîchie régulièrement, en y récrivant périodiquement à
très court intervalle (millisecondes) la même valeur qui est déjà
stockée.

Les mémoires dynamiques consomment beaucoup moins que les mémoires
statiques et offrent des capacités de stockage largement supérieures,
car une cellule de mémoire comporte beaucoup moins d'éléments
(essentiellement un transistor par cellule). En contrepartie, les
temps d'accès aux mémoires statiques sont nettement meilleurs et on
n'a pas à se préoccuper de rafraîchissement.


## Adressage

Les cellules des mémoires sont organisées en petits groupes appelés
**mots**, de façon à ce que l'on puisse accéder à chaque groupe
indépendamment. Toutes les cellules d'un mot sont lues ou écrites
ensemble.

Cet accès individuel aux mots, appelé **adressage**, est une
caractéristique de flexibilité essentielle. Le temps d'accès aux
données est le même, quel que soit l'endroit dans la mémoire où un mot
en particulier est stocké. Les mots sont généralement constitués d'un
nombre de bits multiple de huit: 8, 16 ou 32 bits sont des tailles de
mot courantes. Un groupe de huit bits est appelé **octet**.

L'adressage se fait au moyen d'un **décodeur d'adresses**, qui est
simplement un décodeur binaire tel que nous l'avons vu à la section
[6.9](#orgf1cfdd4). Le nombre de bits d'adresse détermine la capacité (en nombre
de mots) de la mémoire: pour $k$ adresses, on aura $2^k$ mots
distincts. Les tailles de mémoire sont souvent exprimées au moyen de
multiplicateurs: K (kilo) correspondant à $2^{10}$, M (méga)
correspondant à $2^{20}$ ou G (giga) correspondant à $2^{30}$.

![img](Sources_images_logiques/images/memoire.png "Schéma d'une mémoire")


### Lecture et écriture

L'opération choisie, écriture ou lecture, est commandée par une ou des
entrées à cet effet. L'accès à un espace mémoire (un mot) se fait
selon une séquence bien précise. Pour une écriture:

1.  Les bits d'adresse du mot sont appliqués aux lignes d'adresse.
2.  Les données à écrire sont appliquées aux lignes d'entrée.
3.  On active l'entrée de commande `Écriture`.

Les données de l'entrée sont alors stockées dans la case mémoire adressée.

Pour une lecture:

1.  Les bits d'adresse du mot sont appliqués aux lignes d'adresse.
2.  On active l'entrée de commande `Lecture`.

Les données présentes dans la case mémoire adressée sont ensuite
disponibles à la sortie de la mémoire.

Les mémoires offertes sur le marché optent souvent pour une
combinaison des signaux de contrôle, avec un seul signal qui détermine
le sens de l'action, comme le montre le tableau
[71](#org1d5fe28). Le signal `Enable`, parfois appelé `Chip
select`, permet d'activer une mémoire dans un ensemble où plusieurs
mémoires sont utilisées.

<table id="org1d5fe28" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 62 :</span> Signaux de contrôle d'une mémoire</caption>

<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right"><code>Enable</code></th>
<th scope="col" class="org-right"><code>Lecture/écriture</code></th>
<th scope="col" class="org-left">Action</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">X</td>
<td class="org-left">Aucune</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">Écriture</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">Lecture</td>
</tr>
</tbody>
</table>


### Bus de données

Pour acheminer les données lues ou à écrire dans la mémoire, on
utilise des tampons émetteurs-récepteurs de bus (voir section [6.14](#org47179c9)), organisés en vecteur, pour créer un
**bus de données** qui permet un aller-retour des données, selon le sens
de l'action. Cela permet de diminuer de moitié le nombre de connexions
nécessaires pour l'échange des données.  Un signal dérivé des signaux
`Lecture/écriture` et `Chip select (CS)` est typiquement utilisé pour
commander l'entrée de contrôle (voir figure [904](#orge7c4a78)).

![img](Sources_images_logiques/images/bus_trans8.svg "Bus de données, 8 bits")


### Chronogrammes

La figure [906](#orge1d5ebc) présente un chronogramme qui décrit
l'opération d'écriture dans une mémoire RAM. Les valeurs d'adresse
sont d'abord présentées aux entrées d'adressage.  Le signal `L/not E`
est amené au niveau bas, en même temps que le signal `CS` est activé
(au niveau bas). Après un court délai, les données sont mises sur le
bus de données et seront écrites dans la mémoire. On peut voir que les
lignes du bus de données sont en mode **haute impédance** lorsque le bus
est inactif (situation représentée symboliquement sur l'illustration
par un signal situé entre les niveaux 0 et 1).

![img](Sources_images_logiques/images/chron_ram_ecriture.svg "Mémoire RAM, chronogramme pour l'écriture")

La figure [908](#org9be5476) présente un chronogramme qui décrit
l'opération de lecture d'une mémoire RAM. Les valeurs d'adresses sont
d'abord présentée aux entrées d'adressage.  Le signal `L/not E` est
maintenu au niveau élevé en même temps que le signal `CS` est activé
(au niveau bas). Après un court délai, les données sont disponibles sur
le bus de données.

![img](Sources_images_logiques/images/chron_ram_lecture.svg "Mémoire RAM, chronogramme pour la lecture")

La cellule de base d'une mémoire RAM qui permet de stocker un bit est
illustrée à la figure [910](#org607cd02). Elle est construite autour d'un
loquet SR et de portes logiques pour le contrôle. Une mémoire complète
de $m$ mots de taille $n$ bits sera constituée d'une matrice de
format $m \times n$ de telles cellules, avec un décodeur d'adresse
pour sélectionner quel mot sera affecté par l'opération choisie.

![img](Sources_images_logiques/images/cell_ram.svg "Cellule mémoire RAM")


## Mémoires mortes

Dans son mode d'utilisation normal, une mémoire morte peut seulement
être lue. Il n'est donc pas nécessaire de préciser l'opération qui
sera effectuée. Il y aura donc des entrées pour les adresses et un
signal de contrôle de type `CS`.

La figure [914](#org92e3efd) montre l'essentiel d'une mémoire ROM de
16 mots de 4 bits. Un décodeur d'adresse permet de sélectionner quel
mot sera lu, et la sortie est disponible sur les lignes $A_3, \ldots,
A_0$. 

Pour simplifier la représentation de ce genre de configuration, on
utilise une schématisation symbolique compacte pour les portes OU de
sortie, dans laquelle chacune des 16 lignes horizontales représente en
fait 16 entrées d'une porte OU. La présence d'une croix à
l'intersection d'une ligne horizontale et d'une ligne verticale
signifie que le signal de la ligne horizontale est connecté à une des
entrées de la porte.  Avec cette schématisation, on peut voir que les
deux premiers mots stockés dans la mémoire illustrée dans l'exemple
seraient 0101 et 1101. La même schématisation compacte s'emploie aussi
pour des portes ET.

![img](Sources_images_logiques/images/proto_rom1_prog.svg "Modèle d'une mémoire ROM")

Cette mémoire relativement petite comporte ainsi 64 intersections
programmables, permettant de définir la valeur des 16 mots de mémoire
de 8 bits chacun.


### Implémentation de fonctions combinatoires

Comme on l'a vu dans la section [6.9](#orgf1cfdd4), un décodeur permet de
générer les $2^k$ minterms possibles avec ses $k$
entrées. Regrouper avec une porte OU les minterms d'une
fonction permet d'implémenter cette fonction. Une mémoire ROM permet
de faire exactement cela sans avoir rien à ajouter, car elle est munie
d'un décodeur d'entrée et la porte OU de sortie fait déjà partie de
la ROM. On peut donc interpréter le fonctionnement d'une mémoire ROM
de $k$ bits d'adresse et avec des mots de taille $m$ comme un
dispositif qui permet, pour les entrées qui sont ses adresses, de
mettre en oeuvre $m$ fonctions combinatoires différentes (une par
bit de mot) de $k$ entrées.

Par exemple, la sortie $A_2$ de la mémoire de la figure
[914](#org92e3efd) implémente la fonction $$ A_2 = \sum (0,1,4,8) $$
exprimée en somme de minterms.


### Tableau de correspondance

Cette approche qui consiste à réaliser une fonction logique
combinatoire au moyen d'une mémoire qui spécifie, pour chaque
combinaison d'entrée possible, une valeur de sortie, est largement
utilisée dans les composants programmables. On parle alors de tableau
de correspondance (en anglais, *LookUp Table* (LUT)). Il s'agit ni
plus ni moins que de stocker en mémoire le tableau de vérité de la
fonction à réaliser. Dans les composants programmables, on utilise
plutôt des mémoires RAM pour les tableaux de correspondance, afin que
la configuration des fonctions puisse être changée selon
l'application.


### Catégories de mémoires ROM

On distingue quatre grandes approches technologiques pour réaliser des
mémoires mortes. Leurs usages typiques sont surtout déterminés par la
façon de les configurer (on dit couramment *programmer*, même s'il
s'agit d'une intervention sur le plan matériel).

Dans la **programmation par masque**, la mémoire est programmée lors de
la fabrication de la puce. Le fabricant se base sur un tableau de
vérité fourni par le client pour établir des connexions qui seront
implémentées (ou pas) dans le procédé de fabrication via des masques
qui empêchent le dépôt de matériau conducteur sur les couches du
circuit intégré.  Cette approche convient à la production de masse à
grand volume.

Dans la **programmation sur mesure**, on utilise un type de mémoire qui
comporte initialement des connexions entre toutes les sorties du
décodeur et toutes les entrées des portes OU de sortie (la mémoire en
configuration initiale comporte des 1 partout). La programmation, qui
peut se faire chez le développeur au moyen d'un dispositif de
programmation (ou programmeur) spécialement conçu à cette fin,
consiste à supprimer les connexions qui ne sont pas nécessaires en
envoyant des impulsions à forte tension pour faire fondre les fusibles
de connexions spécifiques. Un fusible fondu (pas de connexion)
correspond à un bit 0 dans la mémoire. Cette programmation est bien
entendu irréversible: impossible de rétablir la connexion une fois que
le fusible est fondu.

Avec une **PROM** (pour *Programmable ROM*), il est possible d'effacer la
configuration dans son ensemble en soumettant la puce à une lumière
ultraviolette pendant un certain temps. Ce bombardement énergétique
permet de décharger les grilles flottantes des dispositifs qui
implémentent les connexions. La mémoire PROM peut être configurée de
nouveau.

Avec la **programmation électrique**, il est possible de reconfigurer
l'ensemble d'une mémoire dite EEPROM (*Electrically Erasable PROM*)
en la soumettant à un signal électrique d'effacement. 

Les ROM à **programmation *flash*** sont semblables aux EEPROM, mais la
reconfiguration peut se faire adresse par adresse.  Il est notamment
possible de reconfigurer une mémoire sans la retirer de son circuit.
Fonctionnellement, ces mémoires sont à mi-chemin entre la mémoire RAM
et la mémoire sur disque. Les mémoires *flash* tendent d'ailleurs de
plus en plus à remplacer ce dernier type dans les systèmes portables:
téléphones, ordinateurs portables, etc.


# Logique programmable


## Objectifs

-   Se familiariser avec les différents types de composants logiques
    programmables
-   Reconnaître les avantages et limitations des différents types
-   Comprendre le fonctionnement d'une matrice logique programmable
-   Comprendre le fonctionnement d'un composant logique à matrice programmable
-   Comprendre le fonctionnement d'un circuit séquentiel programmable
-   Se familiariser avec le concept de bloc logique programmable
-   Comprendre l'organisation d'une cellule logique programmable et
    apprécier sa flexibilité


## Dispositifs programmables

Nous avons vu qu'une mémoire ROM est un dispositif logique
programmable qui, grâce à la matrice d'interconnexion entre son
décodeur (qui génère tous les minterms) et les portes OU de sortie,
permet de réaliser des fonctions logiques arbitraires. D'autres
composants utilisent à divers degrés cette approche pour offrir des
possibilités de configuration flexibles.

Il existe une grande variété de dispositifs programmables, des plus
simples aux plus complexes. De nombreux manufacturiers offrent des
variantes plus ou moins équivalentes dans chacune des gammes de
produits. Nous allons nous limiter à présenter brièvement les grandes
familles typiques, en ordre de complexité croissante.


### Matrice logique programmable (PLA)

Une **matrice logique programmable** (en anglais, *Programmable Logic
Array* (PLA)) est un dispositif spécifiquement conçu pour la
réalisation de fonctions combinatoires arbitraires. Elle fonctionne
selon une approche qui s'apparente à l'utilisation d'une mémoire morte
pour réaliser une fonction logique arbitraire.

La figure [938](#org61706ce) montre une matrice permettant de
réaliser deux fonctions pouvant comporter jusqu'à quatre termes
produits de trois variables. Puisque le nombre de termes produits est
limité, il n'est généralement pas possible de se baser directement sur
les minterms des fonctions pour l'implémentation. On doit donc
simplifier les fonctions avant l'implémentation. Un même terme produit
peut contribuer à plus d'une fonction.

La programmation des portes XOR de sortie permet de choisir
la fonction directe ou son complément. 

Les PLAs offertes sur le marché proposent des configurations avec de
plus grands nombres d'entrées, de termes et de sorties, typiquement
des dizaines.

![img](Sources_images_logiques/images/pla.svg "Matrice logique programmable")


### Logique à matrice programmable (PAL)

Les dispositifs à **logique à matrice programmable** (an anglais,
*Programmable Array Logic* (PAL)) sont une autre variante sur ce
thème, avec une matrice OU fixe et une matrice ET configurable. Ils
sont moins flexibles que les PLA.

La figure [942](#org7d6952f) montre un dispositif de logique à matrice
programmable à quatre variables d'entrée, permettant de réaliser trois
fonctions pouvant comporter jusqu'à trois minterms. Les sorties
(directes et complémentée pour la première fonction) peuvent être
acheminées aux entrées des autres fonctions. Encore ici, le nombre de
termes produits est limité et on doit simplifier les fonctions avant
l'implémentation. Cependant, puisqu'il n'y a pas de matrice OU, il
n'est pas possible de partager un terme produit entre deux fonctions.

Les PAL offerts sur le marché proposent des configurations avec de
plus grands nombres d'entrées, de termes et de sorties, typiquement
des dizaines.

![img](Sources_images_logiques/images/pal.svg "Logique à matrice programmable")


### Logique programmable séquentielle

En combinant un **dispositif logique programmable** (en anglais,
*Programmable Logic Device* (PLD)) avec un certain nombre de
bascules, il est possible de proposer un circuit programmable
séquentiel. La configuration générale est illustrée sur la
figure [944](#org20805a2).

![img](Sources_images_logiques/images/circuit_seq_prog.png "Modèle de circuit séquentiel programmable") 

Plusieurs fabricants proposent une variété de dispositifs de ce type,
avec diverses options de configuration, d'interconnexion, etc.  On
offre par exemple des dispositifs complexes qui combinent plusieurs
cellules programmables sur un même circuit intégré, reliables au moyen
d'un réseau d'interconnexion configurable. La disposition générale de
ce genre de dispositif complexe est présentée à la figure [946](#org9ab7675).

![img](Sources_images_logiques/images/CPLD.png "Modèle de circuit séquentiel programmable complexe")


## Circuits intégrés programmables

La version la plus sophistiquée des circuits logiques programmables
est sans contredit le **circuit intégré programmable** (en anglais, *Field
Programmable gate array* (FPGA)). Un FPGA est constitué d'une matrice
de blocs polyvalents appelés **blocs logiques programmables** qui
permettent, selon leur configuration, de réaliser n'importe quelle
fonction logique. Un bloc logique est typiquement constitué d'une ou
de quelques **cellules logiques** élémentaires.

La figure [952](#org0dffdf4) montre une version simplifiée d'une cellule
logique comportant:

-   un tableau de correspondance (LUT) à quatre entrées
-   un additionneur complet
-   une cellule de mémoire

![img](Sources_images_logiques/images/cell_logique.svg "Cellule logique")

Le tableau de correspondance (LUT) à quatre entrées $a, b, c, d$ est
fractionné en deux LUT à trois entrées, combinés par un multiplexeur
contrôlé par l'entrée $d$. Pour des opérations arithmétiques, les
sorties des LUT à trois entrées sont additionnées avec une retenue
externe $R_i$. Le multiplexeur du centre, commandé par le signal de
sélection $S_1$, sélectionne le résultat d'addition ou la fonction
réalisée par la LUT à 4 entrées. Selon le signal de sélection $S_2$,
la valeur obtenue peut être acheminée directement en sortie de la
cellule (cellule en mode combinatoire) ou être stockée dans la bascule
D (cellule en mode séquentiel). Dans d'autres configuration typiques
de cellules, l'additionneur complet est remplacé par un tableau de
correspondance.

En plus de la matrice de blocs logiques, un circuit intégré
programmable comporte également des composants consacrés aux
entrées/sorties, des lignes d'interconnexion programmables pour relier
les blocs entre eux, des lignes de distribution de signaux d'horloge,
et possiblement de la mémoire RAM supplémentaire.

Les LUTs font appel à de la mémoire RAM pour implémenter les tableaux
de vérité, ce qui permet une configuration dynamique qui doit être
chargée lors de la mise en route du circuit programmable. Un autre
avantage est que ces mémoires permettent des vitesses de
fonctionnement nettement plus rapides que si on utilisait des mémoires
ROM.  Les données de configuration peuvent être stockées dans de la
mémoire *flash* externe par exemple. Le circuit FPGA peut donc être
reconfiguré et adapté à différentes fonctions, simplement en écrivant
de nouvelles données dans la mémoire externe qui contient ses
informations de configuration.

La configuration et la programmation d'un circuit programmable FPGA se
fait au moyen d'outils de synthèse spécialisés, souvent en fonction
d'une spécification au moyen d'un langage descriptif de matériel (en
anglais, *Hardware Description Language* (HDL)).


# Langages descriptifs et de modélisation


## Objectifs

-   Expliquer la différence entre un langage descriptif de matériel et
    un langage de programmation
-   Expliquer les mécanismes d'assignation de signaux et la notion de concurrence
-   Faire la distinction entre une description d'entité et une architecture
-   Faire la distinction entre un modèle structural et un modèle
    comportemental
-   Faire la distinction entre un signal et une variable
-   Se familiariser avec les principaux types utilisés en descriptions
    de circuits
-   Préparer une description (modèle) de circuit en langage VHDL
-   Préparer un banc d'essai permettant de tester un modèle de circuit
-   Simuler un modèle VHDL au moyen d'un banc d'essai et interpréter les
    résultats
-   Élaborer une description complète en VHDL pour un système simple


## Modélisation et simulation

Lorsque vient le temps de concevoir, simuler, tester et élaborer des
systèmes numériques complexes, les approches manuelles que nous avons
employées jusqu'ici ne suffisent plus. Il faut alors faire appel à des
familles d'outils plus puissants de conception assistée par
ordinateur. Avec ces outils, il est possible de concevoir et de
spécifier précisément le design voulu, en simuler le fonctionnement,
le valider par une batterie de tests, afin de s'assurer que le tout
correspond aux besoins de l'application avant même de solliciter une
seule porte logique physique.

Un élément clé de cette démarche est la possibilité de décrire
précisément le ou les circuits qui seront implémentés au moyen d'un
langage approprié. Un tel **langage descriptif de matériel** (en anglais
*Hardware Description Language* (HDL)), qui s'apparente à un langage
de programmation, permet de décrire de façon textuelle les différents
éléments de notre circuit, leurs interconnexions et interactions.

Alors qu'un langage de programmation spécifie essentiellement des
procédures et les données qui y sont associées, un HDL est un langage
de modélisation qui décrit des structures matérielles et le
comportement de systèmes logiques. Un HDL peut spécifier des
diagrammes logiques, des expressions logiques, voire des tableaux de
vérité. Il permet aussi de décrire le comportement du système à
différents niveaux d'abstraction et les relations hiérarchiques entre
les différents sous-systèmes qui le composent.

On peut voir un modèle HDL comme la description des relations entre
les entrées et les sorties du système. Entrées et sorties sont
modélisées comme des **signaux**.


## Langage VHDL

Parmi les nombreux HDL en usage, quelques-uns ont été
standardisés. Les plus répandus sont *Verilog* et VHDL. C'est ce
dernier langage que nous allons utiliser.  Le V dans l'acronyme VHDL
(*VHSIC Hardware Description Language*) provient d'un autre acronyme,
VHSIC pour *Very High Speed Integrated Circuits* (circuits intégrés à
très haute vitesse). On comprend que le langage a été créé dans
l'optique de concevoir des circuits intégrés rapides et complexes.

Un design en VHDL est un ensemble d'entités de conception. Une entité,
celle du plus haut niveau, invoque les autres entités comme
composants.  Le design dans son ensemble est structuré de façon
hiérarchique.


## Entité

Une **entité** définit le nom d'un modèle et spécifie ses interfaces,
c'est-à-dire les entrées et les sorties qui permettent au modèle
d'interagir avec son environnement. Le nom, la direction et le type
de chaque signal d'interface sont déclarés dans le **port** de
l'entité. La fonction du modèle n'est aucunement précisée. Il s'agit
uniquement de décrire la «coquille» d'une boîte noire.

La déclaration d'entité spécifie le nom de l'entité et la liste des
ports d'entrée et de sortie. La forme générale est comme ci-dessous (les
éléments entre crochets sont optionnels). 

    entity Nom_Entite is 
    [generic generic_declarations);]
    
    port (noms_signaux: mode type;
    
    noms_signaux: mode type;
      .
      .
      .
    noms_signaux: mode type);
    
    end [Nom_Entite];

La déclaration commence avec le mot réservé `entity`, suivi du nom et
du mot réservé `is`. Viennent ensuite les déclarations de ports avec le
mot réservé `port`. La déclaration se termine avec le mot réservé
`end` et optionnellement, le nom de l'entité.

-   `Nom_Entite` est un nom arbitraire choisi par le concepteur ou la
    conceptrice.

-   `noms_signaux` donne une liste d'un ou de plusieurs identifiants
    séparés par des virgules qui définissent les signaux externes
    d'interface.

-   **mode**: est un des mots réservés suivants, qui définissent la
    direction des signaux:
    -   `in`: le signal est une entrée
    
    -   `out`: le signal est une sortie de l'entité, qui peut être lue
        par les autres entités qui y sont raccordées
    
    -   `buffer`: le signal est une sortie qui peut être lue de
        l'intérieur de l'architecture de l'entité
    
    -   `inout`: le signal peut être une entrée ou une sortie

-   `type`: est un type de signal prédéfini ou défini par le concepteur
    ou la conceptrice. Par exemple, `bit, bit_vector, Boolean,
       character, std_logic, ou std_ulogic`.
    -   `bit`: une valeur binaire  0 ou 1
    
    -   `bit_vector`: un vecteur de bits
    
    -   `std_logic, std_ulogic, std_logic_vector, std_ulogic_vector`: des
        valeurs binaires plus nuancées (voir librairies)
    
    -   `boolean`: deux valeurs possibles: TRUE ou FALSE
    
    -   `integer`: des valeurs entières
    
    -   `real`: des valeurs réelles
    
    -   `character`: des caractères
    
    -   `time`: des valeurs de temps

-   **generic:** les déclarations génériques sont optionnelles et
    spécifient des constantes locales utilisées pour préciser par
    exemple des valeurs de temps ou des tailles de vecteur. Un
    générique peut avoir une valeur de défaut. La syntaxe est comme
    ci-après.

    generic (
    
    nom_constante: type [:=valeur];
    
    nom_constante: type [:=valeur];
    .
    .
    .
    nom_constante: type [:=valeur] );

Le listage qui suit montre un exemple simple de déclaration d'entité. 

    entity ALU is
    port (argl, arg2: in bit_vector;
    add_or_sub: in bit;
    result: out bit_vector);
    end ALU;


## Architecture

Une **architecture** est une réalisation (ou implémentation) de
l'intérieur de la boîte noire. Jumelée à une entité, elle décrit
comment les sorties de l'entité sont obtenues à partir de ses
entrées. Il est possible d'associer de multiples architectures à une
même entité.

Une architecture peut contenir:

-   des déclarations de données

-   des affectations concurrentes de signaux

-   des blocs processus

-   des instanciations de composants

La structure typique d'une architecture est comme dans le listage suivant.

    architecture nom_d_architecture of NOM_ENTITE is
    
    -- Déclarations de types de données
    
    -- Déclarations de composants
    
    -- Déclarations de signaux
    
    -- Déclarations de constantes
    
    -- Déclarations de fonctions
    
    -- Déclarations de procédures
    
    begin
    
    -- Énoncés concurrents ou séquentiels
    
    end nom_d_architecture;

Les énoncés qui peuvent se trouver dans le corps de l'architecture
(entre le `begin` et le `end` peuvent être des instanciations de
composants, des assignations de signaux ou des énoncés de processus.


## Signaux et assignation

Un signal représente en quelque sorte un «fil». Une assignation comme

A <= NOT(B);

signifie que A et B sont des signaux reliés dont l'un est l'inverse
logique de l'autre.  Ainsi,

A <= B; 

signifie que les deux signaux A et B auront la même valeur logique.


## Notes sur la syntaxe

Des expressions aussi complexes que désiré peuvent être écrites, en
utilisant des parenthèses pour spécifier les priorités d'évaluation
des opérations (si elles doivent être différentes de la priorité
implicite de VHDL).

Voici des exemples d'expressions.

    a <= ((b and c and f) or (t nor r)) nand p;
    
    a(3 downto 0) <=
    b(4 downto 1) when (p and q)
    else (p & q & q & p);

Les commentaires sont possibles: tout ce qui suit deux tirets (- -)
est ignoré.  Toutes les assignations doivent se terminer avec un
point-virgule (;)

Voici d'autres exemples d'assignations.

    A <= B OR C;
    
    A <= B AND C;
    
    A <= B NOR C;
    
    A <= B NAND C;
    
    A <= B XOR C;
    
    A <= NOT B; --ceci est un commentaire
    
    A <= (B AND C) OR (D AND E); --(aucune priorité 
                                 -- préétablie de AND/OR)

Nous nous contenterons de ces opérations pour le moment. Les
parenthèses permettent de préciser l'ordre des opérations.

    A <= B AND C AND D; -- ceci fonctionne
    
    A <= B NAND C NAND D; -- pas ceci: NAND n'est pas associatif
    
    A <= NOT(B AND C AND D); -- ceci fonctionne

Voici encore d'autres exemples d'assignations.  Le dernier de ces
exemples fait appel à des vecteurs de signaux. Nous verrons plus loin
comment définir ces regroupements de signaux.

    Sum <= A XOR B XOR Cin;
    
    Cout <= (A AND B) OR (A AND Cin);
    
    Cout <= (A AND B) OR (A AND Cin) OR (B AND Cin);
    
    a <= b when c else a; -- sélection (multiplexage)
    
    a(6 downto 1) <= c & d(3 downto 0) & e; -- concaténation 
                                            -- bit-à-bit ("&")

De façon générale, VHDL est insensible aux MAJUSCULES ou minuscules
et ignore les espaces supplémentaires et sauts de lignes. On doit
déclarer le type de tous les objets: signaux, constantes ou variables.


## Concurrence

Dans un corps d'architecture, les assignations sont
**concurrentes**. Par exemple, dans ce qui suit, les deux énoncés sont
évalués en parallèle. Les valeurs pour q et qb sont continuellement
mises à jour: dès qu'un des signaux à droite de l'assignation change
(on dit qu'un évènement se produit sur le signal), l'énoncé est évalué
de nouveau.

    q <= r nor qb; -- énoncé 1
    qb <= s nor q; -- énoncé 2

**Ce n'est pas comme en programmation** où les énoncés sont évalués
l'un après l'autre, une seule fois. Tous les énoncés concurrents sont
continuellement évalués.

L'effet de ces énoncés sera exactement le même si on les place dans un
autre ordre dans la description, comme ci-dessous.

    qb <= s nor q; -- énoncé 1
    q <= r nor qb; -- énoncé 2

Le langage décrit à la base un circuit et non pas une procédure:
toutes les portes sont toujours alimentées et les fils sont toujours
connectés. L'ordre dans lequel on donne la description n'a aucune
importance. Nous verrons plus loin qu'il est aussi possible de définir
des blocs dans lesquels l'exécution est séquentielle comme en
programmation.


## Vecteurs de bits

Il est possible de grouper des signaux pour en faire des vecteurs, qui
sont des groupes ordonnés de bits: un mot, un bus, etc. De cette
façon, les spécifications sont plus compactes et faciles à
interpréter.

La convention la plus naturelle ordonne les indices de bits 
A(msb) $\longleftrightarrow$ A(lsb),
mais l'ordre inverse est également possible. Il vaut mieux établir une
convention et s'y tenir pour éviter les erreurs d'interprétation.

    A(VALEUR_HAUTE downto VALEUR_BASSE)
    
    A(15 downto 0) -- A comporte 16 bits
    
    A(7 downto 3) -- 5 bits du milieu de A
    
    A(0 to 7) -- A comporte 8 bits, énumérés de façon croissante

L'opérateur de concaténation `&` permet de combiner des groupes de bits.

    A(15 downto 0) <= B(7 downto 0) &
                      C(7 downto 0);

Considérons par exemple la partie du calcul de somme de la description
d'un additionneur 8 bits ci-dessous.  Avec des déclarations adéquates,
on pourrait écrire un calcul de somme plus compact.

    Sum(7 downto 0) <= A(7 downto 0)
    xor B(7 downto 0)
    xor C(7 downto 0);
    
    C(7 downto 0) <= (A(7 downto 0) and
    B(7 downto 0)
    )
    or (A(7 downto 0) and
    (C(6 downto 0) & Cin)
    )
    or (B(7 downto 0) and
    (C(6 downto 0) & Cin)
    );
    
    Cout <= C(7);

    Sum <= A xor B xor (C(6 downto 0) & Cin);
    
    C <= (A and B) or
    (A and (C(6 downto 0) & Cin) ) or
    (B and (C(6 downto 0) & Cin) );
    
    Cout <= C(7);


## Modèle complet

Considérons la bascule JK maître-esclave de la figure [1023](#org98bc27f)
ci-dessous, construite au moyen de portes simples.  Un modèle
VHDL complet pour cette bascule JK maître-esclave est donné ensuite.

![img](Sources_images_logiques/images/JK-MS.svg "Bascule JK maître-esclave à modéliser")

    library ieee;
    use ieee.std_logic_1164.all;
    use ieee.numeric_std.all;
    
    -- Bascule JK maître-esclave.
    -- La bascule maître mémorise sur une horloge haute, 
    -- la bascule esclave mémorise sur une horloge basse. 
    -- Les deux rétroactions évitent les conditions 
    -- interdites aux entrées 
    entity mainJK is
      port (
        J: in std_logic; -- entrée J (set) de la bascule
        C: in std_logic; -- entrée d'horloge
        K: in std_logic; -- entrée K (reset) de la bascule
        Q: out std_logic; -- bit stocké
        notQ: out std_logic -- inverse du bit stocké
        );
    end main;
    
    architecture Complet of mainJK is
      signal notQ_temp: std_logic;
      signal Q_temp: std_logic;
      signal s0: std_logic;
      signal s1: std_logic;
      signal s2: std_logic;
    begin
      s0 <= NOT C;
      s2 <= NOT ((notQ_temp AND J AND C) OR s1);
      s1 <= NOT (s2 OR (C AND K AND Q_temp));
      Q_temp <= NOT ((s2 AND s0) OR notQ_temp);
      notQ_temp <= NOT (Q_temp OR (s0 AND s1));
      Q <= Q_temp;
      notQ <= notQ_temp;
    end Complet;


## Modèle comportemental

Un modèle comportemental d'une entité est un ensemble d'énoncés qui
sont exécutés séquentiellement. Ces énoncés peuvent se trouver dans
des blocs `process, function` ou `procedure`. Un tel bloc est concurrent
avec les autres énoncés du modèle général. Il est possible d'utiliser
des variables à l'intérieur des processus. Un énoncé d'assignation
spécifique aux variables permet d'assigner (sans délai) une valeur à
une variable qui a été préalablement déclarée. On se rapproche alors
de la programmation traditionnelle. Les variables sont locales aux
processus. Dans un bloc processus, il est possible d'avoir des
boucles, des branchements conditionnels, etc. Dans le corps de
l'entité, un bloc processus apparaît comme une grosse porte logique
arbitrairement définie lors de la conception du bloc.


## Modèle flux de données

Dans un modèle flux de données, c'est le mouvement des données qui est
exprimé par un ensemble d'énoncés concurrents. On peut faire appel à
des opérateurs logiques AND, OR, NOT, etc., pour décrire les relations
entre les signaux.


## Modèle structural

Un modèle structural décrit des ensembles de composants
interconnectés. Un énoncé d'instanciation d'un composant (qui revient
à dire quelque chose comme «utiliser le composant X ici» est un énoncé
concurrent qui indique de créer une instance de la «chose» spécifiée.

Une telle description structurale se contente de préciser quels
composants seront reliés à quels autres composants, sans référence au
comportement desdits composants.

Les énoncés qui suivent le `begin` spécifient l'instanciation de
composants et les interconnexions. Un énoncé d'instanciation de
composant crée un nouveau niveau hiérarchique. Chaque ligne commence
avec un *nom d'instance*, suivi d'un deux-points (':'), d'un nom de
composant et du mot réservé **`port map`**.  Ce `port map` spécifie les
interconnexions du composant. Rappelons que l'ordre de ces
énoncés est sans conséquences.


## Bloc processus

Un énoncé `process` permet de définir un processus. Le format est le
suivant.

    [étiquette_processus:] process [ (liste_sensibilité) ] [is]
    [déclarations_processus]
    begin
    --   liste d'énoncés séquentiels tels que:
    -- assignations de signaux 
    -- assignations de variables
    -- énoncés case
    -- énoncés exit
    -- énoncés if 
    -- énoncés loop 
    -- énoncés next
    -- énoncés null
    -- appels de procedure
    -- énoncés wait
    end process [étiquette_processus];

Voici un exemple d'un modèle avec bloc processus d'une bascule D
déclenchée sur un front montant avec mise à zéro asynchrone.

    library ieee;
    use ieee.std_logic_1164.all;
    
    entity DFF_CLEAR is
       port (CLK, CLEAR, D : in std_logic;
          Q : out std_logic);
    
    end DFF_CLEAR;
    
    architecture COMPORT_DFF of DFF_CLEAR is
    begin
    DFF_PROCESS: process (CLK, CLEAR)
       begin
          if (CLEAR = '1') then
             Q <= '0';
          elsif (CLK'event and CLK = '1') then
             Q <= D;
          end if;
       end process;
    end COMPORT_DFF;

Le processus, déclaré à l'intérieur d'une architecture, est un énoncé
concurrent.  Mais tout ce qui se déroule à l'intérieur du processus
est exécuté de façon séquentielle. Comme tout énoncé concurrent, le
processus lit et écrit des signaux sur ses ports d'interface. Dans
l'exemple précédent, la sortie Q reçoit des valeurs par assignation au
sein du processus. L'expression `CLK'*event* *and* CLK = '1'` teste une
condition de front montant sur l'interface d'entrée CLK.

Il ne peut pas y avoir de déclarations de signaux dans un processus;
seules des variables ou des constantes peuvent être déclarées.

Une **liste de sensibilité** est un ensemble de signaux qui déclenchent
l'exécution du processus. N'importe quel changement sur un des signaux
de la liste provoque l'exécution immédiate du processus.

S'il n'y a pas de liste de sensibilité, il faudra inclure un énoncé
`wait` pour s'assurer que le processus se termine. Il n'est pas permis
d'avoir à la fois une liste de sensibilité et un énoncé `wait` pour un
même processus. Les variables et constantes utilisées dans le
processus sont définies dans la portion `déclarations_processus`. 

Les énoncés entre **`begin`** et **`end`** sont exécutés séquentiellement. Les
assignations de variables, dénotées :=, sont exécutées immédiatement. 

Un énoncé concurrent est comme un processus d'une seule ligne, dont la
liste de sensibilité est constituée de tous les signaux qui sont à
droite de l'assignation.

Il est possible de définir un processus dont le corps est une
description combinatoire. Par exemple, le processus suivant permet de
modéliser une porte OU entre les entrées a et b. 

    proc1: process
      begin
        wait on a, b;
        s <= a or b;
      end process proc1;

La sensibilité d'un tel processus (ici obtenue au moyen de l'énoncé
`wait on a, b;)` doit comporter tous les signaux utilisés pour que
l'exécution se fasse dès qu'une des entrées change de valeur.

Les assignations de signaux dans un processus ne prennent effet qu'une
fois que le processus est suspendu. Cela veut notamment dire que c'est
seulement la dernière assignation à un signal donné qui sera
effectivement exécutée.

Si un processus effectue une lecture d'un signal qui se verra aussi
assigner une valeur par le processus, la lecture prendra en compte la
valeur précédente du signal **avant** qu'il soit affecté par
l'assignation. Il est donc possible de créer de la rétroaction au sein
d'un même processus.


## Modélisation du délai

Deux formes de délai peuvent être modélisés en VHDL. Le délai inertiel
et le délai de transport.


### Délai inertiel

Le délai inertiel est la forme de délai par défaut. Le mot réservé
`after` suppose par défaut un délai inertiel. Avec du délai inertiel,
deux changements consécutifs du signal d'entrée qui sont plus
rapprochés temporellement que la valeur de délai ne seront pas
reflétés sur le signal de sortie. On modélise alors une inertie du
circuit, qui est trop lent pour réagir lorsque les changements
d'entrée sont trop rapides pour lui. Par exemple, avec une
assignation comme la suivante:

    b <= a after 30 ns;

Si le signal a passe de '0' à '1' à 10 ns et de '1' à '0' à 20 ns, la
sortie ne changera pas du tout et restera tout le temps à '0'.


### Délai de transport

Le délai de transport applique un retard dans le signal de sortie. Par
exemple, avec la spécification suivante:

    b <= transport a after 20 ns;

Si le signal a passe de '0' à '1' à 10 ns et de '1' à '0' à 20 ns, la
sortie passera de '0' à '1' à 30 ns et de '1' à '0' à 40 ns,
reproduisant en sortie la même forme d'onde qu'en entrée, mais
retardée de 20 ns.


## Librairies

Des librairies de types peuvent être définies pour préciser des types
d'objets qui pourront ensuite être utilisés de façon standard. Par
exemple, la librairie IEEE `std_logic_1164` définit le type logique
`std_logic` qui apporte plus de nuances que le simple type binaire,
qui lui ne comporte que deux valeurs numériques '0' et '1'.

Le tableau suivant donne la liste des valeurs possibles avec
`std_logic`. Comme on peut le voir, les signaux pourront ainsi assumer
des valeurs comme Z (haute impédance pour les signaux trois-états), X
(pour valeur inconnue), - pour valeur facultative, etc. Il y a même
des nuances pour la solidité des valeurs logiques.

<table id="org236ae00" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 63 :</span> Valeurs pour <code>std_logic</code></caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Symbole</th>
<th scope="col" class="org-left">Interprétation</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">'1'</td>
<td class="org-left">1 Logique</td>
</tr>


<tr>
<td class="org-left">'0'</td>
<td class="org-left">0 Logique</td>
</tr>


<tr>
<td class="org-left">'Z'</td>
<td class="org-left">Haute impédance</td>
</tr>


<tr>
<td class="org-left">'W'</td>
<td class="org-left">Signal faible, indéterminé entre 0 ou 1</td>
</tr>


<tr>
<td class="org-left">'L'</td>
<td class="org-left">0 faible, <i>pulldown</i></td>
</tr>


<tr>
<td class="org-left">'H'</td>
<td class="org-left">1 faible, <i>pullup</i></td>
</tr>


<tr>
<td class="org-left">'-'</td>
<td class="org-left"><i>Don't care</i></td>
</tr>


<tr>
<td class="org-left">'U'</td>
<td class="org-left">Non initialisé</td>
</tr>


<tr>
<td class="org-left">'X'</td>
<td class="org-left">Inconnu, conflit entre sources multiples</td>
</tr>
</tbody>
</table>

Une clause `use` permet de spécifier les librairies à utiliser au
début du fichier de spécification. Par exemple, le fichier VHDL
pourrait commencer avec les déclarations du listage suivant:

    library ieee;
    use ieee.std_logic_1164.all;
    use ieee.numeric_std.all;

Nous avons déjà vu un exemple de l'utilisation de librairies dans le modèle
de la bascule JK maître-esclave.


## Encapsulation

Il est possible de grouper des énoncés et de les réutiliser
au besoin, dans d'autres modèles. Ceci nous permet de «cacher» la
description dans une boîte. Dans ce cas-ci, il s'agit d'un loquet SR
construit avec des portes NOR.

    entity rs is
    port(r, s: in bit; q, qb: out bit);
    end rs;
    
    architecture norlogic of rs is
    begin
    q <= r nor qb;
    qb <= s nor q;
    end nor_logic;

L'entité définie est un composant qui peut être utilisée dans
d'autres circuits, à l'intérieur d'une hiérarchie de design. Voici
comment on peut utiliser le composant loquet pour modéliser un loquet D.

    entity Dlatch is
    port (clk,d: in bit; q,qb: out bit);
    end Dlatch;
    
    architecture test of Dlatch is
    --
    signal db, cr, cs: bit;
    --
    component rs_ff
    port (r, s: in bit;
    q, qb: out bit);
    end component;
    --
    label rs0;
    --
    for rs0: rs_ff
    use entity rs(nor_logic);
    
    begin
    db <= not d;
    cr <= db and clk;
    cs <= d and clk;
    rs0: rs_ff port map(cr, cs, q, qb);
    end test;

Voici un exemple de bascule maître-esclave conçue de façon structurale
à partir du composant loquet:

    entity MS is
    port (clear,reset,set,clock: in bit;
    q, qbar: out bit);
    end MS;
    
    architecture ms_struct of MS is
    signal clrbar, r0, s0, q0, qbar0,
    r1, s1, cbar: bit;
    label rs0, rs1;
    component rs_ff
    port (r,s: in bit; q,qbar: out bit);
    end component;
    for rs0, rs1: rs_ff
    use entity RS(nor_logic);
    begin
    clrbar <= not clear;
    cbar <= not clock;
    r0 <= (reset and clock) or clear;
    s0 <= (set and clock) and clrbar;
    rs0: rs_ff port map(r0,s0,q0,qbar0);
    r1 <= (qbar0 and cbar) or clear;
    s1 <= (q0 and cbar) and clrbar;
    rs1: rs_ff port map(r1,s1,q,qbar);
    end ms_struct;

Voici un exemple de compteur élaboré à partir de cette bascule maître-esclave:

    entity CNTER is
    port (clock, clear: in bit;
    a: out bit_vector(3 downto 0));
    end CNTER;
    
    architecture count of CNTER is
    signal b: bit_vector(3 downto 0);
    component ms_ff
    port (clr, r, s, c: in bit;
    q, qbar: out bit);
    end component;
    label ms0, msl, ms2, ms3;
    for ms0, msl, ms2, ms3: ms_ff
    use entity MS(ms_struct);
    begin
    ms0: ms_ff port map(
    clear,a(0),b(0),clock,a(0),b(0));
    ms1: ms_ff port map(
    clear,a(1),b(1),a(0),a(1),b(1));
    ms2: ms_ff port map(
    clear,a(2),b(2),a(1),a(2),b(2));
    ms3: ms_ff port map(
    clear,a(3),b(3),a(2),a(3),b(3));
    end count;


## Description de design en VHDL

La description complète du système à simuler est placée dans un
fichier avec extension .vhdl qui est ensuite compilé et simulé.  On
appelle cette description «fichier de design» ou «design» tout court.

Un design en VHDL est un ensemble d'entités de conception. L'entité de
plus haut niveau invoque les autres entités comme composants. Le design
dans son ensemble est appelé «hiérarchie de design».


### Multiplicateur huit bits

Voici l'exemple d'un multiplicateur huit bits construit à partir de
plusieurs autres composants.  Les listages qui suivent donnent le
détail de la modélisation.

    entity multiply is
    port (load, clock: in bit;
    input1, input2: in
    bit_vector(7 downto 0);
    product: out
    bit_vector(15 downto 0);
    output_valid: out bit);
    end multiply;
    --
    entity adder is
    port(a: in bit_vector(7 downto 0);
    b: in bit_vector(7 downto 0);
    cin: in bit;
    sum: out bit_vector(7 downto 0)
    cout: out bit) ;
    end adder;
    --
    entity D_FF is
    port(din: in bit_vector(7 downto 0)
    dout: out bit_vector(7 downto 0)
    enable: in bit);
    end D_FF;

    architecture logic of adder is
    signal cw, cx: bit_vector(7 downto 0);
    --
    begin
    cw(0) <= cin;
    cw(7 downto 1) <= cx(6 downto 1);
    cx <= (a and b) or (a and cw) or (b and cw);
    sum <= a xor b xor cw;
    cout <= cx(7);
    end logic;

    architecture edge of D_FF is
    -- une bascule D de 8 bits de large
    signal x, y, z, w, qb, e :
    bit_vector(7 downto 0);
    begin
    e <= "11111111" when enable else 0;
    x <= din nand y;
    y <= e nand (not w);
    z <= e nand w;
    w <= z nand x;
    dout <= z nand qb;
    qb <= y nand dout;
    end edge;

    architecture mult of multiply is
    signal mux1, mux2, mux3, mux4:
    bit_vector(7 downto 0);
    signal control, adder_out:
    bit_vector(7 downto 0);
    signal accum:
    bit_vector(15 downto 0);
    signal carry_out: bit;
    label l1, l2, l3, l4;
    
    component add
    port (argl, arg2: in bitvec;
    c_in: in bit;
    result: out bitvec;
    c_out: out bit);
    end component;
    for l4: add use entity adder(logic);
    
    component latch
    port (xin: in bitvec;
    xout: out bitvec; enable: in bit);
    end component;
    for l1, l2, l3: latch use
    entity D_FF(edge);

    begin mux1(7 downto 0) <= 255 when load else "0" & contro1(7 downto
    1); l1: latch port map ( mux1, control, clock);
    
    mux2 <= 0 when load else
    carry_out & adder_out(7 downto 1);
    l2: latch port map (
    mux2, accum(15 downto 8), clock);
    
    mux3 <= input2 when load else
    adder_out(0) & accum(7 downto 1);
    l3: latch port map (
    mux3, accum(7 downto 0), clock);
    
    mux4 <= input1 when accum(0) else 0;
    l4: add port map (
    mux4, accum(15 downto 8), "0",
    adder_out, carry_out);
    
    output_valid <= not(control(0));
    product <= accum when output_valid
    else 0;
    end mult;


## Banc d'essai

Pour simuler un circuit avec un HDL, on doit lui appliquer des signaux
aux entrées afin que le simulateur puisse générer les sorties
correspondantes. Une description qui vise à générer ces signaux
d'entrée est appelée un **banc d'essai**.

![img](Sources_images_logiques/images/banc_essai.png "Banc d'essai")

Le bloc stimulus génère les signaux d'excitation qui sont appliqués
aux entrées du modèle à tester. Un bloc se charge de valider les
sorties observées, ce qui peut être fait automatiquement.

On commence par définir une entité de niveau supérieur pour le banc
d'essai:

    entity test_bench is
    
    end entity test_bench;

L'entité ne comporte pas de ports, puisque le banc d'essai ne comporte
pas d'entrées ou de sorties externes.


## Instanciation

Il faut ensuite instancier le modèle à tester. L'instanciation peut se
faire comme composant ou directement. À moins de vouloir définir un
*package* pour le modèle à tester, le composant doit être défini **avant**
le code principal. 

Voici un exemple de déclaration d'instanciation par composant. Les
noms de composant et de ports doivent correspondre à ceux du modèle à
tester.

    component and_gate is 
    port ( 
       a : in std_logic; 
       b : in std_logic; 
       and_out : out std_logic 
    ); 
    end component and_gate; 

Le composant est ensuite relié au modèle de test. 

    and_gate_instance: component and_gate
      port map (
        a       => signal_a,
        b       => signal_b,
        and_out => signal_and_out
      );

Chaque instanciation doit avoir son propre nom. Ici, c'est
`and_gate_instance`. Les noms de signaux à gauche sont les noms des
ports du composant. Les noms à droite sont les signaux qui sont reliés
aux ports. Ces signaux doivent être déclarés avant utilisation et
avoir le bon type.

Voici un exemple d'instanciation directe:

    and_gate_instance: entity work.and_gate(ltr)
      port map (
        a       => signal_a,
        b       => signal_b,
        and_out => signal_and_out
      );

Dans ce cas, il faut également préciser la librairie et l'architecture
pour le modèle à tester. Ici, la librairie est «work» et
l'architecture est «ltr».


## Écoulement du temps

Pour tester le modèle, on doit typiquement produire des signaux qui
varient en fonction du temps. Pour ce faire, il est possible
d'utiliser les énoncés `after` et `wait`. Il existe un type prédéfini
VHDL pour le temps, qui utilise les unités suivantes:

<table id="org8d5bc09" border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
<caption class="t-above"><span class="table-number">Tableau 64 :</span> Unités de temps</caption>

<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Unité</th>
<th scope="col" class="org-left">Valeur</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">fs</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">ps</td>
<td class="org-left">1000 fs</td>
</tr>


<tr>
<td class="org-left">ns</td>
<td class="org-left">1000 ps</td>
</tr>


<tr>
<td class="org-left">us</td>
<td class="org-left">1000 ns</td>
</tr>


<tr>
<td class="org-left">ms</td>
<td class="org-left">1000 us</td>
</tr>


<tr>
<td class="org-left">sec</td>
<td class="org-left">1000 ms</td>
</tr>


<tr>
<td class="org-left">min</td>
<td class="org-left">60 sec</td>
</tr>


<tr>
<td class="org-left">hr</td>
<td class="org-left">60 min</td>
</tr>
</tbody>
</table>

La plus petite unité de temps correspond à une femtoseconde ($10^{-15}$ seconde).

Voici des exemples d'énoncés liés au temps:

    time_ex <= 100 ps; -- 100 picoseconds 
    time_ex <= 1.2 ns; -- 1200 picoseconds
    time_ex <= 1.2 sec; -- 1200 milliseconds

1.  Énoncé `after`

    L'énoncé `after` ajoute un aspect temporel à une assignation. La
    partie de l'énoncé qui précède la virgule est une assignation qui
    fonctionne comme toute assignation normale. La deuxième partie de
    l'énoncé spécifie une nouvelle valeur pour le signal, qui prendra effet
    au temps (futur) indiqué.
    
        <signal> <= <valeur_initiale>, <valeur_finale> after <temps>;
    
    Voici un exemple d'utilisation pour créer un signal de mise à zéro:
    
        reset <= '1', '0' after 1 us;
    
    L'exemple suivant montre une méthode simple pour générer un signal
    d'horloge. La période obtenue sera le double du délai, soit ici 20 ns.
    
        clock <= not clock after 10 ns;

2.  L'énoncé `wait`

    L'énoncé `wait` suspend l'exécution dans un bloc processus pendant un
    certain temps. Rappelons que le processus ne peut pas avoir de liste
    de sensibilité. Trois types d'usage de `wait` sont possibles:
    
        wait for <time>; 
        
        wait until <condition> for <time>;
        
        wait on <signal_name>;
    
    Dans le premier cas, l'exécution est stoppée pendant la durée
    indiquée.
    
    Dans le deuxième cas, l'exécution est stoppée jusqu'à ce que la
    condition soit remplie. Il est possible de fonder les conditions sur
    des macros pour les fronts montants `rising_edge` ou descendants
    `falling_edge`. La portion `for` est optionnelle. Elle permet de
    prévoir un temps d'attente maximal. L'attente s'arrêtera donc si la
    condition est remplie ou après l'écoulement du temps spécifié.
    
    Dans le troisième cas, on attend simplement qu'un évènement se
    produise sur le signal spécifié pour cesser l'attente. Il est possible
    de spécifier une liste de signaux en les séparant par des virgules:
    
        wait on sig_a, sig_b;


## Exemples de banc d'essai

Testons un circuit séquentiel simple comportant deux entrées A et
B qui passent par une porte ET et une bascule avec sortie Q.


### Création d'une entité vide pour le banc d'essai

L'extrait de code suivant montre le point de départ de notre banc
d'essai.

    entity exemple_tb is
    end entity exemple_tb;
    
    architecture test of exemple_tb is
    
    --
    
    end architecture exemple_tb;


### Instanciation du modèle à tester

Nous faisons une instanciation directe. L'extrait de code suivant
montre comment la spécifier, en supposant que les signaux `in_a, in_b`
et `out_q` ont été déclarés précédemment:

    
    -- Instanciation du modèle à tester 
    dut: entity work.exemple_design(rtl)
      port map (
        a => in_a,
        b => in_b,
        q => out_q
       );


### Génération de l'horloge et du signal de mise à zéro

Il faut ensuite générer les signaux d'horloge et de mise à zéro, en
spécifiant les éléments temporels. Les deux signaux seront définis de
façon concurrente. Nous prévoyons une inversion d'horloge à toutes les
10 ns, ce qui donne une période de 20 ns qui correspond à une
fréquence de 50 MHz. L'extrait de code suivant montre les détails:

    -- Reset et clock
    clock <= not clock after 10 ns;
    reset <= '1', '0' after 50 ns;


### Stimulus

Le dernier élément à spécifier est le stimulus, c'est-à-dire les
signaux qui seront appliqués aux entrées de notre modèle à
tester. Nous utilisons un processus pour générer les quatre
combinaisons possibles de nos deux entrées.

      -- Génération du stimulus
      stimulus:
      process begin
        -- Attendre que reset soit activé
        wait until (reset = '0');
    
        -- Générer chaque condition, avec 2 périodes entre chaque
        -- itération pour laisser du temps pour la propagation
        and_in <= "00";
        wait for 20 ns;
        and_in <= "01";
        wait for 20 ns;
        and_in <= "10";
        wait for 20 ns;
        and_in <= "11";
    
        -- Fin du test
        wait;
      end process stimulus;
    
    end architecture exemple_tb;


### Exemples complets

Dans le premier exemple, nous faisons appel ici au mot réservé `alias`
qui permet de rendre le code plus facile à comprendre en nommant un
sous-ensemble du type `array` qui a été utilisé pour générer les
combinaisons d'entrées.

    entity exemple_tb is
    end entity exemple_tb;
    
    architecture test of exemple_tb is
      signal clock  : std_logic := '0';
      signal reset  : std_logic := '1';
      signal and_in : std_logic_vector(1 down 0) := (others => '0');
      alias in_a is and_in(0);
      alias in_b is and_in(1);
      signal out_q  : std_logic;
    begin
      -- Reset et clock
      clock <= not clock after 10 ns;
      reset <= '1', '0' after 50 ns;
      -- Instanciation du modèle à tester 
      dut: entity work.exemple_design(rtl)
        port map (
          a => in_a,
          b => in_b,
          q => out_q );
      -- Génération du stimulus
      stimulus:
      process begin
        wait until (reset = '0');  -- Attendre reset relâché
        -- Générer chaque condition, avec 2 périodes entre chaque
        -- itération pour laisser du temps pour la propagation
        and_in <= "00";
        wait for 2 ns;
        and_in <= "01";
        wait for 2 ns;
        and_in <= "10";
        wait for 2 ns;
        and_in <= "11";
        -- Fin du test
        wait;
      end process stimulus;
    end architecture exemple_tb;

Le listage du deuxième exemple de banc d'essai, qui teste le
fonctionnement d'un compteur haut/bas de quatre bits modélisé de façon
comportementale, est présenté en trois portions. Une façon différente
de générer le signal d'horloge y est utilisée.

    library ieee;
    use ieee.std_logic_1164.all;
    use ieee.numeric_std.all;
    
    
    entity up_down_counter is
      port( clock : in std_logic;
            reset : in std_logic;
            up_down : in std_logic;
            counter : out std_logic_vector(3 downto 0));
    end up_down_counter;
    
    architecture bhv of up_down_counter is
      signal t_count: unsigned(3 downto 0);
    begin
      process (clock, reset)
      begin
        if (reset='1') then
          t_count <= "0000";
        elsif rising_edge(clock) then
          if up_down = '0' then
            t_count <= t_count + 1;
          else
            t_count <= t_count - 1;
          end if;
        end if;
      end process;
    
      counter <= std_logic_vector(t_count);
    end bhv;
    
    
    library ieee;
    use ieee.std_logic_1164.all;
    use ieee.numeric_std.all;
    
    entity tb_up_down is
    end tb_up_down;

    39  architecture behavior of tb_up_down is
    40  
    41  -- déclaration de composant pour le modèle à tester
    42  
    43  component up_down_counter
    44  port(
    45  clock : in std_logic;
    46  reset : in std_logic;
    47  up_down : in std_logic;
    48  counter : out std_logic_vector(3 downto 0)
    49  );
    50  end component up_down_counter;
    51  
    52  --Inputs
    53  signal clock : std_logic := '0';
    54  signal reset : std_logic := '0';
    55  signal up_down : std_logic := '0';
    56  
    57  --Outputs
    58  signal counter : std_logic_vector(3 downto 0);
    59  
    60  -- Clock period definitions
    61  constant clock_period : time := 20 ns;
    62  
    63  begin
    64  
    65  -- Instanciation du composant à tester
    66  uut: component up_down_counter
    67    port map (
    68      clock => clock,
    69      reset => reset,
    70      up_down => up_down,
    71      counter => counter
    72  );
    73  

    73  
    74  -- Processus d'horloge
    75  clock_process: process
    76  begin
    77  clock <= '0';
    78  wait for clock_period/2;
    79  clock <= '1';
    80  wait for clock_period/2;
    81  end process;
    82  
    83  -- Processus de stimulus
    84  stim_proc: process
    85  begin
    86  -- hold reset state for 100 ns.
    87  wait for 20 ns;
    88  reset <= '1';
    89  wait for 20 ns;
    90  reset <= '0';
    91  up_down <= '0';
    92  wait for 200 ns;
    93  up_down <= '1';
    94  wait;
    95  end process;
    96  
    97  end;


## Compilation et simulation

Voici enfin les grandes étapes permettant de passer de la spécification d'un
modèle à une simulation du comportement du circuit modélisé. 

1.  Créer un fichier VHDL. Ce fichier ne contient qu'une seule paire
    entité.architecture de niveau supérieur, qui sera le banc
    d'essai. Il y aura typiquement d'autres entités de niveau
    inférieur, notamment le modèle de circuit à simuler.

    entity MACHIN is
    ...
    end MACHIN;
    
    architecture TRUC of MACHIN is
    ...
    end TRUC;

1.  Compiler cette description. Les commandes à utiliser dépendent du
    simulateur qui est utilisé, mais deux étapes sont normalement
    requises:
    -   l'**analyse** du code source
    -   l'**élaboration** du design

2.  Une fois le design élaboré, on peut **simuler** le résultat. Si le
    simulateur ne permet pas directement la visualisation des
    résultats, il faudra sauvegarder les résultats de simulation sous un
    format qui permettra ensuite de les visualiser avec un autre outil.

3.  Pour **visualiser** le résultat, on peut utiliser un outil intégré ou encore un
    outil externe qui permet de visualiser les signaux obtenus (formes d'ondes,
    résultats interprétés).


# Préparation et simulation des modèles VHDL


## Éditeurs

N'importe quel éditeur de programmation peut être utilisé pour éditer
les modèles VHDL. Certains simulateurs comportent un éditeur
intégré. Il peut être avantageux d'utiliser un éditeur avec fonction
de surlignage syntaxique pour le langage.


## Simulateurs gratuits

Voici quelques simulateurs gratuits. 


### Modelsim/Questa

Des versions de ce simulateur sont offertes par plusieurs fabricants
de circuits intégrés programmables:

Intel: 

[FPGA Software Download Center](https://www.intel.com/content/www/us/en/collections/products/fpga/software/downloads.html?s=Newest&f=%255B%257B%2522name%2522%3A%2522quartusedition%2522%2C%2522facetId%2522%3A%2522quartusedition%2522%2C%2522currentValues%2522%3A%255B%255D%257D%2C%257B%2522name%2522%3A%2522quartusaddon%2522%2C%2522facetId%2522%3A%2522quartusaddon%2522%2C%2522currentValues%2522%3A%255B%257B%2522value%2522%3A%2522Intel%25C2%25AE%2520FPGA%2520Simulation%2520Tools%2522%2C%2522state%2522%3A%2522idle%2522%2C%2522children%2522%3A%255B%257B%2522value%2522%3A%2522Questa*-Intel%25C2%25AE%2520FPGA%2520Starter%2520Edition%2522%2C%2522state%2522%3A%2522selected%2522%257D%255D%257D%255D%257D%2C%257B%2522name%2522%3A%2522fpgadevicefamily%2522%2C%2522facetId%2522%3A%2522fpgadevicefamily%2522%2C%2522currentValues%2522%3A%255B%255D%257D%2C%257B%2522name%2522%3A%2522fpgaplatform%2522%2C%2522facetId%2522%3A%2522fpgaplatform%2522%2C%2522currentValues%2522%3A%255B%255D%257D%2C%257B%2522facetId%2522%3A%2522os-rdc%2522%2C%2522name%2522%3A%2522OperatingSystem%2522%2C%2522currentValues%2522%3A%255B%255D%257D%2C%257B%2522facetId%2522%3A%2522%40emtcontenttype_en%2522%2C%2522name%2522%3A%2522ContentType%2522%2C%2522currentValues%2522%3A%255B%255D%257D%2C%257B%2522facetId%2522%3A%2522lastupdated-rdc%2522%2C%2522name%2522%3A%2522lastupdated%2522%2C%2522currentValues%2522%3A%255B%255D%257D%255D&q=lite)

-   Fonctionne sous Windows ou Linux (Red Hat ou Ubuntu)
-   Un des simulateurs les plus populaires
-   L'utilisation requiert une licence (gratuite) spécifique à un
    ordinateur donné, qu'il faut demander par courriel
-   L'installation et l'activation comportent plusieurs étapes

Lattice:

[iCEcube2 Design Software](http://www.latticesemi.com/icecube2)

-   Fonctionne sous Windows ou Linux (Red Hat)
-   Fait partie d'une suite logicielle en support à la gamme de FPGA du
    fabricant
-   L'utilisation requiert une licence (gratuite) spécifique à un
    ordinateur donné

Microchip:

[Libero SoC Design Suite](https://www.microchip.com/en-us/products/fpgas-and-plds/fpga-and-soc-design-tools/fpga/libero-software-later-versions#downloads)

-   Fonctionne sous Windows ou Linux (Red Hat)
-   Fait partie d'un suite logicielle (Libero) en support à la gamme de
    FPGA du fabricant
-   L'utilisation requiert une licence (gratuite) spécifique à un
    ordinateur donné


### Active-HDL (version étudiante)

[Free Active-HDL Student Edition](https://www.aldec.com/en/products/fpga_simulation/active_hdl_student)

-   Fonctionne sous Windows
-   Licence gratuite pour la communauté étudiante (on doit indiquer son université)
-   L'inscription donne accès à une page de téléchargement


### Vivado (Xilinx)

[Xilinx téléchargements](https://www.xilinx.com/support/download.html)

-   Fonctionne sous Windows ou Linux (Red Hat ou Ubuntu)
-   Cette suite pour conception de circuits intégrés programmables
    comporte un simulateur
-   L'utilisation requiert une licence (gratuite) spécifique à un
    ordinateur donné


### GHDL/GTKWave

<http://ghdl.free.fr/>

<https://github.com/ghdl/ghdl>

<http://gtkwave.sourceforge.net/>

<https://github.com/gtkwave/gtkwave>

Ces deux logiciels sont à code source ouvert, donc entièrement
gratuits.

-   Fonctionnent sous Windows, Mac ou Linux
-   GHDL est utilisé pour la simulation
-   GTKWave est utilisé pour visualiser les résultats


### EDA Playground

[EDA Playground](https://www.edaplayground.com/)

-   Cette option, utilisable via un fureteur Web, ne nécessite pas
    d'installation et peut donc s'utiliser sur toutes les plateformes
-   On doit s'enregistrer
-   Il est possible de choisir le simulateur
-   On y trouve également des exemples de codes


# Exercices


## Série 1


### Question

Effectuez la conversion des nombres suivants dans la base demandée:

1.  $(32)_{10} = ( )_{2}$

2.  $(F8,A7)_{16} = ( )_{2}$

3.  $(65)_{8} = ( )_{16}$

4.  $(240,51)_{8} = ( )_{10}$

5.  $(25)_{10} = ( )_{8}$

6.  $(100101011)_{2} = ( )_{10}$

7.  $(28)_{10} = ( )_{2}$

8.  $(E3)_{16} = ( )_{2}$

9.  $(B3)_{16} = ( )_{8}$

10. $(11001011101)_{2} = ( )_{16}$

11. $(754)_{8} = ( )_{10}$

12. $(106)_{8} = ( )_{16}$

13. $(27,52)_{10} = ( )_{2}$

14. $(4F,3D9)_{16} = ( )_{2}$

15. $(73,313)_{8} = ( )_{16}$

16. $(364,3)_{8} = ( )_{10}$

17. $(25)_{10} = ( )_{8}$

18. $(111101011)_{2} = ( )_{10}$

19. $(31,22)_{10} = ( )_{2}$

20. $(43,39)_{16} = ( )_{2}$

21. $(43,37)_{8} = ( )_{8}$

22. $(36)_{8} = ( )_{10}$

23. $(25)_{10} = ( )_{8}$

24. $(101101111)_{2} = ( )_{10}$


### Question

Donnez le nombre minimum de bits nécessaires pour définir un code
   pour représenter:

1.  les chiffres de 0 à 9

2.  les nombres de -17 à 17

3.  les lettres A &hellip; Z et les chiffres 0 &hellip; 9

4.  alphanumérique pour les lettres A &hellip; Z, a &hellip; z et les
    chiffres 0 &hellip; 9


### Question

Calculez les compléments suivants (pour un nombre de bits $n$):

1.  complément à deux de $(1101011)_2$ en supposant $n=8$

2.  complément à deux de $(110101)_2$ en supposant $n=8$

3.  complément à un de $(0101101)_2$ en supposant $n=8$

4.  complément à deux de $(01112)_3$ en supposant $n=7$

5.  complément à cinq de $(32402)_5$ en supposant $n=7$

6.  compl. à 2 de $(10110001)_2$

7.  compl. à 2 de $(0001101)_2$

8.  compl. à 1 de $(0101101)_2$

9.  compl. à 2 de $(02112)_3$

10. compl. à 5 de $(42102)_5$


### Question

Effectuez les calculs suivants selon la méthode indiquée:

1.  $(2CF3)_{16} + (2B)_{16}$, (add. directe base 16). Réponse: $( )_{16}$

2.  $(704)_{8} + (230)_{8}$, add. directe base 8, conversion). Réponse: $( )_{8} = ( )_{10}$

3.  $(34)_{8} - (42)_{8}$, complément à 2, conversion. Réponse: $( )_{2} = ( )_{16}$

4.  $(11011101)_{2} - (55)_{10}$, complément à 2, conversion. Réponse: $( )_{2}$

5.  $(AC)_{16} + (4)_{16}$ par addition directe en base 16. Réponse: $( )_{16}$

6.  $(E1)_{16} - (1B)_{16}$ en utilisant le complément à 1 en base 2. Réponse: $( )_{16}$

7.  $(46)_{8} - (73)_{8}$ en utilisant le complément à 2 en base 2. Réponse: $( )_{16}$

8.  $(BE)_{16} + (22)_{16}$, (add. directe base 16). Réponse: $( )_{16}$

9.  $(73)_{8} + (103)_{8}$, add. directe base 8, conversion). Réponse: $( )_{8} = ( )_{10}$

10. $(22)_{8} - (26)_{8}$, compl. à 2, conversion. Réponse: $( )_{2} = ( )_{16}$

11. $(11011100)_{2} - (57)_{10}$, compl. à 2, conversion. Réponse: $( )_{2}$

12. $(AE)_{16} + (12)_{16}$, (add. directe base 16). Réponse: $( )_{16}$

13. $(63)_{8} + (135)_{8}$, add. directe base 8, conversion). Réponse: $( )_{8} = ( )_{10}$

14. $(35)_{8} - (26)_{8}$, compl. à 2, conversion. Réponse: $( )_{2} = ( )_{16}$

15. $(11011100)_{2} - (55)_{10}$, compl. à 2, conversion. Réponse: $( )_{2}$


### Question

Vous disposez de blocs permettant de calculer les fonctions
   suivantes:

-   **C4:** complément à un d'un nombre de 4 bits

-   **ADD4:** addition de deux nombres de 4 bits, avec entrée pour retenue et
    retenue de sortie.

Indiquez par un schéma-bloc comment on peut relier ces blocs pour
calculer:

1.  le complément à deux d'un nombre de 4 bits

2.  le complément à deux d'un nombre de 8 bits

3.  la somme de deux nombres de 8 bits

4.  la soustraction de nombres de 4 bits


### Question

Un réseau informatique comporte 60 ordinateurs. On doit assigner à
   chacun de ces ordinateurs un mot-code binaire unique.

1.  Combien de bits par mot sont nécessaire pour la codification?

2.  Combien de mots-code ne seront pas utilisés?


### Question

Selon les critères d'achat du service des achats d'une entreprise, un
  article sera acheté s'il remplit au moins une des conditions
  suivantes:

-   il est peu coûteux ou de qualité, tout en étant disponible
    rapidement,

-   il est peu coûteux et n'est pas disponible rapidement,

-   il est coûteux et de mauvaise qualité, tout en étant disponible
    rapidement.

En utilisant la notation suivante:

-   **A:** coûteux

-   **B:** de bonne qualité

-   **C:** disponible rapidement

-   Exprimez les critères d'achat sous forme d'une expression
    booléenne (non-simplifiée).

-   Donnez le tableau de vérité de la fonction logique des critères
    d'achat.

-   Donnez la forme canonique, en somme de produit, de la fonction
    logique des critères d'achat.

-   Déterminez si les expressions logiques suivantes sont égales à la
    fonction logique des critères d'achat:
    
    $$F_1 = A^{\prime} B^{\prime} + B^{\prime} C^{\prime}$$
    
    $$F_2 = A^{\prime} B^{\prime} C^{\prime} + A^{\prime} B^{\prime} C + A^{\prime} B C^{\prime} + A B^{\prime} C^{\prime}$$
    
    $$F_2 = B^{\prime} C^{\prime} + A^{\prime} B^{\prime} + A^{\prime} C$$


### Question

Donnez le nombre minimum de bits nécessaires pour définir un code pour représenter

1.  les jours de la semaine

2.  les jours du mois

3.  les jours dans l'année (nombre entre 1 et 365)

4.  les jours de l'année (mois et date)

5.  une date de naissance (jour, mois, année)


## Série 2


### Question

La fonction logique à trois entrées $S = F(A,B,C)$ donnée par son 
   tableau de vérité:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(A\)</th>
<th scope="col" class="org-right">\(B\)</th>
<th scope="col" class="org-right">\(C\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(S\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>
</tbody>
</table>

doit être implémentée par un circuit logique.

1.  Donnez l'expression de cette fonction:
    -   Selon la première forme canonique ( $\sum m_i$ )
    
    -   Selon la deuxième forme canonique ( $\prod M_i$ )

2.  Trouvez une expression simplifiée pour la fonction en utilisant
    les théorèmes de l'algèbre de Boole.

3.  Dessinez le circuit logique correspondant à l'expression
    simplifiée trouvée.


### Question

Trouvez le complément de la fonction logique donnée par l'expression
   suivante en utilisant trois méthodes différentes.
   $$
    s = b (a^{\prime} c^{\prime} + a d + a c) + (b + c^{\prime}+
      d)^{\prime} + a^{\prime} b c^{\prime} d + a b c d
    $$


### Question

Considérez la fonction logique définie par l'expression $F =
      [ (C + B) A^{\prime} + (A+B)^{\prime} ] B^{\prime}$.

1.  Dessinez le circuit logique correspondant.

2.  Dessinez un circuit équivalent qui n'utilise que des portes
    NAND.

3.  Dessinez un circuit équivalent qui n'utilise que des portes
    NOR.


### Question

On doit concevoir un circuit logique qui détermine le complément à deux
  d'une entrée $a$ binaire (signée) de 4 bits notés
  $a_3, a_2, a_1, a_0$. Il y aura donc 4 bits de sortie, $s_3,
      s_2, s_1, s_0$. En considérant chacun des bits de sortie comme une
  fonction des quatre bits d'entrée, par ex. $s_3 = f(a_3, a_2, a_1,
      a_0)$, donnez les tableaux de vérité pour $s_3, s_2, s_1$, et $s_0$.


### Question

Complétez la figure ci-dessous (en ajoutant des connexions) afin de
  réaliser la fonction 
  $$
    S= a^\prime + b^\prime + c d
    $$
  ![img](Modeles_exercices/exbloc2a.svg)


### Question

Complétez la figure ci-dessous (en ajoutant des connexions) afin de
  réaliser une fonction dont la sortie est 

-   $S=1$ lorsque l'entrée est $ \leq 3$ ou impaire
-   $S=0$ dans les autres cas.

    L'entrée $(a_3,a_2,a_1, a_0)$ représente un nombre entier
   décimal codé en BCD. Les entrées $ \geq 9$ peuvent donner
   n'importe quelle sortie.
![img](Modeles_exercices/exbloc2b.svg)


### Question

Dessinez le circuit logique de la fonction $S = a b + c^\prime +
    d^\prime $ en utilisant au plus quatre portes NAND.


### Question

Simplifiez la fonction logique donnée par l'expression suivante:
  $$
    s = b (a^{\prime} c^{\prime} + a d + a c) + (b + c^{\prime}+
      d)^{\prime} + a^{\prime} b c^{\prime} d + a b c d
    $$ 
  au moyen d'un
  diagramme de Karnaugh. Identifiez sur le diagramme les regroupements
  essentiels, les regroupements absoluments inutiles et les
  regroupements pour lesquels on a le choix. Donnez deux solutions
  aussi simplifiées.


### Question

Considérez la fonction logique définie par l'expression 
  $$
    F = [ (A + B) C^{\prime} + (A+B)^{\prime} ] B^{\prime}
    $$

1.  Dessinez le circuit logique correspondant.

2.  Dessinez un circuit équivalent qui n'utilise que des portes
    NAND.

3.  Dessinez un circuit équivalent qui n'utilise que des portes
    NOR.

4.  Dessinez un circuit équivalent qui ne comporte que trois niveaux de
    portes (incluant les inversions).


### Question

Simplifiez la fonction logique donnée par l'expression suivante:
  $$
    s = a b ( c^{\prime} d^{\prime} + c d) + c^{\prime}(a^{\prime}
      b^{\prime} + a^{\prime} b)
    $$
   au moyen d'un diagramme de Karnaugh. Donnez deux solutions aussi simplifiées.


### Question

Considérez la fonction logique définie par l'expression $F = (AB + C)
      A^{\prime} + C + A^{\prime}$.

1.  Dessinez le circuit logique correspondant.

2.  Dessinez un circuit équivalent qui n'utilise que des portes
    NAND.

3.  Dessinez un circuit équivalent qui n'utilise que des portes
    NOR.

4.  Dessinez un circuit équivalent qui ne comporte que deux niveaux de
    portes (excluant les inversions).


### Question

Donnez le tableau  de vérité des deux fonctions qui, à partir d'une
  entrée binaire non-signée sur trois bits, donnent en sortie la
  représentation binaire non-signée sur deux bits du plus grand diviseur
  $< 3$ de l'entrée, s'il y a lieu. Simplifiez les deux fonctions en
  tenant compte des cas facultatifs.


### Question

Complétez la figure ci-dessous (en ajoutant des connexions) afin de
  réaliser une  fonction NAND à trois entrées $S = (a b c)^\prime$.
  ![img](Modeles_exercices/exbloc2c.svg)


### Question

Dans une application numérique, on doit concevoir un circuit logique
qui permet de détecter les nombre composés, qui peuvent être
décomposés en facteurs (nombres qui ne sont pas premiers. Le circuit
doit donner une sortie 1 quand un nombre composé est présenté à
l'entrée; par exemple, le circuit doit donner 1 pour une entrée 4
(0100) et 0 pour une entrée 3 (0011). Les nombres 0 et 1 seront
considérés comme des cas facultatifs.

1.  Donnez le tableau de vérité pour réaliser cette application pour
    un mot d'entrée (non-signé) de quatre bits, $a, b, c$ et $d$.

2.  Au moyen d'un diagramme de Karnaugh, trouvez une expression
    logique simplifiée pour cette fonction logique et ne représentez
    que les impliquants premiers retenus pour la solution.

3.  Donnez le schéma du circuit logique qui implémente cette fonction
    en somme de produit à l'aide de portes NON-ET (pas de restrictions
    sur le nombre d'entrées).


## Série 3


### Question

À l'aide d'un diagramme de Karnaugh, simplifiez 
  $$
    S = A B^\prime +
    B^\prime CD + A^\prime B + B^\prime D + A^\prime B^\prime D
    $$
  en produit de sommes.


### Question

À l'aide d'un diagramme de Karnaugh, simplifiez 
  $$
    S = ( A^\prime +
    B^\prime + C + D)(A+B^\prime +C^\prime +D)(A^\prime +B^\prime
    +C+D^\prime )(A+B^\prime +C^\prime +D^\prime )(A+C^\prime +D)
    $$
  en tenant compte des cas facultatifs suivants: $\sum(3,8,11,14)$.

1.  Donnez une solution qui n'utilise pas l'entrée $D$.
2.  Donnez une solution qui n'utilise pas l'entrée $B$.


### Question

À l'aide de la méthode Quine-McCluskey, simplifiez l'expression
  logique suivante: 
  $$
    F= A^\prime BCDEF^\prime  + A^\prime BCDEF+ AB^\prime CDEF+ ABCDEF^\prime 
    $$
  Tenez compte des cas facultatifs suivants: 
  $$
    A^\prime BCD^\prime EF^\prime +
    ABCDE^\prime F^\prime + A^\prime BCDE^\prime F+ ABCDEF
    $$


### Question

Complétez la figure ci-dessous pour obtenir un multiplicateur dont
  la sortie (5 bits) est le produite de deux entrées (de 3 bits et 2
  bits, respectivement). Comme on peut voir sur la figure, on dispose
  de quatre additionneurs complets à 1 bit et de six portes ET. La
  multiplication sera $$(P_4, P_3, P_2, P_1, P_0)_2 = (y_2, y_1, y_0)_2
    \times (z_1, z_0)_2$$.
  ![img](Modeles_exercices/exbloc3a.svg)


### Question

Considérez la fonction logique $F$ définie par le tableau de vérité suivant

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(A\)</th>
<th scope="col" class="org-right">\(B\)</th>
<th scope="col" class="org-right">\(C\)</th>
<th scope="col" class="org-right">\(D\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(F\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Vous devez réaliser cette fonction au moyen d'un multiplexeur à huit
entrées sans utiliser la variable $A$ dans les lignes de
sélection. Complétez le tableau de réalisation et la figure
ci-dessous.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-left">\(E_0\)</th>
<th scope="col" class="org-left">\(E_1\)</th>
<th scope="col" class="org-left">\(E_2\)</th>
<th scope="col" class="org-left">\(E_3\)</th>
<th scope="col" class="org-left">\(E_4\)</th>
<th scope="col" class="org-left">\(E_5\)</th>
<th scope="col" class="org-left">\(E_6\)</th>
<th scope="col" class="org-left">\(E_7\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">\(A\)</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
</tr>


<tr>
<td class="org-left">\(A^\prime\)</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
</tr>
</tbody>
</table>

![img](Modeles_exercices/exbloc3b.svg)


### Question

Simplifiez la fonction logique à six entrées
  $$
    S = F(A,B,C,D,E,F)
    $$
  représentée par la liste de minterms suivants

010000, 101000, 110100, 110101, 110110, 111100

en tenant compte des cas facultatifs représentés par les minterms
suivants

000000, 001100, 000111, 101001, 110111

par la méthode de Quine-McCluskey. Vous devez donner le détail de
toutes les étapes, remplir les tableaux de couverture initial et
réduit, identifier les impliquants premiers essentiels (i.p.e.), les
impliquants premiers absolument inessentiels (i.p.a.i.) et les
impliquants premiers inessentiels tout court (i.p.i.). Donnez la
solution sous la forme d'une expression en $A,B,C,D,E,F$.


### Question

Réalisez les fonctions logiques suivantes au moyen d'un multiplexeur
  quatre-vers-un.

1.  $$f_1(a,b,c) = \sum m(2, 4, 5, 7)$$

2.  $$f_2(a,b,c) = \prod M(0, 6, 7)$$


### Question

Identifiez la fonction réalisée par le circuit ci-dessous, en donnant
  la liste des minterms en fonction des entrées $a, b, c$ et $d$.
![img](Modeles_exercices/exbloc3c.svg)


### Question

Un circuit combinatoire est défini par les trois fonctions logiques
  suivantes. Dessinez un circuit réalisant ces trois fonctions en
  utilisant un décodeur constitué de portes NAND (vous devez dessiner
  le schéma du décodeur), et des portes NAND et ET
  externes.
  $$
     F_1  = x y^{\prime} + x^{\prime}y
    z^{\prime} 
    $$
  $$
    F_2  =  (x + y^{\prime})z 
    $$
  $$ F_3  =  (x^{\prime}
    y + x y^{\prime} z)^{\prime}
    $$


### Question

Simplifiez la fonction donnée par l'expression suivante
  $$
    a^{\prime} b^{\prime} c d + a b c d + a b^{\prime} c^{\prime} d +
	a b c d^{\prime}
    $$
  en considérant les cas facultatifs suivants
  $$
    a b c^{\prime} + a^{\prime} b c^{\prime} d^{\prime} + a b^{\prime}
	c d^{\prime}
    $$
  par la méthode de Quine-McCluskey. Vous devez
  donner le détail de toutes les étapes, identifier à la fin les
  impliquants premiers essentiels (i.p.e.), les impliquants premiers
  absolument inessentiels (i.p.a.i.) et les impliquants premiers
  inessentiels tout court (i.p.i.). et donner la solution finale avec
  les variables.


### Question

Concevez un circuit qui permet de comparer deux mots de 3 bits et qui
  donne 1 lorsqu'ils sont égaux et 0 sinon. Vous devez utiliser des
  portes XOR et d'autres portes.


### Question

La fonction logique à quatre entrées $S = F(A,B,C, D)$ donnée par son 
  tableau de vérité:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">\(A\)</th>
<th scope="col" class="org-right">\(B\)</th>
<th scope="col" class="org-right">\(C\)</th>
<th scope="col" class="org-right">\(D\)</th>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">\(S\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">X</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">X</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">X</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-left">&#xa0;</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

doit être implémentée par un circuit logique.

1.  Simplifiez la description de cette fonction en utilisant un diagramme de Karnaugh.

2.  Trouvez le tableau de couverture pour la fonction et réduisez-le en tableau réduit.

3.  Identifiez les impliquants premiers essentiels (i.p.e.), les
    impliquants premiers absolument inessentiels (i.p.a.i.) et les
    impliquants premiers inessentiels tout court (i.p.i.).

4.  Dessinez le circuit logique simplifié, réalisé en n'utilisant que des portes NAND.


### Question

Un circuit combinatoire est défini par les trois fonctions logiques
  suivantes. Dessinez un circuit réalisant ces trois fonctions en
  utilisant un décodeur et des portes externes.
  $$
    F_1  = x^{\prime} y^{\prime} z^{\prime} + xz 
    $$
  $$
    F_2  = x y z^{\prime} + x^{\prime} y 
    $$
  $$
    F_3  = x^{\prime} y^{\prime} z + x y
    $$


### Question

 Identifiez la fonction logique $F(A,B,C,D)$ définie par le circuit
   logique suivant:
![img](Modeles_exercices/exbloc3d.svg)

1.  Donnez son tableau de vérité.

2.  Donnez la forme canonique somme de produits de cette fonction.


### Question

Considérez le tableau de couverture suivant:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">&#xa0;</th>
<th scope="col" class="org-right">0101</th>
<th scope="col" class="org-right">0110</th>
<th scope="col" class="org-right">0000</th>
<th scope="col" class="org-right">1100</th>
<th scope="col" class="org-right">1101</th>
<th scope="col" class="org-right">1011</th>
<th scope="col" class="org-right">0111</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">−10−</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
</tr>


<tr>
<td class="org-left">110−</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
</tr>


<tr>
<td class="org-left">1011</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
</tr>


<tr>
<td class="org-left">−00−</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
</tr>


<tr>
<td class="org-left">01−−</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
</tr>


<tr>
<td class="org-left">−111</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
<td class="org-right">&#xa0;</td>
</tr>
</tbody>
</table>

1.  Complétez le tableau en mettant les '+' dans les cases
    appropriées.

2.  Identifiez les i.p.e. et les i.p.a.i.

3.  Donnez les cas facultatifs qui ont été utilisés pour obtenir les
    i.p.

4.  Donnez le tableau réduit correspondant.

5.  Donnez un exemple de ligne qui en domine une autre.

6.  Donnez un exemple de colonne qui en domine une autre.

7.  Donnez une forme canonique de la fonction.

8.  Donnez l'expression simplifiée de la fonction $F(u,v,w,x)$.


### Question

Trouvez l'expression minimale pour les deux fonctions suivantes,
   sachant qu'elles doivent être implémentées dans un même
   circuit. Utilisez la méthode Quine-McCluskey.
   $$
     F_1(A, B, C, D)
     =\sum(2,5,6,7,10,11,14,15)
     $$
   $$
     F_2 = A B C D + A^\prime B C D +
     A^\prime B^\prime C D + A B^\prime C + ABC
     $$


### Question

La fonction logique à trois entrées $S = F(A,B,C)$ représentée par le
  tableau de vérité:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">A</th>
<th scope="col" class="org-right">B</th>
<th scope="col" class="org-right">C</th>
<th scope="col" class="org-right">S</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

doit être implémentée par un circuit logique.

1.  Donnez l'expression de cette fonction:
    -   Selon la première forme canonique ( $\sum m_i$ )
    
    -   Selon la deuxième forme canonique ( $\prod M_i$ )

2.  Trouvez une expression simplifié pour cette fonction en utilisant
    un diagramme de Karnaugh en format horizontal.

3.  Donnez l'expression du **complément** de cette fonction:
    -   Selon la première forme canonique ( $\sum m_i$ )
    
    -   En complémentant votre expression simplifiée au moyen du
        théorême de DeMorgan.

4.  Dessinez le circuit logique à partir de l'expression simplifiée
    trouvée.


### Question

Simplifiez la fonction logique donnée par la forme canonique
  suivante:
  $$
    m_0 + m_2 + m_4 + m_5 + m_8 + m_A + m_B + m_E
    $$
  au
  moyen d'un diagramme de Karnaugh (la numérotation des termes est en
  hexadécimal). Identifiez sur le diagramme les regroupements
  essentiels, les regroupements absoluments inutiles et les
  regroupements pour lesquels on a le choix. Donnez deux solutions
  aussi simplifiées.


### Question

Considérez la fonction logique définie par l'expression
  $$
    F =
      (A + B) A^{\prime} C + C^{\prime}(A+B^{\prime}) + A^{\prime}B
      C^{\prime}
    $$

1.  Dessinez le circuit logique correspondant.

2.  Dessinez un circuit équivalent qui n'utilise que des portes
    NAND.

3.  Dessinez un circuit équivalent qui n'utilise que des portes
    NOR.

4.  Dessinez un circuit équivalent qui ne comporte que 3 niveaux de
    portes (incluant les inversions).


### Question

Donnez le tableau de vérité pour les fonctions logiques correspondant
  à:

1.  $$f(A, B) = A + B^{\prime}$$

2.  $$f(a, b, c) = a(b+c^{\prime})(b^{\prime}+c)$$


### Question

Considérez la fonction logique donnée par l'expression suivante:

\begin{multline*}
F = A^{\prime} B^{\prime} C^{\prime} D^{\prime} E^{\prime} + {A} B^{\prime} C^{\prime} D^{\prime} E^{\prime} + A^{\prime} B^{\prime} {C} D^{\prime} E^{\prime} + A^{\prime} {B} {C} {D} E^{\prime} \\ + {A} {B} C^{\prime} D^{\prime} {E} + {A} B^{\prime} C^{\prime} D^{\prime} {E} + {A} B^{\prime} D^{\prime} E^{\prime} \\ + {A} B^{\prime} {C} {D} {E} + {A} B^{\prime}  {C} D^{\prime} {E}
\end{multline*}

Les cas suivants sont facultatifs:

\begin{displaymath}
A^{\prime} B^{\prime} C^{\prime} D^{\prime} {E} + {A} {B} C^{\prime} {D} {E} +  A^{\prime}B^{\prime} {C} D^{\prime} {E} + {A} {B} {C} D^{\prime} {E}
\end{displaymath}

1.  Simplifiez cette expression logique par la méthode de
    Quine-McCluskey, en tenant compte des cas facultatifs. Identifiez
    clairement les implicants essentiels et non-essentiels.

2.  Dessinez un réseau logique qui réalise votre expression logique
    simplifiée en n'utilisant que des portes NAND.


### Question

Vous devez concevoir un circuit logique combinatoire qui calcule la
valeur absolue d'un nombre de 4 bits signé en complément à deux. Les
seules valeurs d'entrée possibles sont donc de -7 à 7 inclusivement,
les autres nombres seront considérées comme des cas facultatifs. Vous
disposez de composants programmables pour réaliser cette fonction.

1.  Réalisez votre circuit logique combinatoire en utilisant un PROM à
    quatre entrées et deux sorties tel qu'illustré.
    Vous devez mettre des croix aux endroits où vous voulez que les
    connections soient effectuées (dans la section programmable).

![img](Modeles_exercices/prom4.svg)

1.  Réalisez votre circuit logique combinatoire en utilisant le PAL à
    quatre entrées et trois sorties tel qu'illustré.
    Vous devez mettre des croix aux endroits où vous voulez que les
    connections soient effectuées (dans la section programmable).

![img](Modeles_exercices/pal3.svg)


### Question

Considérez le circuit logique ci-dessous. Le signal $A$ passe de 0 à 1
l'instant 15 ns; le signal $B$ passe de 1 à 0 à l'instant 15 ns; le
signal $C$ passe de 1 à 0 à l'instant 60 ns.
![img](Modeles_exercices/exbloc3e.svg)

1.  Complétez un chronogramme qui montre les traces pour chacun des
    signaux d'entrée $A, B, C$ et de sortie $T, U, V, X, Y, Z_1,
           Z_2, Z_3, F$, en supposant un temps de propagation de 10 ns
    pour toutes les portes. Identifiez clairement sur le
    chronogramme les temps de propagation et les éventuels problèmes
    (glitchs) occasionnés par les délais.

2.  Identifiez la fonction logique réalisée par ce circuit logique.

3.  Déterminer le délai de propagation (des entrées à la sortie)
    maximal pour ce circuit, et précisez le chemin critique.

4.  Si ce circuit doit être utilisé à répétition, de façon périodique,
    quelle est la plus courte période qu'on puisse utiliser tout en
    étant sûr que le circuit fonctionne correctement.

5.  On désire remplacer ce circuit par un circuit à trois niveaux
    logiques. Donnez le schéma d'un circuit en forme somme de produit
    qui remplit la même fonction.

6.  Donnez le délai de propagation maximal pour le nouveau circuit
    somme de produit.


## Série 4


### Question

Construisez un décodeur 5-vers-32 en utilisant quatre décodeurs
  3-vers-8 avec entrée *enable*.


### Question

Vous devez concevoir un encodeur à priorité à quatre
  entrées. L'entrée $D_0$ doit avoir la plus grande priorité et
  l'entrée $D_3$ doit avoir la plus faible priorité, avec la
  priorité des autres entrées qui suivent le même ordre. Les sorties
  seront $s_1, s_0$ et $v$ qui indique la validité des sorties:
  $v=0$ si toutes les entrées sont à 0; $v=1$ si au moins une
  entrée est 1.


### Question

Un circuit séquentiel à deux bascules D, $A$ et $B$, comporte
  deux entrées $x$ et $y$ et une sortie $z$. Les équations de
  prochain état sont:

$$A_{n+1} = x^\prime y + x A$$

$$B_{n+1} = x^\prime B + x A$$

L'équation de sortie est 

$$z=B$$

1.  Dessinez le schéma logique du circuit

2.  Déterminez le tableau d'états

3.  Dessinez le diagramme d'état


### Question

 Considérez le circuit logique suivant:
![img](Modeles_exercices/exbloc4a.svg)

1.  Quelle est la fonction combinatoire réalisée par la section
    logique combinatoire, c'est-à-dire, quelle est la fonction $S =
             f(A,B)$ ?

2.  Complétez le diagramme temporel de la figure, en supposant un
    temps de propagation **maximum** de 10 ns pour les portes NOR et OU,
    et de 40 ns pour les bascules.

3.  Si les temps de maintien $t_{h}$ et de mise en place $t_{su}$
    sont de 5 ns pour toutes les bascules, quelle est la fréquence
    maximale d'horloge utilisable pour que le circuit fonctionne
    convenablement? Utilisez un diagramme temporel pour évaluer la
    période minimum.


### Question

 Analysez le circuit logique suivant:
![img](Modeles_exercices/exbloc4b.svg)

1.  Analysez le comportement du circuit, en supposant qu'au départ les
    entrées sont $A=0$ et $B=0$ et la sortie $S=0$. Vous devez
    supposer des changements des valeurs d'entrées et décrire les
    changements des sorties, en tenant compte de la mémoire du
    circuit.

2.  Identifiez la fonction des entrées $A$ et $B$.

3.  Identifiez la fonction du circuit.


### Question

Considérez circuit séquentiel décrit par le diagramme d'état suivant:

![img](Modeles_exercices/ex_bloc5b.svg)

1.  En utilisant l'assignation d'états $a = 00, b = 01, c = 10, d
             = 11$, construisez le tableau d'état pour ce circuit séquentiel.

2.  Concevez le circuit en utilisant des portes standards et des
    bascules D.


### Question

Vous devez concevoir un circuit logique séquentiel à une entrée et
  une sortie qui identifie les deux séquences d'entrée 0110 et 11111
  appliquées immédiatement après une remise à zéro asynchrone du
  circuit. Donnez le diagramme d'état simplifié pour ce circuit.


### Question

Vous devez concevoir un circuit logique séquentiel à une entrée et
 une sortie qui identifie les deux séquences d'entrée 0110
 et 11111. Les séquences d'entrée doivent être identifiées à
 n'importe quel moment où elles apparaissent en entrée.


### Question

Déterminez le diagramme d'état pour un circuit séquentiel synchrone
  avec une entrée $x$ et une sortie $z$ qui est utilisé pour
  reconnaître la séquence d'entrée 101. La sortie doit donc être $z=1$
  lorsque le dernier 1 de la séquence 101 est identifié. $z$ est
  ensuite remis à zéro au prochain coup d'horloge. Deux séquences 101
  peuvent se chevaucher. On a par exemple,
  $$
    x  =  010101101
    $$
  $$ z = 000101001
    $$


### Question

Déterminez le diagramme d'état pour un circuit séquentiel synchrone
  avec une entrée $x$ et une sortie $z$ qui est utilisé pour
  reconnaître la séquence d'entrée 101. La sortie doit donc être $z=1$
  lorsque le dernier 1 de la séquence 101 est identifié. $z$ est
  ensuite remis à zéro au prochain coup d'horloge. Les chevauchements de 101 ne sont pas 
  permis. Par exemple,
  $$
    x = 010101101
    $$
  $$
    z = 000100001
    $$


### Question

Concevez le circuit séquentiel synchrone décrit par le tableau
  d'état ci-dessous. Vous devez considérer des bascules JK et D et
  choisir la solution la plus simple. Présentez clairement toutes les
  étapes, jusqu'au schéma du circuit correspondant.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-right">État courant</th>
<th scope="col" class="org-right">Entrée</th>
<th scope="col" class="org-right">Prochain</th>
<th scope="col" class="org-right">Sortie</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-right">00</td>
<td class="org-right">0</td>
<td class="org-right">01</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">00</td>
<td class="org-right">1</td>
<td class="org-right">11</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">01</td>
<td class="org-right">0</td>
<td class="org-right">10</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">01</td>
<td class="org-right">1</td>
<td class="org-right">00</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">11</td>
<td class="org-right">0</td>
<td class="org-right">00</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">11</td>
<td class="org-right">1</td>
<td class="org-right">10</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-right">10</td>
<td class="org-right">0</td>
<td class="org-right">10</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-right">10</td>
<td class="org-right">1</td>
<td class="org-right">01</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>


### Question

Les deux bascules du circuit suivant sont activées par les
   transitions montantes du signal présent à leur entrée
   d'horloge. 
   ![img](Modeles_exercices/exbloc4c.svg)

Tracez le chronogramme pour $X, X^\prime, Y, S$


### Question

Vous devez analyser le circuit séquentiel suivant:
![img](Modeles_exercices/exbloc4d.svg)

1.  Donnez les équations pour le décodeur de prochain état.

2.  Donnez le tableau d'activation avec état présent, entrée, entrées
    des bascules, prochain état, sortie.

3.  Donnez le diagramme d'état correspondant.

4.  tracez le chronogramme de fonctionnement, en
    faisant abstraction des délais de propagation.

5.  En sachant que la bascule a les caractéristiques suivantes:
    
    -   temps de pré-positionnement minimum: 11 ns
    
    -   temps de maintien minimum: 9 ns
    
    -   temps de propagation maximum: de Horloge à $Q$ ou
        $Q^{\prime}$: $t_{pLH}$ = 15 ns, $t_{pHL}$ = 13 ns.
    
    et en suppoosant un délai de propagation de 15 ns pour la porte
    XOR, déterminez la période minimale et la fréquence
    maximale qu'on puisse utiliser tout en étant assuré que le circuit
    fonctionne correctement. Donnez les détails de votre raisonnement.


### Question

Vous devez concevoir un circuit logique utilisé dans un système
permettant de trier des données. Le circuit reçoit deux nombres
non-signés de 4 bits, multiplexés en série sur une même entrée. Par
exemple, si les entrées sont 1010 et 1110, le circuit recevra

1.  Le circuit doit acheminer le plus grand des deux nombres à

une sortie (parallèle) appelée PG et le plus petit à une sortie
(parallèle) appelée PP. Vous devez réaliser votre circuit en utilisant
les éléments suivants:

-   démultiplexeur un-vers-deux

-   multiplexeur 4 bits deux-vers-un (il s'agit de quatre
    multiplexeurs deux-vers-un à un bit avec le même signal de
    commande, et qui traitent ainsi en parallèle des mots de quatre bits)

-   registre à décalage entrée série/sortie parallèle

-   comparateur de magnitude: deux entrées parallèles de 4 bits: $A$ et
    $B$, trois sorties: $A>B$, $A=B$, $A<B$

-   registre entrée parallèle/sortie parallèle

Donnez un schéma-bloc de votre circuit en indiquant seulement les
blocs qui traitent les données (pas les blocs qui serviront à contrôler
le circuit).


### Question

On doit concevoir un système séquentiel avec une entrée $E$ et une
sortie, et qui génère les séquences de sortie suivantes:

-   si $E=0$, séquence de sortie = 1100, périodique

-   si $E=1$, séquence de sortie = 1011, périodique

On envisage deux versions du système:

-   **version 1:** si  $E$ change, la séquence de sortie suit le
    changement au vol.

-   **version 2:** si $E$ change, la séquence de sortie recommence à
    partir du début.

Par exemple,

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Entrée</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">1</th>
<th scope="col" class="org-right">0</th>
<th scope="col" class="org-right">0</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Sortie version 1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">Sortie version 2</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">0</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

Donnez un diagramme d'état pour chacune des deux versions.


### Question

Considérez le tableau d'état suivant:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">État présent</th>
<th scope="col" class="org-right">Entrée \(A\)</th>
<th scope="col" class="org-left">État suivant</th>
<th scope="col" class="org-right">Sortie \(S\)</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">a</td>
<td class="org-right">0</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">a</td>
<td class="org-right">1</td>
<td class="org-left">a</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">0</td>
<td class="org-left">e</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">b</td>
<td class="org-right">1</td>
<td class="org-left">f</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">0</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">c</td>
<td class="org-right">1</td>
<td class="org-left">d</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-right">0</td>
<td class="org-left">a</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">d</td>
<td class="org-right">1</td>
<td class="org-left">b</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">0</td>
<td class="org-left">e</td>
<td class="org-right">0</td>
</tr>


<tr>
<td class="org-left">e</td>
<td class="org-right">1</td>
<td class="org-left">f</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-right">0</td>
<td class="org-left">c</td>
<td class="org-right">1</td>
</tr>


<tr>
<td class="org-left">f</td>
<td class="org-right">1</td>
<td class="org-left">f</td>
<td class="org-right">1</td>
</tr>
</tbody>
</table>

correspondant à un circuit séquentiel synchrone.

1.  Simplifiez ce tableau d'état en identifiant les états
    équivalents, en utilisant la méthode du tableau d'implication.

2.  Donnez le diagramme d'état simplifié correspondant au tableau
    d'état simplifié. Nommez les états simplifiés qui restent a,
    b, c, &hellip;

3.  Assignez des codes aux états, en commençant avec la
    représentation binaire de 0 pour a, de 1 pour b, etc.

4.  Donnez les diagrammes de Karnaugh pour le décodeur de prochain
    état en supposant des bascules JK, et les fonctions simplifiées
    correspondantes.

5.  Donnez le diagramme de Karnaugh pour le décodeur de sortie.

6.  Dessinez le schéma du circuit séquentiel obtenu.


### Question

Considérez le circuit séquentiel synchrone ci-dessous.
![img](Modeles_exercices/exbloc4e.svg)

Déterminez la vitesse d'horloge maximale en considérant les
caractéristiques suivantes:

-   Portes: temps de propagation maximum: 10 ns.

-   Bascules: temps de mise en place minimum: 12 ns.

-   Bascules: temps de maintien minimum: 15 ns.

-   Bascules: temps de propagation maximum: de H à $Q$ ou
    $Q^{\prime}$: $t_{pLH}$ = 25 ns, $t_{pHL}$ = 20 ns.


## Série 5


### Question

Faire le diagramme d'état d'un circuit séquentiel synchrone qui génère
à sa sortie un 1 lorsqu'il détecte à son entrée la séquence 0110 ou la
séquence 0101.


### Question

Un circuit séquentiel synchrone est construit à partir de trois
   bascules, $A$, $B$, et $C$. Il comporte une entrée $x$ et
   une sortie $y$. Son diagramme d'état est donné ci-dessous. 
![img](Modeles_exercices/ex_bloc5.svg)

Vous devez concevoir ce circuit en considérant les états inutilisés
comme des cas facultatifs. Le circuit final doit être analysé pour
déterminer si, à partir des états inutilisés, le système revient vers
son fonctionnement normal.

1.  Conception avec des bascules D
2.  Conception avec des bascules JK


### Question

Faire le diagramme d'état d'un compteur synchrone qui produit les
  séquences d'états suivants, selon la valeur de l'entrée $x$

-   $x=0$, séquence: 0, 6, 2, 1, 4, 0, 6, 2, 1, 4, &hellip;
-   $x=1$, séquence: 0, 6, 5, 7, 2, 1, 0, 6, 5, 7, 2, 1, &hellip;


# Notes de bas de page

<sup><a id="fn.1" href="#fnr.1">1</a></sup> Pour simplifier, dans le contexte, on appellera ici ces cinq
lettres des *chiffres* de la notation hexadécimale.

<sup><a id="fn.2" href="#fnr.2">2</a></sup> Certains postulats viennent en paires; nous les distinguons ici au
moyen d'étiquettes &spades; ou &hearts;.
