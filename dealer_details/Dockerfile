FROM node:20-bookworm-slim AS builder

# Stage 1: Build dependencies
WORKDIR /app
COPY package.json .
RUN npm install

# Stage 2: Copy application code
COPY server.js server.js
COPY utils/dealers.json utils/dealers.json

# Stage 3: Final image
FROM node:22-bookworm-slim

WORKDIR /app
COPY --from=builder /app/node_modules /app/node_modules
COPY . .

EXPOSE 8080
CMD ["npm", "start"]
