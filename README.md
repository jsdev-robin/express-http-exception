# express-http-exception

[![npm version](https://badge.fury.io/js/express-http-exception.svg)](https://www.npmjs.com/package/express-http-exception)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)

A lightweight, TypeScript-friendly HTTP exception class for Node.js and Express applications. Provides consistent error handling with automatic status categorization and operational error tracking.

## Features

- 🚀 **Simple & Lightweight** - Minimal footprint with zero dependencies
- 📦 **TypeScript Support** - Full type definitions included
- 🔍 **Automatic Status Categorization** - Automatically sets `fail` for 4xx errors and `error` for 5xx errors
- 🛡️ **Operational Error Flag** - Distinguish between operational and programming errors
- 🎯 **Express-Ready** - Designed to work seamlessly with Express error handlers
- 📝 **Stack Trace Support** - Preserves stack traces for easier debugging

## Installation

```bash
npm install express-http-exception
```

```tsx
import { HTTPException } from 'express-http-exception';

// Throw HTTP errors
throw new HTTPException('User not found', 404);
throw new HTTPException('Bad request', 400);
throw new HTTPException('Server error', 500);
```
