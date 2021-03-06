## selectors

    ul {							<- propriedades aninhadas
      color: green;
      li {
        font-size: 16px;		

        &:hover {						<- li:hover
          font-size: 20px;
        }
      }
    }

## variables

    $largura: 100%;
    $cor-de-fundo: green;
    $cor-da-borda: solid 1px $cor-de-fundo;
    $margem: 10px 25px 10px 25px;				                        <- listas
    $cor-de-icones: ( facebook: #3b5998, flickr: #0063db, souncloud: #f60 )		<- maps *

    body { width: $largura; background-color: $cor-de-fundo; border-color: cor-da-borda }
    div { margin: $margem }

## properties

    $name: teste;   					<- nome de uma classe ou id
    $borda: border; 

    p.#{$teste} {						<- elemento com a classe teste da cor azul
      #{$borda}-color: blue;	  	
    }

## extend

            SCSS 							CSS
                                  
    .msg {							.msg, .mdg-success, msg-error {	
      border: solid 1px;					  border: solid 1px;	
      text-align: center;					  text-align: center;	
    }							}

    .msg-success {						.msg-success {
      @extend .msg;					  	  border-color: green;
      border-color: green;					  background-color: green;
      background-color: green;				}
    }

    .msg-error {						.msg-error {	
      @extend .msg;   					  border-color: green;
      border-color: green;					  background-color: red;	
      background-color: red;          			}	
    }

## mixins 

    @mixin teste($radius, $color: blue) {
      border-radius: $radius;
      color: $color;
    }

    .box {
      @include teste(4px);					<- borda com 4px de radius
    }

    .box2 {
      @include teste(4px, green)				<- borda com 4px de radius e cor verde
    }

    @mixin teste2($valor...) {				<- deixa a quantidade de parâmetros implícito
      padding: $valor;
    }

    p {
      @include teste2(10px 10px);
    }

    h1 {
      @include teste2(10px 5px 10pox 5px);	
    }

## placeholders

    %centro {
      display: block;
      margin: 0 auto;
    }

    div {
      @include %centro;
    }
    --ou--

    div {
      @extend %centro;
    }							<- agrupa os dois com o mesmo estilo
    p {
      @extend %centro;
    }

## operations

    font-size: 10px + 2 // 10px - 2 // 10px * 2 // (10px /2) // 27px % 2

## functions

    @function calc-fluid($alvo, $container) {
      @return ($alvo / $container) * 100;
    }

    div {
      width: calc-fluid(500, 100);
    }

## if/else

    $template: blue;

    header {
      @if($template == dark) {
        color: #000;
      } @else if($template == blue) {
        color: #blue;
      } @else {
        color: red; 
      }
    }

## for

    @for $i from 1 through 3 {					<- itera até o 3 
      .item-#{$i} {
         width: 2em * $1;
      }
    }

    @for $i from 1 to 3 {						<- itera até o 2
      .item-#{$i} {
         width: 2em * $1;
      }
    }

## each

    @each $animal in gato, cao, lebre {
      .#{animal}-icon {
        background-image: url('/img/#{animal}.png');
      }
    }
    --ou--
    $animals: in gato, cao, lebre;

    @each $animal in gato, cao, lebre {
      .#{animal}-icon {
        background-image: url('/img/#{animal}.png');
      }
    }

## while

    $i: 6;

    @while $1 > 0 {
      .item-#{$i} {
        width: 2px * $i;
      }
      $i: $i - 2;
    }

## media

    .sidebar {
      width: 30%;
      @media screen and (orientation: landscape) {
        width: 40%; 
      }
    }

## import

    @import arquivo.scss;

    @import "teste.css";
    @import "teste" min-width: 400px;
    @import "http://teste.com";
    @import @import url("http://fonts.googleapis.com/css?family=Droid+Sans");
