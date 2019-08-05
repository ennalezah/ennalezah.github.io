---
layout: post
title:      "Reflection"
date:       2019-08-05 23:33:15 +0000
permalink:  reflection
---


A couple weeks ago, I stumbled upon a documentary on Netflix called “The Great Hack.” Although I was only paying half-attention to it, I kept hearing how our information was unethically scraped by the infamous British political consulting firm, Cambridge Analytica. (If you can recall, this is around the time that Facebook was under a lot of heat due to Cambridge Analytica secretly scraping peoples' information through their Facebook profiles... Yikes!) As I listened to the documentary in the background, I remember thinking to myself, “Wow, that must have taken some serious programming. I wonder how they did that…”

Well, I guess the universe was listening in on my thoughts because here I am now, performing web scraping.

For my first project, I decided to have some fun with it since doing the actual scraping can be a doozy. And as someone who enjoys reading horoscopes, I felt it was appropriate to base my project on this.

#### Setting Up Daily Horoscope
I’m so grateful for Avi’s videos and unlimited Google searches because without ‘em, I would probably still be trying to set up my project. Although I’ve been able to go through all the labs and lessons these past few weeks, I didn’t pay as much attention as I should on how to connect the files together. More specifically, using require, require_relative, or require_all in my file.

```
require 'pry'
require 'nokogiri'
require 'open-uri'
require 'colorize'

require_relative '../lib/daily_horoscope/scraper'
require_relative '../lib/daily_horoscope/zodiac_sign'
require_relative '../lib/daily_horoscope/cli'
require_relative '../lib/daily_horoscope/version' 
```

The snippet above was placed in my environment file, an important file to have so that all your files have access to each other and the gems that you need. And as you can tell, there is a "pattern" to it. I learned that using require is usually meant for gems, require_relative is used when you’re requiring a file that is in the current directory you’re working in, and require_all is used to require an entire directory outside of your current project directory. At one point during my project setup, I was blindly using require on a file instead of require_relative, which was the big reason why I was getting an error and couldn’t display any outut on my terminal.

#### Building My Classes and Methods
As soon as I completed my setup, I began creating my classes and methods. I was constantly referring back to old labs such as the Music CLI and all the lessons in Object Relationships, but I was still having a hell of a time trying to connect everything together.


```
def scrape_profile
	DailyHoroscope::ZodiacSign.all.each do |sign|
		@profile_doc = self.class.get_any_doc(sign.profile_url)
		profile = profile_doc.css("div main-horoscope div.more-horoscopes")
		
		profile.each do |info|
			sign.love_url = info.css("a")[1]['href']
			sign.career_url = info.css("a")[2]['href']
			sign.money_url = info.css("a")[3]['href']
			sign.health_url = info.css("a")[4]['href']
		end
	end        
end
```

Take this code for example. This method was located in the Scraper class, and I could NOT figure out how to let the sign instance know about its new url attributes. Every time I tried to put out any of the urls to the terminal, it came out blank. I spent wayyy too long trying to figure this issue out, so I decided to make my Scraper class only be responsible for one thing: to scrape the index page for zodiac signs and call on the ZodiacSign class to create new instances with this scraped info.

#### Refactoring
There’s exactly one week before my project is due, but I was able to finish all my code very late last night—or early morning. Haha. I’m so happy that I have working code, but now it’s time to refactor. I was able to condense a good chunk of my code. I had four methods that I was able to cut in half, all because of one new method I wrote.

I went from this:
```
def career
	url = self.class.profile_doc.css("div.main-horoscope div.more-horoscopes a")[2]['href']
	doc = Nokogiri::HTML(open("#{BASE_URL}#{url}"))
	title = doc.css("div.flex-start h1").text.split[0..1].join(' ').cyan
	description = doc.css("div.main-horoscope p").first.text.split(/\d\s-\s/)[1]
	"#{title} \n#{description}"
end
```

To this:
```
def career
	url = profile_doc.css("div.main-horoscope div.more-horoscopes a")[2]['href']
	@career ||= "\n\u{1F4BC}  #{get_horoscope(url)}"
end
```

Because of this: 
```
def get_horoscope(url)
	doc = Nokogiri::HTML(open("#{BASE_URL}#{url}"))
	title = doc.css("div.flex-start h1").text.split[0..1].join(' ').cyan
	description = doc.css("div.main-horoscope p").first.text.split(/\d\s-\s/)[1]
	"#{title} \n#{description}"
end
```

The new method I wrote combined getting the Nokogiri doc for the page I was going to scrape, then using that doc to set the title and description of the horoscope and using that as my return.

I know there is still one more thing I can do to make my code DRY, but it brings me back to the issue of connecting the second-layer of scraped info to its specific sign, which I’m still stumped on. I’m pretty sure I spent 3-4 hours on trying to get it to work. No luck yet, but I have a 1:1 scheduled in a couple days, so I’m hoping to get some kind of guidance on this annoying issue.

Aside from shortening methods, another thing I did to help me refactor was look at my code as if I was another developer looking at it. Does my naming convetion for my methods and variables make sense? Could I easily tell what the main "purpose" of each method/class is just by quickly glancing at the names? Are my methods short and straight to the point? If not, are there comments to help me understand? Is the flow easy to follow?

Lastly, user testing! I had my husband use my app out loud. While he was interacting with my app, I had him talk about what seemed confusing, what was difficult to read, what I could do to make it better, and I had him try to "break" my app. By doing this, I was able to get an idea of what I needed to edit in my CLI class.

#### Designing My CLI
Spending the entire week last week on coding has my brain feeling a bit fried, and trying to read the boring black and white output on the terminal did absolutely nothing for me. Lol. Since I feel like I’m ahead of schedule for my project, I wanted to make my CLI interface more user-friendly… and fun. Thank goodness for Colorize and unix code! 

Colorize is a Ruby gem that allows you to add color, as well as bold, italic, and underline styling to strings. To use Colorize, all you need to do is install it like you would for any other gem:

```
gem install colorize
```

Here is the documentation I followed to get my terminal looking awesome: [https://rdoc.info/github/fazibear/colorize](https://rdoc.info/github/fazibear/colorize)

By adding some color to the CLI, the output on the terminal is SOOO much easier to read. I also added some emojis to my CLI because… why not? I did this by adding unix code within my string.

Here's a sneap-peak of how it looks now that I've added some design to it. So much better, right?!<br />
<img src="https://media-private.canva.com/MADhum-iMEQ/1/screen.jpg?response-expires=Tue%2C%2006%20Aug%202019%2000%3A10%3A57%20GMT&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20190805T214937Z&X-Amz-SignedHeaders=host&X-Amz-Expires=8479&X-Amz-Credential=AKIAJJATJK7JCUD446NA%2F20190805%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=8f1d09693cc4118c7b5be9125ae9b9f36cc03bc4011de74701f4b124dca7564f" style ="width: 50%; margin: 10px" />

#### Overall Thoughts About My First Project
This first project put me through a whirlwhind of emotions, but being able to complete the code and have it working how I wanted it has me feeling AHHH-MAZING! In the beginning of it all, I will admit that I was banging my head on the table and doubting myself. I wasn't sure if I actually knew what I was doing or if I learned anything at all (no thanks to imposter syndrome). 

I *do* know what I'm doing, and I did grasp OOP just fine. During this project, I also got a better of using "self" and whether I should be creating an instance or class method:

*  A class method is used if you want to change the data for the ENTIRE class.
* An instance method should be used if you're focusing on one specific instance or changing data only to a specific instance of the class.
* Using self alone refers to the instance itself.
```
 def profile_doc
      Nokogiri::HTML(open("#{BASE_URL}#{self.profile_url}"))
   end
```

* Using self with a method name is a class method and refers to the class
```
   def self.find_by_input(input)
      self.all[input.to_i - 1] 
   end
```

* Using self in an instance method when you want to refer to the class would look something like this, where "self.class" is actually the name of the class. As for the lonely self to the right of the shovel, that is referring to the instance.
```
   def save
      self.class.all << self
   end
```

Overall, I'm very happy with how my project turned out, and I'm thrilled to be able to have learned this much about Ruby in the past 2 few months! Aside from learning about Ruby concepts, I also learned and confirmed a few things about myself:

* I won't quit until I have the solution, even if it means spending a few long hours on it.
* I started to think about how to solve problems in different ways, as well as all the wrong ways, to do something.
* I should probably ask for more help. I rarely asked for help, which is probably why it took me longer than usual to get to a solution on a problem I was having.
* How much I enjoy programming! I really feel like this is what I'm supposed to be doing with my life.


