---
# layout: home
layout: page
---

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>Boise Math Student's circle (BMC)</h3>
      <p>
        The Boise Math Students' Circle is for Treasure Valley young people with some experience with algebra who want to experience creative mathematics.
      </p>
      <ul>
        <li><a href="bmc-schedule">Upcoming session calendar</a></li>
        <li><a href="bmc-archive">Past sessions</a></li>
        <li><a href="bmc-about">About the BMC</a></li>
        <li><a href="bmc-faculty">Faculty biographies</a></li>
        <li><a href="bmc-whatis">What is a math circle?</a></li>
      </ul>
    </td>
    <td width="50%" valign="top">
      <h3>Boise Math Teacher's circle (BMTC)</h3>
      <p>
        The Boise Math Teachers' Circle is a community for Treasure Valley K–12 math educators.
      </p>
      <ul>
        <li>Check out the <a href="bmtc1718">current BMTC program</a></li>
        <li>You can also see our past programs:<br/>
          <a href="bmtc1516">BMTC 2015–2016</a><br/>
          <a href="bmtc1617">BMTC 2016–2017</a></p>
        </li>
      </ul>
    </td>
  </tr>
</table>

<!--
* [About the BMTC](bmtc-about)
* [What is a math teacher's circle?](bmtc-whatis)
* [Upcoming session calendar](bmtc-schedule)
* [Past sessions](bmtc-recent)
* [Faculty biographies](bmtc-faculty)
-->

## Recent sessions

{% for post in site.posts limit: 6 %}

  {% if post.img %}
![head image]({{ site.baseurl}}/assets/bmc-headers/{{ post.img }})  
{: style="width:150px; float:left; " }
  {% endif %}
[{{ post.title }}]({{ post.url }})  
{{ post.excerpt | remove: '<p>' | remove: '</p>' | strip }}  
<span class="post-meta"><span class="category_name">{{ post.categories }}</span> posted on {{ post.date | date: "%b %-d, %Y" }}</span>
{: style="margin-left:160px"}

<div style="clear:both;"></div>
  
{% endfor %}
