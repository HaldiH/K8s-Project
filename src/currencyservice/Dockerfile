FROM node:20-alpine
WORKDIR /usr/src/app
RUN apk add --no-cache python3 make g++
COPY package*.json ./
RUN npm install --only=production
COPY . .

FROM node:20-alpine
WORKDIR /usr/src/app
COPY --from=0 /usr/src/app .
ARG PORT=7000
ENV PORT=$PORT
EXPOSE $PORT
CMD ["node", "server.js"]