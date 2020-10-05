# Use Ionic Image
FROM beevelop/ionic AS ionic

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy app source
COPY . .

# build ionic app
RUN ionic build

# Bind the port that the image will run on
EXPOSE 8080

# Run ionic app using nginx
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html