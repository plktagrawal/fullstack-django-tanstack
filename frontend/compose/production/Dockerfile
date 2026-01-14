# Build
FROM node:lts-bookworm-slim AS builder
WORKDIR /app

ENV NODE_OPTIONS=--max-old-space-size=3072
RUN corepack enable && corepack prepare pnpm@latest --activate

COPY pnpm-lock.yaml package.json ./
RUN pnpm install --frozen-lockfile --prefer-offline --network-concurrency=1

COPY . .
ENV VITE_CJS_IGNORE_WARNING=true
ENV NITRO_PRESET=node-server
RUN pnpm build

# Runtime
FROM node:lts-bookworm-slim AS runtime
WORKDIR /app
ENV NODE_ENV=production

COPY --from=builder /app/.output ./.output

EXPOSE 3000
CMD ["node", ".output/server/index.mjs"]
