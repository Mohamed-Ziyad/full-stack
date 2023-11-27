FROM node:16-alpine as builer
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/defult.conf /etc/nginx/conf.d/default.conf
COPY --from=builer ./app/build /user/share/nginx/html

CMD ["npm", "run", "start"]