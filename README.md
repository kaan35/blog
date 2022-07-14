## Description

Blog CMS(Content Management System).

## Getting Started

Blog is a JavaScript, TypeScript, NestJs, Angular, MongoDB based project. A local development environment is available to quickly get up and
running.
This project based on 4 services

- Rest API
    - It is responsible for all data transfer between client and database.
    - It is build with Nest.js framework
- Client
    - It is public frontend web page for visitors.
    - It is build with Angular framework
- Admin
    - It will be control panel for this system. You will manage all data on this web page.
- Database
    - It stores all data related with blog system.
    - All data stored in MongoDB.

## Requirements

- Node.js
    - You will need Node.js and npm installed on your computer to build and update dependencies.
    - macOS: [Node.js download page](https://nodejs.org/en/download/)
    - Windows: [Node.js download page](https://nodejs.org/en/download/)
    - Arch Linux: `pacman -Sy nodejs npm`

- Docker
    - You will need Docker Engine installed on your computer to build and run services.
    - macOS: [Docker Desktop for macOS download page](https://docs.docker.com/desktop/mac/install/)
    - Windows: [Docker Desktop for Windows download page](https://docs.docker.com/desktop/windows/install/)
      installers and binaries.
    - Arch Linux:
  ````
  pacman -Sy docker docker-compose
  systemctl start docker && sudo systemctl enable docker
  usermod -aG docker $USER
  ````

## Installation for development

- To start the development environment for the first time after these steps completed you can visit web page.
    - For public page [http://localhost](http://localhost)
    - For API [http://localhost:81](http://localhost:81)
  ```
  git clone https://github.com/kaan35/blog.git
  cd blog
  git clone https://github.com/kaan35/blog-api.git
  git clone https://github.com/kaan35/blog-client.git
  cp .env.sample .env
  mv blog-client/ client/
  mv blog-api/ api/
  cd api
  cp .env.sample .env
  # Update database config in .env file 
  # DATABASE_URL='mongodb://<host>:<port>/<database>'
  npm i
  cd ..
  cd client
  cd src/environments/
  mv environment.dev.sample.ts environment.dev.ts
  mv environment.prod.sample.ts environment.prod.ts
  # Update api url in environment files
  # apiUrl: 'API_URL',
  cd .. && cd ..
  npm i
  cd ..
  docker compose up
  ```

## Installation for production

- To start the production environment for the first time after these steps completed you can visit web page with server side rendered at
  same address with development environment.

  ```
  git clone https://github.com/kaan35/blog.git
  cd blog
  git clone https://github.com/kaan35/blog-api.git
  git clone https://github.com/kaan35/blog-client.git
  cp .env.sample .env
  # Change env=dev to env=prod in .env file
  mv blog-client/ client/
  mv blog-api/ api/
  cd api
  cp .env.sample .env
  # Update database config in .env file 
  # DATABASE_URL='mongodb://<host>:<port>/<database>'
  npm install --omit=dev
  cd ..
  cd client
  cd src/environments/
  mv environment.dev.sample.ts environment.dev.ts
  mv environment.prod.sample.ts environment.prod.ts
  # Update api url in environment files
  # apiUrl: 'API_URL',
  cd .. && cd ..
  npm install --omit=dev
  npm run build:ssr
  cd ..
  docker compose up
  ```

## Sample Data

- To start with sample blog data you can run these commands on MongoDB shell.
- If you want to run these commands on GUI. You can install [MongoDB Compass](https://www.mongodb.com/try/download/compass)

### Sample Articles

````
db.articles.insertMany(
  [
    {
      title: 'Lorem Ipsum is simply dummy text 1',
      content: 'hello world',
      slug: 'lorem-ipsum-is-simply-dummy-text-1',
      comments: [
        {
          _id: ObjectId("629520ba2fdd2616e3694a22"),
          firstname: "John",
          lastname: "Walker",
          data: 'Hello World',
        },
      ],
      publishStatus: "published",
      publishDate: "17/06/2022",
      publishDateTimeStamp: "2022-06-17T16:51:18.582Z",
      createDate: "17/06/2022",
      createDateTimeStamp: "2022-06-17T16:51:18.582Z",
      updateDate: "17/06/2022",
      updateDateTimeStamp: "2022-06-17T16:51:18.582Z",
      author: {
        _id: ObjectId("629520ba2fdd2616e3694a21"),
        firstname: "James",
        lastname: "Thomson",
      },
    },
    {
      title: 'Lorem Ipsum is simply dummy text 2',
      content: 'hello world',
      slug: 'lorem-ipsum-is-simply-dummy-text-2',
      publishStatus: "published",
      publishDate: "17/06/2022",
      publishDateTimeStamp: "2022-06-17T16:51:18.582Z",
      createDate: "17/06/2022",
      createDateTimeStamp: "2022-06-17T16:51:18.582Z",
      updateDate: "17/06/2022",
      updateDateTimeStamp: "2022-06-17T16:51:18.582Z",
      author: {
        _id: ObjectId("629520ba2fdd2616e3694a22"),
        firstname: "John",
        lastname: "Walker",
      },
    },
    {
      title: 'Lorem Ipsum is simply dummy text 2',
      content: 'hello world',
      slug: 'lorem-ipsum-is-simply-dummy-text-2',
      publishStatus: "published",
      publishDate: "17/06/2022",
      publishDateTimeStamp: "2022-06-17T16:51:18.582Z",
      createDate: "17/06/2022",
      createDateTimeStamp: "2022-06-17T16:51:18.582Z",
      updateDate: "17/06/2022",
      updateDateTimeStamp: "2022-06-17T16:51:18.582Z",
      author: {
        _id: ObjectId("629520ba2fdd2616e3694a23"),
        firstname: "David",
        lastname: "Paterson",
      },
    },
    {
      title: 'Lorem Ipsum is simply dummy text 2',
      content: 'hello world',
      slug: 'lorem-ipsum-is-simply-dummy-text-2',
      publishStatus: "published",
      publishDate: "17/06/2022",
      publishDateTimeStamp: "2022-06-17T16:51:18.582Z",
      createDate: "17/06/2022",
      createDateTimeStamp: "2022-06-17T16:51:18.582Z",
      updateDate: "17/06/2022",
      updateDateTimeStamp: "2022-06-17T16:51:18.582Z",
      author: {
        _id: ObjectId("629520ba2fdd2616e3694a24"),
        firstname: "Diana",
        lastname: "Clark",
      },
    },
  ]);
````

### Sample Authors

````
db.authors.insertMany(
  [
    {
      _id: ObjectId("629520ba2fdd2616e3694a21"),
      firstname: "James",
      lastname: "Thomson",
      email: 'info@jamesthomson.com',
      activationStatus: 'active',
    },
    {
      _id: ObjectId("629520ba2fdd2616e3694a22"),
      firstname: "John",
      lastname: "Walker",
      email: 'info@johnwalker.com',
      activationStatus: 'active',
    },
    {
      _id: ObjectId("629520ba2fdd2616e3694a23"),
      firstname: "David",
      lastname: "Paterson",
      email: 'info@davidpeterson.com',
      activationStatus: 'active',
    },
    {
      _id: ObjectId("629520ba2fdd2616e3694a24"),
      firstname: "Diana",
      lastname: "Clark",
      email: 'info@dianaclark.com',
      activationStatus: 'active',
    },
  ],
  );
````

### Sample Pages

````
db.pages.insertMany(
  [
     {
      "title": "About Me",
      "slug": "about-me",
      "content": "<p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>",
      "createDate": "17/06/2022",
      "createDateTimeStamp": "2022-06-17T16:51:18.582Z",
      "publishDate": "17/06/2022",
      "publishDateTimeStamp": "2022-06-17T16:51:18.582Z",
      "publishStatus": "published",
      "updateDate": "17/06/2022",
      "updateDateTimeStamp": "2022-06-17T16:51:18.582Z",
    }
  ],
  );
````