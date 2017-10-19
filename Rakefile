require 'rake'
require 'rake/testtask'
require 'bundler/gem_tasks'
require 'gemfury/tasks'

desc "Default task"
task :default => [ :test ]

# override rubygems' normal release task to use Gemfury
Rake::Task['release'].clear
task :release, [:remote] => ["build", "release:guard_clean", "release:source_control_push"] do
  Rake::Task['fury:release'].invoke(nil, 'patientslikeme')
end

Rake::TestTask.new do |t|
  t.libs = ['lib', 'test']
  t.test_files = Dir["test/**/*_test.rb"]
  t.verbose = true
  t.warning = true
end

