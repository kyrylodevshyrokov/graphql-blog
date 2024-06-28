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

### _Comments_

Retrieve information about all existing comments along with posts under which this comments were created.

```javascript
comments {
    id
    text
    author {
      id
      name
      email
      age
    }
    post {
      id
      title
      body
      published
    }
  }
```

## Mutations

### _createUser_

Creates a new user.

```javascript
createUser(data: {
    name: "John Doe"
    email: "john@gmail.com"
    age: 22
  }) {
    id
    name
    email
    age
  }
```

### _updateUser_

Updates the user.

```javascript
updateUser(id: "your_user_id", data: {
    name: "John Doe 2"
    age: 40
  }) {
    id
    name
    email
    age
  }
```

### _deleteUser_

Deletes the user.

```javascript
deleteUser(id: "your_user_id") {
    id
    name
    email
    age
  }
```

### _createPost_

Creates new post.

```javascript
createPost(data: {
    title: "New post"
    body: "THis is a new post"
    published: true
    author: "your_author_id"
  }) {
    id
    title
    body
    published
    author {
      id
      name
      email
    }
  }
```

### _updatePost_

Updates the post.

```javascript
updatePost(id: "your_post_id" data: {
    title: "Updated post"
    body: "This is the updated post"
    published: false
  }) {
    id
    title
    body
    published
  }
```

### _deletePost_

Deletes the post.

```javascript
  deletePost(id: "your_post_id") {
    id
    title
    body
    published
  }
```

### _createComment_

Creates new comment.

```javascript
createComment(data: {
    text: "Nice post!"
    post: "your_post_id"
    author: "your_user_id"
  }) {
    id
    text
    author {
      id
      name
    }
    post {
      id
      title
    }
  }
```

### _updateComment_

Updates the comment.

```javascript
updateComment(id: "your_comment_id" data: {
    text: "Updated comment to post"
  }) {
    id
    text
  }
```

### _deleteComment_

Deletes the comment.

```javascript
deleteComment(id: "your_comment_id") {
    id
    text
  }
```
