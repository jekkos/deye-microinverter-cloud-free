FROM node:20-alpine

WORKDIR /app

# Copy package files first for better layer caching
COPY package.json package-lock.json ./

# Install dependencies
RUN npm ci --only=production && npm cache clean --force

# Copy application code
COPY . .

# Set environment variables with defaults
ENV LOGLEVEL="info"
ENV MQTT_BROKER_URL="mqtt://127.0.0.1:1883"

# Expose TCP port for logger connections
EXPOSE 10000

CMD ["npm", "start"]
