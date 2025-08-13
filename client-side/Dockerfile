# Node image hỗ trợ multi-arch, không cần BUILDPLATFORM
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

# Chỉ cài dependencies, tránh dev deps nếu không cần
RUN npm ci

COPY . .

RUN npm run build

EXPOSE 3000

CMD ["npm", "start"]
