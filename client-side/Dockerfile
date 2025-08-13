# Node image hỗ trợ multi-arch, không cần BUILDPLATFORM
FROM --platform=linux/arm64 node:20-alpine

WORKDIR /app

# Copy package files và cài dependencies
COPY package*.json ./
RUN npm ci

# Copy toàn bộ source code và build
COPY . .
RUN npm run build

# Stage 2: Serve static files
FROM node:20-alpine
WORKDIR /app

# Cài serve (chỉ cần package này cho production)
FROM --platform=linux/arm64 node:20-alpine

# Copy build output từ stage 1
COPY --from=build /app/dist ./dist

# Expose cổng
EXPOSE 3000

# Chạy serve
CMD ["serve", "-s", "dist", "-l", "3000"]
