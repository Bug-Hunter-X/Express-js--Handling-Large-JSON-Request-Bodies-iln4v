# Express.js: Handling Large JSON Request Bodies

This repository demonstrates a common issue in Express.js applications where large JSON request bodies are not properly parsed due to the default body-parser limit.  The `bug.js` file shows the flawed code, while `bugSolution.js` provides the solution.

## Problem

When sending large JSON payloads to an Express.js app, `req.body` may be empty if the request exceeds the default body-parser limit (100kb by default).  This leads to unexpected errors and makes the application unreliable for handling large datasets.

## Solution

The solution involves setting a larger body-parser limit using `express.json({ limit: '10mb' })`. This ensures that larger JSON requests are properly parsed.

## How to reproduce

1. Clone this repository.
2. Run `npm install` to install Express.js
3. Run `node bug.js`.
4. Send a large JSON payload (larger than 100kb) to the `/data` endpoint using a tool like Postman.
5. Observe that `req.body` is empty.
6. Run `node bugSolution.js`
7. Repeat step 4 and observe that `req.body` now contains the expected data.