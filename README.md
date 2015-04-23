# app-router examples
Example [app-router](https://erikringsmuth.github.io/app-router/) setup to get you running locally.

[Download](https://github.com/erikringsmuth/app-router-examples/archive/master.zip) and un-zip the examples.

#### hash-routing
Hash routing uses hash paths `/#/paths`.

1. Open a terminal in the `hash-routing` directory
2. Start a static content server with node `http-server` or `python -m SimpleHTTPServer 8080`
3. Open [http://localhost:8080/](http://localhost:8080/)

#### pushstate-routing
Push state routing uses regular paths `/path` and extends `<a>` tags with the [pushstate-anchor](https://github.com/erikringsmuth/pushstate-anchor).

```html
<a is="pushstate-anchor" href="/home">Home</a>
```

1. Open a terminal in the `pushstate-routing` directory
2. Start the express.js server with `node server.js`
3. Open [http://localhost:8080/](http://localhost:8080/)

#### Other Routers

Examples of `app-router`, `flatiron-director`, and plain old HTML files.
https://github.com/erikringsmuth/polymer-router-demos

#### HTTP Server Pushstate Configurations

Examples of HTTP Server configurations to get pushstate working.

Apache .htaccess
```
Options +FollowSymLinks
IndexIgnore /
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule (.*) index.html
```

Nginx Conf - to be inserted in your server{} declaration
```
location / {
  try_files $uri @rewrites /index.html;
}
# If no asset matches, send it to your javascript app. Hopefully it's a route in the app!
location @rewrites {
  rewrite .* /index.html last;
}
```
