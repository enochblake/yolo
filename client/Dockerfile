# Stage 1: Build stage
FROM node:16-alpine AS build

# Set working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package*.json ./

# Install only production dependencies
RUN npm install --only=production

# Install webpack and react-scripts separately (these can be dev dependencies)
RUN npm install webpack@latest react-scripts@latest

# Copy all application source code
COPY . .

# Uncomment this if you need to build a production-ready version of the app
# RUN npm run build

# Stage 2: Final stage (lighter image for running the app)
FROM node:16-alpine

# Set working directory
WORKDIR /app

# Copy only the necessary built files from the previous stage
COPY --from=build /app /app

# Expose the application port
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
