MRUBY_VERSION = "1.1.0"
HOST_PLATFORM = "osx"

require 'fileutils'

task :clone do
  FileUtils.mkdir_p "repo"
  Dir.chdir "repo" do
    sh "git clone -b #{MRUBY_VERSION} https://github.com/mruby/mruby.git"
  end
end

task :build do
  Dir.chdir "repo/mruby" do
    # TODO: DISABLE_GEMS
    sh "rake"
  end

  FileUtils.mkdir_p "src"
  FileUtils.cp Dir.glob("repo/mruby/src/*.c"), "src"
  FileUtils.cp Dir.glob("repo/mruby/build/host/src/*.c"), "src"

  FileUtils.cp_r "repo/mruby/include", "."

  dst = "bin/#{HOST_PLATFORM}"
  FileUtils.mkdir_p dst
  FileUtils.cp "repo/mruby/bin/mrbc", dst
end

task :clean do
  FileUtils.rm_rf ["bin", "include", "src"]
  
  Dir.chdir "repo/mruby" do
    sh "rake clean"
  end
end


