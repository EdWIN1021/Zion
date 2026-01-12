# docker-compose.yml

Owner: Edwin

```yaml
version: "3"
services:
  redis-server:
    image: "redis"

  node-app:
    restart: always
    build: .
    ports:
      - "8081:8081"

	web:
			build:
	      context: .
	      dockerfile: Dockerfile.dev
	    ports:
	      - "3000:3000"
	    volumes:
	      - /app/node_modules
	      - ./:/app
			environment:
	      MONGODB_USERNAME: edwin
	      MONGODB_PASSWORD: 8127314
			env_file:
      - ./env/mongo.env
			depends_on:
				   - backend
			networks:
			   - goals-net

volumes:
  data:
  logs:
```

###