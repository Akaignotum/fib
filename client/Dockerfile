#BUILD PHASE , v- as determines a Block for building phase, next FROM will automatically start a new Block
FROM node:alpine as builder 
WORKDIR /app
COPY ./package*.json ./
RUN npm install
COPY . .
RUN npm run build

#RUN PHASE, default command (nginx) will start nginx,
#THIS NGINX IS FOR ROUTING
FROM nginx

#EXPOSE 3000 (CONFIG for porting in AWS EBS)
EXPOSE 3000 
#port3000 Nginx server/DB w/ Prod - React Files
#/client/nginx/default.conf
#THIS NGINX is for DB purposes
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

#port5000 Express Server

COPY --from=builder /app/build /usr/share/nginx/html