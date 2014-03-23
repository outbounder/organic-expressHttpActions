# organel

The Organelle is responsible for mounting Http Routes to the express app wrapped by ExpressHttpServer organelle or any other implementation providing the same interface.

It is roughly described in [wisdom about ExpressHttpActions](http://wisdom.camplight.net/wisdom/5110e488c489a7ef6d000043/Organic---ExpressHttpActions) 

* `reactOn`: String, default `HttpServer`.

  *otional* value if set will indicate the chemical type which will carry 
  Express App instance in its data property.

* `mount`: String

  *optional* value to be used for prefixing all routes. Useful for mounting all actions found to specific root url

* `cwd`: Object

  * optional * , Object containing key:value pairs, where all values will be prefixed with `process.cwd()` and set with their coressponding keys directly to the DNA of the organelle.

* `actions`: String

  provided full path to directory containing `actions` defined within javascript files with the following source code definition:

        module.exports = function(config) {
          return {
            "*": function(req, res, next) {},
            "GET": function(req, res, next) {},
            "POST": function(req, res, next) {}, 
            "PUT": function(req, res, next) {}, 
            "DELETE": function(req, res, next) {}, 
            "OPTIONS": function(req, res, next) {}
          }
        }

* `actionHelpers`: String

  provided full path to directory containing `actionHelpers` defined within commonjs modules. Any exports from them will be attached to context of the `actions` within object with the same name as the corresponding action helper.

* `log`: false

  will print any found action routes to the stdout

# incoming | HttpServer

* data - ExpressHttpServer instance

# outgoing | `ExpressHttpActions`

Send once actions are mounted.
