---
layout: post
title:      "Select an element by a data attribute"
date:       2020-06-17 07:16:39 +0000
permalink:  select_an_element_by_a_data_attribute
---

In JavaScript, one of the things you'll find yourself constantly doing is selecting a specific HTML element to carry out some "task" on. These tasks can include using it as an event handler so that something happens on your webpage when a user interacts with the selected element, or you can use the selected element to set the text that's being displayed to user. However, when selecting an element, sometimes you need to be as precise as possible, and grabbing the ID or class name won't work for what you're trying to do.

### Some background on my JS/Rails Project

In light of the Black Lives Matter movement and COVID-19 keeping us from being able to eat out at our favorite restaurants, for my JS/Rails final project, I decided to create a single-page app that will display Black-owned restaurants that we can support during these tough times by ordering takeout or to-go. My models and associations are as follows:

* City has_many Neighborhoods
* Neighborhood has_many Businesses
* Business belongs_to Neighborhood

Although I'm only choosing to show neighborhoods in Los Angeles for now, I wanted to keep things as dynamic as possible so that I am able to add another city later on.  One of the important things I needed to make sure was that the businesses only show up underneath the neighborhood it is associated with.

### What's a data attribute?

In addition to ids and classes in HTML, you can also create custom attributes to store additional information and can use to manipulate. These are called data attributes. According to [w3schools](https://www.w3schools.com/tags/att_data-.asp),  the data attribute has two parts:
> 1. The attribute name should not contain any uppercase letters, and must be at least one character long after the prefix "data-"
> 2. The attribute value can be any string

Here is an example of using data attributes:
```
<p data-para-id="2" data-page-category="general">This element has two data attributes.</p>
```

### Different ways of selecting the same element
When coding, it is absolutely normal to do the same thing in multiple ways. This also applies when trying to select an element. For example, take a look at this piece of code below from my project:
```
<div class="neighborhood">
   <h3>Hollywood</h3>
			
   <ul id="hollywood-biz" class="businesses" data-neighborhood-businesses="27"></ul>
</div>	 
```

Above, we have a div with a class of "neighborhood", and inside that container, we have the name of the neighborhood, as well as an unordered list with an id, class, and data attribute. (It's a little overkill, but for the sake of showing examples, we'll carry on.)

My main concern was adding a businesses into the unordered list, but only if the business had a neighborhood_id of 27 (data-neighborhood-businesses), which is the primary key for Hollywood.


##### Grab the element by the id

In our JS file, we can grab that entire element by using any of the following code:
```
let oneWay = document.getElementById("hollywood-biz");
```

OR

```
let anotherWay = document.querySelector("#hollywood-biz");
```

**Outcome:** Both examples will return the *first element* it finds in the doc with the id you pass in.


##### Grab the element by class name

```
let thisWay = document.getElementsByClassName("businesses");
```

OR

```
let thatWay = document.querySelector(".businesses");
```

**Outcome:** Both examples will return *all elements* in the doc with that class you pass in.


##### Grab the element by data attributes

```
let dataAttrWay = document.querySelector('[data-neighborhood-businesses='"27"]');
```

**Outcome:** This returns the unordered list, since this was the custom attribute added to the element.


##### Grab the value of the data attribute

Sometimes, you don't need the element, but you need the value of the data attribute to work with. In this case, you can do the following:

```
dataAttrWay.dataset.neighborhoodBusinesses;
```

OR

```
dataAttrWay.getAttribute('data-neighborhood-businesses')
```

**Outcome:** Both will return the value of the data attribute that you pass in, which in this case is 27. Also, if you notice in the first way of getting the value (dataAttrWay.dataset.neighborhoodBusinesses), 'data-' is replaced with 'dataset' and the the rest is converted to camelCase.

### Conclusion
JavaScript and HTML work hand-in-hand to make interactive web pages happen. In JS, it is a common occurence to get an HTML element so that you can manipulate it, whether it's by selecting an element by its id, class name, or custom data attribute. 

This project started out a little tough for me because I was having difficulties selecting specific elements. But after encountering data attributes and learning how to use it, everything became smooth sailing. 

