# Dockerfile

Owner: Edwin

```docker
# pull node image from docker hub
FROM node

# create /app fold in container
WORKDIR /app

COPY  ./package.json ./

# install all dependencies into container
RUN npm install

# copy all files  from local_path into container_path
COPY . /app

# container port
EXPOSE 80

ENV MONGODB_USERNAME=edwin  
ENV MONGODB_PASSWORD=8127314

# start server
CMD ["node","server.js"]

#or

# npm run start
CMD [ "npm", "run", "start" ]
```

[Muti Step Build](Dockerfile%209c74fdb0e1934f0ebe1afe4b25656050/Muti%20Step%20Build%20322a03d925b24f87a7542516bce164a1.md)