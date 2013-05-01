# nginx-this
`nginx-this` is a hack shell script for OSX that pushes the specified directory into your nginx configuration and 
reloads nginx.

This is intended for use with [Homebrew](http://mxcl.github.io/homebrew/) installed nginx.

# Example

    $ [~/Projects/angular] nginx-this .
    # now browse to http://localhost:8080/angular

# Installation

1. Install nginx via Homebrew if you haven't already.

        brew install nginx

2. You can set nginx to start automatically or not; in either case at least follow the post installation instructions
that setup the LaunchAgent configuration:

        mkdir -p ~/Library/LaunchAgents
        cp /usr/local/Cellar/nginx/1.2.7/homebrew.mxcl.nginx.plist ~/Library/LaunchAgents/

3. Modify your nginx.conf, adding the following line within the `http` block (but not the `server` block inside it):

        # vim /usr/local/etc/nginx/nginx.conf

        http {
            # omitted
            include /usr/local/etc/nginx/conf.d/*.conf;
            # omitted
            server {
                #omitted
            }
        }

4. Make the `conf.d` directory:

        mkdir -p /usr/local/etc/nginx/conf.d

5. Add `nginx-this/bin` to your `$PATH` environment variable

