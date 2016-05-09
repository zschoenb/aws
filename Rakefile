require 'jsonlint/rake_task'
JsonLint::RakeTask.new do |t|
  t.paths = %w(
    stacks/**/*.json
    params/**/*.json
  )
end

task :copy_artifacts do
  if ENV['CI'] == 'true' && ENV['TRAVIS_PULL_REQUEST'] == 'false'
    `mkdir -p build/cloudformation/branch/#{ENV['TRAVIS_BRANCH']};
     cp -R stacks build/cloudformation/branch/#{ENV['TRAVIS_BRANCH']};
     cp -R params build/cloudformation/branch/#{ENV['TRAVIS_BRANCH']};`
  end
end

task default: [:jsonlint, :copy_artifacts]
