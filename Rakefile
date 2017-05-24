require "kramdown"

namespace :converter do
  task :content do
    Dir::glob("_content/post/*").each do |src|
      # destination path will be "content/{filename}.html"
      dst_path = src[1..-1].sub(/(.*)\.md/, '\1.html')

      open(dst_path, "w") do |dst|
        content = open(src) { |f| f.read }

        # keep front matter
        content = content.sub(/(---.*---\n)/m, "")

        content = embedding_tweet(content)

        # write with concatenating front matter
        dst.write($1 + Kramdown::Document.new(content).to_html)
      end
    end
  end
end