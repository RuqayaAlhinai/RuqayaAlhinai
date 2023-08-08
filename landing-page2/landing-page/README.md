# Landing Page Project

## Table of Contents

* [Instructions](#instructions)

## Instructions

The starter project has some HTML and CSS styling to display a static version of the Landing Page project. You'll need to convert this project from a static project to an interactive one. This will require modifying the HTML and CSS files, but primarily the JavaScript file.

To get started, open `js/app.js` and start building out the app's functionality

For specific, detailed instructions, look at the project instructions in the Udacity Classroom.


# Project Name

Project Name is Loading page that has four sections can transport between them by dynamic navbar

## Installation

can Install the project from the udacity website

## Usage

You can move between the sections through the navigation bar in top the page and they can move easily because I use the smooth scroll between the sections.
this is the code:
*{
scroll-behavior: smooth;
}

and I use hamburger to appears the list in an orderly manner when using small screens.
this is the code:

/*Create hamburger by JavaScript*/
  const hamburger = document.querySelector(".hamburger");
const navMenu = document.querySelector(".navbar__list");

hamburger.addEventListener("click", mobileMenu);

function mobileMenu() {
    hamburger.classList.toggle("active");
    navMenu.classList.toggle("active");
}

## Features

- Move easily between the section by two way
  1- click the item and move the specific section
2-On scroll to go to position

## Contributing

Create a Branch in their forked repository. This helps keep their changes separate from the main branch.
Make Changes this helps keep their changes separate from the main branch.

## License

This project is licensed under the [MIT License](https://opensource.org/license/mit-0/)

## Credits

- [w3schools](https://www.w3schools.com/) - It help me to get some code and how I use it in correct way.
- [stackoverflow](https://stackoverflow.com/) - I get answer about any question I faced

## Documentation



//Create Navbar List Items 

/**
 Define Global Variables**/
 const sec = document.querySelectorAll("section");
const navList = document.getElementById("navbar__list");
const items = ["Section 1", "Section 2", "Section 3", "Section 4"];
const li = document.querySelectorAll(".menu__link");



//Build the nav
items.forEach((item, i) => {
  const el = document.createElement("a");
  
  el.innerHTML = item;
  el.classList.add("menu-link");
 // el.setAttribute("id", `menu-${i + 1}`);
  el.href = `#section${i + 1}`;
  
  // Create a list item
  const li = document.createElement("li")

  // Append the anchor to the list item
  li.appendChild(el);
  
  // Append the list item to the list
  navList.appendChild(li);
});



//Active Navbar list item When you click the item
var tabLink = document.querySelectorAll('a');
 

function clearActiveItemMenu(){
	tabLink.forEach(function(item){
  	if(item.classList.contains('active')){
    	item.classList.remove('active');
    }
  });
}

tabLink.forEach(function(item){

    item.addEventListener('click', function(){
        clearActiveItemMenu();
        item.classList.add('active')
    }, false)

})


window.onscroll = () => {
  var current = "";

  sec.forEach((section) => {
    const sectionTop = section.offsetTop;
    if (scrollY >= sectionTop - 60) {
      current = section.getAttribute("id"); }
  });

  li.forEach((li) => {
    li.classList.remove("active");
    if (li.classList.contains(current)) {
      li.classList.add("active");
    }
  });
};

/*Scroll to section on link click*/
// Get all sections that have an ID defined
const sections = document.querySelectorAll("section[id]");

// Add an event listener listening for scroll
window.addEventListener("scroll", navHighlighter);

function navHighlighter() {
  
  // Get current scroll position
  let scrollY = window.scrollY;
  
  // Now we loop through sections to get height, top and ID values for each
  sections.forEach(current => {
    const sectionHeight = current.offsetHeight;
    const sectionTop = current.offsetTop - 50;
    sectionId = current.getAttribute("id");
    
  
    if (
      scrollY > sectionTop &&
      scrollY <= sectionTop + sectionHeight
    ){
      document.querySelector(".navbar__list a[href*=" + sectionId + "]").classList.add("active");
    } else {
      document.querySelector(".navbar__list a[href*=" + sectionId + "]").classList.remove("active");
    }
  });
}


/*Create hamburger by JavaScript*/
  const hamburger = document.querySelector(".hamburger");
const navMenu = document.querySelector(".navbar__list");

hamburger.addEventListener("click", mobileMenu);

function mobileMenu() {
    hamburger.classList.toggle("active");
    navMenu.classList.toggle("active");
}



document.addEventListener("scroll", function () {
  const navbar = document.querySelector(".navbar__list");
  const navbarHeight = 100;
  const distanceFromTop = Math.abs(
    document.body.getBoundingClientRect().top
  );
  if (distanceFromTop >= navbarHeight) navbar.classList.add("fixed-top");
  else navbar.classList.remove("fixed-top");
});
