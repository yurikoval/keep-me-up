require 'net/http'

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
    url = URI.parse(host)
    req = Net::HTTP::Get.new(url.path)
    res = Net::HTTP.start(url.host, url.port) {|http|
        http.request(req)
    }
    puts "ok"
  end
end

def print_and_flush(str)
  print str
  $stdout.flush
end
