# 💳 Credit Card Reward Maximizer

## 🎯 Overview

**Problem:** Managing multiple credit cards with different reward structures leads to suboptimal card usage and missed rewards. Users lose ₹10,000-15,000 annually due to poor card selection.

**Solution:** An automated recommendation engine that analyzes all your credit cards, calculates expected rewards for each purchase category, and instantly recommends the optimal card.

## ✨ Features

### Core Functionality
- ✅ **Smart Recommendation Engine** - Calculates optimal card based on reward multipliers
- ✅ **Multi-Card Management** - Support unlimited credit cards per user
- ✅ **Dynamic Reward Rules** - Flexible category-based reward multipliers (2x, 5x, 10x points)
- ✅ **Purchase Intent Tracking** - Log and analyze planned purchases
- ✅ **Recommendation History** - Track past recommendations and rewards

### Technical Features
- 🔐 **JWT Authentication** - Secure, stateless authentication
- 🏗️ **Layered Architecture** - Controller-Service-Repository pattern
- 📊 **RESTful APIs** - Standard HTTP methods with proper status codes
- 📝 **Swagger Documentation** - Interactive API testing interface
- ⚡ **Transaction Management** - ACID compliance for financial data
- 🛡️ **Multi-Level Validation** - Entity, service, and controller validation
- 🚨 **Centralized Exception Handling** - Consistent error responses

## 🛠️ Technology Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| **Java** | 17 | Core backend language |
| **Spring Boot** | 3.2.0 | Application framework |
| **Spring Security** | 6.x | Authentication & authorization |
| **Spring Data JPA** | 3.x | Data persistence |
| **Hibernate** | 6.x | ORM framework |
| **MySQL** | 8.0 | Database |
| **JWT** | 0.11.5 | Token-based auth |
| **BCrypt** | - | Password encryption |
| **Swagger/OpenAPI** | 3.0 | API documentation |

## 🚀 Getting Started

### Prerequisites
- Java 17+
- Maven 3.8+
- MySQL 8.0+

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/Mathan-raj7/Credit-Card-Reward-Maximizer.git
   cd credit-card-reward-maximizer
   ```

2. **Setup MySQL Database**
   - Create database: `reward_maximizer`
   - Create user with appropriate privileges

3. **Configure Application**
   - Update `application.properties` with database credentials
   - Set JWT secret key (minimum 256 bits)
   - Configure server port (default: 8080)

4. **Build & Run**
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

5. **Access Swagger UI**
   ```
   http://localhost:8080/swagger-ui.html
   ```

## 📖 Using Swagger UI

Swagger provides an interactive interface to test all APIs without writing code.

### Step-by-Step Testing Guide

#### **Step 1: Register & Authenticate**

1. Open Swagger UI at `http://localhost:8080/swagger-ui.html`
2. Navigate to **Auth Controller** → **POST /api/auth/register**
3. Click **"Try it out"** and enter user details (name, email, password)
4. Execute and copy the JWT token from response
5. Click **"Authorize"** button (🔓 green lock icon at top)
6. Enter: `Bearer <your-jwt-token>` and click **Authorize**

> All subsequent requests will now be authenticated!

#### **Step 2: Add Credit Cards**

1. Go to **Credit Card Controller** → **POST /api/cards**
2. Add your cards with details:
   - Card name (e.g., "HDFC Regalia")
   - Card number, bank name
   - Annual fee, active status
3. Note the `cardId` from each response

#### **Step 3: Define Reward Rules**

1. Go to **Reward Rule Controller** → **POST /api/rewards**
2. Add reward multipliers for each card:
   - **DINING**: 5x points
   - **TRAVEL**: 4x points
   - **GROCERIES**: 3x points
   - **SHOPPING**: 2x points
3. Create multiple rules per card for different categories

#### **Step 4: Create Purchase Intent**

1. Go to **Purchase Intent Controller** → **POST /api/purchases**
2. Enter your planned purchase:
   - Category (e.g., DINING, TRAVEL)
   - Amount (e.g., 5000)
   - Purchase date
3. Note the `intentId` from response

#### **Step 5: Generate Recommendation**

1. Go to **Recommendation Controller** → **POST /api/recommendations/generate**
2. Enter your `userId` and `intentId`
3. Get instant recommendation with:
   - Best card to use
   - Expected reward value
   - Purchase details

#### **Step 6: View History**

1. Go to **GET /api/recommendations/user/{userId}**
2. View all your past recommendations
3. Analyze which cards gave best rewards

### Available Reward Categories

- **DINING** - Restaurants, food delivery
- **GROCERIES** - Supermarkets
- **TRAVEL** - Flights, hotels
- **FUEL** - Petrol, diesel
- **ENTERTAINMENT** - Movies, streaming
- **SHOPPING** - Online/offline retail
- **UTILITIES** - Bills, internet
- **HEALTHCARE** - Medical, pharmacy
- **EDUCATION** - Courses, books
- **DEFAULT** - Other categories

### Testing Tips

✅ **Create multiple cards** with different reward structures to see recommendations in action

✅ **Test different categories** to see which card gets recommended for each

✅ **Try edge cases** like inactive cards, missing rules, or invalid amounts

✅ **Check response codes** - 200/201 = Success, 400 = Bad Request, 401 = Unauthorized

## 📁 Project Structure

```
├── config/          → Security & JWT configuration
├── controller/      → REST API endpoints
├── dto/             → Data transfer objects
├── model/           → JPA entities (database tables)
├── repository/      → Database access layer
├── service/         → Business logic & algorithms
├── util/            → Helper utilities (JWT, validation)
└── exception/       → Error handling
```

**⭐ Star this repo if you find it useful!**

---

**Built with ❤️ using Spring Boot | Maximizing rewards, one transaction at a time**
