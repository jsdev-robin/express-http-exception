# HTTPException

A custom error class for handling HTTP errors in a structured and operational manner.

## Class Definition

```typescript
export class HTTPException extends Error {
  readonly statusCode: number;
  readonly status: string;
  readonly isOperational: boolean;

  constructor(message: string, statusCode: number) {
    super(message);
    this.statusCode = statusCode;
    this.status = statusCode.toString().startsWith('4') ? 'fail' : 'error';
    this.isOperational = true;
    Error.captureStackTrace(this, this.constructor);
  }
}
```

## Properties

| Property        | Type      | Description                                                                  |
| --------------- | --------- | ---------------------------------------------------------------------------- |
| `statusCode`    | `number`  | The HTTP status code (e.g., 404, 500)                                        |
| `status`        | `string`  | Either `"fail"` (for 4xx client errors) or `"error"` (for 5xx server errors) |
| `isOperational` | `boolean` | Always `true`, indicating this is an expected operational error              |

## Example Usage

```typescript
// Client error (4xx)
const notFound = new HTTPException('Resource not found', 404);
console.log(notFound.statusCode); // 404
console.log(notFound.status); // "fail"
console.log(notFound.message); // "Resource not found"

// Server error (5xx)
const serverError = new HTTPException('Database connection failed', 500);
console.log(serverError.statusCode); // 500
console.log(serverError.status); // "error"
console.log(serverError.isOperational); // true
```
