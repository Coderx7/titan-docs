#!/usr/bin/env ruby

# Invisible Tasks

objects = Rake::FileList.new "titan-*.markdown", "titan-*.md"
rule ".7" => ".markdown" do |t|
  sh "pandoc -s -t man #{t.source} -o #{t.name}"
end

task :copy => objects.ext(".7") do |t|
  sh "cp #{t.source} /usr/local/share/man/man7/#{t.source}"
end

# Visible Tasks

desc "Install generated manfile in /usr/local/man directory"
task :install => :copy do
  sh "mandb"
end

desc "Compile manfile from markdown. Check with: man -l FILE"
task :default => objects.ext(".7")
