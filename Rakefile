# coding: utf-8

## please put chef souce to ./chef
$:.push(File.expand_path('../chef/lib', __FILE__))
require 'chef'

desc 'create all words'
task :default do
  Rake::Task[:platform].invoke
end


desc 'create platform ilst'
task :platform do
  File.open('platform.dict', 'w') do |f|
  f.write Chef::Platform.platforms.keys.map {|x| x.to_s}.join("\n")
  end
end
