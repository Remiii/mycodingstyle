# myCodingStyle

```
                    ______          ___             _____ __        __
   ____ ___  __  __/ ____/___  ____/ (_)___  ____ _/ ___// /___  __/ /__
  / __ `__ \/ / / / /   / __ \/ __  / / __ \/ __ `/\__ \/ __/ / / / / _ \
 / / / / / / /_/ / /___/ /_/ / /_/ / / / / / /_/ /___/ / /_/ /_/ / /  __/
/_/ /_/ /_/\__, /\____/\____/\__,_/_/_/ /_/\__, //____/\__/\__, /_/\___/
          /____/                          /____/          /____/
```

TODO : traduction en Anglais.

## Introduction

Ce document présente la norme de codage mise en place pour mes projets. Non exhaustif, il est important que toute personne développant du logiciel lise ce document afin de satisfaire à une volonté d’uniformiser au maximum les codes développés pour mes projets. Le but étant qu’ils soient maintenables par un maximum de personnes et surtout réutilisable le plus simplement (et donc rapidement) possible. Le respect de cette norme fera l’objet de lectures de codes. Tout code écrit pour mes projets devra respecter cette norme pour pouvoir être intégré.

## Table of content

* Général
* Passage de paramètre aux programmes
* Les variables
* Les fonctions
* Les classes
* Mise en forme du code
* Remarques complémentaires sur le C/C++
* Remarques complémentaires sur l'HTML
* Remarques complémentaires sur le PHP
* Remarques complémentaires sur Symfony2
* Remarques complémentaires sur PHP/Twig
* Remarques complémentaires sur les BDD el le SQL
* Les fichiers
* Organisation des fichiers en C/C++
* Génération automatique de la documentation

## Général

Toute personne amenée à développer du code pour mes projets devra avoir pris connaissance de ce document et en avoir fait une lecture complète. En effet, afin de toujours conserver la possibilité de travailler à plusieurs sur un même code, il est préférable d’imposer certaines règles. Cependant elles ne doivent pas être une contrainte et dans certains cas, on admettra que, le bon sens prenne le pas sur ces dernières.

Les noms de fonction ou de variable doivent être écrits en anglais. Il est essentiel que les noms utilisés permettent une compréhension explicite du rôle de la fonction ou de la variable et du contenu des fichiers. Les commentaires doivent également être rédigés en anglais afin d'être compréhensibles par un maximum de personnes.

## Passage de paramètre aux programmes

Les paramètres à envoyer aux programmes créés doivent respecter certains principes.

Les paramètres sont de 3 types :

* Mot clef
* Lettre clef
* Autre paramètre

### Mot clef

Les mots clefs sont définis par le programme selon ses besoins. Ils sont toujours précédés de 2 tirets. Si plusieurs mots clefs doivent être envoyés, il faut laisser un espace et mettre à nouveau les 2 tirets.

Exemple :

```bash
$ ./mysportconnectAppli --help --run
```

### Lettre clef

Les lettres clefs sont définies par le programme selon ses besoins. Elles sont toujours précédées de 1 tiret. Si plusieurs lettres clefs doivent être envoyées, il n'est pas nécessaire de laisser un espace et de mettre à nouveau le tiret. Les 2 méthodes sont possibles.

Exemple :

```bash
$ ./mysportconnectAppli -h –r
$ ./mysportconnectAppli -hr
```

### Autre paramètre

Tous les autres paramètres sont écrits sans rien ajouter en laissant des espaces entre chacun d'eux. Pour passer une chaine de caractères pouvant contenir des espaces il faut l'encadrer de guillemets.

Exemple :

```bash
$ ./mysportconnectAppli --message "My message"
$ ./mysportconnectAppli --delay 200
```

### Paramètres obligatoires

Les paramètres suivants peuvent être passés à tout programme codé :
* --help affiche une aide sommaire sur la sortie standard et quitte le programme
* -h affiche une aide sommaire sur la sortie standard et quitte le programme
* --version affiche la version du programme sur la sortie standard et quitte le programme
* -v passe en mode verbose. Les logs sont plus nombreux
* -s passe en mode silent. Aucun log n'est effectué

## Les variables

### Types

Il est important de veiller à utiliser les bons types de variable mêmes pour des langages à typage dynamique. L’absence de rigueur sur ce point peut amener de nombreux dysfonctionnement dans le code.

#### Les types en C/C++

<table>
    <tr>
        <td>Type</td>
        <td>Taille en mémoire</td>
        <td>Intervalle</td>
    </tr>
    <tr>
        <td>unsigned char</td>
        <td>1 octet</td>
        <td>0 à 255</td>
    </tr>
    <tr>
        <td>signed char</td>
        <td>1 octet</td>
        <td>-128 à 127</td>
    </tr>
    <tr>
        <td>unsigned short</td>
        <td>2 octet</td>
        <td>0 à 65535</td>
    </tr>
    <tr>
        <td>signed short</td>
        <td>2 octet</td>
        <td>-32 768 à 32 767</td>
    </tr>
    <tr>
        <td>signed int</td>
        <td>2 ou 4 octets</td>
        <td>?</td>
    </tr>
    <tr>
        <td>unsigned int</td>
        <td>2 ou 4 octets</td>
        <td>?</td>
    </tr>
    <tr>
        <td>unsigned long</td>
        <td>4 octets</td>
        <td>0 à 4 294 967 295</td>
    </tr>
    <tr>
        <td>signed long</td>
        <td>4 octets</td>
        <td>-2 147 483 648 à 2 147 483 647</td>
    </tr>
    <tr>
        <td>unsigned long long</td>
        <td>8 octets</td>
        <td>0 à 18 46 744 073 709 551 615</td>
    </tr>
    <tr>
        <td>signed long long</td>
        <td>8 octets</td>
        <td>-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807</td>
    </tr>
    <tr>
        <td>float</td>
        <td>4 octets</td>
        <td>1.2E-38 à 3.4E+38</td>
    </tr>
    <tr>
        <td>double</td>
        <td>8 octets</td>
        <td>2.3E-308 à 1.7E+308</td>
    </tr>
    <tr>
        <td>long double</td>
        <td>10 octets</td>
        <td>3.4E-932 à 1.1E+4932</td>
    </tr>
</table>

Le type "int" est à proscrire, car sa taille varie en fonction de la cible (x86, PowerPC, ARM...). On préférera l’utilisation des types "short" et "long". Lors de la déclaration d’un type, le préfixe "signed" ou "unsigned" doit toujours être spécifié. Sauf pour la déclaration d'un caractère, le type "char" est alors utilisé. Lors de la déclaration d'un nouveau type (typedef) le type créé portera le suffixe "_t".

#### Les types en PHP

<table>
    <tr>
        <td>Type</td>
        <td>Taille en mémoire</td>
        <td>Intervalle</td>
    </tr>
    <tr>
        <td>integer</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>boolean</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>float</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>string</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>array</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>object</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>unset</td>
        <td></td>
        <td></td>
    </tr>
</table>


### Définition des noms de variables

#### Général

La séparation des mots dans un nom de variable est symbolisée par une majuscule (ex : type_MyGlobalVariable, type_myLocalVariable) / CamelCase. Le nom de la variable doit être le plus explicite possible même s'il est long.

Pour une meilleure lisibilité :

* Le nom d’une constante sera écrit en majuscules (précédé de son type) (ex : type_CONST)
* Le nom d’une variable globale commencera par une majuscule (ex : Variable)
* Le nom d’une variable locale commencera par une minuscule (ex : variable)

Exemple en C/C++ :

```c
usigned long ul_sizeOfStack1 = 0 ;
```

Exemple en PHP :

```php
$sizeOfStack1 = 10 ;
echo $sizeOfStack1 ;
```

#### Définition des noms de variables en C/C++

Le plus simple et le plus logique pour la définition des noms de variables est d'utiliser la notation hongroise. Cette méthode permet de définir dans le nom de la variable, le type de la variable.

Le nom de la variable est défini par son type en minuscule suivi d’un "_" suivie du nom de la variable en commençant par une majuscule s’il s’agit d’une variable globale (ex : type_Variable), ou d’une minuscule s’il s’agit d’une variable locale (ex : type_variable), le reste du nom doit être en minuscule. De plus, 2 préfixes précédant le type préciseront s’il s’agit d’un tableau ou d’un pointeur (ou d'une combinaison des 2).

Tableau récapitulatif :

<table>
    <tr>
        <td>Préfixe 1</td>
        <td>Préfixe 2</td>
        <td>Type</td>
        <td>Nom</td>
        <td>Suffixe</td>
        <td>Traduction</td>
    </tr>
    <tr>
        <td>t</td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td>tabeau</td>
    </tr>
    <tr>
        <td>p</td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td>pointeur</td>
    </tr>
    <tr>
        <td></td>
        <td>t</td>
        <td></td>
        <td></td>
        <td></td>
        <td>tableau</td>
    </tr>
    <tr>
        <td></td>
        <td>p</td>
        <td></td>
        <td></td>
        <td></td>
        <td>pointeur</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>str</td>
        <td></td>
        <td></td>
        <td>structure</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>e</td>
        <td></td>
        <td></td>
        <td>enum</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>u</td>
        <td></td>
        <td></td>
        <td>union</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>uc</td>
        <td></td>
        <td></td>
        <td>unsigned char</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>c</td>
        <td></td>
        <td></td>
        <td>char</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>ch</td>
        <td></td>
        <td></td>
        <td>cher</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>us</td>
        <td></td>
        <td></td>
        <td>unsigned short</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>s</td>
        <td></td>
        <td></td>
        <td>signed short</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>ui</td>
        <td></td>
        <td></td>
        <td>unsigned int</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>i</td>
        <td></td>
        <td></td>
        <td>int</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>ul</td>
        <td></td>
        <td></td>
        <td>unsigned long</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>l</td>
        <td></td>
        <td></td>
        <td>long</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>ull</td>
        <td></td>
        <td></td>
        <td>unsigned long long</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>ll</td>
        <td></td>
        <td></td>
        <td>long long</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>f</td>
        <td></td>
        <td></td>
        <td>float</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>d</td>
        <td></td>
        <td></td>
        <td>double</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>ld</td>
        <td></td>
        <td></td>
        <td>long double</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td>o</td>
        <td></td>
        <td></td>
        <td>other type</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td></td>
        <td>variableName</td>
        <td></td>
        <td>variable local</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td></td>
        <td>VariableName</td>
        <td></td>
        <td>variable global</td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td>t</td>
        <td>type personnel</td>
    </tr>
</table>

Exemple en C/C++ :

```c
unsigned char uc_GlobalVar1 ;
MON_ENUM_t *tpe_GlobalVar2 [ 10 ] ;
myStructure_t **ppstr_GlobalVar3 ;
myFunction ( signed short s_flagPMT )
{
    signed short *ps_localVar1 ;
    float f_localVar2 ;
}
```

#### Définition des noms de variables en PHP

Il n’y a pas de particularité dans la définition des noms de variable en PHP - sauf bien sûr le respect des règles énoncées dans la partie générale.

Exemple en PHP :

```php
$sizeOfStack1 = 10 ;
echo $sizeOfStack1 ;
```

## Les fonctions

### Convention et syntaxe

Le nom d’une fonction ne contient pas "_", la séparation des mots est symbolisée par une majuscule. La première lettre est en minuscule.

Exemple en C/C++ :

```c
void functionName ( void )
{
    //
}
```

Exemple en PHP :

```php
function functionName ( )
{
    //
}
```

### Entête de fonctions

Le prototype de déclaration d’une routine doit être précédé de l’entête suivante

```c
/**
 * @brief brief description of the function.
 * complementary comments.
 * @param description of an input parameter.
 * @return description of an output parameter.
 * @retval description of a return value.
 */
```

Exemple en C/C++ :

```c
/**
 * @brief A simple function for a test.
 * @param s_flagPMT is a flag for the PMT.
 * @return Error code according to the execution of the function.
 * @retval NO_ERROR The function ends normally.
 * @retval EINVAL The value of an argument made no sense.
 */
unsigned char myFunction ( signed short s_flagPMT ) ;
```

Exemple en PHP :

```
/**
 * @brief A simple function for a test.
 * @param s_flagPMT is a flag for the PMT.
 * @return Error code according to the execution of the function.
 * @retval NO_ERROR The function ends normally.
 * @retval EINVAL The value of an argument made no sense.
 */
myFunction (s_flagPMT ) ;
```

## Les classes

### Convention de syntaxe

Le nom d’une classe ne contient pas "_", la séparation des mots est symbolisée par une majuscule. La première lettre est en majuscule.

Exemple en C/C++ :

```c
class ClasseName { } ;
```

Exemple en PHP :

```php
class ClasseName { } ;
```

### Entête des classes

La déclaration d’une classe doit être précédé de l’entête suivante.

```c
/**
 * @brief Brief description of the function.
 * complementary comments.
 */
```

Exemple en C/C++ :

```c
/**
 * @brief A simple class for a test.
 * This class is just an example.
 */
class MyClass
{
    //
} ;
```

## Mise en forme du code

### Introduction

Pour des raisons d'uniformisation du logiciel et de clarté, il faut que le logiciel soit écrit de la même manière, en respectant les indentations.

Remarque : Il ne faut pas utiliser de tabulation, pour permettre une meilleure compatibilité entre les différents éditeurs de texte. Les indentations sont constituées de 4 espaces. Astuce : pour les utilisateurs de *vim* les lignes suivantes placées dans le fichier
".vimrc" de votre HOME permettent d'utiliser la touche tab pour créer des indentations de 4 espaces.

```bash
set tabstop=4
set shiftwidth=4
set expandtab
```

Vous pouvez égelement regarder mon depot git mydotfile.

Remarque: Pour les Makefiles (en C/C++) le langage impose de ne pas utiliser d'espace pour les indentations. Il faut laisser une indentation entre le bloc et les instructions du même bloc. Il en va de même pour les instructions de contrôle du "C/C++" telles que : "while", "for", "switch", "do..while", "if..else", etc...

Les commentaires sont obligatoires (il n’y en a jamais trop). Ils doivent permettre de décrire le fonctionnement global d'une fonction, d'un automate ou d'un calcul. Ils facilitent la compréhension du logiciel en particulier si on doit modifier un logiciel des mois ou des années plus tard ou si une autre personne doit modifier ce logiciel. Toutefois la déclaration d'une variable locale ne nécessite pas de commentaire si son nom est suffisamment explicite !

### Règles générales

Règles générales :
* Placer un espace avant et après les opérateurs et à l'intérieur des parenthèses
* Placer un espace avant et après une virgule séparant les paramètres d'une fonction
* Laisser les accolades seules sur leur ligne
* Placer un espace avant le point-virgule de la fin d’instruction
* Placer un espace avant et après les parenthèses sauf en fin de ligne

Exemple en C/C++ :

```c
void beginStream ( unsigned char *puc_firstParam , float f_secondParam )
{
    unsigned char uc_i ; // used as a counter in loop instructions
    for ( uc_i = 0 ; uc_i <= 10 ; uc_i++ )
    {
        // Instructions to execute
    }
}
```

Exemple en PHP :

```php
function beginStream ( firstParam , secondParam )
{
    for ( i = 0 ; i <= 10 ; i++ )
    {
        // Instructions to execute
    }
}
```

#### Instruction *for*

Exemple en C/C++ :

```c
for ( uc_i = 0 ; uc_i < VAL_MAX ; uc_i++ )
{
    printf ( "Hello world!!!\n" ) ;
}
```

Exemple en PHP :

```php
for ( i = 0 ; i < VAL_MAX ; i++ )
{
    echo 'Hello world!!!' ;
}
```

#### Instruction *if*

Toujours utiliser le mot clef "else" même si il n'y a rien à faire pour éviter des cas non prévu.

Exemple C/C++ :

```c
if ( uc_test >= VAL_MAX )
{
    uc_action = EXIT ;
}
else
{
    // Nothing to do because VAL_MAX is not reached
}
```
#### Instruction *switch*

Toujours utiliser le mot clef "default" même si tous les cas de figure ont théoriquement été couverts.

Exemple en C/C++ :

```c
switch ( uc_test )
{
    case VAL_1 :
        uc_action = STREAM ;
        break ;
    case VAL_2 :
        uc_action = RECORD ;
        break ;
    default :
        uc_action = EXIT ;
        break ;
}
```

#### Commentaires

Remarque : Pour effectuer un commentaire non intérprété par *Doxygen* il ne faut surtout pas mettre "/**".

Exemple en C/C++ :

```c
/*
 * Gros commentaire
 * blablabla
 */

// Petit commentaire

/*
 * Definition of riri
 */
unsigned short us_riri ;
us_riri = 0 ;

//---
```

### Mise en forme du code en C/C++ (PHP)

#### #define

Les "define" sont écrits en majuscules avec des "_" pour séparer les mots.

Exemple en C/C++ :

```c
#define MY_EXAMPLE 33
```

#### #ifndef, #define, #endif

Pour éviter les doubles inclusions de fichier d'en-tête, les instructions #ifndef et #define doivent débuter tout fichier h et l'instruction #endif doit le finir.
Le nom de ce define est composé d'un "_" suivit du nom du fichier (sans l'extension) mis en majuscule. Avec des "_" séparant les mots. Et pour terminer : "_H". Ce nom est repris en commentaire sur le #endif. Exemple: pour le fichier mysportconnectAppli.h

```c
#ifndef _MYSPORTCONNECT_APPLI_H
#define _MYSPORTCONNECT_APPLI_H
// content of the file
#endif // _MYSPORTCONNECT _APPLI_H
```

#### Fonction private et protected

Les fonctions "private" et "protected" sont précédées d’un "_".

Exemple en C++ :

````c
private _myFunctionPrivate ( ) ;
protected _myFunctionProtected ( ) ;
```

Exemple en PHP :

````php
private _myFunctionPrivate ( ) ;
protected _myFunctionProtected ( ) ;
```

## Remarques complémentaires sur le C/C++

### Prototypes

Les prototypes de fonctions sont obligatoires. Même si la fonction est déclarée avant d'être appelée dans le même fichier. En effet, les commentaires Doxygen (Cf. Génération automatique de la documentation) sont placés devant les prototypes. Seul la fonction "main" échappe à cette règle (les commentaires du "main" sont placés devant la fonction elle-même et elle n'a pas de prototype).

### Déclarations

Les déclarations de variables se font toujours au début de chaque fonction. Aucune déclaration ne doit être faite après la première instruction de code. Les variables ne doivent pas être initialisées à la déclaration (pour une question de portabilité de code).Toutefois une exception est faite pour les chaînes de caractères (tableaux de caractères pour être plus précis) afin de n pas avoir à taper la longueur de la chaîne.

Exemple en C/C++ :

```c
unsigned long ul_port ;
char *pch_unixSocket = "/tmp/mysql.sock" ;
unsigned long ul_clientFlag ;
char tch_argOption[] = "test_libmysqld_CLIENT" ;
ul_port = 0 ;
ul_clientFlag = 0 ;
```

### Utilisation de structures

Il est vivement recommandé d’utiliser des structures et/ou des unions lorsqu’une tâche doit envoyer plusieurs données vers une autre tâche. Il est en effet plus commode d’échanger un objet (structure) plutôt qu’un ensemble parfois exhaustif de variables. Cela tend à avoir une approche un peu plus haut niveau (plus orientés objet) et donc plus facilement appréhendable par une autre personne. Les variables contenues dans la structure sont nommées suivant les règles habituelles. Préfixes spécifiant le type suivit d'un "_" puis du nom de la variable en lui même en commençant par une minuscule. Le nom d'un nouveau type porte alors le suffixe "_t". Le nom du type commence par une minuscule et les
séparations de mots sont symbolisées par une majuscule.

Exemple de déclaration :

```c
/** @brief comment for the new type */
typedef struct
{
    /** @brief description of uc_Var1 */
    unsigned char uc_var1 ;
    /** @brief description of uc_Var2 */
    unsigned char uc_var2 ;
    ...
} myStructure_t ;
```

### Points de sortie multiples

Pour les fonctions retournant des valeurs, on préférera s’en tenir à une seule instruction return par fonction. En effet, lorsqu’une fonction se complique, la présence de plusieurs return nuit à la compréhension et au débuggage. Cependant, dans certains cas, le recours à plusieurs return est justifié auquel cas, le bon sens l’emporte sur la règle.

### Utilisations des types énumérés

Le recours aux enum doit être une habitude. Ils permettent de rendre le code très lisible en nommant de façon explicite des indices ou index de tableaux. Le nom doit être en majuscules, les mots étant séparés par des "_".

Exemple en C/C++ :

```c
/** @brief List of DVB table*/
enum TABLE_DVB {
PAT = 0 , CAT = 1 , TSDT = 2 , PMT = 3 , NIT = 4 , SDT = 5 , EIT = 6
} ;
```

Ainsi si on utilise un tableau de tables DVB, on peut facilement accéder aux différentes tables sans avoir recours aux indices numériques du tableau.

Exemple en C/C++ :

```c
DVBTable_t *tpstr_listOfTables [ NB_TABLES ] ;
tpstr_listOfTables [ EIT ] = pstr_EITTable ;
```

Dans le cas d'un typedef enum le nom de l'enum sera suivi du suffixe "_t". Lors de l'instanciation de cet enum la variable portera le préfixe "e_" pour préciser qu'il s'agit d'un enum.

Exemple en C/C++ :

```c
/** @brief List of DVB table*/
typedef enum
{
    PAT = 0 , CAT = 1 , TSDT = 2 , PMT = 3 , NIT = 4 , SDT = 5 , EIT = 6
} TABLE_DVB_t ;

TABLE_DVB_t e_indexTable ;
```

Il est préférable d'utiliser des enum en créant un type (typedef enum) cependant si une variable peut prendre des valeurs définies dans des enum différents on ce contentera d'un enum sans typedef.

### Utilisation de if{}

A chaque **if**, sera associé un else même si ce dernier ne contient aucune instruction (optionnel).

```c
if ( uc_test >= VAL_MAX )
{
    uc_action = EXIT ;
}
else
{
    // Nothing to do
}
```

### Macros

Les macros ne comportant que des bouts d’instructions (pas de ";") seront encadrées par des parenthèses. Les macros de plusieurs lignes d’instructions seront quant à elles encadrées par des accolades.

### While

Les boucles "while" ne doivent jamais être bloquantes. Un nombre max d’itérations doit toujours être explicité en commentaire ou prévu sous forme d’une condition de sortie (compteur, flag).

### L'instruction goto

Ne jamais utiliser l’instruction "goto" du C/C++.

### Utilisation de "define"

Les valeurs "en dur" sont à proscrire. Elles doivent être remplacées par des "define" qui permettent une modification du code plus rapide et surtout moins risquée (en effet, seule la valeur du define déclaré dans le .h du fichier concerné est à modifier. Cette modification s’applique alors automatiquement à toutes les apparitions du define, il n’y a donc aucun risque d’oubli et surtout aucune obligation de maîtriser parfaitement le code pour en modifier certains points. De plus, le code sera plus lisible.

### Utilisation de tableaux de structures

Quand un module traite de la même manière des groupes de données de structure identique, il est judicieux de les rassembler dans un tableau. Ainsi, rajouter ou supprimer un groupe devient plus aisé.

### Utilisation de gestion dynamique de la mémoire

Lors de la déclaration d'un pointeur, la valeur NULL doit lui être assignée. De même lors de la libération de la mémoire. Pour l'allocation mémoire, il convient d'indiquer le nombre d'éléments ainsi que leurs tailles ( nombreElements * sizeof ( typeElement ) ). Naturellement un test doit vérifier si l'allocation s'est bien passée.

Exemple en C/C++ :

```c
char *pch_string ;
pch_string = NULL ;
pch_string = ( char * ) malloc ( MAX_SIZE_OF_STRING * sizeof ( char ) ) ;
if ( pch_string == NULL )
{
    printf ( "ERROR\n" ) ; // Utilisation de pch_string
}
free ( pch_string ) ;
pch_string = NULL ;
```

## Remarques complémentaires sur l’HTML

-

## Remarques complémentaires sur le PHP

### Utilisation de echo et print

Préférer l’utilisation de **echo** à **print** (car plus rapide à l’exécution). Mettre les chaines de caractère de préférence entre " ' " plutôt qu’entre " " ".

Exemple en PHP :

```php
echo 'Hello World !!!' ;
```

### Utilisation de echo dans des boucles

Préférer la concaténation des strings dans une boucle puis un seul affichage à la fin de la boucle.

Exemple en PHP :

```php
// Exemple NOK
for ( $i = 0 ; $max = count ( $myArray ) ; $i++ )
{
    echo $myArray [ $i ] . ' ' ;
}

// Exemple OK
for ( $i = 0; $max = count ( $myArray ) ; $i++ )
{
    $string .= $myArray [ $i ] . ' ' ;
}
echo $string ;
```

### Utilisation de if{}

A chaque "if", sera associé un else même si ce dernier ne contient aucune instruction (optinnel).

### While

Les boucles "while" ne doivent jamais être bloquantes. Un nombre max d’itérations doit toujours être explicité en commentaire ou prévu sous forme d’une condition de sortie (compteur, flag).

## Remarques complémentaires sur Symfony2

### Bases

### Namespace de la société

Les namespaces utilisés pour mes diférents porjet sont les suivants :
* "remiii" pour mes projets personnels
* "msc" pour les projets de mySportConnect
* ...

```php
// eg. msc\ChannelBundle
// eg. remiii\EmailBundle
```

### Controlleur

A chaque page web on doit crée un controlleur sauf pour les pages générer automatiquement. Il faut donc par exemple crée un controlleur "about", "home", "videoliste" mais il faut un seul controlleur pour crée toutes les
pages "video/#id".

### Traduction

Les clés de traduction doivent répondre aux critères suivants :
* Etre en Anglais
* Etre en minuscule
* Les mots doivent êtres séparés par des "_"
* Pour les phrases de moins de 5 mots la clé de traduction doit entre la traduction exacte, pour les phrases plus longues ou pour les paragraphes la clé de traduction doit être une courte description
* Ne pas réutiliser le nom de la rubrique dans la clé
* Ne pas mettre de majuscule dans le mot en début de phrase préférée l’utilisation de "Capitalize" dans Twig
* Mettre les traductions entre '''
* Inclure la ponctuation dans les phrases et les paragraphes

```php
// eg. subrcribe_newsletter
```

Les clés de traductions sont organisées par rubrique. Voici une liste des rubriques de base.

```php
global:
mess:
modal:
meta:
title:
header:
nav:
content:
footer:
```

Remarque : les clés de traduction fréquemment utilisées doivent être dans le bundle global.

### Bundle Global

L’ensemble des ressources, fonction, bundle, config, entity… qui est partagé par plusieurs bundle et qui n’est pas prévue pour être dans le dossier app/ de Symfony doit être mis dans le bundle global.

### Assetic

L’ensemble des assets qui sont partagés par plusieurs bundles doivent êtres dans le dossier app/. Seules les images utilisées dans la CSS doivent être dans le dossier web.

### Fichiers .dist

Les fichiers app.php.dist et app_dev.php.dist sont disponibles dans le dossier app/config/config-web/.

### Composer

Les vendors ajouté dans Composer doivent êtres si possible des versions Tagé ou des numéro de commit.

### Appel AJAX

Les requêtes AJAX doivent utiliser dans le controlleur "isXmlHttpRequest". Il faut utiliser un nom de route de la forme : nomDeLaPage/ajax/xxx.

### Autres

TODO : Dans les contrôleurs Service ou FctPrivate. Quand utiliser un autre système.

TODO : Mettre les fct en privates sauf nécessiter. Utiliser ailleurs et dès que duplication de code faire des fonctions.

### Email

Les emails doivent être dans les deux formats HTML et TXT.

## Remarques complémentaires sur le PHP/Twig

### Global

Les commentaires doivent être effectué en language Twig dans le but de ne pas être disponible sur la page HTML envoyé.

### Utilisation des variables fournis à la Template

Les variables PHP qui seront utilisées par Twig sont découpées en 3 parties :
* Var print (varPrint_nameOfVar)
* Var link (varLink_nameOfVar)
* Var fonctionnel (varFct_nameOfVar)

Exemple en PHP/Twig :

```php
varPrint_nameOfVar
varLink_home
varFct_login
```

### Liens hypertextes

Tous les liens doivent êtres formés en PHP puis ensuite affichés grâce à Twig.

Exemple en PHP/Twig :

```php
$varLink_companyFaq = $baseRoot . '/company/faq/ ' ;

// ...
// Some code
// ...

/* Render or Twig Template */

echo $twig -> render ( 'index.html' , array ( 'varLink_companyFaq' => $varLink_companyFaq ) ) ;

/* Twig Template */
<a class="test" href="{{ varLink_companyFaq }}"/>
```

## Remarques complémentaires sur les BDD et le SQL

### Nommage des tables de la BDD

Le nom des tables doit être en Anglais, en minuscule, au singulier et s’il est composé de plusieurs mots il doit être séparé par des "_".

Exemple :

```c
user
user_admin
video
video_request
club
```

### Mise en forme

Les mots clefs doivent toujours être en majuscule et alignés.

Exemple en PHP :

```php
$query = 'SELECT user.fname AS user_fname ,
                user.name AS user_name ,
                video.name AS video_name
         FROM user
             INNER JOIN video ON user.id = video.user_id
         WHERE email = contact@apple.com' ;
```

### Renommage des colonnes

Lors de utilisation de plusieurs table il faut renommer les colonnes de la forme suivante : nomDeLaTable_nomDeLaColonne

Exemple :

```php
user.fname AS user_fname
```

## Les fichiers

### Convention de syntaxe

Chaque fichier sera affecté à une tâche ou à un module bien défini. Son nom devra être le plus explicite possible. Le nom est écrit en minuscules avec une majuscule à chaque début de mot (ex : moduleName.c, moduleName.php).

Le fichier contenant le main d'une application porte le nom de l'exécutable (avec l'extension .c ou .cpp bien évidement). Exemple : le fichier scan.c contient la fonction main de l'exécutable scan.

Les fichiers d'entêtes en C/C++

Les fichiers portant l’extension ".h" contiennent dans cet ordre :
* l'en-tête doxygen
* la licence
* les instructions préprocesseur #ifndef et #define pour éviter les doubles inclusions (Cf. #ifndef, #define, #endif)
* des inclusions standards
* des inclusions des fonctions communes (chemin depuis le common/include <ratatouille/team.h>)
* des inclusions locales (propre à la fonction)
* des constantes (define) devant être exportés
* des constantes (const) devant être exportés
* des macros des définitions de type (typedef, struct, union) devant être exportés
* des déclarations d’exportation de fonctions ou de variables (extern)
* des prototypes de fonctions devant être exportés
* l'instruction préproceseur #endif suivie d'une ligne vide

Exemple :

```c
/**
* @file checkTeam.h *
* @brief Headers of the checkTeam.c file *
* @see
*
* $Author: $
* $Date: $
*
* $Revision: $
*/
￼￼￼￼￼￼￼

/*
 * Licence
 */
#ifndef _CHECK_TEAM_H
#define _CHECK_TEAM_H

/* * Standard includes */
#include <string.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <errno.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <sys/ioctl.h>

/* * DVB api includes */
#include <linux/dvb/frontend.h> #include <linux/dvb/dmx.h>

/* * Includes from common */
#include <ratatouille/team.h> #include <ratatouilleTeam.h>

/* * Local includes */
#include "checkTeam.h"

/* * Defines */
/** @def EXEMPLE * Just an example */
#define EXEMPLE 33

/* * Const */
...

/* * Macros */
...

/* * Typedef */
/** @brief defining the the audio/video (/data ?) part of a service */
typedef struct
{
    /** @brief comment about the pid */
    char * pch_nickName ;

    /** @brief the pid */ unsigned char uc_age ;

} ratatouille_t ;

/*
 * Extern
 */

extern unsigned char uc_toto ;

/*
 * Functions
 */

/**
 * @brief Function used to check the team *
 * @param pstr_ratatouilleTeam A pointer on a ratatouille_t structure *
 * @return Error code of the function
 * @retval 0 No error
 * @retval -1 An error occurred
 */
signed char checkTeam ( ratatouille_t * pstr_ratatouilleTeam ) ;

#endif // _CHECK_TEAM_H
```

## Les fichiers sources en C/C++

Les fichiers portant l’extension ".c" (ou ".cpp" pour les fichiers C++) contiennent dans cet ordre :
* l'en-tête doxygen
* la licence
* l'inclusion du header associé (ex: #include "moduleName.h")
* des définitions de type (typdef, struct, union, enum) **ne devant pas être exportés**
* des constantes (const ou define)
* des déclarations de variables
* les prototypes des fonctions définies dans le même fichier et ne devant pas être exportés
* du code suivi de deux lignes vide

**La fonction main doit se situer après les déclarations globales et avant l'implémentation des fonctions et méthodes, donc en haut du fichier !!!**

Exemple :

```c
/**
 * @file checkTeam.c *
 * @brief Example code used in the Wiki *
 * @see
 *
 * $Author: $
 * $Date: $
 *
 * $Revision: $
 */

/*
 * Licence
 */

#include "checkTeam.h"

/**
 * @brief Usage function is used when help is asked, or when too much arguments are send
 */
void usage ( void ) ;
int main ( int i_argc, char ** ppch_argv )
{
    signed char c_return = OK ;
    ratatouilleDevelopper_t tstr_ratatouilleDevelopper [ 8 ] = { { "BuzzLeCleir" , 24 , "Hard" } , { "CimCim" , 24 , "Soft" } , { "Felixzm" , 26 , "Soft" } , { "Laurence" , 23 , "Hard...
    ratatouilleTeam_t str_ratatouilleTeam = { ( ratatouilleDevelopper_t * ) &tstr_ratatouilleDevelopper [ 0 ] , 8 } ;
    if ( i_argc == 1 )
    {
        if ( printTeam ( str_ratatouilleTeam ) < 0 )
        {
            printf ( "I don't know how you can be here !!!!\n" ) ;
        }
        else
        {
        }
    }
    // No use to get an else here, but we have to write it
    else if ( i_argc == 2 && ( strcmp ( ppch_argv[1],"?" ) != 0 ) && ( strcmp ( ppch_argv[1],"help" ) != 0 ) )
    {
        if ( checkTeam ( ppch_argv[1], str_ratatouilleTeam ) < 0 )
        {
            c_return = ERROR;
        }
        else
        {
        }
    }
    else // No use to get an else here, but we have to write it
    {
        usage ( );
    }
    return (int) c_return; }
    void usage ( void ) {
    printf ( "\nThis is just little program used as example in the WiKi.\n" ) ;
    printf ( "Usage: checkTeam [ ? | help | NAME]\n\n" ) ;
    printf ( "\t? or help ==> this help\n" ) ;
    printf ( "\tNAME ==> check if NAME is in the team list\n\n" ) ;
}
```

### Entête de fichier

L’entête de chaque fichier doit contenir un commentaire utilisable par doxygen (cf. $7).

Exemple :

```c
/**
 * @file testFile.c *
 * @brief A simple test for demonstration
 * This program doesn't really do something it's just an example *
 * $Author: updated by subversion $
 * $Date: updated by subversion $ *
 * $Revision: updated by subversion $
 */

/* Licence */
```

## Organisation des fichiers en C/C++

Le dossier racine est organisé en 3 sous-dossiers :
* modules : Contient des dossiers représentants l'ensemble des fonctionnalités
* lib : Contient les librairies produites et utilisées par notre application
* bin : Contient les fichiers exécutables

Le dossier racine contient également le Makefile, ainsi qu'un README.

Chaque dossier « modules » est décomposé en 3 sous-dossiers :
* src : Contient les sources liées à chaque fonctionnalité
* include : Contient les headers liées aux sources, et propres à chaques fonctionnalité
* obj : Contient les objets, lors de la compilation

Chacun de ces sous-dossiers contient un Makefile, et peut contenir un README.

Il est à noter la présence d'un module spécial, nommé "common". Celui-ci contient l'ensemble des headers et autres sources qui seront nécessaires à plusieurs fonctionnalités. Cela afin d'éviter d'avoir à redéfinir plusieurs fois un même en-tête.

Le dossier src est décomposé en sous dossier pour les besoins des différentes applications. Les fichiers sources propres à une application sont placés dans un répertoire du nom de cette dernière, lui-même situé dans le répertoire src. Les modules communs à plusieurs applications sont placés dans le répertoire src et hiérarchisé selon leur répertoire propre.

Exemple : Dans l'exemple suivant, le dossier racine s'appelle mySportConnect. 1 programme est créé : VideoConvert. On retrouve également le module common, qui contient des applications qui seront utilisées par plusieurs programmes. On peut donc considérer que dans la majeure partie des cas, le dossier common ne contiendra que des sources de librairies. Dans le répertoire include (toujours sous common) se trouvent les fichiers « .h » nécessaires à la compilation des modules. On y retrouve également tous les fichiers décrivant la structure des sections et des descripteurs de la norme MPEG. Etant donné que ces structures seront largement utilisées dans nos applications, ils y ont leurs places.

## Organisation des fichiers en Symfony2

TODO

## Génération automatique de la documentation

Doxygen est un outil de génération de documentation à partir de code source. Pour cela il utilise des commentaires placés dans le code. Il sera utilisé pour générer un document de synthèse du logiciel. Il existe plusieurs manières d'écrire des commentaires. Doxygen en utilise certain d'entre eux qui sont rédigés avec une syntaxe particulière. Les commentaires que Doxygen doit analyser commencent par la séquence "/**" et se terminent comme un commentaire classique "*/".

Exemple :

```c
/** Texte en commentaire */
```

Note : Ces commentaires peuvent également être placés sur plusieurs lignes.

### Règles

Doxygen analyse les commentaires qui le concernent. Dans ces commentaires il s'attend à trouver certains mots-clefs lui permettant de comprendre le sens desdits commentaires. Ces mots-clefs commencent par un arobase (@), en voici une liste non exhaustive.

Dans l'entête du fichier :
* @file : définit le nom du fichier.
* @brief : donne une description brève du fichier.

Devant un #define :
* @def : définit le nom du \#define.

Devant un typedef :
* @brief : donne une description brève du typedef.

Devant une macro :
* @brief : donne une description brève de la macro.
* @param : décrit un paramètre d'entrée de la macro.
* @return : décrit un paramètre de sortie de la macro.
* @retval : décrit les valeurs possibles pour la sortie de la macro.

Devant une fonction ou un prototype de fonction :
* @brief : donne une description brève de la fonction.
* @param : décrit un paramètre d'entrée de la fonction.
* @return : décrit un paramètre de sortie de la fonction.
* @retval : décrit les valeurs possibles pour la sortie de la fonction.

Si la fonction ne possède aucun paramètre d’entrée ni de sortie, il faut rajouter une ligne vide plus une ligne supplémentaire de commentaire afin que Doxygen prenne en compte le code de la fonction.

Les commentaires de fonctions sont toujours placés devant le prototype (sauf pour la fonction main qui n'en a pas) plutôt que devant la fonction elle-même.

Les commentaires utilisés sans mots-clefs sont considérés comme des descriptions longues de ce qui suit le commentaire.

En plus de ces mots-clefs, Doxygen comprend les keywords propres à Subversion/GIT tels que :
* $Author$ : définit le nom de l'auteur du fichier
* $Date$ : définit la date de dernière modification du fichier
* $Revision$ : définit la version du fichier

Ces keywords sont automatiquement mis à jour par Subversion/GIT à chaque commit.

### Exemples

#### En-tête de fichier

```c
/**
 * @file mySportConnectAppli.c *
 * @brief Main application of the mySportConnect *
 * $Author: Rémi BARBE $
 * $Date: 2011-10-12 17:23:35 +0200 (ven., 12 octobre. 2011) $ *
 * $Revision: 438 $
 */

/* Liscence */
```

#### #define en C/C++

```c
/** @def EIT_MAX_SIZE * max size of an EIT table */
#define EIT_MAX_SIZE 4096
```

#### typedef struct en C/C++

```c
/** @brief list of the descriptor component */
typedef struct
{
    /** @brief tag descriptor */
    unsigned char uc_descriptor_tag : 8 ;
    /** @brief length descriptor */
    unsigned char uc_descriptor_length : 8 ;
    ...
} descComponent_t ;
```

#### typedef enum en C/C++

```c
/** @brief List of DVB table*/
typedef enum
{
    PAT = 0 ,
    CAT = 1 ,
    TSDT = 2 ,
    PMT = 3 ,
    NIT = 4 ,
    SDT = 5 ,
    EIT = 6
} TABLE_DVB_t ;

TABLE_DVB_t e_indexTable ;
```

#### enum en C/C++

```c
/** @brief List of DVB table*/
enum TABLE_DVB
{
    PAT = 0 ,
    CAT = 1 ,
    TSDT = 2 ,
    PMT = 3 ,
    NIT = 4 ,
    SDT = 5 ,
    EIT = 6
} ;
DVBTable_t *tpstr_listOfTables [ NB_TABLES ] ;
tpstr_listOfTables [ EIT ] = pstr_EITTable ;
```

#### Fonction

```c
/**
 * @brief A simple function for a test.
 * @param s_flagPMT is a flag for the PMT.
 * @param us_count is a counter for the PMT.
 * @return Error code according to the execution of the function. * @retval NO_ERROR The function ends normally.
 * @retval EINVAL The value of an argument made no sense.
 */
unsigned char myFunction ( signed short s_flagPMT , unsigned short us_count ) ;
```

#### Classe

```c
/**
 * @brief A simple class for a test. * This class is just an example.
 */
class MyClass { } ;
```

By the way, if you found a typo, please fork and edit this repository. Thank you so much!

