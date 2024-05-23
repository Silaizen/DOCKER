FROM node:18

EXPOSE 3000


RUN apt update
RUN apt install mc -y


WORKDIR /app

COPY ./src /app

RUN npm install

CMD ["npm", "start"]