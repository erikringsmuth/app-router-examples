## app-router examples
Example [app-router](http://erikringsmuth.github.io/app-router/) setup to get you running locally.

[Download](https://github.com/erikringsmuth/app-router-examples/archive/master.zip) and un-zip the examples.

#### hash-routing
Hash routing uses hash paths `/#/paths`.
1. Open a terminal in the `hash-routing` directory
2. Start a static content server with node `http-server` or `python -m SimpleHTTPServer 8080`
3. Open [http://localhost:8080/](http://localhost:8080/)

#### pushstate-routing
Push state routing uses regular paths `/path` and extends`<a>` tags with [html5-history-anchor](https://github.com/erikringsmuth/html5-history-anchor). Example: `<a is="html5-history-anchor" href="/link" pushstate popstate>/link</a>`
1. Open a terminal in the `full-page-load-routing` directory
2. Start the express.js server with `node server.js`
3. Open [http://localhost:8080/](http://localhost:8080/)

#### full-page-load-routing
Full page load routing uses regular paths `/path`.
1. Open a terminal in the `full-page-load-routing` directory
2. Start the express.js server with `node server.js`
3. Open [http://localhost:8080/](http://localhost:8080/)
