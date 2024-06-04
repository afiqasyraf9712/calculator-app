# Stage 1: Install dependencies
FROM node:13-alpine3.11 AS installer

# Create app directory
RUN mkdir /app
WORKDIR /app

# Install app dependencies
COPY package.json /app/
RUN npm install

# Stage 2: Build the application
FROM node:13-alpine3.11

# Create app directory
RUN mkdir /app
WORKDIR /app

# Copy application files
COPY public /app/public
COPY index.js /app
COPY counter.js /app
COPY defaultMetrics.js /app
COPY gauge.js /app
COPY histogram.js /app
COPY summary.js /app

# Copy the node_modules and package.json from the installer stage
COPY --from=installer /app/package.json .
COPY --from=installer /app/node_modules ./node_modules

# Expose the application port
EXPOSE 8080

# Command to run the application
CMD ["npm", "start"]
