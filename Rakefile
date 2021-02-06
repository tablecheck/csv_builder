require 'rdoc/task'
require 'rspec/core'
require 'rspec/core/rake_task'

# Temporary hack from https://stackoverflow.com/questions/35893584/nomethoderror-undefined-method-last-comment-after-upgrading-to-rake-11
module TempFixForRakeLastComment
  def last_comment
    last_description
  end
end
Rake::Application.send :include, TempFixForRakeLastComment

desc 'Generate documentation for the csv_builder plugin.'
Rake::RDocTask.new(:rdoc) do |rdoc|
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title    = 'CSV Builder'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README.md')
  rdoc.rdoc_files.include('CHANGELOG.rdoc')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

desc 'Test the csv builder'
RSpec::Core::RakeTask.new(:spec) do |t|
  t.pattern   = "./spec/**/*_spec.rb"
end

desc 'Default: run specs.'
task :default => :spec
