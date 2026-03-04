Generate a Next.js App Router API route handler.

Arguments: $ARGUMENTS (format: "route-path [HTTP methods] [description]", e.g. "api/posts GET,POST CRUD for blog posts")

Instructions:
1. Parse $ARGUMENTS to extract the route path, HTTP methods (default GET), and description.
2. Create `app/<route-path>/route.ts`.
3. Export a typed handler function for each specified method (GET, POST, PUT, PATCH, DELETE).
4. Use `NextRequest` and `NextResponse` from `next/server`.
5. For routes with path params, use the `{ params }: { params: { id: string } }` second argument pattern.
6. Validate request bodies with Zod for POST/PUT/PATCH. Return 400 with validation errors on failure.
7. Return appropriate HTTP status codes: 200/201 for success, 400 for bad input, 404 for not found, 500 for server errors.
8. Add a comment block at the top of the file documenting the endpoint contract (method, path, body, response shape).
9. Output the complete file contents labeled with its path.
