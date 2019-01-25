ENV["SINATRA_ENV"] ||= "development"

require_relative './config/environment'
require 'sinatra/activerecord/rake'
require 'pry'
# Type `rake -T` on your command line to see the available rake tasks.

task :console do
  Pry.start
end

task :migrations do
  puts "Migrating Development and Test Databases"
  system("rake db:migrate && rake db:migrate SINATRA_ENV=test")
end

task :drop do
  puts "Dropping databases..."
  system("rm db/development.sqlite && rm db/test.sqlite && rm db/schema.rb")
end

task :reset_databases do
  Rake::Task['drop'].execute
  Rake::Task['migrations'].execute
  system("shotgun")
end
