# Ruby on Rails 
##### LEARN WEB DEVELOPMENT WITH RAILS - *by Michael Hartl*

## INTRODUCTION
Ruby on Rails (or just `“Rails”` for short) is a web development framework written in the Ruby programming language.

```scss
//TYPE IN TERMINAL
rails new app_name 
or 
rails new SchoolApp --database=postgresql
```
```scss
//TYPE IN TERMINAL
cd name_of_your_app
```
```scss
//TYPE IN TERMINAL
bundle install
```
## Model-View-Controller (MVC)

This is a hint that Rails follows the model-view-controller (MVC) architectural pattern, which enforces a separation between the data in the application

When interacting with a Rails application, a `browser sends a request`, which is received by a webserver and passed on to a `Rails controller`.

Which is in charge of what to do next. In some cases, the `controller will immediately render a view`.

Which is a template that gets converted to `HTML and sent back to the browser`.

`The controller interacts with a model`, which is a Ruby object that represents an element of the site (such as a user) and is `in charge of communicating with the database`. 

After invoking the model, the controller then renders the view and returns the complete web page to the browser as HTML.
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