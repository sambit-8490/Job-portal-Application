FROM node:16-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Step 2: Serve the app with a lightweight web server
FROM nginx:stable-alpine

# Copy built assets from the builder
COPY --from=builder /app/dist /usr/share/nginx/html

# Copy custom nginx config (optional, if needed)
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
