#!/usr/bin/env ruby
require 'rake/testtask'
require 'rubygems'
require 'rake'
require 'haml'

Rake::TestTask.new(:test) do |t|
  t.libs << 'test'
  t.test_files = FileList['test/test_*.rb', 'test/*_test.rb']
  t.verbose = true
end

task default: :compile

task :compile do
  FileList.new('./src/*.html.haml').each do |filename|
    if filename =~ /([^\/]+)\.haml$/
      File.open($1, 'w') do |f|
        f.write Haml::Engine.new(File.read(filename)).render
      end
    end
  end
end

task :clean do
  FileUtils.rm_r(Dir.glob("./*.html"), force: true)
end
