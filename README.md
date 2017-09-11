# nginx redirect generator

crappy version 1

1. Stick it in a folder with a `redirects.csv` that has two columns `old` and `new`
1. Open the `index.html` file in a local server
1. Copy/paste the spat out results into your nginx config file

_____

# I am a lazy developer

I don't mean to imply that I cut corners and churn out shoddy code. I just hate doing repetitiive tasks that bore the bejesus out of me. Obviously, I'm not alone in this - it's the reason [task runners](https://www.smashingmagazine.com/2016/06/harness-machines-productive-task-runners/) exist.

Recently, at work, I replatformed an existing e-commerce site which resulted in, amongst other things, a giant list of redirects from existing urls to the new url structure.

[Permanent redirects (301s for the people who like numbers) are essential for persistence of good SEO](https://moz.com/learn/seo/redirection). The downside is adding the old url and the new url to the line `rewrite ^/oldlocation$ http://www.newdomain.com/newlocation permanent;` in my nginx config file. What's a lazy guy to do when you have to do this 438 times?

Well, this immediately looks like a case for loops and variables!

## How do _you_ do this wizardry?!

tl;dr - Clone this repo!

### Step 1 - Convert the `.csv` to `.json`

Since the output of the csv file is consistent, and so it the format of a JSON object, I just needed to replace line endings with the correct curly braces!

### Step 2 - Define the redirect line structure
As demonstrated above, each line in the config file is identical apart from the old and new url values

### Step 3 - Populate the new format
Loop through each instance in the JSON object and print out the new config line

From here, copy the whole output and paste it into the config file.

:tada:

Now, I'm sure there are better/different ways to do this but, off the top of my head, this seemed quick and simple enough to whip together.

I've no idea how long it would have taken me to manually do this but I'm certain it would have taken longer than to write this bit of code.
