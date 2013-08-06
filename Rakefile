require 'open-uri'
namespace :up do
  desc "Keep me up"
  task :all do
    upfile = File.join(File.dirname(__FILE__), "Upfile")
    File.readlines(upfile).each do |line|
      host = line.chomp
      task('up:host').execute(host)
    end
  end

  desc "Keep host up"
  task :host, :host do |t, host|
    print_and_flush "Keeping #{host} up... "
    get_url host
    puts "ok"
  end
end

def print_and_flush(str)
  print str
  $stdout.flush
end

def get_url(url)
    response = URI.parse(url).read
end
