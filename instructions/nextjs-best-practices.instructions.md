---
applyTo: "**/*.{tsx,ts,jsx,js}"
---

# Next.js Best Practices and Standards

**Purpose** – Enforce consistent Next.js development patterns, performance optimizations, and modern full-stack practices.

**Guidelines:**
- Use App Router (app directory) over Pages Router
- Server Components by default, Client Components ('use client') only when needed
- TypeScript with strict mode for type safety
- Proper metadata for SEO optimization
- next/image for optimized images
- NextAuth.js for authentication
- Zod for input validation
- Proper error handling with error.tsx files
- React Suspense for loading states
- Middleware for route protection

**When to Apply:**
1. Component/page creation
2. API route development
3. Data fetching implementation
4. Authentication setup
5. Performance optimization
6. SEO implementation
7. Testing and deployment

**Project Structure:**
```
app/
├── layout.tsx              # Root layout
├── page.tsx                # Home page
├── loading.tsx             # Loading UI
├── error.tsx               # Error UI
├── (auth)/                 # Route groups
│   ├── login/page.tsx
│   └── register/page.tsx
├── dashboard/
│   ├── layout.tsx
│   ├── page.tsx
│   └── settings/page.tsx
├── api/                    # API routes
│   ├── auth/route.ts
│   └── users/route.ts
components/
├── ui/                     # Reusable UI components
├── forms/                  # Form components
└── layout/                 # Layout components
lib/
├── auth.ts                 # Authentication
├── db.ts                   # Database
└── utils.ts                # Utilities
middleware.ts               # Next.js middleware
```

**Key Patterns:**

**Server Component:**
```tsx
export const metadata = { title: 'Dashboard' };

export default async function DashboardPage() {
  const session = await getServerSession(authOptions);
  if (!session) redirect('/login');

  return (
    <div>
      <h1>Dashboard</h1>
      <Suspense fallback={<div>Loading...</div>}>
        <UserProfile userId={session.user.id} />
      </Suspense>
    </div>
  );
}
```

**Client Component:**
```tsx
'use client';
import { useState } from 'react';

export function SearchBox({ onSearch }: { onSearch: (q: string) => void }) {
  const [query, setQuery] = useState('');

  return (
    <input
      value={query}
      onChange={(e) => setQuery(e.target.value)}
      onKeyDown={(e) => e.key === 'Enter' && onSearch(query)}
    />
  );
}
```

**API Route:**
```typescript
import { NextRequest, NextResponse } from 'next/server';
import { getServerSession } from 'next-auth';
import { z } from 'zod';

const schema = z.object({ email: z.string().email() });

export async function POST(request: NextRequest) {
  const session = await getServerSession();
  if (!session) return NextResponse.json({ error: 'Unauthorized' }, { status: 401 });
  
  const body = await request.json();
  const { email } = schema.parse(body);
  
  // Process request
  return NextResponse.json({ success: true });
}
```

**Middleware:**
```typescript
import { withAuth } from 'next-auth/middleware';

export default withAuth({
  callbacks: {
    authorized: ({ token, req }) => {
      return req.nextUrl.pathname.startsWith('/admin') 
        ? token?.role === 'admin' 
        : !!token;
    },
  },
});
```

**Performance & SEO:**
- Use `next/image` with proper sizes
- Implement `loading.tsx` and `error.tsx`
- Generate metadata for each page
- Use proper heading hierarchy (h1, h2, h3)
- Implement structured data (JSON-LD)
- Optimize Core Web Vitals

**Security:**
- Validate inputs with Zod
- Use environment variables for secrets
- Implement proper CORS
- Use HTTPS in production
- Implement rate limiting

**Output Format:**
- TypeScript with proper types
- Consistent naming conventions
- Proper error boundaries
- Accessibility compliance
- SEO optimization
