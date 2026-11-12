FROM node:18-alpine

WORKDIR /app

COPY package.json ./
RUN npm install --production

COPY . .
RUN mkdir -p /app/data/uploads

ENV PORT=3333
ENV DATA_DIR=/app/data

VOLUME ["/app/data"]

EXPOSE 3333

CMD ["node", "server.js"]
