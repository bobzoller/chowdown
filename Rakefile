require 'rubygems'
require 'bundler'
Bundler.require(:default)
require 'shellwords'

desc "Generate blog files"
task :generate do
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => ".",
    "destination" => "_site"
  })).process
end

desc "Generate and publish to S3"
task :publish => [:generate] do
  system "aws s3 sync --acl public-read --delete _site/ s3://recipes.zoller.us/"
end

desc "Serve"
task :serve do
  system "bundle exec jekyll serve"
end

task :default => :serve
