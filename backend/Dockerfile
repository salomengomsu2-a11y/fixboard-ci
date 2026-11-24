FROM node:22-slim

WORKDIR /app

COPY package*.json ./
RUN npm install --omit=dev \
 && rm -rf /usr/local/lib/node_modules/npm \
           /usr/local/lib/node_modules/corepack \
           /usr/local/bin/npm \
           /usr/local/bin/npx \
           /usr/local/bin/corepack

COPY . .

RUN groupadd --gid 1001 nodejs \
 && useradd  --uid 1001 --gid nodejs --shell /bin/bash --create-home nodeuser \
 && mkdir -p /app/uploads \
 && chown -R nodeuser:nodejs /app/uploads

USER nodeuser

EXPOSE 3000

CMD ["node", "src/server.js"]