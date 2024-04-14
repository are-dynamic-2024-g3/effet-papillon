# L'EFFET PAPILLON DANS TOUTE SA SPLENDEUR
 
    Designed by the magnificients Suvana, Madina, Sathursjan

    
Liens vers les titres :
**|[Les bases de la théorie de l'attracteur de Lorenz](#introduction)|**
**[Les Equations et éléments à prendre en compte](#équations)|**
**[Comment modéliser le phénomène étudié](#modélisation)|**
**[Dépendance des paramètres initiaux](#animation)|**
**[Bibiliographie](#ressources)|**
**[Tableau de bord](#calendrier)|**

L'effet papillon, ou aussi appelé attracteur de Lorenz, a été decouvert par Edward Lorenz, météorologue et mathématicien. Certains disent qu'un battement de papillon peut amener à une tornade à plus de 1000 kilomètres. Ses recherches montrent celà, car ces dérnières sont basées sur un principe fondamental, la dépendance sensible aux conditions initiales dans un système dynamique non linéaire.

<img width="680" alt="Capture d'écran 2024-03-08 093158" src="https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/assets/160217704/ece84bb6-992d-44f9-a504-b22166f5597d">

# <a name="introduction"></a> Les bases de la théorie de l'attracteur de Lorenz   

Il y a trois points qui expliquent clairement les bases qui ont permis à la théorie de l’attracteur de Lorenz d’exister :

- La dépendance sensible aux conditions initiales
- La conséquence des changements des états initiaux : entraîner de grandes différences dans un état ultérieur
- Principalement tirée de la théorie du chaos, crée également par Edward Lorenz

Explication plus précise :

Maintenant qu’on a vu les éléments qui servent de base a la théorie de l’attracteur de Lorenz, il faut que vous compreniez réellement ce que c’est ;

L’attracteur de Lorenz, c’est la théorie qu’une simple action, qui paraît être un détail futile, peut avoir de conséquences hors-norme sur le système. Prenons un exemple :

On est ici dans un système dit chaotique, et vous allez comprendre pourquoi. Prenons un ensemble de boule de billard,et que l’on vient frapper une boule de ces boules, même en étant extrêmement précis, il est impossible que la boule de billard tape exactement au même endroit avec la même force deux fois de suite.Ainsi, la conséquence qui va s’en suivre, c’est qu’il n’y aura jamais deux parties qui se ressembleront.

 ![billard](
 https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/assets/160217704/d2a946f3-61cc-41fe-bf37-532a94e387ea)

 Comme il n’a suffi que d’un tout petit écart au moment de la frappe pour obtenir un résultat totalement différent, on dit que le jeu du billard est un système chaotique.
 
 Ici, on a un exemple assez générale de l’attracteur de Lorenz, passons maintenant à une explication plus « scientifique ».

# <a name="équations"></a>  Les Equations et éléments à prendre en compte

<img width="273" alt="Capture d'écran 2024-03-08 094334" src="https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/assets/160217704/f453ed7e-c933-479c-b1d9-5f996019c8a0">

x, y, z : Représentent un point d'intérêt dans l'espace tridimensionnel, décrivant la position à un moment donné.
σ, ρ, β : Ces éléments numériques définissent l'attracteur de Lorenz, modulant les trajectoires et influençant la sensibilité aux conditions initiales

Ici, ce qu'il faut comprendre, c'est que les équations données représentent une forme géometrique complexe de l'attracteur de lorenz, ou plus précisément le comportement "chaotique" d'un système dynamique en trois dimensions.
Les variables x, y, z, représentent un point d'intérêt dans l'espace en question, décrivant la position de ce point à un moment donné.
σ, ρ, β, représentent les trajectoires et influencent la sensibilité aux conditions initiales, ce sont donc ces éléments là qui vont nous interesser car c'est selon ces variables , que les conditions initiales se définissent, et font qu'on obtienne des resultats totalement différents à la fin. 

Pour vous expliquer cette partie un peu plus en detail, nous allons la modeliser.

#  <a name="modélisation"></a> Comment modéliser le phénomène étudié 

Voici les étapes clés qui vont nous permettre de modéliser l'attracteur de lorenz, elles vous permettront de mieux cerner les paramètres.

### Définir les Équations du Système Dynamique:

- Établir les équations fondamentales de Lorenz.
- Description de la dynamique tridimensionnelle du système.

```py
sigma = 10
rho = 28
beta = 2.667
def lorenz(x, y, z, sigma, rho, beta):
    deriv_x = sigma*(y - x)
    deriv_y = rho*x - y - x*z
    deriv_z = x*y - beta*z
    return deriv_x, deriv_y, deriv_z
```
     

### Définir les Valeurs Initiales:

- Préciser les conditions de départ pour x, y, et z.
- Préciser le temps entre chaque pas. #dt
- Définir un tableau "t" qui représente les instants de temps auxquels le système de Lorenz est évalué.
- rôle majeur dans la trajectoire globale de l'Attracteur.
```py
dt = 0.009999
t = np.arange(0, dt*2000, dt) 
etat_initial = [0.0, 2.0, 6.0]
```


### Résolution de l'équation différentielle du système de Lorenz:

-Utiliser la fonction "odeint" pour pouvoir intégrer et ainsi résoudre l'équation différentielle du système.

-Obtenir les tableaux de x,y,z contenant les valeurs des variables x, y et z du système de Lorenz à différents instants de temps, ce qui nous permet ensuite de visualiser et d'analyser l'évolution de ces variables au fil du temps.

```py
solution = odeint(lorenz, etat_initial, t, args=(sigma, rho, beta))

x = solution[:, 0]
y = solution[:, 1]
z = solution[:, 2]
```

### Procéder au Plot:

- Transposer les résultats dans un graphique.
- Observer et analyser la forme résultante de l'Attracteur de Lorenz.

 
```py
ax = plt.figure().add_subplot(projection='3d')
ax.scatter(x, y, z,s = 2)
ax.plot(x, y, z, color = 'r')
ax.set_xlabel("X Axis")
ax.set_ylabel("Y Axis")
ax.set_zlabel("Z Axis")
ax.set_title("Lorenz Attractor")

plt.show()
```


![Capture d’écran_24-3-2024_144318_github com](https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/assets/160217704/a4e3644e-abb9-4649-8396-21f73403d9ea)


# <a name="animation"></a> Dépendance des paramètres initiaux 

Voici donc la modélisation de l'attracteur une fois terminé, nous avons ici les paramètres de bases qui nous permettent d'obtenir la modélisation du fameux "effet papillon", qui est nommé comme cela notamment pour la forme qui nous fait penser à un papillon.

Cette modélisation est basée sur des sliders, nous avons réalisé une capture vidéo pour mieux voir la différence dans la trajectoire de l'attracteur de lorenz, il suffit de regarder dans le fichier .....

[![video](https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/assets/160217704/4c0cb92f-933e-4dcb-87ff-9ff1dafb90c6)](https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/blob/main/beta-sliders.mp4)


 
###  <a name="ressources"></a> Bibiliographie : 

[comprendre la théorie](https://couleur-science.eu/?d=717abd--cest-quoi-un-attracteur-de-lorenzun-systeme-chaotique)

[sliders](https://www.geeksforgeeks.org/matplotlib-slider-widget/amp/)

[couleurs_matplotlib](https://matplotlib.org/stable/users/explain/colors/colormaps.html)

[spicy.integrate](https://cpge.frama.io/fiches-cpge/Python/%C3%89quation%20diff%C3%A9rentielle/0-Equation%20diff%C3%A9rentielle/)

[Animation_gif]( https://resteche.github.io/REsteche_blog/chaos%20theory/butterfly%20effect/python%20animation/2021/10/20/Lorenz_animation.html)

###  <a name="calendrier"></a> Tableau de bord : 

SEANCE 1 : Nous avons rassemblé les informations sur l’attracteur de lorenz, réparti les tâches, et avons avons essayé de s'habituer à github . 

SEANCE 2 : Après avoir acquis les bases, nous avons fait la mise en page du site web, introduit l’attracteur de lorenz, sans codage, seulement du texte dans le readme. Cela nous a permis d’organiser le site et d’avoir un aperçu de ce qu’on pouvait faire ou non. Nous nous sommes basés sur le diaporama fait pour présenter notre projet, pour pouvoir agencer notre site.

SEANCE 3 : Durant cette séance, nous nous sommes focalisés sur la modélisation et l’animation de l’attracteur de lorenz, l’idée était de pouvoir voir l’attracteur de lorenz sous ses différentes formes lorsque les conditions initiales sont modifiées. 

SEANCE 4 : Nous nous sommes répartis les tâches qui nous restaient, améliorer la mise en page du readme, et avons travaillé sur les sliders de nos modélisations.

SEANCE 5 : Nous avons importé des sliders interactifs avec matplotlib et %matplotlib notebook, nous sommes sur le peaufinement des modélisations, pour pouvoir les importer sur notre readme comme nous le souhaitions. Le principal problème était que nous ne pouvions pas faire de modèle interactifs avec l’utilisateur du site. Nous avons également exporté notre readme vers un site.

SEANCE 6 : Nous avons rajouter des liens de racourcis dans le site pour accéder aux paragraphes plus rapidement, nous avons fait une recherche par rapport aux thèmes qu’on peut utiliser pour le site, et tester differents thèmes.

SEANCE 7 :  Nous avons rajouter des liens de racourcis dans le site pour accéder aux sites des ressources plus rapidement, et avons rajouté un fichier mp4 pour la vidéo sur les sliders.

