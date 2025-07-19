# Use a specific version of the Node.js base image for stability
FROM node:24.4

# Set a non-root user for security
RUN useradd --create-home appuser

# Set the working directory
WORKDIR /app

# Copy only the package files first to leverage Docker's caching mechanism
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Change ownership of the application files to the non-root user
RUN chown -R appuser:appuser /app

# Switch to the non-root user
USER appuser

# Expose the application port
EXPOSE 8080

# Define the default command to run the application
CMD ["node", "server.js"]