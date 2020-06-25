# frozen_string_literal: true

require 'bundler/gem_tasks'
require 'rake/testtask'

desc 'Release a new version'
namespace :decoro do
  task :release do
    version_file = './lib/decoro/version.rb'
    File.open(version_file, 'w') do |file|
      file.puts <<~EOVERSION
        # frozen_string_literal: true

        module Decoro
          VERSION = '#{Decoro::VERSION.split('.').map(&:to_i).tap { |parts| parts[2] += 1 }.join('.')}'
        end
      EOVERSION
    end
    module Decoro
      remove_const :VERSION
    end
    load version_file
    puts "Updated version to #{Decoro::VERSION}"

    `git commit lib/decoro/version.rb -m "Version #{Decoro::VERSION}"`
    `git push`
    `git tag #{Decoro::VERSION}`
    `git push --tags`
  end
end

Rake::TestTask.new(:test) do |t|
  t.libs << 'test'
  t.libs << 'lib'
  t.test_files = FileList['test/**/*_test.rb']
end

task default: :test
