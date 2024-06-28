# GraphQL Blog API

## About 

This blog API allows you to manage posts and comments along with the ability to see changes to the latest ones in real time.

## Features

- Each user can carry out the full range of CRUD operations on posts and comments.
- Each user can see changes in relation to posts and comments in real time thanks to subscriptions.

## Technologies

- GraphQL: an open-source data query and manipulation language for APIs and a query runtime engine.
- GraphQL Yoga: the fully-featured GraphQL Server with focus on easy setup, performance and great developer experience.
- Babel: a free and open-source JavaScript transcompiler that is mainly used to convert ECMAScript 2015+ code into backwards-compatible JavaScript code that can be run by older JavaScript engines.

## Getting Started

1. Clone the repository on your local machine.
2. Run `npm install` command to upload all dependencies.
3. Run `npm start` to start the server.
4. Open browser and enter `http://localhost:4000` to start writing queries.

## Queries

### _Users_

Retrieve information about users along with posts and comments that were created by each user. Each post contains informations about itself as well comments that are related to this post. Each comment contains information about itself as well the post under which this comment was created.

```javascript
users {
    id
    name
    email
    age
    posts {
      id
      title
      body
      published
      comments {
        id
        text
        author {
          id
          name
          age
        }
      }
    }
    comments {
      id
      text
      post {
        id
        title
        body
        published
      }
    }
  }
```

### _Posts_

Retrieve informations about all existing posts along with comments that were created under each post. Each post and comment has author field.

```javascript
posts {
    id
    title
    body
    published
    author {
      id
      name
      email
      age
    }
    comments {
      id
      text
      author {
        id
        name
        email
        age
      }
    }
  }
```
