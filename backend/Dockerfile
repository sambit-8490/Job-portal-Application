# Use official Node.js LTS base image
FROM node:16-alpine

# Set working directory in container
WORKDIR /app

# Copy only package files first for layer caching
COPY package*.json ./

# Install dependencies (prod only)
RUN npm ci --only=production

# Copy rest of the source code
COPY . .

# Expose the port your server listens on
EXPOSE 4000

# Set environment variables (optional fallback)
ENV NODE_ENV=production

# Start the app
CMD ["node", "server.js"]
