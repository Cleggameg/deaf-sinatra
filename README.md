# Deaf Sinatra 1 Synchronous Forms

## Learning Competencies

* Read a foreign code base and be able to contribute code review and changes
* Map the flow of data through a web application
* Use URL parameters to pass data into a server application
* Use form controls to pass data into a server application
* Use ruby flow control to change server response
* Use redirect and render and know when to use each

## Summary

We're going to build our first and very simple web application using
[Sinatra][], a lightweight framework for building web
applications in Ruby.

This challenge is basically a web version of Deaf Grandma.

## Releases

### Release 0: Running the App

This repo includes the Sinatra skeleton you'll use for this challenge. Explore the directory structure.  Controllers are in `app/controller` and views are in `app/views`.

Run `bundle` to install the necessary gems.  Note that this application uses Postgres for its database, not SQLite.  If there's a database-related error at any point grab a staff member to make sure the machine is configured correctly and Postgres is running.

To launch the web application this command from the application root directory:

```text
$ shotgun config.ru
```

Sinatra, like Rails, is a [Rack-based](http://rack.github.com/) framework, which means the main point of entry is this `config.ru` file.  The `ru` stands for "rackup."

Tip: No need to include the argument `config.ru` to `shotgun`. By default `shotgun` looks for a `config.ru` file.

You should now be able to visit your web app at [http://localhost:9393](http://localhost:9393).  `localhost` always refers to "the current machine," so you actually have a tiny web server running on your own computer!

It should look like this:

<p style="text-align: center"><img src="screenshot.png"></p>

If it looks different call a staff member over!

### Release 1: Make Grandma Talk

First, visit [http://localhost:9393/?grandma=hey!](http://localhost:9393/?grandma=hey!).  Notice how the value of the URL parameter `grandma` is rendered on the page.  Try to find where in the code this logic exists.  How do we extract information from the URL parameters?

Note: When you enter a URL in your web browser, it makes an HTTP GET request. Notice how that matches the `get '/'` route defined in `app/controllers/index.rb`?

Try modifying the value of the `grandma` query parameter. What if you change the query parameter name to `grandpa`?

The string after a URL that looks like `?param1=value1&param2=value2` is called a **query string**, and it contains the parameters of the request.

Load up the web app, type something into the talk-to-Grandma box, and click "Say it!"  What happens and why?

### Release 2:  Make Grandma Logical

Finally, change `app/controllers/index.rb` so that after you send a message to Grandma via the form her reponse is displayed via the `app/views/index.erb` template. Take inspiration from the `get '/'` route.

If you typed in something in ALL CAPS make her respond humorously.  If you typed in something else make her response with "Speak up, kiddo!"

Read the [Sinatra documentation][] on [browser redirect][] and the [handlers section][] of the [Sinatra Book][].  You'll want to redirect back to `http://localhost:9292/?grandma=foobar` (where `foobar` is whatever Grandma has to say) after the user submits their form.

### Submit your code!

**Only your `index.rb` file should have changed.**  Create a pull request with your changes.

## Resources

* [Sinatra Online Documentation][Sinatra] (_less-comprehensive but direct_)
* [Sinatra Book][Sinatra Book] (_more comprehensive, but less direct_)

[Sinatra documentation]: http://www.sinatrarb.com/intro
[browser redirect]: http://www.sinatrarb.com/intro#Browser%20Redirect
[handlers section]: http://sinatra-book.zencephalon.com/#handlers
[Sinatra Book]: http://sinatra-book.zencephalon.com/
[Sinatra]: http://www.sinatrarb.com/
