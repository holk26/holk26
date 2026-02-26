# ─── Stage 1: Build ───────────────────────────────────────────────────────────
FROM node:20-alpine AS builder

WORKDIR /app

# Install dependencies
COPY package.json package-lock.json* ./
RUN npm ci

# Copy source and build
COPY . .
RUN npm run build

# ─── Stage 2: Serve (lightweight static server) ───────────────────────────────
FROM nginx:1.27-alpine AS server

LABEL maintainer="Homero Cabrera Araque <homero9726@gmail.com>"
LABEL description="Professional CV – Homero Cabrera Araque | Astro static site"

# Copy built static files from builder stage
COPY --from=builder /app/dist /usr/share/nginx/html

# Custom nginx config for SPA-style routing and gzip
RUN printf 'server {\n\
    listen 80;\n\
    listen [::]:80;\n\
    root /usr/share/nginx/html;\n\
    index index.html;\n\
    gzip on;\n\
    gzip_types text/plain text/css application/javascript;\n\
    location / {\n\
        try_files $uri $uri/ /index.html;\n\
    }\n\
}\n' > /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
