# CPAN-212-Assignment-5-6

Team: Abdulhamid Weheliye (n01756626, Section A), Mbaye Fall (n01764121, Section A), Cheyenne Hunsley (N01747035, Section A), Bandanpreet Kaur Malhi (n01726650, Section A), Laura Sofia Santana Acosta (N01737339,Section B)

## Backend Setup

## Setup

1. Place your PFX file in:
   - `backend-api/cert/server.pfx`

2. Configure `.env` in `backend-api/`

3. Configure `.env.local` in `frontend-api`

4. Install backend dependencies:
   ```bash
   npm install

5. Install frontend dependencies:
   ```bash
   npm install

## Implemented Features
- Admin User creation
- Admin User update
- Admin User List
- Role Assignment and Revocation
- Admin User status update
- Self-service suspension
- Own Profile edits

## API Usage

API's were used to: 
- Create users
   - Form submitted on frontend
   - React Client sends an HTTP POST request to /api/admin/users
   - Backend recieves request and routes request to userAdminRoutes
   - userAdminRoutes calls createUser from userAdminController
   - userAdminController calls createUser from userAdminService
   - userAdminService calls create from userRepository
   - userRepository creates user in MongoDB backend using .create() method
- Update users
   - Form submitted on frontend
   - React Client sends an HTTP PUT request to /api/admin/users/:userId
   - Backend recieves request and routes request to userAdminRoutes
   - userAdminRoutes calls updateUser from userAdminController
   - userAdminController calls updateUser from userAdminService
   - userAdminService calls updateByID from userRepository
   - userRepository creates user in MongoDB backend using .findByIdAndUpdate() method
- Allow user's to edit specific profile fields
   - User submits form on frontend
   - React frontend sends a HTTP PUT Request to /profile/me
   - Backend recieves request and routes request to profileRoutes
   - profileRoutes calls updateOwnProfile from profileController
   - profileController calls updateOwnProfile from profileService
   - profileService uses Object.assign() method and user.save() method to update user in MongoDB
- Get users
   - React frontend sends a HTTP GET Reqeuest to /api/admin/users
   - Backend recieves request and routes request to userAdminRoutes
   - userAdminRoutes calls listUsers from userAdminController
   - userAdminController calls listUsers from userAdminService
   - userAdminService calls findAll from userRepository
   - userRepository uses .find().populate() to query MongoDB and return all users