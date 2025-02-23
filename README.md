# Installation

You need to have `git` and `node` intalled in your system to run the project

```bash
git clone https://github.com/nthalt/hotel-backend.git
```

```bash
cd hotel-backend
```

```bash
npm install
```

# Config JSON setup

Create a file named `config.json` in project root and copy your own configuration values into it according to the format provided in `config.example.json`

```bash
cp config.example.json config.json
```

# Run the project

```bash
npm run dev
```

# Hotel API Testing Instructions

This README provides step-by-step instructions for testing the Hotel API and Room API endpoints using Postman or any other API testing tool.

## Setup

1. Install Postman (or your preferred API testing tool).
2. Create a new collection in Postman called "Hotel API".
3. Set up an environment variable:
   - Name: `baseUrl`
   - Value: `http://localhost:3000` (adjust if your server runs on a different port)

## Hotel Endpoints

### 1. Get All Hotels

- **Method**: GET
- **URL**: `{{baseUrl}}/hotel`
- **Example**: `{{baseUrl}}/hotel`
- **Expected Response**: 200 OK with an array of hotel objects

### 2. Get Specific Hotel

- **Method**: GET
- **URL**: `{{baseUrl}}/hotel/:hotel-slug` (replace with any other hotel slug)
- **Example**: `{{baseUrl}}/hotel/luxury-suite-downtown`
- **Expected Response**: 200 OK with the hotel object, including its rooms

### 3. Create New Hotel

- **Method**: POST
- **URL**: `{{baseUrl}}/hotel`
- **Headers**:
  - Content-Type: application/json
- **Body** (raw JSON):

  ```json
  {
    "slug": "new-test-hotel",
    "images": ["/images/hotels/new-test-hotel/main.jpg"],
    "title": "New Test Hotel",
    "description": "A test hotel for API testing",
    "guest_count": 2,
    "bedroom_count": 1,
    "bathroom_count": 1,
    "amenities": ["Wi-Fi", "TV"],
    "host_information": { "name": "Test Host", "phone": "1234567890" },
    "address": "123 Test St, Test City, 12345",
    "latitude": 40.7128,
    "longitude": -74.006
  }
  ```

# Room API Testing Instructions

This guide provides step-by-step instructions for testing the Room API endpoints using Postman or any other API testing tool.

## Setup

1. Install Postman (or your preferred API testing tool).
2. Create a new collection in Postman called "Room API".
3. Set up an environment variable:
   - Name: `baseUrl`
   - Value: `http://localhost:3000` (adjust if your server runs on a different port)

## Room Endpoints

### 1. Get All Rooms for a Hotel

- **Method**: GET
- **URL**: `{{baseUrl}}/hotel/:hotelSlug/rooms`
- **Example**: `{{baseUrl}}/hotel/luxury-suite-downtown/rooms`
- **Expected Response**: 200 OK with an array of room objects for the specified hotel

### 2. Get Specific Room

- **Method**: GET
- **URL**: `{{baseUrl}}/hotel/:hotelSlug/room/:roomSlug`
- **Example**: `{{baseUrl}}/hotel/luxury-suite-downtown/room/master-bedroom`
- **Expected Response**: 200 OK with the room object

### 3. Create New Room

- **Method**: POST
- **URL**: `{{baseUrl}}/hotel/:hotelSlug/room`
- **Example**: `{{baseUrl}}/hotel/luxury-suite-downtown/room`
- **Headers**:
  - Content-Type: application/json
- **Body** (raw JSON):
  ```json
  {
    "room_slug": "new-test-room",
    "room_image": "/images/rooms/new-test-room.jpg",
    "room_title": "New Test Room",
    "bedroom_count": 1
  }
  ```
