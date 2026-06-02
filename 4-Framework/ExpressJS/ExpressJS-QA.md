# ExpressJS – Interview Q&A

## � BASIC

**Q:** What is Express.js?
**A:** Node.js web framework for building web servers and APIs. Lightweight, flexible. Handles routing, middleware, HTTP request/response. Industry standard for Node.js backend development.

**Q:** What are key features of Express?
**A:** Routing (define endpoints), middleware (process requests), template engines, static files, error handling, built-in JSON support, environment variables, scalable architecture.

**Q:** What is a route in Express?
**A:** Maps HTTP method + URL path to handler function. Syntax: `app.get('/path', (req, res) => {})`. Methods: GET, POST, PUT, DELETE, PATCH. Handles requests to specific endpoints.

**Q:** What is middleware?
**A:** Function processing request before reaching route handler. Syntax: `app.use((req, res, next) => {})`. Can modify request/response. Call `next()` to pass to next middleware. Used for logging, auth, validation.

**Q:** What is the difference between `app.use()` and `app.get()`?
**A:** `app.use()`: middleware applies to all routes. `app.get()`: route handler for specific GET endpoint. Order matters: middleware first, then routes. `app.use()` can be path-specific.

**Q:** What are HTTP methods?
**A:** GET (retrieve), POST (create), PUT (update entire), PATCH (partial update), DELETE (remove). Express routes for each. RESTful API uses appropriate methods.

**Q:** What is Express Router?
**A:** Modularize routes. Create mini-app: `const router = express.Router()`. Define routes: `router.get('/', handler)`. Export and use: `app.use('/api', router)`. Organize large apps.

**Q:** What is request object (req)?
**A:** Contains request data. `req.params`: URL parameters. `req.query`: query string. `req.body`: POST data. `req.headers`: HTTP headers. `req.method`: HTTP method.

**Q:** What is response object (res)?
**A:** Send response to client. `res.send()`: send data. `res.json()`: send JSON. `res.status()`: set HTTP status. `res.sendFile()`: send file. `res.redirect()`: redirect URL.

**Q:** What is status code?
**A:** HTTP response code indicating request result. 200: success. 201: created. 400: bad request. 401: unauthorized. 403: forbidden. 404: not found. 500: server error.

**Q:** What is error handling?
**A:** Catch and handle errors gracefully. Try-catch for sync errors. `.catch()` for promises. Error middleware: `(err, req, res, next) => {}`. Send error response to client.

**Q:** What is environment variable?
**A:** Configuration value from process.env. Stored in `.env` file. `dotenv` package loads. Different values for dev/production. Never commit `.env` to git.

---

## � INTERMEDIATE

**Q:** What are async/await in Express?
**A:** Handle asynchronous operations. `async` function returns promise. `await` pauses until resolved. Cleaner than callbacks/promises. Error handling with try-catch.

**Q:** What is CORS (Cross-Origin Resource Sharing)?
**A:** Security feature allowing cross-origin requests. Browser blocks by default. `cors` package enables. Specify allowed origins, methods, headers. Required for frontend/backend on different ports.

**Q:** What is authentication?
**A:** Verify user identity. Username/password, JWT token, OAuth. Express middleware for auth check. Routes protected: redirect if unauthorized. Sessions or tokens store auth state.

**Q:** What is authorization?
**A:** Verify user has permission for action. Role-based access control (RBAC). Admin vs user permissions. Middleware checks role. Different from authentication (identity vs permission).

**Q:** What is JWT (JSON Web Token)?
**A:** Token format for stateless authentication. Header.Payload.Signature. `jsonwebtoken` package encodes/decodes. Send in request headers. Server verifies signature without session lookup.

**Q:** What is session management?
**A:** Maintain user state across requests. `express-session` stores session data. Session ID sent as cookie. Server-side session data lookup. Stateful (vs JWT stateless).

**Q:** What is cookie?
**A:** Small data sent with each request. Set-Cookie header. Client-side storage. Auto-sent to matching domain. `res.cookie()`, `req.cookies` access. Secure, httpOnly flags available.

**Q:** What is validation?
**A:** Check request data correctness. `joi`, `validator.js` packages. Validate types, required fields, format. Return error if invalid. Server-side validation essential (client can be bypassed).

**Q:** What is sanitization?
**A:** Clean user input removing malicious content. Prevent XSS, SQL injection. `express-validator` package. Trim, escape, lowercase. Before storing data.

**Q:** What is rate limiting?
**A:** Limit requests per user/IP. Prevent abuse, DDoS. `express-rate-limit` package. Set max requests per timeframe. Return 429 status if exceeded.

**Q:** What is logging?
**A:** Record application events. `morgan` for HTTP logs. `winston`, `pino` for app logs. Log levels: error, warn, info, debug. Essential for debugging, monitoring.

**Q:** What is the difference between PUT and PATCH?
**A:** PUT: replace entire resource. PATCH: partial update. PUT: requires all fields. PATCH: only changed fields. Both modify resources. Use appropriately per REST principles.

**Q:** What is REST API?
**A:** Architectural style for APIs. HTTP methods represent operations. URLs represent resources. Stateless. JSON for data. RESTful API: follows REST principles. Standard for modern APIs.

**Q:** Real-life (Indian fintech): Implement secure login with JWT?
**A:** User submits credentials. Validate against database. Generate JWT with user ID, expiry. Send in response. Client stores token. Send token in Authorization header. Server verifies on each request.

**Q:** Real-life: Handle file uploads?
**A:** `multer` middleware for uploads. Save to server or cloud (S3). Validate file type, size. Return file URL. Handle errors (too large, invalid type). Secure from malicious uploads.

---

## � ADVANCED

**Q:** What is middleware chaining?
**A:** Multiple middleware execute in order. Each calls `next()` to proceed. Early exit possible without calling `next()`. Flexible request processing pipeline. Error middleware at end catches all.

**Q:** What is error handling middleware?
**A:** Catches errors from routes/middleware. Signature: `(err, req, res, next) => {}`. Must have 4 parameters (Express identifies as error handler). Log error, send response. Place last in app.

**Q:** What is request validation middleware?
**A:** Validate request before route handler. Check body, params, query. `express-validator` for implementation. Return error if invalid. Protects routes from bad data.

**Q:** What is compression?
**A:** Reduce response size. `compression` middleware gzips responses. Smaller payload = faster transfer. Enable in production. Transparent to client.

**Q:** What is caching strategies?
**A:** Store computed results. HTTP caching: ETags, Cache-Control headers. Application caching: Redis. Reduce database queries. Set appropriate expiry. Balance freshness vs performance.

**Q:** What is connection pooling?
**A:** Reuse database connections. Don't create new per request (expensive). Pool maintains connections. `pg-pool` for PostgreSQL. Improves performance significantly. Configure pool size.

**Q:** What is database transactions?
**A:** Execute multiple queries atomically. All succeed or all fail. Prevents data inconsistency. `BEGIN TRANSACTION`, `COMMIT`, `ROLLBACK`. Important for critical operations (payments).

**Q:** What is API versioning?
**A:** Support multiple API versions. `/api/v1/`, `/api/v2/` endpoints. Gradual deprecation of old versions. Backward compatibility. Headers alternative: `Accept: application/vnd.api+json;version=1`.

**Q:** What is load balancing?
**A:** Distribute requests across multiple servers. Nginx, HAProxy. Improves performance, availability. Session persistence for stateful apps. Scaling horizontally.

**Q:** What is horizontal vs vertical scaling?
**A:** Vertical: more powerful server (limited). Horizontal: more servers with load balancer (recommended). Redundancy, reliability. Cloud-native approach.

**Q:** What is containerization with Docker?
**A:** Package app + dependencies in container. Dockerfile defines image. Run consistent environments. `docker-compose` for multi-container apps. Easy deployment, scaling.

**Q:** What is CI/CD pipeline?
**A:** Continuous Integration: auto test on commits. Continuous Deployment: auto deploy to production. Tools: GitHub Actions, Jenkins, GitLab CI. Faster, safer releases.

**Q:** What is monitoring and alerting?
**A:** Track application health. Metrics: response time, error rate, CPU, memory. Tools: DataDog, New Relic, Prometheus. Alerts for anomalies. Quick issue detection.

**Q:** Real-life (Indian payment gateway): Build PCI-DSS compliant API?
**A:** Never handle card data directly. Use tokenization service. Validate all inputs. Use HTTPS. Encrypt sensitive data. Log transactions. Rate limiting for security. Regular security audits.

**Q:** Real-life: Implement webhook system?
**A:** Store webhook URLs for clients. Trigger events (payment success). POST to stored URLs with data. Retry on failure with exponential backoff. Verify signature for security.

**Q:** Real-life: Handle background jobs?
**A:** Use job queue (Bull, RabbitMQ). Long-running tasks: file processing, emails, reports. Async execution. Worker processes handle jobs. Retry failed jobs. Monitor queue.

**Q:** Calculation: API handling 10,000 requests/sec. Response time 100ms each. Without caching: 10,000 × 100ms = 1,000,000ms = 1000s needed. With caching: 90% cache hit = 1,000 DB queries × 100ms = 100s total. Massive improvement (10x faster).

**Q:** Calculation: Server with 4GB RAM, each request uses 1MB (sessions, data). Without connection pooling: 4,000 concurrent requests max. With connection pooling and caching: 10,000+ concurrent requests. Better resource utilization.

---

## 📋 Quick Reference

| Method         | Purpose      |
| -------------- | ------------ |
| `app.use()`    | Middleware   |
| `app.get()`    | GET route    |
| `app.post()`   | POST route   |
| `app.put()`    | PUT route    |
| `app.delete()` | DELETE route |
| `app.patch()`  | PATCH route  |

| Object | Property                     |
| ------ | ---------------------------- |
| req    | params, query, body, headers |
| res    | send, json, status, redirect |

| Status Code | Meaning      |
| ----------- | ------------ |
| 200         | OK           |
| 201         | Created      |
| 400         | Bad Request  |
| 401         | Unauthorized |
| 403         | Forbidden    |
| 404         | Not Found    |
| 500         | Server Error |

| Package             | Purpose          |
| ------------------- | ---------------- |
| `cors`              | Enable CORS      |
| `jsonwebtoken`      | JWT auth         |
| `express-validator` | Validation       |
| `multer`            | File uploads     |
| `helmet`            | Security headers |
