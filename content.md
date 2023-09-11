# Bulletin Board 1

In this project, we're going to practice building complete, database-backed CRUD resources. But this time we're going to see some shortcuts.

<div class="bg-red-100 py-1 px-5" markdown="1">
Note that there is a walkthrough video linked at the bottom of this lesson, but please read through the notes before you watch the video
</div>

## Data model

[Our aim is to build an app like this.](https://bulletin-board-bootstrap.matchthetarget.com/)

It is an app that lets anyone create a bulletin board, and then anyone can make posts on that board. In other words — this app doesn't have sign in/sign out yet. Everyone is anonymous and the site looks the same to everyone.

When creating a post, the author must specify a title, body, and date that the post expires on. The board displays active posts and expired posts in separate sections.

Take a moment and try to guess what tables and columns are in the database for the app.

## Setup 

This project includes automated tests, so click on this button to get started:

LTI{Load Bulletin Board 1 assignment}(https://grades.firstdraft.com/launch)[S9ymPy6WCsn18gLbByVbZQ7k]{vfdtzJb5bLYqYwuqgeRKpc5d}(10)[Bulletin Board 1 Project]

Then, fork the repository and create your codespace.

## Target with no CSS

Here is our target for Bulletin Board 1: [bulletin-board-1.matchthetarget.com](https://bulletin-board-1.matchthetarget.com/) 

This is the same as the app linked above, but without any of the fancy styling. (We'll soon learn powerful shortcuts for adding the styling! But for now, we're still focused on the functionality.)

## Generating resources

Here is the database architecture for the app:

Normally, the steps would be:

- Generate the model and migration with the `rails generate model...` shortcut.
- Build out the RCAVs for index, show, create, update, etc.

However, as we've seen, the RCAVs for CRUD are pretty much the same from table to table. The names of files, variables, and columns vary; but the basic logic is identical.

So: Rails provides a way to automate writing this boilerplate code — resource generators.

[Read more about the `draft:resource` generator here.](https://learn.firstdraft.com/lessons/133-draft-resource-generator)

Then, come back and let's generate our two tables, but with the resource generator. At a bash prompt, generate the `Board` table using the `draft:resource` generator rather than the `model` generator:

```
rails generate draft:resource board name:string
```

You'll see that it generates the model and migration, but also all of the RCAVs for index, show, create, update, and destroy.

Next, let's generate the `Post` resource:

```
rails generate draft:resource post title:string body:text expires_on:date board_id:integer
```

Execute the generated migrations with:

```
rake db:migrate
```

Then start your server with `bin/dev`, and in your live app preview, navigate to `/boards` and `/posts`. You should see that they work!

Now, let's massage the generated, boilerplate code until it matches the target.

- What are the differences between the generated code and the targe? List them out.
- Make a git commit.
- Try to match the target on your own. You have all the building blocks to do so; try inventing solutions on your own.
- Then, watch [the walkthrough video](https://share.descript.com/view/DlxVNV7HMx4).

## Walkthrough video

[Here is a walkthrough video that you should follow along with.](https://share.descript.com/view/DlxVNV7HMx4)

---

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }
	
---
