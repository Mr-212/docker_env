FROM node:16-alpine AS node_dev

# COPY --from=node_dev /usr/local/lib/node_modules /usr/local/lib/node_modules
# COPY --from=node_dev /usr/local/bin/node /usr/local/bin/node
RUN ln -sf /usr/local/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm
RUN npm install --global npx yarn -f