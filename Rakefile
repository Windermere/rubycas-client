#!/usr/bin/env rake
require 'bundler/setup'
require 'rake'
require 'bundler/gem_tasks'

require 'appraisal'

require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new

task :default => [:spec]

namespace :spec do
  desc 'run the specs and features against every gemset.'
  task :all do
    system("bundle exec rake -s appraisal spec ;")
  end
end

module Bundler
  class GemHelper
    def rubygem_push(path)
      gem_server_url = ENV['GEM_SERVER_URL']
      sh("gem inabox '#{path}' --host #{gem_server_url}")
      Bundler.ui.confirm "Pushed #{name} #{version} to #{gem_server_url}"
    end
  end
end
