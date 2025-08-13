FROM --platform=$BUILDPLATFORM node:20-alpine
WORKDIR /app

# Copy package.json & lock trước
COPY package*.json ./

# Cài dependencies
RUN npm ci

# Copy toàn bộ source code
COPY . .

# Build app
RUN npm run build

# Expose cổng app
EXPOSE 3000

# Start server
CMD ["npm", "start"]
