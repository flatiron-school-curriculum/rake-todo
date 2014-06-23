# This is an example of a Rake Task called "hello_rake"
task :hello_rake do
  puts "Hello, from rake"
end

# Define new tasks below

task :default do
  puts "Hello, from default task!"
end

task :environment do
  require_relative './config/environment'
end

task :upcoming_todos => [:environment] do
  User.with_upcoming_todos.each do |user|
    puts "Emailing #{user}"
  end
end

task :overdue_todos => [:environment] do
  User.with_overdue_todos.each do |user|
    puts "Emailing #{user}"
  end
end

namespace :todos do
  task :mark_overdue => [:environment] do
    Todo.mark_overdue
  end
  task :mark_upcoming => [:environment] do
    Todo.mark_upcoming
  end
end

desc "Loads an interactive console."
task :console => [:environment] do
  load './bin/console'
  exit
end

namespace :user do
  desc "Send a summary to a User"
  task :send_summary, [:email] => [:environment] do |t, args|
    # [email] is the argument array
    # [environment] is the prerequisite task array
    puts "Sending summary to user with #{args[:email]}"
  end
  desc "Send a reminder to User"
  task :todo_reminder => [:environment] do
    # ENV is a constant that represents all of our environmental variables
    # set through our shell. It stores things like your PATH and such. It is a
    # Hash like object.
    my_ruby_home = ENV["MY_RUBY_HOME"]
    puts "ENV includes #{my_ruby_home}"

    puts "Sending todo reminder to #{ENV["EMAIL"]}"
  end
end