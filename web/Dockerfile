FROM node:20-slim
ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"
RUN corepack enable

WORKDIR /app
COPY . .

# Installation et Build du monorepo
RUN pnpm install
RUN pnpm --filter @imput/cobalt-web build

# Utilisation d'un serveur léger pour servir le dossier build
RUN pnpm add -g serve
EXPOSE 3000
CMD ["serve", "-s", "web/build", "-l", "3000"]