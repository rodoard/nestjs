## Solution
 
 1. Uses Sqlite instead of Postgres
 2. Uses Swagger to document API
 3. Uses Prisma Class Generator to bridge between Swagger and Prisma
 4. Uses ValidationPipe/Class Validator to validate user data
 5. Uses Bearer Authorization via a custom ApiKeyGuard to protect api from unauthorized access
 6. Uses a mockPrismaService in e2e tests to mock database
 7. Uses  ExcludeNullInterceptor to remove null values from results


Test files:

```
server\test\app.e2e-spec.ts
server\src\posts\posts.controller.spec.ts
```

Sample .env file:

```
DATABASE_URL="file:./dev.db"

USE_SWAGGER="true"

API_KEYS="KRANE-API"
```

### Assumptions

 1. text_body is optional based on prisma schema and excluded when not set

## Technical Details

Find API Endpoints under `./client/src/commons/constants/index.ts`

```

UPLOAD_POST: "/api/post"

GET_POSTS: "/api/post"

```

  

Client-side `UPLOAD_POST` payload:

```

title: title,

text_body: body,

```

  

Expected returns

`GET_POSTS` should return an array of posts `{Record[]}`

`UPLOAD_POST` should return the newly created post `{Record}`
