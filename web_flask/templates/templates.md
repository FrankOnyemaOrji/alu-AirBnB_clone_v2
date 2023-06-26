**10-hbnb_filters.html**
<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" type="text/css" href="static/styles/4-common.css">
    <link rel="stylesheet" type="text/css" href="static/styles/3-header.css">
    <link rel="stylesheet" type="text/css" href="static/styles/3-footer.css">
    <link rel="stylesheet" type="text/css" href="static/styles/6-filters.css">
    <link rel="icon" href="static/images/icon.png" />
    <title>HBNB</title>
  </head>
  <body>
    <header>
      <div class="logo"></div>
    </header>
    <div class="container">
      <section class="filters">
	<div class="locations">
	  <h3>States</h3>
	  <h4>&nbsp;</h4>
	  <div class="popover">
	  {% for state in states.values()|sort(attribute='name') %}
      <ul>
	      <li>
		      <h2>{{ state.name }}</h2>
		      {% for city in state.cities|sort(attribute='name') %}
              <ul>
		          <li><div class="list_content">{{ city.name }}</div></li>
              </ul>
			  {% endfor %}
	      </li>
      </ul>
	  {% endfor %}
	  </div>
	</div>
	<div class="amenities">
	  <h3>Amenities</h3>
	  <h4>&nbsp;</h4>
	  <div class="popover">
      {% for amenity in amenities.values()|sort(attribute='name') %}
      <ul>
	      <li><div class="list_content">{{ amenity.name }}</div></li>
      </ul>
	  {% endfor %}
      </div>
	</div>
	<button type="button">Search</button>
      </section>
    </div>
    <footer>
      <p>Holberton School</p>
    </footer>
  </body>
</html>


**100-hbnb.html**

<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" type="text/css" href="static/styles/4-common.css">
    <link rel="stylesheet" type="text/css" href="static/styles/3-header.css">
    <link rel="stylesheet" type="text/css" href="static/styles/3-footer.css">
    <link rel="stylesheet" type="text/css" href="static/styles/6-filters.css">
    <link type="text/css" rel="stylesheet" href="static/styles/8-places.css">
    <link rel="icon" href="static/images/icon.png" />
    <title>HBNB</title>
  </head>
  <body>
    <header>
      <div class="logo"></div>
    </header>
    <div class="container">
      <section class="filters">
	<div class="locations">
	  <h3>States</h3>
	  <h4>&nbsp;</h4>
	  <div class="popover">
	  {% for state in states.values()|sort(attribute='name') %}
	    <ul>
	      <li>
		  <h2>{{ state.name }}</h2>
          {% for city in state.cities|sort(attribute='name') %}
		    <ul>
		    <li><div class="list_content">{{ city.name }}</div></li>
		    </ul>
          {% endfor %}
	      </li>
        </ul>
      {% endfor %}
	  </div>
	</div>
	<div class="amenities">
	  <h3>Amenities</h3>
	  <h4>&nbsp;</h4>
	  <div class="popover">
      {% for amenity in amenities.values()|sort(attribute='name') %}
	    <ul>
	      <li><div class="list_content">{{ amenity.name }}</div></li>
	    </ul>
      {% endfor %} 
	  </div>
	</div>
	<button type="button">Search</button>
      </section>
   <section class="places">
	<h1>Places</h1>
	{% for place in places.values()|sort(attribute='name') %}
	<article>
	  <div class="title_box">
	    <h2>{{ place.name }}</h2>
	    <div class="price_by_night">${{ place.price_by_night }}</div>
	  </div>
	  <div class="information">
	    	<div class="max_guest">{{ place.max_guest }} Guest</div>
            <div class="number_rooms">{{ place.number_rooms }} Room</div>
            <div class="number_bathrooms">{{ place.number_bathrooms }} Bathroom</div>
	  </div>
	  <div class="user"><b>Owner:</b> {{ place.user.first_name }} {{ place.user.last_name }}</div>
        {% autoescape false %}  
		<div class="description">{{ place.description }}</div>
		{% endautoescape %}
	</article>
	{% endfor %}    
  </section>
    </div>
    <footer>
      <p>Holberton School</p>
    </footer>
  </body>
</html>


**5-number.html**

<!DOCTYPE html>
<HTML lang="en">
    <HEAD>
        <TITLE>HBNB</TITLE>
    </HEAD>
    <BODY>
        <H1>Number: {{ n }}</H1>
    </BODY>
</HTML>


**6-number_odd_or_even.html**
<!DOCTYPE html>
<HTML lang="en">
    <HEAD>
        <TITLE>HBNB</TITLE>
    </HEAD>
    <BODY>
        <H1>Number: {{ n }} is {% if n % 2 == 0 %}even{% else %}odd{% endif %}</H1>
    </BODY>
</HTML>


**7-states_list.html**

<!DOCTYPE html>
<HTML lang="en">
    <HEAD>
        <TITLE>HBNB</TITLE>
    </HEAD>
    <BODY>
        <H1>States</H1>
        <UL>
		{% for state in sorted_states %}
            <LI>{{ state.id }}: <B>{{ state.name }}</B></LI>
		{% endfor %}
        </UL>
    </BODY>
</HTML>


**8-cities_by_states.html**

<!DOCTYPE html>
<HTML lang="en">
    <HEAD>
        <TITLE>HBNB</TITLE>
    </HEAD>
    <BODY>
        <H1>States</H1>
        <UL>
			{% for state in states.values()|sort(attribute='name') %}
            <LI>{{ state.id }}: <B>{{ state.name }}</B>
                <UL>
				{% for city in state.cities|sort(attribute='name') %}
                        <LI>{{ city.id }}: <B>{{ city.name }}</B></LI>
				{% endfor %}
                </UL>
            </LI>
			{% endfor %}
        </UL>
    </BODY>
</HTML>


**9-states.html**

<!DOCTYPE html>
<HTML lang="en">
    <HEAD>
        <TITLE>HBNB</TITLE>
    </HEAD>
    <BODY>
		{% if id == None %}
            <H1>States</H1>
    	    <UL>
				{% for state in states.values()|sort(attribute='name') %}
            	<LI>{{ state.id }}: <B>{{ state.name }}</B></LI>
				{% endfor %}
            </UL>
		{% elif states.get('DeclarativeMeta.' + id) %}
			<H1>State: {{ states['DeclarativeMeta.' + id].name }}</H1>
			<H3>Cities:</H3>
			<UL>
				{% for city in states['DeclarativeMeta.' + id].cities|sort(attribute='name') %}
				<LI>{{ city.id }}: <B>{{ city.name }}</B></LI>
				{% endfor %}
        	</UL>
		{% else %}
            <H1>Not found!</H1>
		{% endif %}
    </BODY>
</HTML>
