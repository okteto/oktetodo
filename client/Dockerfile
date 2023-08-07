# Use an official Node.js runtime as the base image
FROM node:16

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React app
RUN npm run build

# Expose the application port
EXPOSE 3000

ENV REACT_APP_NAME_COLOR blue

# Serve the built app using a static server
CMD [ "npm", "start", "—-host", "0.0.0.0"]