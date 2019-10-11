---
layout: post
title:      "TenTen--I'd do it again"
date:       2019-10-10 20:54:24 -0400
permalink:  tenten--id_do_it_again
---

I know you're probably thinking, "What? Do what again?"

Before I tell you, let me provide you with some hindsight.

These past few weeks, I've hammered into my noggin' writing RESTful routes, creating forms, and working with ActiveRecords and Sinatra. These were topics that I've been interested in learning since I've seen it on plenty of job descriptions I've came across. This mod, I took a little longer on my lessons and labs (I even pulled a few all-nighters) just so I can fully grasp what the heck is going and why/how things worked the way they did. 

Tackling on projects and applying everything you've learned in the past something weeks can be pretty stressful to most. Not only are you digging deep into your brain to try and recollect all the new information you quickly learned, but you also have to make sure that your project is meeting the specs that were given to you--and for me, I want this project to look good visually, too.

Since this is my second project for this course, I did things a little differently to prevent the unecessary stress and anxiety I got during my first project. 

Remember how I said, "I would do it again?" Well, these are the steps I'd do again to make project time flow smoother:

**1. Decide what your project is going to be about, and write it down.**

In other words: What problem do you want to solve with your project? What are the basic features you need in order to solve this problem, while meeting the proect specs?

When I figured this part out, I wrote it down so that I wouldn't get sidetracked while I was coding it out. I also made sure to have that information in front of me.

For my Sinatra project, which is called "TenTen" (you see what I did there with this blog's title? haha), the problem I was trying to solve is to lessen the time, stress, and inconvenience of making plans to go out. Instead of wasting hours on searching (and scrolling) through Google and Yelp to find what restaurant, bar, or cafe to go to, my app allows users to only get the the places that people highly recommend. I designed my app to have various categories so that a user who is making plans can click on a category, and get the recommendations for that specific one they clicked on. Aside from reading recommendations from other people, the user can also post their own recommendation.

**2. Write (or type) your pseudocode for your entire project.**

It may seem like this is a waste of time and another task to add to your project to-do list, but let me tell you, this is the complete opposite of that. It actually help saved me a ton of time because I had something to follow while I was coding. Besides, writing your pseudocode should only take about 30 minutes tops.

When you're writing pseudocode, you're writing the steps you need to do in plain ol' English--something that anyone and everyone can understand, and no code involved at all. You can think of it like, you're writing out the instructions of a recipe, except your recipe would be your project.

I grouped my pseudocode according to the pages I would have on my app. What would a user see, what options are they given, and what do they need to do to proceed? You'll also need to add in your psuedocode what you're going to do with the information a user gives you (this info comes from forms).

I already knew that my project needed to have the get, post, patch, and delete route controls, so most of my pseudocode had this format:

**Create:**
- User lands on a page with a form to make something (e.g. a new post).
- User submits the form, and I take that information to create a new post and save it into the database.

**Read:**
- After creating the new post, the appropriate page is shown so the user can preview their new post. That page also gives the option of editing or deleting the post.

**Update:**
- If user clicks edit, user lands on edit page with another form to make changes to their post.
- User submits their edits, so I find their original post in the database, update that post with the edited information, and save it into the database again.

**Destroy:**
- If user clicks delete from the edit page (note: this is a hidden form, where the delete link is actually a submit button), I find that post in the database and delete it.
- Once its deleted, the user gets redirected to another page.

**3. Organize your coding time into chunks based on your pseudocode, and start coding.**

It was very helpful to group my pseudocodo into chunks because it guided me on what I needed to work on for the day. This is what, definitely, saved me a bunch of time.

During this step, I set up my project files. I created the things I knew I needed in order to get everything working: database, migration files, models, associations, the views, and of course, the controllers.

**4. Test, test, and test your app again.**

After writing out the code for my app and got it working on the bare minimum, I spent an hour or two trying to "break" my app. I also had my husband test it out. I used this time to jot down where the problem areas were and what I can do or add to make it better for users.

**5. Add the rest of the features.**

I went back to the project specs and checked off the parts that my app already met. The parts I still had to do, I added it. This included the validations, password authetication,  and sessions. Once I got those added, I tested all over again to make sure that everything was still working fine.

After checking and meeting all the specs, I took my notes about making my app more user-friendly and incorporated this. Most of this was just styling. I also added more categories  for users to choose from.

**6. Repeat step 4.**

Yup, test it again and make adjustments as necessary.

Overall, I'm pretty pleased with my project and how it turned out. I'm also glad that this time around, it wasn't *too* stressful, thanks to the steps I took to get my project done.
