# nginx-this
`nginx-this` is a hack shell script for OSX that pushes the specified directory into your nginx configuration and 
reloads nginx.

This is intended for use with [Homebrew](http://mxcl.github.io/homebrew/) installed nginx.

# Example

    $ [~/Projects/angular] nginx-this .
    # now browse to http://localhost:8080/angular/

# Installation

1. Install nginx via Homebrew if you haven't already.

        brew install nginx

2. You can set nginx to start automatically or not; in either case at least follow the post installation instructions
that setup the LaunchAgent configuration:

        mkdir -p ~/Library/LaunchAgents
        cp /usr/local/Cellar/nginx/1.2.7/homebrew.mxcl.nginx.plist ~/Library/LaunchAgents/

3. Modify your nginx.conf, adding the following line within the `server` block:

        # vim /usr/local/etc/nginx/nginx.conf

        http {
            # omitted
            server {
                #omitted
                include conf.d/*.conf;
            }
        }

4. Make the `conf.d` directory:

        mkdir -p /usr/local/etc/nginx/conf.d

5. Add `nginx-this/bin` to your `$PATH` environment variable

# Usage

You can use `nginx-this` with any directory name as the first parameter. The end result is a `directory.conf` file will
be created in your `/usr/local/etc/nginx/conf.d/` directory which aliases the current directory to the nginx server
section.

A few other command line scripts become available as well: `reload-nginx`, `stop-nginx` and `start-nginx`.

