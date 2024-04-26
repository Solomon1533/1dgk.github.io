---
layout: post
title: How to Upgrade to a New Ubuntu Version
---
Before you begin, know that you can only upgrade one version ahead of what you're currently using. If you're too far behind the newest release, it probably makes more sense to spin up a fresh install. 

In this case, I'm going from Mantic Minotaur to Noble Nombat. Not sure what a nombat is, but more to follow. 

Start with the usual updates:

`sudo apt update`\
`sudo apt upgrade`

Then update to the next release:

`sudo do-release-upgrade`

You'll be prompted to make a couple of decisions, but that's pretty much it. It takes a while because it must download a bunch then install. Voila!