require "rubygems"
require "bundler/setup"
require "stringex"

# http://culttt.com/2015/08/05/understanding-and-using-ruby-rake/

posts_dir = "_posts"
new_post_ext = "md"

desc "This is a description!"
task :hello, :world do |t, args|
  puts "[INFO] Hello world"
end

desc "Preview page"
task :view do |t, args|
  puts "[INFO] Previewing and watching using jekyll serve"
  jekyllPid = Process.spawn("jekyll serve")
  trap("INT") {
    [jekyllPid].each { |pid| Process.kill(9, pid) rescue Errno::ESRCH }
    puts "[INFO] Trapped CTRL+C, killed children, exited properly"
    exit 0
  }

  [jekyllPid].each { |pid| Process.wait(pid) }
end

# usage rake new_post[my-new-post] or rake new_post['my new post'] or rake new_post (defaults to "new-post")
desc "Begin a new post in ./#{posts_dir}"
task :post, :title do |t, args|
  if args.title
    title = args.title
  else
    title = get_stdin("Enter a title for your post: ")
  end
  filename = "./#{posts_dir}/#{Time.now.strftime('%Y-%m-%d')}-#{title.to_url}.#{new_post_ext}"
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end
  puts "Creating new post: #{filename}"
  #open(filename, 'w') do |post|
  #  post.puts "---"
  #  post.puts "layout: post"
  #  post.puts "title: \"#{title.gsub(/&/,'&amp;')}\""
  #  post.puts "date: #{Time.now.strftime('%Y-%m-%d %H:%M:%S %z')}"
  #  post.puts "comments: true"
  #  post.puts "categories: "
  #  post.puts "---"
  #end
end

