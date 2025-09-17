**Carbon Route Optimizer - Functional & Technical Specification**

**Executive Summary**

Carbon Route Optimizer is a web-based application that helps users reduce their carbon footprint by comparing multiple route options and selecting the most environmentally efficient path for their journeys. The system leverages Google's routing infrastructure to provide real-time route optimization with AI.

**1\. Functional Specification**

**1.1 User Registration & Authentication**

**Purpose:** Secure user account management with personalized data tracking

**User Flow:**

1. User navigates to registration page
2. Enters name, email, password (minimum 6 characters)
3. System validates unique email and creates account
4. User redirected to login page. If it does not navigate(odd bug) then remove the /login and go to /dashboard.
5. Upon login, JWT token stored in browser cookie (7-day expiration)

**Security Features:**

- Passwords hashed with bcrypt (12 salt rounds)
- JWT tokens for session management
- Protected routes via middleware
- Automatic logout on token expiration

**1.2 Route Optimization**

**Core Functionality:** Users input origin and destination to receive three optimized route options

**Input Requirements:**

- Origin: Text field accepting addresses or landmarks
- Destination: Text field accepting addresses or landmarks
- Vehicle Type: Dropdown selection from 7 preset vehicles

**Vehicle Options:**

| **Vehicle Type** | **CO₂ Emissions (g/km)** |
| --- | --- |
| Electric | 0   |
| Hybrid | 90  |
| Compact Car | 120 |
| Sedan | 150 |
| SUV | 190 |
| Van | 250 |
| Truck | 300 |

**Output - Three Route Options:**

1. **Fastest Route:** Minimizes travel time, typically using highways
2. **Most Efficient:** Minimizes distance and emissions
3. **Balanced Option:** Optimal combination of time and emissions

**Each route displays:**

- Total distance (km)
- Estimated duration (hours and minutes)
- CO₂ emissions (kg)
- CO₂ saved compared to baseline (kg)
- Option to view in Google Maps

**1.3 Dashboard Features**

**Statistics Cards:**

- Total routes optimized (lifetime)
- Total CO₂ emissions saved (kg)
- Total distance traveled (km)
- Environmental equivalents (trees planted)

**Route History:**

- Last 10 optimized routes displayed
- Shows origin, destination, date, savings
- Color-coded optimization type badges

**CO₂ Savings Chart:**

- 7-day trend line graph
- Daily emissions saved visualization
- Responsive to user activity patterns

**1.4 Analytics Page**

**Comprehensive metrics including:**

- Vehicle usage breakdown (pie chart)
- Optimization preference distribution
- Daily/weekly/monthly activity trends
- Environmental impact equivalents:
  - Trees planted equivalent (20kg CO₂ = 1 tree)
  - Gallons of gas saved (2.3kg CO₂ = 1 gallon)
  - Miles optimized

**1.5 Route Comparison Page**

**Enhanced comparison interface:**

- Side-by-side route cards
- Visual recommendation badges
- One-click route selection
- Detailed metrics per route
- Environmental impact summary

**2\. Technical Specification**

**2.1 System Architecture**

**Frontend:**

- Framework: Next.js 14 (App Router)
- Language: TypeScript 5.x
- Styling: Tailwind CSS 3.x
- Components: shadcn/ui (Radix UI based)
- State Management: React useState/useEffect
- Data Visualization: Recharts

**Backend:**

- Runtime: Node.js 18+
- API: Next.js API Routes (serverless functions)
- ORM: Prisma 5.x
- Authentication: Custom JWT implementation

**Database:**

- PostgreSQL 15 (Supabase hosted)
- Connection: PgBouncer pooling (port 6543)
- Connection limit: 1 (serverless optimization)

**2.2 External Integrations**

**Google Routes API:**

- Version: v2 (endpoint)
- Authentication: API Key with domain restrictions
- Rate Limiting: 40,000 requests/month (free tier)
- Field Masks: Optimized response size
- Fallback: Mock data on API failure

**2.3 Security Measures**

- HTTPS only (enforced by Vercel)
- Environment variables for secrets
- API key domain restrictions
- SQL injection prevention (Prisma ORM)
- XSS protection (React default escaping)
- CORS configured for production domain

**2.4 Browser Compatibility**

**Responsive Design:**

- Mobile: 320px minimum width
- Tablet: 768px breakpoint
- Desktop: 1024px+ optimized

**3\. User Interface Specifications**

**3.1 Design System**

**Color Palette:**

- Primary: Green (#10b981)
- Secondary: Blue (#3b82f6)
- Warning: Yellow (#f59e0b)
- Error: Red (#ef4444)
- Neutral: Gray scale

**Typography:**

- Font: Inter
- Headers: Bold, 2xl-3xl
- Body: Regular, base size
- Captions: Small, gray-600

**3.2 Page Structure**

**Public Landing Page:**

- Hero section with value proposition
- Global statistics display
- Feature grid (4 cards)
- How it works (3 steps)
- Call-to-action sections

**Dashboard Layout:**

- Fixed header with navigation
- 3-column grid for stats cards
- 2-column layout for form and charts
- Responsive table for route history

**4\. Deployment & Infrastructure**

**4.1 Hosting**

**Platform:** Vercel

- Automatic deployments from GitHub main branch
- Serverless functions for API routes
- CDN distribution globally
- SSL certificate included

**4.2 Environment Configuration**

**Required Environment Variables:**

- DATABASE_URL: PostgreSQL connection string
- NEXTAUTH_SECRET: JWT signing secret
- NEXTAUTH_URL: Production URL
- GOOGLE_ROUTES_API_KEY: Google Cloud API key

**5\. System Limitations**

- Route calculations limited to driving mode only
- Maximum route distance: ~5,000 km (Google API limitation)
- Historical data retention: Unlimited (may require archiving at scale)
- Concurrent route calculations: Limited by Google API rate limits

**6\. Future Enhancement Considerations**

- Multi-stop route optimization
- Fleet management features
- Mobile native applications
- Public transit integration
- Carbon offset purchasing
- Team/enterprise accounts
- Route scheduling
- API for third-party integrations

This specification represents the current production state of the Carbon Route Optimizer application as deployed at <https://cfo-platform.vercel.app>.