# Functional Requirements:

- Create a short URL from log URL.
    - Support aliases
    - Support expiration date
- Redirect user from short URL to long URL.
- Register using Google.

# Non Functional Requirements:

- Low Latency on redirect (indexed database)
- Unsure uniqueness for the short urls

# Core Entities:

## User

- email
- password
- URLS
- CreatedDate
- name
- id

## URL

- id (short url)
- long url
- userId
- experation date
- alias

## Analythics

- id
- urlId
- clicktimestamps
- device
- location
- reffering site

# API

## Authentication

- Registration:
    
    POST `/register` → jwt token
    
    ```java
    {
    	email,
    	name,
    	password,
    }
    ```
    
- Login
    
    POST `/login` → jwt token
    
    ```java
    {
    	email,
    	password
    }
    ```
    

## shorten a url

- **POST** `/urls`  → shortUrl

```bnf
{
	originalUrl,
	alias? (Optional),
	experationTime? (optional)
}
```

- **GET** `/{shortenUrl}`  → redirection to originalUrl

- **DELETE** `/{shortenUrl}` → delete

- **PUT** `/{shortenUrl}` → shortUrl

```java
{
	originalUrl,
	alias? (Optional),
	experationTime? (optional)
}
```

## **Overall system design**

![Screenshot From 2025-03-10 02-11-06](https://github.com/user-attachments/assets/a0ccc8e2-e4aa-4fdd-8b53-6921e945e36a)
