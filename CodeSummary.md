


Introduction


While I was a student at The Tech Academy, I was given the opportunity to work with teams on four different sprints.


SpaceBar Project


During the first sprint, I used Python and Django to contribute to a space information web site. I used Beautiful Soup to render the headlines from the top six stories on newscientist.com and display them on our site. I wrote the following code in views.py, amongst others:
from django.shortcuts import render
import requests
from bs4 import BeautifulSoup

page = requests.get("https://www.newscientist.com/article-topic/alien-life/")
soup = BeautifulSoup(page.content, 'html.parser')

newsList = soup.find(class_="section-article-list--three-col")
headline_0 = newsList.find_all(class_="card__heading")[0].get_text()
headline_1 = newsList.find_all(class_="card__heading")[1].get_text()
headline_2 = newsList.find_all(class_="card__heading")[2].get_text()
headline_3 = newsList.find_all(class_="card__heading")[3].get_text()
headline_4 = newsList.find_all(class_="card__heading")[4].get_text()
headline_5 = newsList.find_all(class_="card__heading")[5].get_text()

page_two = requests.get("https://www.newscientist.com/article-topic/alien-life/page/2/")
soup_two = BeautifulSoup(page_two.content, 'html.parser')

newsList_bottom = soup_two.find(class_="section-article-list--three-col")
headline_6 = newsList_bottom.find_all(class_="card__heading")[0].get_text()
headline_7 = newsList_bottom.find_all(class_="card__heading")[1].get_text()
headline_8 = newsList_bottom.find_all(class_="card__heading")[2].get_text()
headline_9 = newsList_bottom.find_all(class_="card__heading")[3].get_text()

def index(request):
    context={'headline_2':headline_2, 'newsList':newsList, 
    'headline_3':headline_3 ,'headline_0':headline_0, 'headline_1':headline_1,
    'headline_4':headline_4, 'headline_5':headline_5, 'headline_6':headline_6,
    'headline_7':headline_7, 'headline_8':headline_8, 'headline_9':headline_9}
    return render(request, 'alienWiki/alienWiki.html', context)
 

That sprint helped me understand the power behind Python and Django. There are so many things that can be done and many tools to help with your code. I also learned setting up and using virtual environments.

Management

During my second sprint I worked with teams to develop a C#, ASP.net site helping managers and employees keep track of profiles, jobs, company news, etc.

I expanded on an existing profile questionnaire. I added new questions, updated views, models, controllers and worked with SQL. Some example code:

 




  

Theatre

During my third sprint I worked with teams to develop a C#, ASP.net site helping a theatre company manage rental space, calendars and shows.

I worked mainly on ENUMS and adding new areas for admin and subscribers. Some sample Enum code:

using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
namespace TheatreCMS.Enum
{
    //Enum for the Wiki Schema
    public enum ContentEnum { Production, Sponsor, Info, Links };
}






Hobbies

During my final sprint I worked with teams to develop Django-based site allowing users to track their hobbies. I worked on a comic book database, allowing users to maintain a database of their personal comic books. I did front-end work, including animated social media links and an animated comic book graphic.


/* Start animated comic book container for Comics_home.html*/
.book_container {
    height: 475px;
    align: center;
    background: #2e517d;
    margin: 0;
    margin-left:50%;
    margin-top:-24%;
    margin-bottom:-17%;
    width:350px;
    transform: translate(-50%, -50%);
    perspective: 1000px;
    position: absolute;
    z-index: 10;
}
.cover {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0px;
    background-color: #345b8c;
    transform-style: preserve-3d;
    transform-origin: left;
    transition: all .5s ease-in;
}
.book_container:hover .cover {
    transform: rotateY(-180deg);
}
figure {
    margin: 0;
    display:block;
    width:100%;
    height:100%;
    backface-visibility:hidden;
}
figure.front {
    position:absolute;
}
figure.back {
    position:absolute;
    transform: rotateY(180deg);
}
/* End Comic book animation */





{% block templatecontent %}
<section>
    <div id="footyPic">
        <img src="{% static 'images/superhero.jpg' %}">
        <!-- Load superhero background - position and z-index keep the background pic behind the animated comic book-->
        <img src="{% static 'images/superhero.jpg' %}" style="z-index: -1 position:absolute">
        <!-- Start animated comic book section-->
        <div class="book_container" style="background-image: url({% static 'images/my_comic_page.jpg' %})">
            <div class="cover">
                <figure class="front" style="background-image: url({% static 'images/MoreFun.jpg' %})"></figure>
                <figure class="back" style="background-image: url({% static 'images/Comic_Book_guy.png' %})"></figure>
            </div>
        </div>
        <!-- End animated comic book section -->
        <span class="footy_center"><strong>Welcome to the Comics App</strong><br/>
        Keep track of your comic book collection. Learn all about your favorite superheros -
            from powerstats to biographies and more! You can also view all of the comics currently





    position: fixed;
    bottom: 30px;
    margin: 0;
    width: 10%;
    width: 50%;
    background:transparent;
}
/* code no longer necessary - replaced by social media icons section
.footer .item.social > a:hover {
    opacity:0.9;
}
*/
.footer .copyright {
   font-style:italic;
    padding-bottom:14px;
    padding-bottom:0px;
    font-size:13px;
    margin-bottom:0;
    color:#fff;
}
/* Footer social media icons */
.fa {
    font-family: 'FontAwesome' !important;
}
.social {
  position: fixed;
  bottom: 60px;
}
.social a {
  color: #fff;
  text-decoration: none;
}
.social ul {
  padding: 0px;
  -webkit-transform: translate(-270px, 0);
  -moz-transform: translate(-270px, 0);
  -ms-transform: translate(-270px, 0);
  -o-transform: translate(-270px, 0);
  transform: translate(-270px, 0);
}
.social ul li {
  display: block;
  margin: 5px;
  background: rgba(0, 0, 0, 0.36);
  width: 300px;
  text-align: right;
  padding: 10px;
  -webkit-border-radius: 0 30px 30px 0;
  -moz-border-radius: 0 30px 30px 0;
  border-radius: 0 30px 30px 0;
  -webkit-transition: all 1s;
  -moz-transition: all 1s;
  -ms-transition: all 1s;
  -o-transition: all 1s;
  transition: all 1s;
}
.social ul li:hover {
  -webkit-transform: translate(110px, 0);
  -moz-transform: translate(110px, 0);
  -ms-transform: translate(110px, 0);
  -o-transform: translate(110px, 0);
  transform: translate(110px, 0);
  background: rgba(255, 255, 255, 0.4);
}
.social ul li:hover a {
  color: white;
}
.social ul li:hover i {
  color: #fff;
  background: #675036;
  -webkit-transform: rotate(360deg);
  -moz-transform: rotate(360deg);
  -ms-transform: rotate(360deg);
  -o-transform: rotate(360deg);
  transform: rotate(360deg);
  -webkit-transition: all 1s;
  -moz-transition: all 1s;
  -ms-transition: all 1s;
  -o-transition: all 1s;
  transition: all 1s;
}
.social ul li i {
  margin-left: 0px;
  color: #000;
  background: #fff;
  padding: 10px;
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border-radius: 50%;
  width: 35px;
  height: 35px;
  font-size: 20px;
  background: #ffffff;
  -webkit-transform: rotate(0deg);
  -moz-transform: rotate(0deg);
  -ms-transform: rotate(0deg);
  -o-transform: rotate(0deg);
  transform: rotate(0deg);
}
/* End footer social media icons */



    <!-- Social Media effects -->
    <link href='https://fonts.googleapis.com/css?family=Raleway:400,200' rel='stylesheet' type='text/css'>
    <link href="//netdna.bootstrapcdn.com/font-awesome/4.1.0/css/font-awesome.min.css" rel="stylesheet">


                    <nav class="social">
                          <ul>
                              <li><a href="https://twitter.com/thetechacad">Twitter <i class="fa fa-twitter"></i></a></li>
                              <li><a href="https://www.facebook.com/learncodinganywhere/">Facebook <i class="fa fa-facebook"></i></a></li>
                              <li><a href="https://www.instagram.com/thetechacademy">Instagram <i class="fa fa-instagram"></i></a></li>
                              <li><a href="https://www.youtube.com/channel/UCSgp87lgUhT4hSvR6i4izYA">YouTube <i class="fa fa-youtube"></i></a></li>
                          </ul>
                    </nav>



