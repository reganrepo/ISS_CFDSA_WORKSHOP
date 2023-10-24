FROM node:21
LABEL name==dov-bear
WORKDIR /app
COPY main.js .
COPY package.json .
COPY package-lock.json .
COPY public public
COPY views views

ENV PORT=5000 INSTANCE_NAME="Dov Bear" INSTANCE_HASH=242424

RUN npm install

HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
	CMD curl -s -f http://localhost:${PORT}/healthz || exit 1

EXPOSE ${PORT}

ENTRYPOINT node main.js
