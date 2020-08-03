# NUCSA

Hey Eboard!

We know, maintaining organizational websites isn't always easy, especially when passing down old code year after year. Hopefully this repo will help  ease that pain for a few more years. This project will allow you to generate static website files and deploy them to the school's webserver. Adding or editing new pages is as simple as editing markdown files. Adding a new eboard just involves adding a new file. And hopefully when a new person comes along who can code, they can change the theme and layouts with ease.


# Requirements
This project is built with [Jekyll](https://jekyllrb.com/), a static site generator.
### Mac
First install [Brew](https://brew.sh/)
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
sudo chown -R $USER /usr/local
brew install ruby
```
Install Jekyll and bundler for Ruby
```bash
gem install jekyll bundler
```

### Linux
```bash
# Debian
sudo apt update && sudo apt install ruby
# Centos
sudo yum update && sudo yum install ruby

gem install jekyll bundler
```
### FOR WINDOWS USERS: Install a Virtual Machine to do this (recommend Oracle VM VirtualBox)

### If you encounter errors trying to install these packages 
#### - "You don't have write permissions for the /var/lib/gems/2.3.0 directory":
Check this link (https://stackoverflow.com/questions/37720892/you-dont-have-write-permissions-for-the-var-lib-gems-2-3-0-directory) 
#### - "Bundler::GemRequireError: There was an error while trying to load the gem 'jekyll-minifier'. Gem Load Error is: Could not find a JavaScript runtime. See https://github.com/rails/execjs for a list of available runtimes"
Run these commands in your command prompt:
- brew install v8@3.15
- bundle config build.libv8 --with-system-v8
- bundle config build.therubyracer --with-v8-dir=$(brew --prefix v8@3.15)
- bundle install

And within nucsa_website/Gemfile, and this line at the very end of the script: gem 'therubyracer', :platform => :ruby


# Quick Start
This will run the website locally at [http://127.0.0.1:4000/csa/](http://127.0.0.1:4000/csa/)
```bash
git clone git@github.com:northeasterncsa/nucsa_website.git
cd nucsa_website
./script/bootstrap  # Run only once, or whenever the Gemfile is edited
./script/server
```


# Development
So you want to change some content on the site? Maybe it's adding a new eboard, or editing some text on a page.
Here, we'll be using best git practices. Git is just version control software for keeping track of code changes.
Below, replace `new_feature_name` with a name for the change being made. Alphanumeric and underscores only!

```bash
git checkout -b new_feature_name
```

Great! Now you can make whatever code changes you need (see below for some options)! You can make as
many commits as you want here. We'll be merging all the commits into a single commit below we deploy.
When you change / add files, use the `git add` command to mark them the commit. Then `git commit` with
some helpful message to remember what you did.

```bash
git add files.md you.html edited.yml
git commit -m "Helpful message on what you did"
```

Okay, now lets say you tested the website locally with your changes and now you want to deploy to the public
website. You're going to switch back to the master branch, merge your changes into master, and commit with a
detailed message on what you did. Then you'll push it to the public git repo so everyone else can have access
to the latest code.

```bash
git checkout master
git merge --squash new_feature_name
git commit -m "Detailed message on what was done in this commit"
git push
```

## Edit Existing Page
When you want to change content on static pages like home, mission, meetings, or contact. Find the corresponding
markdown (.md) file. So for the mission page, it would be `mission.md`. Then edit the text using
[Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) syntax. It's easy to learn and helps you
quickly format text without knowing HTML or CSS.

```markdown
---
layout: default
title: Mission
permalink: /mission/
icon_class: lightbulb-o
---

## Look!
I'm changing the content of the Mission page by editing text in the section below the weird header above.
Now I just need to save my files and reload the page to see my changes in action.

```

## Adding New Page
Adding a new page is as simple as adding a new markdown file. Lets say you wanted to add an events page.
Create a file called `events.md` and format it something like

```markdown
---
layout: default
title: Events
permalink: /events/
icon_class: calender 
---

# Interested in events?
Lalala some as above, just save then access through http://127.0.0.1:4000/csa/events/
```

To add this to the navigation, you need to event a YAML file in [`_data/site_nav.yml`](\_data/site_nav.yml). Add the events page
like show in the example below.
```yaml
top_nav:
  - page: Home
    url: /csa/
  - page: Mission
    url: /csa/mission/
  - title: Eboard
    subfolderitems:
      - page: Current
        url: /csa/eboard/all/2017/
      - page: All
        url: /csa/eboard/all/
  - page: Meetings
    url: /csa/meetings/
  - page: Events
    url: /csa/events/
  - page: Contact
    url: /csa/contact/
    class: button special
```

## Adding New Eboard
New eboard? Alright, I'm hoping to make this as painless as possible. Just create one file and edit another.

In the `_eboards` directory, create a `2059.html`, but use the year the eboard starts. Then fill it with YAML like below.
```yaml
---
year: 2059
image: eboard_photo.jpg
video_url: http://www.wiztube.com/potter/intro_video
video_image: screenshot_of_video.jpg
video_description: Watch our into video!
members:
  - position: Headmaster of Hogwartz
    name: Dumbledore
    major: Wizardry
    year: 2060
    facebook: coolwizard123
  - position: The Boy Who Lived
    name: Harry Potter
    major: Defence Against the Dark Arts
    year: 2061
    facebook: mrpotter
    image: harry.jpg
    bio: >-
      Hello, I like battling evil and kissing girls with stereotypical Asian names.
---

```

Now throw all the eboard images into `assets/images/eboard/2059/`. Please don't use huge images! Try to size them
down them down to a realistic size for modern computers to show at 100%

Then edit `_data/site_nav.yml` and update the year for the current eboard. After saving everything, you should be all done!

# Deployment
Note: If you are editing off campus, you must be connected to the Northeastern VPN.

Once you pushed your change to the GitHub repo's master branch, you are ready to deploy to the actual webservers
hosting the public website. In most cases, the script below should do.
```bash
./script/deploy
```

Sometimes you need to wipe out the files on the server because you have changed the directory structure, need some files
to be deleted, or other weirdness. You can run this script below, which will first wipe out the public webserver, then
deploy the latest code.
```bash
./script/clean_deploy
```
