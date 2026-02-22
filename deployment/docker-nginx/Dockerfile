# Use official Nginx image
FROM nginx:alpine

# Set working directory
WORKDIR /etc/nginx

# Copy custom nginx configuration
COPY deployment/nginx/sites-enabled/default.conf /etc/nginx/conf.d/default.conf

# # Ensure directories exist for static/media/minio mounts
# RUN mkdir -p /home/web/static /home/web/media /home/web/minio

# Expose the container port (matches ECS containerPort)
EXPOSE 8090

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]