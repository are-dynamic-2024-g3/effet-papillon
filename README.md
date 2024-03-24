# L'EFFET PAPILLON DANS TOUTE SA SPLENDEUR
    Designed by the magnificients Suvana, Madina, Sathursjan

L'effet papillon, ou aussi appelé attracteur de Lorenz, a été decouvert par Edward Lorenz, météorologue et Mathémticien. Certains disent qu'un battement de papillon peut amener à une tornade à plus de 1000 kilomètres. Ses recherches montrent celà, car ces dérnières sont basées sur un principe fondamental, la dépendance sensible aux conditions initiales dans un système dynamique non linéaire.

<img width="680" alt="Capture d'écran 2024-03-08 093158" src="https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/assets/160217704/ece84bb6-992d-44f9-a504-b22166f5597d">

# Les bases  de la théorie de l’attracteur de Lorenz   

Il y a trois points qui expliquent clairement les bases qui ont permis à la théorie de l’attracteur de Lorenz d’exister :

- La dépendances sensible aux conditions initiales
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

# Les Equations et éléments à prendre en compte

<img width="273" alt="Capture d'écran 2024-03-08 094334" src="https://github.com/are-dynamic-2024-g3/effet-papillon.github.io/assets/160217704/f453ed7e-c933-479c-b1d9-5f996019c8a0">

x, y, z : Représentent un point d'intérêt dans l'espace tridimensionnel, décrivant la position à un moment donné.
σ, ρ, β : Ces éléments numériques définissent l'attracteur de Lorenz, modulant les trajectoires et influençant la sensibilité aux conditions initiales

Ici, ce qu'il faut comprendre, c'est que les équations données représentent une forme géometrique complexe de l'attracteur de lorenz, ou plus précisément le comportement "chaotique" d'un système dynamique en trois dimensions.
Les variables x, y, z, représentent un point d'intérêt dans l'espace en question, décrivant la position de ce point à un moment donné.
σ, ρ, β, représentent les trajectoires et influencent la sensibilité aux conditions initiales, ce sont donc ces éléments là qui vont nous interesser car c'est selon ces variables , que les conditions initiales se définissent, et font qu'on obtienne des resultats totalement différents à la fin. 

Pour vous expliquer cette partie un peu plus en detail, nous allons la modeliser.

# Comment modéliser le phénomène étudié 

Voici les étapes clés qui vont nous permettre de modéliser l'attracteur de lorenz, elles vous permettront de mieux cerner les paramètres.

### Définir les Équations du Système Dynamique:

- Établir les équations fondamentales de Lorenz.
- Description de la dynamique tridimensionnelle du système.

```py
def lorenz(x, y, z, sigma=10, rho=28, beta=2.667):
    deriv_x = sigma*(y - x)
    deriv_y = rho*x - y - x*z
    deriv_z = x*y - beta*z
    return deriv_x, deriv_y, deriv_z
```
     

### Définir les Valeurs Initiales:

- Préciser les conditions de départ pour x, y, et z.
- rôle majeur dans la trajectoire globale de l'Attracteur.
```py
nb_pas = 1500
x = np.empty(nb_pas + 1)
y = np.empty(nb_pas + 1)
z = np.empty(nb_pas + 1)
x[0], y[0], z[0] = (1.0, 3.0, 5)
```


### Avancer dans le "Temps":

- Calculer les dérivées partielles au point actuel.
- Utiliser ces dérivées pour estimer le point suivant dans l'évolution du système.
    
```py
dt = 0.01
for i in range(nb_pas):
    deriv_x, deriv_y, deriv_z = lorenz(x[i], y[i], z[i])
    x[i + 1] = x[i] + (deriv_x * dt)
    y[i + 1] = y[i] + (deriv_y * dt)
    z[i + 1] = z[i] + (deriv_z * dt)
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


# Modélisation de l'Attracteur de Lorenz

(Modèle de l'attracteur en version interactive)

Voici donc la modélisation de l'attracteur une fois terminé, nous avons ici les paramètres de bases qui nous permettent d'obtenir la modélisation du fameux "effet papillon", qui est nommé comme ca notamment pour la forme qui fait penser a un papillon.

( image )

Cette modélisation est interactif ! Vous pouvez donc changer les paramètres de bases, et constater par vous meme la fascinante experience de k'attracteur de Lorenz !



### Bibiliographie : 
https://resteche.github.io/REsteche_blog/chaos%20theory/butterfly%20effect/python%20animation/2021/10/20/Lorenz_animation.html
https://couleur-science.eu/?d=717abd--cest-quoi-un-attracteur-de-lorenzun-systeme-chaotique
