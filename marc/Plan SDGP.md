# Plan

## Disclaimer

Nous allons parler de bonnes pratiques, mais :

* rapidement alors que nous pourrions en parler pendant des heures
* Nous ne ferons que les effleurer, donc ce sera sous forme de grands principes
* Il y a plusieurs donc c'est une sélection
* Nous allons nous centrer sur des axes 

## Pourquoi développons nous des logiciels ?



## Qu'est-ce qu'il fait que cela part en sucette ?

* Nous faisons un travail de traduction de nos idées en code
  * Or traduire, c'est trahir
  * nous avons des difficultés à percevoir le lien entre les idées et le code
  * Cela demande des efforts, comme apprendre une langue étrangère
* Nous sommes dépassés par la complexité
* Nous sommes incapables de faire évoluer le logiciel sans tout casser
* Nous sommes effrayés

## C'est là qu'interviennent les bonnes pratiques

Ensemble de recettes, de principes et de règles. Nous allons en parler sur plusieurs plans

* Attitude
* Principes de conception
* Principes de codage
* Validation

## Axe principal de notre démarche ?

Nos capacités, notre cerveau, ses qualités et ses défauts.

## Principes généraux

Je ne sais pas encore si je 
* Décomposition en problème simples
* Small is beautiful
* Go up and down the ladder
  * zoom in and zoom out
* Delegate 
* Isolate

## Attitudes

### Build for human
* Be coherent, don't create dissonance
* Don't overload
* Be regular, previsible

### Take time

The young person walks faster than the old one, +
but the old one knows the way.

* Programming without really learning it is like pretending to play piano without have been learning: you can make sounds, repeat

### Take time to learn

* Your langage
* Your tools
* Don't copy without understanding
* Take notes about the path you take.

### Calm down the mess you have in your head
* Talk, write, draw

## Conception

### Disclaimer

Ces principes sont valable quelque soit l'échelle d'abstraction utilisée



> Je ne vais pas décrire tous les principes de SOLID, car certains sont trop abstraits pour la population
>
> que nous allons rencontrer.
>
> Segregation of Interface par exemple n'est pas adapté au python, y compris OO.
>
> Mieux vaut remplacer cela par multiple rôles ?

### Breaking down complexity

Icic expliquer que la meilleure solution est de casser en petites briques indépendantes
d'avoir des briques indépendantes

* Divide into small units
* adopt a scaling point of view
* Low coopling



### Separation Of Concern

Several sample with more and more complex sample

* barista
* restaurant
* making a movie

#### Several level of complexity

* Idea: prepare a coffee from a machine
  * How many actions needed ? 1
    * select coffee 
    * wait for coffee
    * take coffee
  * complexity: very low

**here make a graph with one step**

* Idea: Sell a simple coffee to a customer
  * How many actions : a few
    * take the order
    * prepare the coffee
    * bring the coffee
    * cash in and give change
  * complexity: low
  * Concern: 2 
    * coffee
    * casch in 
    * order    

But there's some problem: only one perso

* Idea: sell various and customized coffees to a lot a customer 
  * how many actions
    * Take the order
    * check the order
    * collect coffee ingredients
    * prepare coffee
    * put in all ingredient
    * make a drawing
    * hand coffee to customer
    * cash in and give change
  * complexity low
  * concerns: a few



**Faire un graphique**

Concern: cash and money, coffee



You're a film maker, you're going to shoot a movie accross Europe with a team of 100 people, a few actors and you're moving every day from place to place.

Mission: to shoot the film, and there's a lot of thing to do.

* Shoot the movie
* Bring people to the shooting stage
* Prepare texts for actors
* Prepare instructions for stage decorators
* Record sound
* Rents cars
* Prepare costumes, design Costumes

A movie lifecycle is cut into three main stage

* 	Development
* 	Pre-production
* 	Production
* 	Post-production
* 	Distribution

The main departements for a movie only for phase production (shooting)

* Production 
* Art
* Camera
* Lighting
* Special Effect (live)
* Sound
* Stunt

Credits https://www.youtube.com/watch?v=CrL-lNtN140 à partir de 2:06


see https://nofilmschool.com/film-crew-jobs

https://www.projectcasting.com/tips-and-advice/crew-jobs-every-film-crew-position-job-description/

L'idée du film https://en.wikipedia.org/wiki/Film_crew#Camera_and_lighting

Une bonne ressource: https://filmincolorado.com/resources/job-descriptions/

**le document clef est le script**



> problem domain concern
>
> solution domain concern
>
> Exemple tirés de https://ris.utwente.nl/ws/portalfiles/portal/5428452/Aksit01six.pdf
>
> for each
> one concern, other concerns are
> irrelevant

This way it's complex, it's quickly overwhelming, but you're brave, you're committed to your work and build such a big thing : The _MealProvider_

*Group fonction by concern and limit required knowledge to work*

**Minimaliser la connaissance des autres domaines** 

#### 


### Single Responsability

You are in a rush, you need to change something => électricité source => pas d'impact sur les caméras.

* Faciliter de traduction / lien à l'idée
* Think Small
* Pas de confusion possible
* Identification rapide
* Les modifications ont moins de chance de perturber les autres fonctions, puisqu'il ne porte qu'une seule responsabilité

Exemple avec le costumier.

Sa responsabilité c'est de gérer les costumes

### Open/Closed

La camera est louée, elle ne peut être modifiée. Pourtant l'équipe en as besoin pour faire un gros plan.

Elle est fermée en modification => impossible de l'ouvrir pour la modifier au risque que cela coûte très cher

Elle est ouverte en extension: il est possible de changer l'objectif.

* Ce principe est utile dans les cas suivants
  * Forte notion de partage des composants
    * vers l'extérieur
    * à travers plusieurs projets
  * Ne pas vouloir revalider des composants éprouvés de A à Z
  * Ne pas risquer de tomber sur des cas non prévus par le concepteur, c'est dire vous, dans quelques années.

#### Exemple de la caméra

Le concept de caméra est utilisée sur tous les tournages.
Les équipes de tournage (Camera Crew) utilise des caméras.

Une caméra est constituée d'un coeur.

Elle peut être utilisée en plan rapproché, sous l'eau, en l'air.

Il existe plusieurs caméras, mais toute basées sur le même coeur.

Exemple de la caméra ouverte en extension avec :

* le changement d'objectif
* l'adaptation à un caisson étanche

Exemple de la caméra fermée en modification

Possibilité de spécialiser la caméra:

* une version étanche pour faciliter la prise de vue sous-marine,
* Une version portable en steady-cam

#### Exemple de l'acteur

De même il n'est normalement pas possible de modifier un acteur, mais on peut l'étendre avec du maquillage et des effets spéciaux :)


### Substitution de Liskov

Dans le processus de la prise de scène, la caméra, qu'elle soit sous-marine, en steady-cam, quelque soit l'objectif, doit pouvoir être utilisée selon le même protocole.

```
setup_camera(camera)
is_ready(camera)
start_shooting(camera)
stop_camera(camera)
teardown_camera(camera)
```

Le fabricant de la camera ne sait pas forcément comment sa caméra sera utilisée, pourtant il doit prévoir une interface commune à tout ces usages.

Exemple de violation de la substitution



```python
setup_camera(camera):
	if isinstance(camera,SteadyCam):
        # do something
    elif isinstance(camera,AquaticCam)
    	# do anotherthing
```



### Segregation of interface



La ségrégation des interfaces consiste à présenter les différents aspects comme des interface limitées

> Dans le cas de python il n'y a pas vraiment de notion d'interface en raison du duck typing.
>
> Il est possible d'utiliser des choses comme les métaclasses ou ABC, mais c'est chaud.



```python
from abc import ABC, abstractmethod

class Camera(ABC):
    @abstractmethod
    def start_shooting(self):
        pass
    @abstractmethod
    def stop_shooting(self):
        pass

class Microphone(ABC):
    @abstractmethod
    def open(self):
        pass
    
    @abstractmethod
    def close(self):
        pass

class IPhone(Camera, Microphone):
    pass

iphone = IPhone()
```



La ségrégation des interfaces consiste avant tout à avoir des contrats clairs et à portée limitée, des rôles.

Il ne faut pas que ces contrats soient pléthoriques, qu'ils soient limités uniquement à ce qui est nécessaire à l'interaction avec les autres.

#### Exemple avec une équipe de cinéma.

An object could have several roles.  For example il could be lighting director and camera manager. It's not very clever, as it violate the Single Responsability Principle, but it could occur.

As film director, I have to avoid my interactions with a person, but I have to interact with role only.

So I interact sometimes with the camera director and sometimes with the lighting director.

It's the same object for now, but maybe in a few days, it could be different object.



Pour que l'organisation ne soit pas révolutionné en permanence, alors que les personnes changent sans cesse, il faut que les contrats soient clairs, il faut pouvoir compter dessus, quelque soit leur nature.

Exemple :

chose qui changent, mais dont l'interface doit rester identique:

* camera
* prise de son
* équipe de décoration
* équipe locale

Ici mettre des dessins avec des interactions et des natures différentes

```python
def take_film_sequence(script_supervisor, clapper):
    sequence_identifiers = script_supervisor.get_new_sequence_identifiers()
    
    clapperboard = clapper.get_clapperboard()
    clapper.load(clapperboard, sequence_identifiers)
    clapper.clap(clapperboard)
    
    camera.start_shooting()
    microphone.start_record()
    
    scene.run()
    
    microphone.stop_record()
    camera.stop_shooting()
    
    sound = microphone.get_current_record()
    video = camera.get_current_sequence()
    
    sequence = FilmSequence(identifiers,video,sound)
    return sequence
    
```


```python
def begin_sequence(camera, microphone):
    camera.start_shooting()
    microphone.start_record()
    
def end_sequence(camera, mircophone):
    microphone.stop_record()
    camera.stop_shooting()
```


The actual nature of each component must not be of any importance !

```python
camera = SonyCameraPMWF55()
microphone = SennheiserMKH416P48U3SuperCardioidShotgunTubeCondenserMicrophone()

take_film_sequence(camera, microphone)
```
is must not change if material is different

```python
camera = joe.get_smartphone()
microphone = barbara.get_smartphone()

take_film_sequence(camera, microphone)
```
or if we want to test function

```python
camera = MockCamera()
microphone = MockMicrophone()

take_film_sequence(camera, microphone)
```

Ce n'est pas vraiment le principe de ségrégation des interfaces

Je peux faire 

preparation -> shooting -> editing

Faire ressortir la différence qu'il y a entre le contrat et l'implémentation



If you don't impose contract as interface, you will finsih with this kind of nightmare

```python
class camera_operator: 
    
    def start_shooting(camera):
    	if isinstance(camera, Smartphone):
    		camera.select_camera_mode()
    		if camera.has_touch('start'):
    			camera.touch('start')
    		elif camera.has_button('start'):
    			camera.press_button('start')
    	
    	if isinstance(camera, ProfessionalCamera):
    		if camera.maker == 'Sony':
    			camera.press_button('record')
    		elif camera.maker == 'Samsung':
    			camera.trigger('LittleRedButton')
#...
```
instead of 

```python
class Camera:
	def setup():
	def is_ready(self)
	def start_record(self)
	def stop_record(self)
	def get_record(self)
```

```python
class camera_operator: 
    
    def start_shooting(camera):
        if not camera.is_ready():
            raise NotReadyException(camera)
        camera.start_record()
        
    def end_shooting(camera):
        camera.stop_record()
```




```python
def take_sequence(camera_operator):
    if camera_operator.name == 'John The Shooter':
        say("Let's go John", camera_operator)
    elif camera_operator.gender == 'Women' :
    	say("Please Ma'ame, could you start filming", camera_operator)
    else :
        say("It runs", camera_operator)
```




### Dependency injection

Principe d'injection, c'est que les composant ne se préoccupent pas de la façon dont ils trouvent leurs dépendances.
C'est une responsabilité qui n'est pas de son ressort. Cela lui permet d'être spécialisé et focalisé sur sa responsabilité.



Il y a un *sachant*

Exemple

L'actrice ne se préoccupe pas de trouver son costume: un costumier s'en charge.

Nuances

Si l'actrice ne porte qu'un costume, il n'est peut-être pas nécessaire d'avoir un costumier, ce n'est pas très pertinent. Elle saura le trouver et le porter elle-même.

Si il y a beaucoup de costume, et que la tâche de gérer les costumes devient conséquente, il faut déléguer à un costumier.

D'une manière plus générale, le principe d'injection de dépendances est le suivant

* décrire ces besoins
* décrire l'ordre des dépendances
* Construire un arbre de dépendances





### Facteur d'échelle et délégation

Exemple avec le costumier

Au début, le film est à petit budget, c'est un court métrage, il y a un unique costume => pas de costumier, quelqu'un dans l'équipe s'en charge.

Ensuite le film devient plus conséquent, il y a plusieurs costumes à prévoir => responsabilité de costumier

* Créer les costumes
* Acheter les costumes
* Louer les costumes
* ranger les costumes 
* Entretenir les costumes
* Préparer les costumes pour les scènes
* aider les acteurs à enfiler les costumes

Le nombre de costumes est conséquent, il y a plusieurs acteurs, des figurants, plusieurs types de costumes, le rangement est complexe, le transport difficile => Délégation

* Responsable design de costumes
* Responsable achat
* Responsable entretien
* Responsable rangement
* Assistant pour mettre enlever



```python
class CostumeDepartement:
	
    def design_costume(self, requirements):
    	#...
    def buy_costume(self, requirements):
    	#...
    def rent_costume(self, requirement):
    	#...
    def get_costume(self, actor, scene) -> costume: 
    	#...
    def store_costum(self, costum):
     
```



Le principe de délégation



```python
class CostumeDepartement:
    
    def design_costume(self, requirements):
        self.designer.design(requirements)
        
    def buy_costume(self, requirements):
        costume = self.buyer.buy(requirements)
        self.storer.store(costume, requirements)
        
    def get_costume(self, actor, scene) -> costume:
        self.storer.find_costume(actor,scene)
```



Sans injection de dépendances

```python
class CostumeDepartement:

    def __init__(self):
        self.designer = Designer()
        self.buyer = Buyer()
        self.storer
```



Injection de dépendances

```python
class CostumeDepartement:

    def __init__(self, designer, buyer, storer):
        self.designer = designer
        self.buyer = buyer
        self.storer = storer
```



### Composition over heritage



OOP make a lot of use of inheritance. Good practices show that you have to be very careful with inheritance.

Inherutance is based on a "IS question"

Composition is based on "What I do"



## Coding

### Namming

small is beautiful for names



# ANNEXES

## SOC cuisine

Imagine you have a mission : to prepare a meal for a traveling  crew of 100 people every evening from money you get for the month. 

It's a rather complex mission, with a lot of steps and concern.

From external point of view, there's a big thing, a meal preparator, wich take money from some guy and out a meal.

List what you have to do :

**Utiliser une liste de fonctionnalités**

```
receive money
count money
pay your furnisher
buy ingredients
prepare a menu
Cook the meal

set the cutlery
wash dishes
take out the tables and chairs
tidying up tables and chairs
...
```





