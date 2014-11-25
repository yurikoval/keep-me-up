require 'open-uri'
namespace :up do
  desc "Keep me up"
  task :all do
    upfile = File.join(File.dirname(__FILE__), "Upfile")
    File.readlines(upfile).each do |line|
      host = line.chomp
      task('up:host').execute(host)
    end
    task('up:deadmanssnitch').execute if ENV['KMA_DMS_KEY']
  end

  desc "Keep host up"
  task :host, :host do |t, host|
    print_and_flush "Keeping #{host} up... "
    get_url host
  end

  desc "Ping deadmanssnitch.com"
  task :deadmanssnitch do
    message = URI.escape(ENV['KMA_MESSAGE'] || 'Hello from keep-me-alive')
    key = ENV['KMA_DMS_KEY']
    url = "https://nosnch.in/#{key}?m=#{message}"
    print_and_flush "Notifying #{url} ... "
    get_url url
    puts "ok"
  end
end

def print_and_flush(str)
  print str
  $stdout.flush
end

def get_url(url)
  begin
    URI.parse(url).read
    puts "ok"
  rescue Exception => e
    puts "failed: #{e.message}"
  end
end
