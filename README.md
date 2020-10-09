# About:

This standalone vanilla JavaScript plugin creates scrollToTop button.  
Button will appear when user will scroll page over 100px.  
Button has default styling in attached CSS file.  



# Implementation
1 - copy scrollToTop.js, scrolltotop.css, up-arrow.png files to your project <br/>
2 - apply scrolltotop.css in ```<header>``` section: <br/>
```<link rel="stylesheet" href="scrolltotop.css" type="text/css">``` <br/>
3 - apply scrollToTop.js beffore closing <body> tag: <br/>
```<script src="scrollToTop.js"></script>``` <br/>
4 - execute below line in your main.js file: </br>
```window.scr00lToTop(); ```
 

# How it works:

```
(function() {

    // create button 
    const createButton = () => { 
        const btn = document.createElement('button'); //create a button element
        btn.className = 'scrollToTop hidden'; // add classes to the btn element (button is hidden by deafult)
        document.body.appendChild(btn); //append btn element to body
        return btn;
    }

    // scrolltotop animation 
    const animateScroll = () => { 
        if (document.documentElement.scrollTop > 0) {
            document.documentElement.scrollBy(0, -10);
            setTimeout(animateScroll, 5); // repeat the animation until condition is met
        }
    }

    // initialaze 
    const init = () => {
        const btn = createButton(); // fire createButton() function 
        btn.addEventListener('click', animateScroll); // add click event for button and apply animateScroll function
        window.addEventListener('scroll', () => { // add scroll event to window object 
            if(document.documentElement.scrollTop > 100) { // setting after how many px the scroll button should appear
                btn.classList.remove('hidden'); //  remove hidden class
            } else {
                btn.classList.add('hidden'); // add hidden class
            }
        }, false);
    }

    // add scr00lToTop property to window object and apply init function 
    window.scr00lToTop = init;
})();
```
