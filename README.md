# Ruby on Rails 
##### LEARN WEB DEVELOPMENT WITH RAILS - *by Michael Hartl*

`I dont own any of the content of this. I'm just using this for educational purposes to teach myself about ruby on rails.`

To learn more about this please go to this link [Ruby on Rails Tutorial by Michael Hartl](https://www.railstutorial.org/book)

## INTRODUCTION
Ruby on Rails (or just `“Rails”` for short) is a web development framework written in the Ruby programming language.

```scss
//TYPE IN TERMINAL
rails new hello_app
or 
rails new hello_app --database=postgresql
```
```scss
//TYPE IN TERMINAL
cd hello_app
```
```scss
//TYPE IN TERMINAL
bundle install
```
---
## Model-View-Controller (MVC)
<details>
<summary>SEE DROPDOWN: TO KNOW MORE ABOUT MVC</summary>

This is a hint that Rails follows the model-view-controller (MVC) architectural pattern, which enforces a separation between the data in the application

When interacting with a Rails application, a `browser sends a request`, which is received by a webserver and passed on to a `Rails controller`.

Which is in charge of what to do next. In some cases, the `controller will immediately render a view`.

Which is a template that gets converted to `HTML and sent back to the browser`.

`The controller interacts with a model`, which is a Ruby object that represents an element of the site (such as a user) and is `in charge of communicating with the database`. 

After invoking the model, the controller then renders the view and returns the complete web page to the browser as HTML.

</details>

---
```rb
# In app/controllers/application_controller.rb
...
  def hello
    render html: "hello world"
  end
...
```
> In the present case, the `controller name is application` and the `action name is hello`
```rb
...
# In config/routes.rb
root 'controller_name#action_name'
...
```
> the Rails router determines where to send requests that come in from the browser
```rb
...
# In config/routes.rb WE TYPE
root 'application#hello'
...
```
---
## First-time repository setup - `Github`
<details>
<summary>SEE DROPDOWN: TO KNOW MORE ABOUT GITHUB REPOSITORY</summary>

- The first step is to navigate to the root directory of the first app and initialize a new repository:
```scss
// TYPE IN TERMINAL
$ git init
```
> Initialized empty Git repository in /home/ubuntu/workspace/hello_app/.git/
```scss
// TYPE IN TERMINAL
$ git add -A
```
> Add all the project files to the repository
```scss
// TYPE IN TERMINAL
$ git status
```
> The added files are initially placed in a staging area, which contains pending changes to our project
```scss
// TYPE IN TERMINAL
$ git commit -m "Initialize repository"
```
> Tell Git we want to keep the changes we use the commit command
- By the way, we can see a list of the commit messages using the `log command`
```scss
// TYPE IN TERMINAL
$ git log
```
> Depending on the length of the repository’s log history, you may have to type q to quit.
```scss
// TYPE IN TERMINAL
$ git checkout -b modify-README
```
> The parent repository is the master branch, and we can create a new topic branch by using checkout with the -b flag
```scss
// TYPE IN TERMINAL
$ git branch
```
> lists all the local branches, and the asterisk * identifies which branch we’re currently on.
```scss
// TYPE IN TERMINAL
$ git add -A
```
```scss
// TYPE IN TERMINAL
$ git commit -a -m "Improve the README file"
```
> git commit provides the `-a flag` as a shortcut for the (very common) case of committing all modifications to existing files

- Merge

```scss
// TYPE IN TERMINAL
$ git checkout master
```
> Switch to branch master
```scss
// TYPE IN TERMINAL
$ git merge modify-README
```
> After you’ve merged in the changes, you can tidy up your branches by deleting the topic branch using git branch -d if you’re done with it
```scss
// TYPE IN TERMINAL
$ git branch -d modify-README
```
> This step is optional, and in fact it’s quite common to leave the topic branch intact. This way you can switch back and forth between the topic and master branches.
```scss
//= DONT DO THIS UNLESS YOU MESS UP =//
// TYPE IN TERMINAL 
$ git checkout -b topic-branch
$ <really mess up the branch>
$ git add -A
$ git commit -a -m "Make major mistake"
$ git checkout master
$ git branch -D topic-branch
```
> Unlike the -d flag, the -D flag will delete the branch even though we haven’t merged in the changes.

- Push

```scss
// TYPE IN TERMINAL
$ git push
```
>  Since we have already done one push on most systems we can omit origin master, and simply run git push:>

</details>

---

## Deploying in `Heroku`
<details>
<summary>SEE DROPDOWN: TO KNOW HOW TO DEPLOY IN HEROKU</summary>

### `Heroku setup`
> Heroku uses the PostgreSQL database we need to add the `pg gem` in the production environment to allow Rails to talk to Postgres.
```rb
#In /Gemfile Type
...

group :production do
  gem 'pg', '0.21.0'
end

...
```
```rb
#In /Gemfile Type
...

#group :development, :test do
  gem 'sqlite3', '1.3.13'
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
  #gem 'capybara', '~> 2.13'
  #gem 'selenium-webdriver'
#end

...
```
> This command make sqlite3 gem from being included in a production environment, since SQLite isn’t supported at Heroku

```scss
// TYPE IN TERMINAL
$ bundle install --without production
```
- To prepare the system for deployment to production, we run bundle install with a special flag to prevent the local installation of any production gems (which in this case consists of the pg gem)
> Because the only gem added is restricted to a production environment, right now this command doesn’t actually install any additional local gems, but it’s needed to update `Gemfile.lock` with the `pg gem`
```scss
// TYPE IN TERMINAL
$ git commit -a -m "Update Gemfile for Heroku"
```
In your terminal
```scss
// TYPE IN TERMINAL
$ heroku version
```
Once you’ve verified that the Heroku command-line interface is installed, use the heroku command to log in and add your SSH key
```scss
// TYPE IN TERMINAL
$ heroku login
$ heroku keys:add
```
```scss
// TYPE IN TERMINAL
$ heroku create
```
> Finally, use the heroku create command to create a place on the Heroku servers for the sample app to live
## Heroku deployment
To deploy the application, the first step is to use Git to push the master branch up to Heroku
```scss
// TYPE IN TERMINAL
$ git push heroku master
```
Renaming the application for heroku
```scss
// TYPE IN TERMINAL
$ heroku rename "name of your app"
```
> Create a random subdomain to prevent someone visiting your app. give this only if its ready for review.

</details>

# THE END