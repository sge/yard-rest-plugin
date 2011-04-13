require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "yard-rest-plugin"
    gem.summary = %Q{A plugin for Yardoc that produces API documentation for Restful web services}
    gem.description = %Q{A plugin for Yardoc that produces API documentation for Restful web services. See README.markdown for more details}
    gem.email = "aisha.fenton@visfleet.com"
    gem.homepage = "http://github.com/visfleet/yard-rest-plugin"
    gem.authors = ["Aisha Fenton"]
    gem.add_dependency("yard", '~>0.6.1')
    gem.files = Dir.glob("{lib,example,templates/rest}/**/*.*").concat(["Rakefile"])
    gem.extra_rdoc_files = ['VERSION', 'README.markdown']
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

namespace :ex do
  desc "Generate example docs"
  task :generate do
    `yardoc 'example/*.rb' -t rest --backtrace -p ./templates -e ./lib/yard-rest-plugin.rb -r example/README.markdown --title 'Sample API'`
  end

  desc "Clean example docs"
  task :clean do
    `rm -R doc`
    `rm -R .yardoc`
  end
end

# PRIVATE GEM: Remove tasks for releasing this gem to Gemcutter
tasks = Rake.application.instance_variable_get('@tasks')
tasks.delete('release')
tasks.delete('gemcutter:release')