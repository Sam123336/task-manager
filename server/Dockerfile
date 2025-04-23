# Use Node.js base image
FROM node:18 as server

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the app
COPY . .

# Expose port for the server
EXPOSE 5000

# Run the server app
CMD ["npm", "start"]
