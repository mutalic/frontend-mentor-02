## Table of contents

- [Overview](#overview)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
- [Author](#author)

### Screenshot

[Mobile Version](./screenshots/mobile.png)
[Desktop Version](./screenshots/desktop.png)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## My process

- HTML architecture & CSS class names
- CSS custom variables
  - colors
  - font styling (sizes)
- Dynamic data fetching for summary aspects (data.json file)
- Mobile design first then desktop design.
- Added hover/focus interactivity for continue button.


### Built with

- Semantic HTML5 markup
- CSS custom properties (color)
- CSS Flexbox
- Mobile-first workflow
- Javascript for dynamic data binding and element generation.

### What I learned

#### 1. Dynamic Data Binding
Instead of hard coding HTML elements, I used async/await to fetch data and dynamically generate HTML elements and bind the fetched data.
Here is my JavaScript code for dynamic data fetching/binding:
```Javascript
async function getData(url) {
      let data = await fetch(url)
        .then((response) => response.json())
        .then((data) => {

          let colors = [
            { color: `--primary--light-red`, bg: `--transparent--light-red`, id: "red" },
            { color: `--primary--orangey-yellow`, bg: `--transparent--orangey-yellow`, id: "yellow" },
            { color: `--primary--green-teal`, bg: `--transparent--green-teal`, id: "teal" },
            { color: `--primary--cobalt-blue`, bg: `--transparent--cobalt-blue`, id: "blue" }
          ]

          data.forEach(function (aspect, i) {
            let aspectHTML = `
              <div id=${colors[i].id} class="summary--aspect" style="background-color: var(${colors[i].bg})">
                <div class="aspect--name">
                  <img src=${aspect.icon} class="aspect--icon"><p class="fs-sm" style="color:var(${colors[i].color})">${aspect.category}</p>
                </div>
                <div class="aspect--score">
                  <p class="fs-sm" style="color: var(--bg--dark-gray-blue)">${aspect.score} <span style="color: gray">/ 100</span></p>
                </div>
              </div>
              `;

            document.getElementById('aspects').innerHTML += aspectHTML;
          })
        })
    }
    getData('./data.json');
```
#### 2. Media Queries
I was able to use @media to set an appropriate breakpoint (960px for this challenge) for mobile/desktop designs. I started with mobile, since it is inherently responsive and the "display: block" of most "container" elements make it easier to design for mobile. I then applied flexbox for the desktop design.

### Continued development

#### 1. Better naming for CSS custom variables (color)
I would like to work on a better color naming system that would allow me to define reusable css custom variables. For now, my variable names are correlated with the actual colors used, which would make me have to redefine new custom variables if I were to change the color theme of the project. I need a consistent, reusable naming system.

#### 2. Better HTML architecture and CSS classnames.
I need to figure out which CSS designs stay the same regardless of user device/screen size, and which designs change depending on device. This way, I can make as few changes as possible when using media queries to style for different devices. I should spend more time planning ahead before starting to code so that this saves time when actually writing HTML and styling elements.

#### 3. Better understanding of how to set width, min/max-width, height, min/max-height.
I noticed that my project wouldn't behave as expected at times and that many times it was the min/max width or height setting doing that. I need to think about how to set those properties before styling them.

## Author

- Github - [mutalic](https://github.com/mutalic)
- Frontend Mentor - [@mutalic](https://www.frontendmentor.io/profile/mutalic)