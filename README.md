## Ruby sass compass
# Ruby
https://rubyinstaller.org/downloads/  --Langage de programmation
ruby --version

# sass
https://sass-lang.com/documentation/
gem install sass  --Langage de programmation

# compass
gem install compass  --Framework

## SASS
# écouter et générer css standard
sass --watch sass:css

# écouter et générer css comprésé
 sass --watch sass:css --style=compressed --no-source-map

# Sans source map
sass --watch sass:css --style=compressed --sourcemap=none

## scss
.btn{
    background: rgb(186, 3, 125);
    &:hover{ // pour coller :
        background: #e30e0e;
    }
    .theme-vert & {// pour .btn qui se trouve dans .theme-vert
        background: #0ee35c;
    }
}

# repetition du texte 
background: {color: #000;repeat: no-repeat;} => background-color: #000;background-repeat: no-repeat;

# @extend
La règle de Sass @extend résout ce problème. C'est écrit @extend <selector>, et cela dit à Sass qu'un sélecteur doit hériter des styles d'un autre
.call-to-action{
    @extend .btn;
}
# %btn
pour créer des regles et peut être utilisé grace à @extend sinion jamais apparait dand css 

# variables
$variable: 20   $

# Unitées
padding: $variable + 10em => 30em

# utiliser les fichiers des variables 
dans libs => responsive.scss => 
$medium-up: "only screen and (min-width: 768px)"
dans style.scss => 
@import "libs/responsive.scss";  // on importe toutes les varibles
pour utiliser la variable => #{$medium-up}
@media #{$medium-up} {
    .btn{
        width: 100%;
    }
   }

# !default
$medium:768px!default; indique qu'il est utilisé uniquement si cette variable ne pas declaré précédément $

## Fonctions 
# darken
background: darken($primary, 20); //assombrire de 20%
# lighten
background: darken($primary, 20); //éclaircir de 20%

# rgba($primary, 0.5)  //ajoute la pransparence

## Mixins
https://sass-lang.com/documentation/at-rules/mixin
Dans fichier mixins.scss =>
@mixin rotate($rotation:10deg){
    -ms-transform: rotate($rotation);
    -webkit-transform: rotate($rotation);
    transform: rotate($rotation);
}
dans style.scss =>
.card{
  @include rotate(60deg)
}


# lightness($primary)>50% //plus clair que $primary

# @debug lightness($primary); //afficher variable dans console

# for 
@for $i from 1 through 4 {
  .m-#{$i}{
    margin: 0 $i * 1rem;
  }
}
resultat .css => 
.m-1 {
  margin: 0 1rem; }
.m-2 {
  margin: 0 2rem; }
.m-3 {
  margin: 0 3rem; }
.m-4 {
  margin: 0 4rem; }

# @each //boucle avec une valeur 
    $animals: bear, lion, camel;
  @each $animal in $animals{
    .icon-#{$animal}{
        background: url(img/#{animal}.png);
    }
  }
   $animals: bear, lion, camel;
  @each $animal in $animals{
    .icon-#{$animal}{
        background: url(img/#{animal}.png);
    }
  }
# @each //boucle avec deux valeurs
  $categories:
  chien #ff0000,
  chat #00FF00,
  poissont #0000ff;
  
  @each $categorie in $categories{
    .#{nth($categorie, 1)}{
        background: nth($categorie, 2);
    }
  }
resultat .css => 
.chien {
  background: #ff0000; }

.chat {
  background: #00FF00; }

.poissont {
  background: #0000ff; }

## Syntaxe SASS
chercher ext:sass en installer

## Commentaires
# //Commentaire non visible dans css final
# /* Commentaire visible dans css final */