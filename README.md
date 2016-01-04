## Website Performance Optimization portfolio project

So we were given a slow loading website and asked to optimize the speed

### Getting started

#### Part 1: Optimize PageSpeed Insights score for index.html

By following the below instructions I was able to test the site on googles speed test 


  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> ngrok http 8080
  ```

Happy to report the speed rates are now above 90

Improving Critical path 
1. This was done by inlineing critical CSS using https://jonassebastianohlsson.com/criticalpathcssgenerator/
2. Placing non critical CSS at the end of the file or giving it a media attribute
3. Async-ed all non critical JS

Compressing Data
1. images were compressed and shrunk when appriote
2. All files minified

TODO
CACHE
Further compress
Grunt or Gulp should be used in compress all imgs and minify all code
  

#### Part 2: Optimize Frames per Second in pizza.html

We started with avery wacky website made to illustrate the dangers of recalulating fixed values in the for loop, and possible when to use web workers but I have yet to tackle that.


Below was the main offender: 

```
function changePizzaSizes(size) {

        //create the array outside the for loop
        var pizzaArray = document.getElementsByClassName("randomPizzaContainer"); //faster api

        //also good outside the loop
        var length = pizzaArray.length;

        var dx = determineDx(pizzaArray[0], size); //bad in loop as it is a fixed number 
        var newwidth = (pizzaArray[0].offsetWidth + dx) + 'px';

        for (var i = 0; i < length; i++) {
            pizzaArray[i].style.width = newwidth;
        }
    }

```

In which the program was recalculating the dx and newwidth variables each iteration even though the the values do not change. 

Other improvements where made such asusing document.getElementsByClassName(). 

### Customization with Bootstrap

there has been some costumization more to come
