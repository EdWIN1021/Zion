# Muti Step Build

Owner: Edwin

```docker
FROM node:16-alpine as builder

WORKDIR /app

COPY  ./package.json ./

RUN npm install

COPY ./ ./

CMD [ "npm", "run", "build" ]

From nginx

COPY --from=builder /app/build /usr/share/ngnix/html
```