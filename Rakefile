require 'rake/testtask'
 
task default: %i(test)

Rake::TestTask.new do |t|
  t.pattern = 'tests/*_test.rb'
  t.warning = false
  t.verbose = true
end