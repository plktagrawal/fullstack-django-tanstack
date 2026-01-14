FROM node:lts-bookworm-slim

ARG APP_HOME=/app

WORKDIR ${APP_HOME}

# RUN apt-get update && apt-get install
RUN corepack enable && corepack prepare pnpm@latest --activate

COPY package.json pnpm-lock.yaml ./

RUN pnpm install

COPY . .

EXPOSE 3000

CMD ["pnpm", "dev", "--host", "0.0.0.0", "--port", "3000"]