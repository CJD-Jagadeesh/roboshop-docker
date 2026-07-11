FROM node:20
WORKDIR /app
COPY *./jS .
COPY *.json .
ENV REDIS_HOST=redis
ENV CATALOGUE_HOST=catalogue
ENV CATALOGUE_PORT=8080
CMD ["node", "server.js"]