# Use the official image as a parent image
FROM node:18.9.1

# Set the working directory
WORKDIR /app

# Copy package.json to the working directory
COPY package.json .

# Install dependencies (skip using the 'node' user for now)
RUN npm install

# Use /tmp as the npm cache directory to avoid permission issues in /app
ENV NPM_CONFIG_CACHE=/tmp/.npm

# Copy the rest of the application code
COPY . .

#ARG REACT_APP_BACKEND_URL
#ENV REACT_APP_BACKEND_URL=$REACT_APP_BACKEND_URL
#RUN npm run build

# Ensure /tmp and /app have proper permissions for any user
RUN chmod -R 777 /app /tmp

# Expose the port
EXPOSE 5173

# Set the default user to whatever OpenShift assigns
USER 1001

# Run the application as the OpenShift-assigned non-root user
CMD ["npm", "run", "dev"]

