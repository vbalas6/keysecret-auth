# readerplus-keysecret-auth
A wrapper around the Hawk authentication framework.

- Client library to generate Key/Secret header for authentication
- Server-side Hapi authentication scheme

# Browser

    <script src="/dist/browser.js"></script>

Then

    var credentials = {
      key: "dh37fgj492je",
      secret : "werxhqb98rpaxn39848xrunpaw3489ruxnpa98w4rxn",
      algorithm: 'sha256'
    }

    var header = keySecret.client.header(URL, METHOD, { credentials: credentials });

Then can add to your request headers

        headers["Authorization"] = header.field;

# Server

    server.register(require('keysecret-auth').scheme, function (err) {
      server.auth.strategy('keySecret', 'keySecret', isKeySecret);
    });


# Example

    node example/server.js

Then open browser ``localhost:3000``