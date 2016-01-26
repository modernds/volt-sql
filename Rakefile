require "bundler/gem_tasks"

task default: 'spec:all'

require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec)

namespace "spec" do
  task :pg do
    ENV['DB'] = 'pg'
    Rake::Task['spec'].execute
  end

  task :sqlite do
    ENV['DB'] = 'sqlite'
    Rake::Task['spec'].execute
  end

  task :mysql do
    ENV['DB'] = 'mysql'
    Rake::Task['spec'].execute
  end
end

desc "Run specs with all db adapters"
namespace "spec" do
  task :all do
    %w[spec:pg spec:sqlite spec:mysql].each do |task_name|
      puts "--------------------------\n #{task_name} \n--------------------------"
      sh "rake #{task_name}" do
        # Ignore errors
      end
    end
    puts "Finished running all specs"
  end
end
