# Use official Nginx image
FROM nginx:alpine

# Set working directory
WORKDIR /etc/nginx

# Copy custom nginx configuration as template
COPY deployment/nginx/sites-enabled/default.conf /etc/nginx/templates/default.conf.template

# Expose the container port (matches ECS containerPort)
EXPOSE 8090

# Default env vars (overridden by ECS task definition)
ENV S3_MEDIA_BUCKET=minisass-staging
ENV S3_MEDIA_REGION=af-south-1

# envsubst replaces ${S3_MEDIA_BUCKET} and ${S3_MEDIA_REGION} in the template,
# then starts nginx
CMD ["/bin/sh", "-c", "envsubst '${S3_MEDIA_BUCKET} ${S3_MEDIA_REGION}' < /etc/nginx/templates/default.conf.template > /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'"]
