# Buffer Talks

## Getting Started

### OSX

Install [Homebrew](http://brew.sh/) (if you haven't already)

Install latest ruby (at least v2.1.0 will work `ruby -v`)

```
brew install ruby
```

Install dependencies

```
bundle install
```

Start the Jekyll Server

```
bundle exec jekyll serve --watch --drafts
```

NOTE: This command restarts the server when file change and will display posts in the \_drafts folder.

Open your browser with http://localhost:4000
