Simple-API
==========

[Following this model](http://github.com/benbalter/simple-api)

Steps:

1) Create a new repo.  [+](https://github.com/GSA/Very-Simple-API/blob/gh-pages/extended_instructions.md#1-create-a-new-repo)   
2) Create a new branch called gh-pages.  In the repository's settings, set gh-pages as the default branch. [+](https://github.com/GSA/Very-Simple-API/blob/gh-pages/extended_instructions.md#2-create-a-new-branch-called-gh-pages)  
3) Create a YML file in a /_data folder, name it `objects.yml`, insert the below, and save.  [+](https://github.com/GSA/Very-Simple-API/blob/gh-pages/extended_instructions.md#3-create-a-yml-file-in-a-_data-folder-name-it-objectsyml-insert-the-below-and-save)     

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

4) Create a json template file, name it `objects.json`, and include the below: [+](https://github.com/GSA/Very-Simple-API/blob/gh-pages/extended_instructions.md#4-create-a-json-template-file-name-it-objectsjson-and-modify-the-term-after-sitedata-to-include-the-name-of-the-yml-file)  

````
---
---
{{ site.data.objects | jsonify }}
````

The end result will now be avialable at http://**username**.github.io/**name-of-repo**/objects.json.  For instance,  http://gsa.github.io/Very-Simple-API/objects.json.

5) Create an xml template file, name it `objects.xml`, and include the below:  [+](https://github.com/GSA/Very-Simple-API/blob/gh-pages/extended_instructions.md#5-create-an-xml-template-file-name-it-objectsxml-and-include-the-below)  

````
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
````

 The end result will now be avialable at http://**username**.github.io/**name-of-repo**/objects.xml.  For instance,  http://gsa.github.io/Very-Simple-API/objects.xml.

6)  Create a csv template, name it `objects.csv`, and include the below:  [+](https://github.com/GSA/Very-Simple-API/blob/gh-pages/extended_instructions.md#6-create-a-csv-template-name-it-objectscsv-and-include-the-below)  

````
---
---
Name,Age,Breed,Color
{% for dog in site.data.objects %}{{ dog[0] }},{{ dog[1].age }},{{ dog[1].breed }},{{ dog[1].color }}
{% endfor %}
````

 The end result will now be avialable at http://**username**.github.io/**name-of-repo**/objects.csv.  For instance, http://gsa.github.io/Very-Simple-API/objects.csv.

7) Create an html template, name it `index.html`, and include the below:  [+](https://github.com/GSA/Very-Simple-API/blob/gh-pages/extended_instructions.md#7-create-an-html-template-name-it-indexhtml-and-include-the-below)  
````
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
````

 The end result will now be avialable at http://**username**.github.io/**name-of-repo**/.  For instance, http://gsa.github.io/Very-Simple-API/.


## Resources 

* [CSV-to-YML converter](http://www.smilingshark.net/webtools/csv2yml.php)
* [YAML Validator](http://yamllint.com/)



