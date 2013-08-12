# coding: utf-8

## please put chef souce to ./chef
$:.push(File.expand_path('../chef/lib', __FILE__))
require 'chef'
require 'active_support/inflector'

desc 'create all words'
task :default do
  Rake::Task[:platform].invoke
  Rake::Task[:methods].invoke
  Rake::Task[:resource_list].invoke
end

def array_to_words(array)
  array.map{|x| x.to_s}.join("\n")
end

def correct_resource_list
  Dir.glob("chef/lib/chef/resource/*").map{|file| File.basename(file, '.rb')}
end

desc 'create platform list'
task :platform do
  File.open('platform.dict', 'w') do |f|
    f.write array_to_words(Chef::Platform.platforms.keys)
  end
end

desc 'create methods'
task :methods do
  %w(resource recipe).each do |cl|
    File.open("#{cl}_methods.dict", 'w') do |f|
      f.write array_to_words(Chef.const_get(cl.classify).instance_methods(false))
    end
  end
end


desc 'create resouce ilst'
task :resource_list do
  File.open('resource_list.dict', 'w') do |f|
    f.write array_to_words(correct_resource_list)
  end
end
