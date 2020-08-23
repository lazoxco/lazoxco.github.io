---
layout: post
title:      "A Rails Project Management App"
date:       2020-08-23 18:47:17 +0000
permalink:  a_rails_project_management_app
---

For my Rails assessment project, I decided to build a project management app that is geared toward DIY and home improvement. The app allows users to create an account and sign in, then create projects. On the projects show page, the project owner can add task items to the project. Other users can comment on projects and discuss ideas. Building this project was a breeze with Ruby on Rails (after I learned how to use it of course).

I originally created my Project model as a Task model, but later found that I would probably make more sense if it was project since the project has task items. Here’s a quick breakdown of how to build CRUD functionality in Rails.

First define you model and get your database together. I used a Rails generator to do this.

$ rails generate resource Task name:string description:text

This will create a Task model with an attribute name as a string data type and description as a text (used for text area fields). This will also create a Tasks controller, RESTful routes, an empty view folder, and the database migration. After you’ve generated your resource, migrate your database!

Next, I wanted to create an index page where everyone can see a list of projects or tasks. Since I knew that I would need additional view, I went ahead and created an new, index, show, and edit template files, as well as a form partial.

After creating my view files, I verified that my routes were working, which they are with rails generate resource magic!

Next, I created the following actions in the Tasks controller.


```
class TasksController < ApplicationController
  def index
    @tasks = Task.all
  end

  def new
      @task = Task.new
  end

  def create
    @task = Task.new(task_params)
    if @task.save
      redirect_to task_path(@task)
    else
      @task
      render :new
    end
  end

  def show
    @task = Task.find(params[:id])
  end

  def edit
    @task = Task.find(params[:id])
  end

  def update 
    @task = Task.find(params[:id])
    @task.update(task_params)
    redirect_to task_path(@task)
  end

  def destroy
    @task = Task.find(params[:id])
    @task.destroy
    redirect_to :root
  end
  
  private

  def task_params
    params.require(:task).permit(:name, :description)
  end
end
```

That will give you all the functionality you need to create a crud app in Rails. The final piece would be to build your views and form for new and edit. Remember, I created a form partial form my index view. The form partial looks like this:

```
<% if @task.errors.any? %>
    <% @task.errors.full_messages.each do |message| %>
      <p><%= message %></p>
    <% end %>
<% end  %>

<%= form_for @task do |f| %>
  <div class="form-group field_with_errors">
    <%= f.label :name %><br>
    <%= f.text_field :name %>
  </div>
  <div class="form-group field_with_errors">
    <%= f.label :description %><br>
    <%= f.text_area :description %>
  </div>
  <%= f.submit%>
<% end %>
```

Just render that partial in your new and edit view and you’re good to go!

In the end, Ruby on Rails is a fantastic and easy to user framework. There is still so much that I have to learn about Rails, but I’m looking forward to learning more!
