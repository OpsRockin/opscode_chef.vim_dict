# coding: utf-8

## please put chef souce to ./chef
$:.push(File.expand_path('../chef/lib', __FILE__))
require 'chef'
require 'chef/knife/configure'
require 'active_support/inflector'

desc 'create all words'
task :default do
  Rake::Task[:platform].invoke
  Rake::Task[:config].invoke
  Rake::Task[:config_knife].invoke
  Rake::Task[:methods].invoke
  Rake::Task[:resource_list].invoke
  Rake::Task[:resource_valiables].invoke
  Rake::Task[:provider_list].invoke
  Rake::Task[:dsl_list].invoke
  Rake::Task[:ohai_provider_list].invoke
end

desc 'remove all *.dict files'
task :clean do
  system('rm *.dict')
  system('git checkout _add_by_hand.dict')
end

def array_to_words(array)
  array.map{|x| x.to_s}.join("\n")
end

def remove_marks_from_words(array)
  array.map{|x| x.to_s}.join("\n")
end

def correct_resource_list
  Dir.glob("chef/lib/chef/resource/*").map{|file| File.basename(file, '.rb')}
end

def correct_provider_consts
  Chef::Provider.constants
end

def correct_dsl_consts
  Chef::DSL.constants
end

desc 'create platform list'
task :platform do
  File.open('platform.dict', 'w') do |f|
    f.write array_to_words(Chef::Platform.platforms.keys)
  end
end

desc 'create config options'
task :config do
  File.open('config.dict', 'w') do |f|
    f.write array_to_words(Chef::Config.keys)
  end
end

desc 'create knife config options'
task :config_knife do
  File.open('config_knife.dict', 'w') do |f|
    f.write array_to_words(Chef::Knife::Configure.instance_methods(false))
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

desc 'create resource list'
task :resource_list do
  File.open('resource_list.dict', 'w') do |f|
    f.write array_to_words(correct_resource_list)
  end
end


desc 'create instance_valiables by resource '
task :resource_valiables do
  correct_resource_list.each do |r|
    File.open("#{r}_valiables.dict", 'w') do |f|
      begin
        content = Chef::Resource.const_get(r.classify).new(r.downcase)
        f.write array_to_words(content.instance_variables + content.allowed_actions)
      rescue => e
        puts "NOTICE: at #{r} #{e.class} #{e.message}"
      end
    end
  end
end

desc 'create provider const list'
task :provider_list do
  correct_provider_consts.each do |p|
    File.open("provider_#{p.downcase}.dict", 'w') do |f|
      f.write array_to_words(Chef::Provider.const_get(p).constants(false).map {|s| ['Chef::Provider', p , s ].join('::')})
    end
  end
end

desc 'create dsl method list'
task :dsl_list do
  correct_dsl_consts.each do |p|
    File.open("dsl_#{p.to_s.underscore}.dict", 'w') do |f|
      f.write array_to_words(Chef::DSL.const_get(p).instance_methods(false))
    end
  end
end

desc 'create ohai default provider_list'
task :ohai_provider_list do
  str =  `grep -e "^\s*provides" ohai/lib/ohai/plugins/* -Rh`
  File.open("ohai_provider.dict", 'w') do |f|
    f.write array_to_words(str.split.map{|s| s.gsub(/"|'|,/,'').strip}.uniq.sort)
  end
end

