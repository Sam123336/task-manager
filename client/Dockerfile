# Use Node.js base image
FROM node:18 as client

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the app
COPY . .

# Expose port for the client
EXPOSE 80

# Run the client app
CMD ["npm", "start"]
