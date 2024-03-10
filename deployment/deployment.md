# Deployment Steps

# 1. Prepare Your Application
npm run build

# 2. Vercel Deployment (Using Vercel CLI)
npm install -g vercel
vercel --prod

# 3. Traditional Web Servers
# Copy the contents of the ./out directory (or the directory specified in your Next.js configuration) to your server
# Configure your web server to serve the Next.js application

# Example Nginx configuration
cat <<EOF > /etc/nginx/sites-available/nextjs
server {
    listen 80;
    server_name your-domain.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
EOF

# Enable the configuration and restart Nginx
ln -s /etc/nginx/sites-available/nextjs /etc/nginx/sites-enabled/
systemctl restart nginx

# 4. Docker Containers
# Create a Dockerfile in the root of your Next.js project
cat <<EOF > Dockerfile
# Dockerfile
FROM node:alpine

WORKDIR /app

COPY package.json .
COPY yarn.lock .

RUN yarn install

COPY . .

RUN yarn build

CMD ["yarn", "start"]
EOF

# Build the Docker image
docker build -t your-image-name .

# Run the Docker container
docker run -p 3000:3000 your-image-name

# 5. Continuous Deployment (Optional)
# Set up continuous deployment with Vercel or Git repository integrations
