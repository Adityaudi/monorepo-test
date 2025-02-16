# Base image
FROM node:18-alpine AS builder

# Set working directory
WORKDIR /app

# Copy monorepo files
COPY ../../ ./

# Install dependencies
RUN npm install --global pnpm@latest
RUN npm install --global turbo@latest

RUN pnpm install

# Build web dengan Turbo
RUN pnpm --filter=docs run build

# Production image
FROM node:18-alpine AS runner

# Set working directory
WORKDIR /app

# Copy hasil build
COPY --from=builder /app/apps/web/.next ./.next
COPY --from=builder /app/apps/web/package.json ./package.json

# Install dependencies untuk production
RUN pnpm install --prod

# Expose port dan run app
EXPOSE 3000
CMD ["pnpm", "start"]