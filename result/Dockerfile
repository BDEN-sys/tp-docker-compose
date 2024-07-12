FROM node:18.12.1-slim AS base
WORKDIR /app
COPY . .
EXPOSE 5000

FROM base AS dev
ENV NODE_ENV=development
RUN npm ci
RUN mv node_modules /node_modules
#CMD [ "/bin/bash" ]
CMD [ "npm","run","dev" ]

FROM base AS prod
ENV NODE_ENV=production
ENV npm_config_cache=/tmp
RUN npm ci --omit=dev
##RUN mv node_modules /node_modules
RUN chown -R 1000:1000 "/tmp"
USER node
CMD [ "npm","start" ]
#CMD ["sleep", "infinity"]