# Development docker-compose template

This is template for new php project with docker usages. It used to fast pet-project infrastructure set up with docker-compose.

## Dependency 
You need already installed docker-compose:
  
https://github.com/Yelp/docker-compose/blob/master/docs/install.md

## How to use
1. git clone
2. add source code as though it's local project (for example - app directory with some code)
3. check docker-compose configuration
4. go to terminal and run:
```
docker-compose up -d
```

Open you browser by `localhost:8086` (docker-compose.yml section `web`) and it would work now!