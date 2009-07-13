require 'rake/clean'
require 'rake/testtask'

require 'rbconfig'
include Config
def CONFIG.rubybin; File.join(*values_at('bindir', 'ruby_install_name')); end
def CONFIG.gembin; rubybin.sub('ruby', '%s') % 'gem'; end

Rake::TestTask.new(:test) do |t|
  t.pattern = 'test/TC_*.rb'
end
task(:logdir) { mkdir_p 'test/log' }
CLEAN.include('test/log')
task :test => %(logdir)

desc "Build analogger gem"
task :gem do
  sh "#{CONFIG.gembin} build analogger.gemspec"
end