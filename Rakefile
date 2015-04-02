#!/usr/bin/env rake
# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require File.expand_path('../config/application', __FILE__)

IvanTheTerriblesBlog::Application.load_tasks


task :precache_fragments => :environment do
  require 'net/http'
  include Rails.application.routes.url_helpers

  puts "\nReplies:"
  Reply.all.each do |reply|
    print "."
    Net::HTTP.get(URI.parse( "http://apple-crisp-4791.herokuapp.com" + reply_path(reply) ))
  end

  puts "\nComments:"
  Comment.all.each do |comment|
    print "."
    Net::HTTP.get(URI.parse( "http://apple-crisp-4791.herokuapp.com" + comment_path(comment) ))
  end

  puts "\nPosts:"
  Post.all.each do |post|
    print "."
    Net::HTTP.get(URI.parse( "http://apple-crisp-4791.herokuapp.com" + post_path(post) ))
  end

end
