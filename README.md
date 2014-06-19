Simple-API
==========


Steps:  
1. Create a new repo  
2. Create a new branch called gh-pages
3. Create a YML file in a /_data folder, name it `objects.yml`, insert the below, and save.  

````
rover:
  age: 2
  breed: lab
  color: black
spot:
  age: 3
  breed: dalmation
  color: white
lassie:
  age: 70
  breed: collie
  color: brown
````

4. Create a json template file and modify the term after 'site.data' to include the name of the yml file  

````
---
---
{{ site.data.dogs | jsonify }}
````

5. Create an xml template 


````
---
---
<dogs>
  {% for dog in site.data.dogs %}
  <dog>
    <name>{{ dog[0] }}</name>
    <breed>{{ dog[1].color }}</breed>
    <age>{{ dog[1].age }}</age>
    <color>{{ dog[1].color}}</color>
  </dog>
  {% endfor %}
</dogs>
````

6. Create an html template 


````
<html>
  <body>
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
    <script>
    $.getJSON( "dogs.json", function(dogs) {
      $.each(dogs, function(name, attributes) {
        document.write("<h2>" + name + "</h2>");
        document.write("Age: " + attributes["age"] + "<br />");
        document.write("Breed: " + attributes["breed"] + "<br />");
        document.write("Color: " + attributes["color"] + "<br />");
      });
    })
    </script>
  </body>
</html>
````

7. Create a csv template 

````
---
---
Name,Age,Breed,Color
{% for dog in site.data.dogs %}{{ dog[0] }},{{ dog[1].age }},{{ dog[1].breed }},{{ dog[1].color }}
{% endfor %}
````


