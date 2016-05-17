# Save Redirect Set Flash

Thanks to the data class option on our form, when we submit and get here, we actually have a genus object. So what do we do now? Well, whatever we want. We save the genus object to the database. So let’s say genus equals form error get data. That’s our genus object. And let’s get the anti-manager with diskette doctor and get manager, and then our classic EM persist genus, and EM flush. And then at the end of every form, we always do the same thing. We re-direct the user to another page. Even if that is to create another new genus, because that avoids the user from just hitting refresh and re-posting the data. 

So let’s return this error, redirect to route, and let’s reject them to this admin genus list page. That’s the list of genuses in the admin section. And remember, redirect route returns a redirect response object, so here we return that. All right? Let’s try it out. So I’ll just refresh this page. We should have a new sea monster after this. Refreshes. Scroll down. Sea monster, sweet. But we didn’t have any cool, “Success!  You’re amazing. You created a new genus message.”  And I’d like to actually one, so I’m gonna go back to genus new, and inside of our controller, right before we redirect, we can set a message to show to the user on the next page after the redirect. It’s called a flash message, and it works like this. This arrow, add flash, success. You’ll see why that string is important in a second. And then we’ll say “Genus created. You are amazing.”  It’s good to keep people encouraged.

So let’s be curious. I’m gonna hold command and actually click into this add flash to see what that does. Okay, cool. You see it behind the scenes. It goes and grabs a session service, gets something called a flash bag, and adds our message to it. So the flash bag is a special part of this session where you can store messages, but those messages only exist for one redirect. So if we store the messages here and then we redirect, on the next page, we can read those messages from the flash bag, and print them to the page. And the purpose of the flash bag is exactly this – to print messages, success messages, to the user. 

Now it’s actually even a little bit cooler than that. Technically, your messages will stay into the flash bag until you ask for them. When you ask for them, they’re automatically removed. So, if you ever have a situation where, for some reason, you set something in the flash bag and then you redirect twice before rendering it, no problem. It will stay in there. So then all we need to do is actually render that flash bag message, and the best place to do this is actually in your base template. Because then you can render a flash message and redirect to any other page in the system, and it’ll show up here in your base template. 

So right above the body block, let’s do four message in app.session – shortcut to get the session object – flashbag.get, and we’ll get out the success key. And then we’ll do end four. So that’s why we used success here. We used it in our controller, and then we used success here in our template. The significance of that string is nothing. It can be anything. It just needs to match up with each other. Usually I have a success one, and I also have an error one in my project, because, now that we know that it’s a success, we can give them a nice happy message. We use the alert success from bootstrap, and we’ll print out the MSG variable. Cool. So we’ll go back, we’ll create a sea monster two. Change its subfamily, give it 200 species count, and let’s save that guy. 

And there it is. Awesome. Systematic way to render some success messages. Love it. So now let’s look at our form, start really controlling how these fields are rendering.