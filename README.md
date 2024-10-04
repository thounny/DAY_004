# DAY_004 | Camille Mormal Slider

This project is part of the daily code challenge series, **DAY_004**, and it showcases an interactive image slider inspired by Camille Mormal's portfolio, which was awarded Site of the Day on [Awwwards](https://www.awwwards.com/sites/camille-mormal-portfolio-22). The slider allows you to navigate through animated `.gif` images with smooth transitions using GSAP (GreenSock Animation Platform).

---

## DEMO
![Camille Mormal Slider Demo](./assets/DAY_004_1.gif)  

## INSPIRATION
![Camille Mormal SOTD](./assets/DAY_004_2.gif)  

---

## Project Structure

```bash
DAY_004/
│
├── assets/
│   ├── img1.gif
│   ├── img2.gif
│   ├── img3.gif
│   ├── img4.gif
│   ├── img5.gif
├── index.html
├── styles.css
└── script.js
```

## Features

- **Interactive Slider**: Click to navigate between slides, or use the preview images to jump to specific slides.
- **GIF Animations**: The slider displays animated `.gif` images with smooth transitions.
- **Custom GSAP Easing**: The animations use a custom `hop` easing function for engaging visual effects.
- **Counter and Titles**: The slider includes an animated counter and changing titles for each image.

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/thounny/DAY_004.git
   ```
2. Open the `index.html` file in your web browser.

## How the JavaScript Works

### GSAP Animations

The JavaScript leverages GSAP for smooth transitions between images, counter, and title updates. A custom easing function `hop` controls the animation timing:

```javascript
CustomEase.create("hop", "M0,0 C0.071,0.505 0.192,0.726 0.318,0.852 0.45,0.984 0.504,1 1,1");

gsap.to(counter, {
  y: counterY,
  duration: 1,
  ease: "hop",
});

gsap.to(titles, {
  y: titleY,
  duration: 1,
  ease: "hop",
});
```

### Navigating Between Slides

When a slide is clicked, the script animates the new image in and moves the old image out of view. The preview thumbnails update accordingly:

```javascript
function animateSlide(direction) {
  gsap.to(currentSlide.querySelector("img"), {
    x: direction === "left" ? 500 : -500,
    duration: 1.5,
    ease: "hop",
  });

  gsap.to(slideImgElem, {
    x: 0,
    duration: 1.5,
    ease: "hop",
  });
}
```

### Resetting the Slider

To prevent performance issues, old images are removed once the total number of images exceeds the allowed limit:

```javascript
function cleanupSlides() {
  const imgElements = document.querySelectorAll(".slider-images .img");
  if (imgElements.length > totalSlides) {
    imgElements[0].remove();
  }
}
```

---
## Author

![logo](https://web.archive.org/web/20091027053343/http://geocities.com/animecap/index_dwn.gif)

**Thounny Keo**  
Frontend Development Student | Year Up United
