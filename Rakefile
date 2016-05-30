require 'rake'
require 'rake/testtask'
require 'bundler/gem_tasks'

Rake::TestTask.new do |t|
  t.pattern = 'test/**/*_test.rb'
  t.libs.push 'test'
end

namespace :test do
  task :coverage do
    require 'simplecov'
    require 'coveralls'

    if ENV['TRAVIS']
      SimpleCov.formatter = Coveralls::SimpleCov::Formatter
    end

    SimpleCov.start do
      add_filter 'test/'
      add_filter 'script/'
      add_filter 'tmp/'

      add_group 'Action',       'lib/hanami/action'
      add_group 'Commands',     'lib/hanami/commands'
      add_group 'Config',       'lib/hanami/config'
      add_group 'Generators',   'lib/hanami/generators'
      add_group 'Mailer',       'lib/hanami/mailer'
      add_group 'Repositories', 'lib/hanami/mailer'
      add_group 'Routing',      'lib/hanami/routing'
      add_group 'Templates',    'lib/hanami/templates'
      add_group 'Views',        'lib/hanami/views'
    end

    Rake::Task['test'].invoke
  end
end

task default: :test

