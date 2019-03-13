# Swagger UI Integration

This module adds Swagger UI v3 integration for Hammock.

## Provides

- Swagger UI v3 web resources.
- Boot ui redirect with configurable api url.

## Usage

- Add  the hammock _swagger-ui_ artifact to your pom.
- When not using hammock _swagger_, provide the swagger api url.
- To disable the online validator use; `swagger-ui.redirect=index.html?validatorUrl=`

## Config

Property | default | Description
--- | --- | ---
swagger-ui.enable | `true` | Enable/Disable swagger ui per environment.
swagger-ui.version | `<version>` | Allows for usage of different webjar version. If you define this, you must have the webjar also defined in your pom as a dependency as well.
swagger-ui.redirect | `index.html` | UI Boot redirect url, note; needs to start with slash or http.
swagger-ui.path | `/swagger-ui` | Base path for ui resources.
swagger-ui.api | `/openapi.json` | The url location to start the swagger ui with.

### Default request sequence

- request /swagger-ui
- redirect /swagger-ui/index.html?url=/openapi.json
- forwards /swagger-ui/* to /META-INF/resources/webjars/swagger-ui/

### UI Customization

There are a couple of options but most common would be a cloned index;

- Make a copy of the original index.html
- Place it in `static.resource.location` like META-INF/resources/example/index.html
- Modify the js/css resources paths to prefix with /swagger-ui
- Change `swagger-ui.redirect` to /example/index.html
