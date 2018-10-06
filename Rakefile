# encoding: UTF-8
require "tmpdir"


# Change your GitHub reponame
GITHUB_REPONAME = "dotenfund/dotenfund.github.io"
GITHUB_REPO_BRANCH = "master"

desc "Generate and publish blog to gh-pages"
task :publish do
  Dir.mktmpdir do |tmp|
    cp_r "_site/.", tmp

    pwd = Dir.pwd
    Dir.chdir tmp

    system "git init"
    system "git checkout --orphan #{GITHUB_REPO_BRANCH}"
    system "git add ."
    message = "Site updated at #{Time.now.utc}"
    system "git commit -am #{message.inspect}"
    system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
    system "git push origin #{GITHUB_REPO_BRANCH} --force"

    Dir.chdir pwd
  end
end
