---
layout: post
title:      "Authentication vs. Authorization"
date:       2019-12-23 07:56:26 +0000
permalink:  authentication_vs_authorization
---


For the longest time, I would confuse the terms 'authentication' and 'authorization'. I knew that they both worked hand-in-hand when it came to a user signing into their account, but that was the extent of it. Fortunately, during this mod and while working on my Rails project, I was able to dig deeper into what these two terms are and what they actually do.

### Authentication
Let's say you have an account for a banking app, and you want to check your available balance so you can budget your Christmas gift shopping. Before you're able to see your account info, 99.999% of the time, you'll need to fill out a login form. You identify yourself by your email and/or username. To prove that you are who you say you are, you'll also need to type in the password you signed up with--this is the authentication part. Because your password is considered a confidential piece of information that *only you* would know, the password field serves the purpose of verifying your identity. With authentication, you are proving and verifying your identity.

### Authorization
Okay, cool. You're all logged into the app, you can finally check your balance. You see that your checking account is running a little low, so you go into your savings account to transfer $100 to your checking account. Because you were able to authenticate yourself, you are able to do things like transfer money and view your balances--this is the authorization part.

Being authorized to do something is being given permission or access to complete a certain action, all because you've successfully identified yourself. But just because you authenticted yourself, it doesn't mean you're authorized to do whatever you please.

When you initially signed up for the bank account app, you were given a specific role as a user. Because of that role, you were granted a limited amount of access on what you can and can't do. For example, with your user account, you are only allowed to view information and perform actions that pertain to only your account--but only to a certain extent. With your role as a user, you can update your contact and login info, make payments, view your statements, deposit/transfer money and checks. But what you can't do, even though it pertains to your account, is try to update your balance to, let's say, $1 million (wouldn't that be nice?!) or delete all your credit charges so you have no bills to pay (again, wouldn't that be nice?!)

### My Rails Project: LinkUp
For my project, LinkUp, I decided to use the [Devise](https://github.com/plataformatec/devise) gem to take care of the authentication part. LinkUp is similar to [MeetUp](https://www.meetup.com/), where users can join groups and find events in their area if they sign up for an account.

Initially, we were taught to use gems like Bcrypt to safely store the passwords into a hash and manually code the methods and controllers that pertained to authenticating a user. But after seeing and hearing about how Devise is widely used, I decided to learn how to implement it on my project, and I have no regrets!

### Devise

With Devise, it has made implementing authentication SOO much easier. After successfully setting it up, the gem took care of creating the User model, as well as the routes, controllers, and views for signing up and logging in. Devise also comes with these methods that will be used frequently throughout the app, whether its in your controllers or views:

* **authenticate_user! -** This limits access to users who visit your site. For example, in my project, a user can create or join groups only if they were logged in.
* **user_signed_in? -** This is pretty self explanatory, thanks to its helpful name. This method returns true or false, based on if a user is logged in or not.
* **current_user -** This returns an instance of the user who is currently logged in.

Another important thing to mention about Devise is that it uses ten modules to handle user authentication. It may seem a bit much, but depending on how involved you want it to be, you only implement the ones you need. I decided to implement five modules--all were auto-enabled after setting Devise up, except for the last one mentioned below:

* **Database authenticable -** This is probably the most important module, since it deals with the password. It salts, hashes, then stores the user's pw into the database. (Side not: Devise uses Bcrypt to do this, but you won't need to install Bcrypt because it's already included with Devise.)
* **Registerable -** This creates the user's registration process. This will create the controller actions and forms for signing up, as well as for editing and deleting their account. 
* **Rememberable -** This add the 'Remember me' checkbox that is frequently seen on login forms. It generates a token to remember the user from a saved cookie.
* **Validatable -** This adds built-in email and password validations (e.g. length, format). However, these validations can be changed by going into 'config/initializers/devise.rb'
* **Omniauthable -** This adds support for Omniauth provider so that users can signup/login through Facebook, Google, Twitter, etc. 

### In Conclusion
Authentication and authorization are two terms that are frequently used with each other when it comes to users logging into their account and being granted certain permissions to perform actions on their account. There is a lot more that can be involved with it (as you can see from the Devise gem), but understanding this much has really helped me get a grasp on the importance of security when it comes to creating a web app that requires users to create an account.
