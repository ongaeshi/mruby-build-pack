require 'fileutils'

task :clone do
  FileUtils.mkdir_p "repo"
  Dir.chdir "repo" do
    sh "git clone -b 1.1.0 https://github.com/mruby/mruby.git"
  end
end

task :build do
  Dir.chdir "repo/mruby" do
    # TODO: DISABLE_GEMS
    sh "rake"
  end
end

task :clean do
  Dir.chdir "repo/mruby" do
    sh "rake clean"
  end
end


