I got it working. I'm now able to run my site locally on Windows. Here's how I did it:

Install bundle
Install ruby
Install jekyll

cd into site directory

bundle exec jekyll serve

I ran into problems before, but it ran without a hitch this time. 

Except you get this warning about how the auto-regenerate function might not work.

A bit of google-fu and I found this add-on to the command:
    bundle exec jekyll serve --force_polling

And that did the trick!