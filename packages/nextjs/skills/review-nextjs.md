Review the current file or selection for Next.js best-practice violations.

Arguments: $ARGUMENTS (optional file path — if omitted, review the currently open/active file)

Instructions:
1. Read the target file (from $ARGUMENTS or ask the user which file to review).
2. Evaluate against these rule categories and flag any violations:
   - **Router**: Is App Router used? Are route files named correctly?
   - **Server vs Client**: Is `"use client"` used unnecessarily? Could any Client Component be a Server Component?
   - **Data fetching**: Is `useEffect` used for data fetching? Are cache options set on `fetch()`?
   - **TypeScript**: Are there any implicit `any` types, missing interfaces, or untyped props?
   - **Images/Fonts**: Is `next/image` used? Is `next/font` used instead of CSS imports?
   - **Performance**: Are there unnecessary `"use client"` boundaries, barrel file imports, or disabled lazy loading?
   - **Error handling**: Are `notFound()` and `redirect()` used from `next/navigation`?
   - **Environment variables**: Are secrets accidentally prefixed with `NEXT_PUBLIC_`?
3. For each violation, output:
   - Line number(s)
   - Rule violated
   - Suggested fix (with corrected code snippet)
4. Conclude with a summary: number of issues found per category, and an overall assessment (Pass / Needs Work / Significant Issues).
