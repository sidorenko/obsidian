Title: {{title}}
Created: {{date:YYYYMMDD}}{{time:HHmm}}
Tags: #docker #angular
__
(ссылка на внешнюю литературу)
### Reference 

1. 

(ссылки/а на родительский топик)
### Zero Links 
1. 

(внутренние ссылки/a)
### Links
1. 



## Content

ng new app
ng build --configuration production


должен быть установлен докер Docker Desctop
запустить его

 docker pull nginx   (в терминале проекта)


добавить код в докер файл в руте

FROM node:latest as builder  
WORKDIR /denali  
COPY /dist/denali /usr/share/nginx/html  
RUN npm i && npm run ng build  
  
FROM nginx:latest  
WORKDIR /usr/share/nginx/html  
RUN rm -rf ./*  
COPY --from=builder denali/dist/denali .  
ENTRYPOINT ["nginx","-g","daemon off;"]

запустить
docker build -t denali .

docker image ls

docker run --rm -it -p 8080:80 angular-nginx
