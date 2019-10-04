---
layout: leftnav-page-content
title: Celebrate In The City 2020
permalink: / events/celebrate-in-the-city/ 
collection_name: resources

##################################################################
# Comment: Edit the data below to edit the content for this page #
##################################################################
Celebrate In The City 2020:
  imgFolderPath: /images/Sample-Pictures/
  docFolderPath: /files/brochures/
  categories:
    - title: "Commemorative Booklet: 50 Years of Quality and Standards"
      list:    
      - img: Chrysanthemum.jpg
        url: https://spring.enterprisesg.gov.sg/Resources/Documents/50_years_of_quality_and_standards/web/html5/index.html
    - title: "SAC Brochures"
      list:    
      - name: "SAC Booklet"
        img: Desert.jpg
     - name: "Accreditation Scheme for Laboratories"
        img: Hydrangeas.jpg
    - name: "Accreditation Scheme for Inspection Bodies"
        img: Jellyfish.jpg
   - name: "Accreditation Scheme for Management System Certification Bodies"
        img: Koala.jpg
- name: "Accreditation Scheme for Product Certification Bodies"
        img: Lighthouse.jpg
- name: "Good Laboratory Practice Compliance Programme"
        img: Penguins.jpg
- name: "Accreditation Scheme for Personnel Certification Bodies"
        img: Tulips.jpg
      - name: "Accreditation Scheme for Proficiency Testing Providers"
        img: Tulips.jpg
              - name: "SAC Accreditation Marks"
        img: Penguins.jpg
      - name: "SAC Accreditation Programmes for the Building and Construction Industry"
        img: Penguins.jpg
        
###############
# End of Data #
###############
---

<!-- the code below is used to create HTML tables and populate with the brochures data listed above -->
{::nomarkdown}

{% assign pageBrochures = page.brochures %}
{% for category in pageBrochures.categories %}
  <h4 style="padding-left:1rem;">{{- category.title -}}</h4>
  <hr/>
  {% unless category.list == empty  %}
    {% assign sample = category.list | first %}
    {% if sample.img %}
      <table class="brochures-table">
        {% for item in category.list %}
          {% assign image = pageBrochures.imgFolderPath | append: item.img %}
          {% if item.doc %}
              {% assign link = pageBrochures.docFolderPath | append: item.doc %}
            {% else if item.url %}
              {% assign link = item.url %}
            {% else %}
              {% assign link = '' %}
          {% endif %}
          {% assign temp = forloop.index | minus: 1 | modulo: 3 %}
          {% if temp == 0 %}
            {% if forloop.first == false %}
              </tr>
            {% endif %}
            <tr>
          {% endif %}
          <td><a href="{{- link -}}" target="_blank"><img src="{{- image -}}" />{% if item.name %}{{- item.name -}}{% endif %}</a></td>
          {% comment %} if there are less than 3 table cells for the entire table, populate with empty cells {% endcomment %}
          {% if forloop.last == true and forloop.index < 4 %}
            {% assign temp = 3 | minus: forloop.index %}  
            {% for i in (1..temp) %}
               <td></td>                                 
            {% endfor %}                                      
            </tr>
          {% endif %}
        {% endfor %}
      </table>
    {% else %}
      <ul>
        {% for item in category.list %}
          {% if item.url %}
              {% assign link = item.url %}
            {% else if item.doc %}
              {% assign link = pageBrochures.docFolderPath | append: item.doc %}
            {% else %}
              {% assign link = '' %}
          {% endif %}
          <li><a href="{{- link -}}" target="_blank">{% if item.name %}{{- item.name -}}{% endif %}</a></li>
        {% endfor %}
      </ul>
    {% endif %}
  {% endunless %}
{% endfor %}

{:/}
