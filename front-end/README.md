# Bolsas Favoritas

This is a solution to the Front-End Test. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
- [Author](#author)


## Overview

### The challenge

- O projeto possui uma única página, com a lista de favoritos e um modal para a busca de cursos;
- A clicar em Adicionar curso, deve abrir o modal de busca;
- A busca deve conter os seguintes filtros:
  - Cidade;
  - Curso;
  - Modalidade (Presencial/EaD);
  - Preço;
- A lista de cursos deve ter ordenação por nome da faculdade;
- Múltiplos cursos podem ser selecionados e adicionados à lista de favoritos;
- O botão Adicionar bolsa(s) deve ficar desabilitado enquanto não houver cursos selecionados;
- Os cursos podem ser removidos da lista de favoritos, através do botão Excluir;
- O botão Ver oferta não leva a lugar algum;
- Bolsas com { enabled: false }, devem aparecer com o botão Indisponível;
- A lista de favoritos deve respeitar o semestre selecionado.

### Screenshot

![](https://github.com/RodrigoGabrielRB/BolsaFavorite/blob/main/gifs/image1.gif?raw=true)
![](https://github.com/RodrigoGabrielRB/BolsaFavorite/blob/main/gifs/image2.gif?raw=true)
![](https://github.com/RodrigoGabrielRB/BolsaFavorite/blob/main/gifs/image3.gif?raw=true)

Here is my app

### Links

- Solution URL: [Project](https://github.com/RodrigoGabrielRB/BolsaFavorite/tree/main/front-end)
- Live Site URL: [Site](http://rodrigorgrb.com.br/100days/013/)

## My process


### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Componentização e reutilização
- Vue

### What I learned

Here, my filter to convert number to money
```js
return value.toLocaleString("pt-br", {style: "currency",currency: "BRL",});
```

Here, Logic to filter courses list
```js
let filtered = this.allCourse.filter(
        (x) =>
          (x.campus.city == this.filter.city || this.filter.city == null) &&
          (x.course.name == this.filter.course || this.filter.course == null) &&
          (x.price_with_discount <= this.filter.moneyToPaid ||
            this.filter.moneyToPaid == null)
      );

      if (!this.filter.presencial || !this.filter.ead) {
        if (this.filter.presencial) {
          filtered = filtered.filter(
            (x) => x.course.kind.toUpperCase() == "Presencial".toUpperCase()
          );
        }

        if (this.filter.ead) {
          filtered = filtered.filter(
            (x) => x.course.kind.toUpperCase() == "EaD".toUpperCase()
          );
        }
      }
```
### Continued development

Yeah, in this project, i have pendents things to do, for example site normal, because i only make the mobile site, Create a mini-framework to css components like Checkbox, radio, select, range, create a global color configuration, tests on the front, a service was created to call the api, but it is not a real api called, create variables to control responsiveness,

### About the test
In general the test is simple, but creating from scratch is very interesting because it brings real difficulty, and things that sometimes go unnoticed by using a framework like changing the style of a checkbox, button or even the range, are things that in the day by day you do it in automatic and when you have to do it from scratch it's really fun.
I really liked it, too bad I didn't have a lot of useful time to play on the project, in general I did it in 2 days but I had a lot of learning


## Author

- Website - [http://rodrigorgrb.com.br](http://rodrigorgrb.com.br)
- Linkedin - [@RodrigoGabrielRB](https://www.linkedin.com/in/rodrigorgrb/)


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

