Simple-API
==========

Steps:

0. Create a new repo.  [+]()   
0. Create a new branch called gh-pages.  [+]()  
0. Create a YML file in a /_data folder, name it `objects.yml`, insert the below, and save.  [+]()     
 <pre>
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
</pre>
0. Create a json template file, name it `objects.json`, and include the below: [+]()  
 <pre>
---
---
{{ site.data.objects | jsonify }}
</pre>
 The end result will now be avialable at http://**username**.github.io/**name-of-repo**/objects.json.  For instance,  http://gsa.github.io/Very-Simple-API/objects.json.
0. Create an xml template file, name it `objects.xml`, and include the below:  [+]()  
 <pre>
---
---
<dogs>
  {% for dog in site.data.objects %}
  <dog>
    <name>{{ dog[0] }}</name>
    <breed>{{ dog[1].color }}</breed>
    <age>{{ dog[1].age }}</age>
    <color>{{ dog[1].color}}</color>
  </dog>
  {% endfor %}
</dogs>
</pre>
 The end result will now be avialable at http://**username**.github.io/**name-of-repo**/objects.xml.  For instance,  http://gsa.github.io/Very-Simple-API/objects.xml.
0. Create a csv template, name it `objects.csv`, and include the below:  [+]()  
 <pre>
---
---
Name,Age,Breed,Color
{% for dog in site.data.objects %}{{ dog[0] }},{{ dog[1].age }},{{ dog[1].breed }},{{ dog[1].color }}
{% endfor %}
</pre>
 The end result will now be avialable at http://**username**.github.io/**name-of-repo**/objects.csv.  For instance, http://gsa.github.io/Very-Simple-API/objects.csv.
0. Create an html template, name it `index.html`, and include the below:  [+]()  
 <pre>
    <html>
      <body>
        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
        <script>
        $.getJSON( "objects.json", function(objects) {
          $.each(objects, function(name, attributes) {
            document.write("<h2>" + name + "</h2>");
            document.write("Age: " + attributes["age"] + "<br />");
            document.write("Breed: " + attributes["breed"] + "<br />");
            document.write("Color: " + attributes["color"] + "<br />");
          });
        })
        </script>
      </body>
    </html>
</pre>
 The end result will now be avialable at http://**username**.github.io/**name-of-repo**/.  For instance, http://gsa.github.io/Very-Simple-API/.

