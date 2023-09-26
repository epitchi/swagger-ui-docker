## Swagger UI Docker
### Overview
I docker composed Swagger Editor, Swagger UI, Swagger mock api server(openapi: 3.x) and nginx to handle them more easily.
If you want to write swagger spec as `swagger: "2.0"`, use `swagger2.0` branch.
There is a sample swagger spec in this so the Editor, UI and the mock API server will run without any configuration from the start.
All you need to do is edit the swagger spec, save as openapi.json, and restart docker. Voila, UI and the mock API server are updated.

### How to Run
```
docker-compose up -d

It will look like this.
docker-compose ps
         Name                       Command               State           Ports
----------------------------------------------------------------------------------------
swagger-editor   sh /usr/share/nginx/docker ...   Up      0.0.0.0:8081->8080/tcp
swagger-ui       sh /usr/share/nginx/docker ...   Up      0.0.0.0:8082->8080/tcp
```

### How to Use
1. Edit swagger spec with swagger-editor
2. Save swagger spec as json from swagger-editor File menu
3. Move and save the json file as `swagger/openapi.json`
4. Execute `docker-compose restart` and swagger-ui and swagger-api(mock server) will be updated
5. If you want to read an external openapi.json file, import the file from swagger-editor `File > Import File` menu.


### swagger-editor
- Can edit swagger spec
- Can export swagger spec as json, yaml and etc. swagger-ui can read the files and they can be beautifly referenced as documentation. apisprout can read the yml and json then it can serve the mock API.

### swagger-ui
- Can referrence the documentation from swagger spec.
- swagger spec can be assined from json file path or API_URL path.
```
environment:
  SWAGGER_JSON: /openapi.json
  # API_URL: ""
```
- ./swagger/openapi.json is refferenced in this repository

