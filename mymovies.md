# MyMoviesAfrica App Project Documentation

## Project Overview

The app.mymovies.africa is a mobile/web application that allows users to explore, search, and watch movies. It offers users a comprehensive database of African movies with rich metadata, personalized recommendations, and a seamless streaming experience.

## Problem Statement

The entertainment industry has seen a significant shift towards digital platforms, with users increasingly consuming content online. However, many platforms are either too expensive, lack local content, or provide a poor user experience. MyMovies Africa aims to address these issues by offering a user-friendly, affordable, and content-rich platform that caters to the African audience. The application aims to revolutionize the African streaming market by providing a platform that is affordable, content-rich, and optimized for the unique needs of African users. By addressing the current challenges in the market, the platform has the potential to become the go-to destination for African entertainment enthusiasts.

## 1. Prerequisites/Libraries

### System Requirements:

- Requires Android version 7.0 or higher; iOS version 12 or higher.

### Libraries/Dependencies:

- React Native, Axios for HTTP requests, Redux for state management.
- React Navigation Stack Installed.

### Development Environment:

- Node.js version
- Required SDKs: Android SDK, iOS SDK
- "Ensure you have Node.js v14+ and npm v6+ installed."

## 2. Installation

### Step-by-Step Installation:

1. Clone the repository:
   git clone https://github.com/Ryan-GM/MyMoviesAfricaTV.git
2. Install the dependencies:
   npm install
3. Set up environment variables

- Create .env file:
  ```
  FIREBASE_API_KEY=AIzaSyDE1wRouoq6nZ5TLuREYy7MOKeURl2Dnd8
  FIREBASE_AUTH_DOMAIN=auth.mymovies.africa
  FIREBASE_PROJECT_ID=mychoicetv-a7f9a
  DATABASE_URL=https://mychoicetv-a7f9a.firebaseio.com
  FIREBASE_STORAGE_BUCKET=mychoicetv-a7f9a.appspot.com
  FIREBASE_MESSAGING_SENDER_ID=1006067861904
  ```

4. Running the app:
   npm start

## 3. Features

### Key Features:

- Search Functionality: Users can search for African movies by title or genre.
- Watchlist: Users can add movies to their watchlist for future viewing.
- Recommendations: Personalized movie recommendations based on viewing history.
- Streaming: High-quality movie streaming directly in the app.

## 4. Architecture

### High-Level Overview:

The app is built using a microservice architecture with the frontend built using React Native and backend powered by Node.js and MongoDB.

### Component Breakdown:

- Authentication Service: Google Firebase.
- Authentication Flow: OAuth.

## 5. Troubleshooting & Issues

### Common Issues:

1. Network Error: Verify that the backend API is running, and ensure the API endpoint is correctly configured.
2. Collections: API sometimes fails to fetch after purchasing a movie.
   ![path to the collections error msg](images\collections.jpg)

### Debugging:

1. Using React Native's react-devtools, or inspecting network requests in the browser.

## 6. Screenshots & User Guide

### Screenshot

1. Including screenshots of key screens.

### Guide to Using the App

1. Login/Signup: Create an account or log in with details such as your fullname, phone number, email.
2. Browsing Movies: Browse for movies using the search bar or our user-friendly UI to access great content.
3. Streaming a Movie: Select a movie of your liking, choose whether to Rent it for 7 days or Own it for life. After that Top-Up your account with your preferred method, pay for the movie and start streaming.
   ![Image for movie details, with trailer](images\moviedetails.jpg)
4. Request Screening: Users can request for screening and fill out a form.
   ![Image for events and request screening](images\homescreenevents.jpg)
   ![Image for events and request screening](images\screening.jpg)
5. See upcoming Events.
   ![Image to the events and onclick on the learn more for events](images\homescreenevents.jpg)
   ![Image to the events and onclick on the learn more for events](images\event.jpg)
   ![Image to the events and onclick on the learn more for events](images\eventlearnmore.jpg)

## Requirements:

### a. User Authentication

- Sign Up/Sign In: Allow users to create accounts using email, phone number, or social media.
  ![Signup Screen](images\signup.jpg)
  ![Login Screen](images\login.jpg)

### b. Content Library

- Browse and Search: Users should be able to browse and search for movies, series, and documentaries.
  ![Movie Browsing/search bar Screen](images\searchbar.jpg)
- Categories and Filters: Implement categories (e.g. genres) and filters to help users find content easily.
  ![Movie Browsing/with search categories Screen](images\searchcategories.jpg)
- Personalized Recommendations: Use machine learning algorithms to recommend content based on user preferences, watch history, and trending content.

### c. Video Playback

- High-Quality Streaming: Support multiple video resolutions and adaptive streaming based on the user's internet connection.
- Offline Viewing: Allow users to download content for offline viewing, with options to choose video quality for downloads.

### d. Subscription and Payment

- In-App Purchases: Allow users to subscribe or purchase content directly within the app using in-app purchases.
  ![subscription, image with alert for purchase in the movie details screen](images\paymentalert.jpg)
- Local Payment Methods: Integrate local payment gateways (e.g., mobile money, bank transfers) to cater to the African market.
  ![Payment options](images\paymentoptions.jpg)

## Backend and API Requirements

### Introduction

MyMovies.Africa API Documentation
The backend API Production URL is https://api.mymovies.africa. Please append the end-points below to this Production URL for when you deploy your feature or project to production.

## GET https://app.mymovies.africa/api/cache

The exception is the endpoint for getting all movie data.

## GET /api/v1/payment/gate/(:id)

This is the endpoint used to display the payment options available. The following parameters need to be passed for successful transactions to occur:

Parameters:

- Customer Id: Passed as part of the url as follows: `https://api.mymovies.africa/api/v1/payment/gate/(:id)`. Transactions cannot proceed without passing the id.

These parameters are passed as query parameters in the url:

-amount--- Pass the amount to be transacted.
-purchase_type--- Pass the transaction type, which is either RENTAL or EST.
-ref--- Pass the reference of the movie to be transacted on.

An example of the payment url:
https://api.mymovies.africa/api/v1/payment/gate/10/?amount=0&purchase_type=rental&ref=3ca1cce0eba8e854
Response:
HTML Click this link to view an Image of the paygate

## POST /api/v1/users/createAccount

Use this endpoint to create a single customer account.

Parameters:
Required Form data:

- String fullname
- String email
- String phone
- String password
- String country
- String city
- String plan_id
- String reason. Should either be 0, 1, 2 or 3. (the reason for the topup)
- String amount (optional)
- String ref (optional)
- String purchase_type. Should either be RENTAL, EST, PVOD, MONO OFFLINE SCREENING, etc.

Response:
```json
{
    "signInResultFor_test_m@gmail.com": {
        "uid": "uIQKO4a3UjMQj13G5Iz01pjPFCm2",
        "emailVerified": false,
        "disabled": false,
        "metadata": {
            "createdAt": "2024-10-08T06:10:52+00:00",
            "lastLoginAt": null,
            "passwordUpdatedAt": {
                "date": "2024-10-08 06:10:52.626000",
                "timezone_type": 3,
                "timezone": "UTC"
            },
            "lastRefreshAt": null
        },
        "email": "test_m@gmail.com",
        "displayName": null,
        "photoUrl": "",
        "phoneNumber": null,
        "providerData": [
            {
                "uid": "test_m@gmail.com",
                "displayName": null,
                "screenName": null,
                "email": "test_m@gmail.com",
                "photoUrl": "",
                "providerId": "password",
                "phoneNumber": null
            }
        ],
        "passwordHash": "UkVEQUNURUQ=",
        "passwordSalt": null,
        "customClaims": [],
        "tokensValidAfterTime": "2024-10-08T06:10:52+00:00",
        "tenantId": null
    },
    "status": true,
    "userId": 11826,
    "rentalFor_test_m@gmail.com": {
        "error": true,
        "message": "Invalid purchase type"
    }
}
```

An error response is yet to be added and documented.

## POST /api/v1/users/phone

Use this endpoint to check if a phone number is already in use by another user account.

Parameters:

- phone
- email

The parameters are passed in the request body as form encoded data (application/x-www-form-urlencoded).

The endpoint will return a raw string of either "true", indicating that the phone number does exist and belongs to another user's account, or "false", indicating that the phone number does not exist in the database.

Response:
The code handling this endpoint does not catch any error, if errors do occur, they will appear as PHP CodeIgniter errors. Contact the backend developer to assist. With that said, the endpoint does provide an error response in form of a JSON string in case the parameters are not passed. Below is the error response:

```json
{
  "error": "true",
  "message": "missing parameters required"
}
```

## POST/api/v1/purchases

Use this endpoint to check all the movies a user has purchased

Parameters:

- user_id
  response

```json
{
  "id": "190",
  "amount": "34.90",
  "createdon": "2024-09-07 16:44:56",
  "invoice": "28106",
  "purchase type": "RENTAL",
  "expired": "0",
  "ref": "d9f374f2d56671f",
  "tittle": "Anthology for #WeWatchKenyan - September 2024"
}
```

parameter is passed in the request body as form encoded data (application/x-www-form-urlencoded).

## POST /api/v1/users/wallet

This endpoint returns the user's balance

Parameters:

user_id

The parameter is passed in the request body as form encoded data (application/x-www-form-urlencoded).

response

```json
{ "balance": "58738", "currency": "NGN" }
```

# POST /api/v1/users/login

This endpoint returns the login infomation
Parameters:

- uid
- email
  response
  ```json
  {
    "user": {
      "email": "test_mer@gmail.com",
      "fullname": "Test_joh",
      "id": "11725",
      "phone": "254712123489",
      "locale": "KE",
      "photo_url": "",
      "ref_id": null,
      "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.ImV5SmxiV0ZwYkNJNkluUmxjM1JmYldWeVFHZHRZV2xzTG1OdmJTSXNJbVY0Y0dseVpYTWlPaUl5TURJMUxUQXhMVEE0SW4wPSI.PJvkD8wFBypSHhwccHsnojKAMnGdogPfgDki1ACihSA",
      "birthday": "00-00-0000",
      "date_joined": "2024-09-25 09:25:31",
      "isPhoneVerified": "0",
      "affiliateCodeUsed": null
    }
  }
  ```
  The parameter is passed in the request body as form encoded data (application/x-www-form-urlencoded).

#### Performance Optimization

To ensure a smooth user experience, the app should be optimized for performance:

Efficient Caching: Implement caching mechanisms to reduce load times and improve performance, especially for frequently accessed content.
Optimized Video Streaming: Use adaptive bitrate streaming to adjust video quality based on the user's internet connection, reducing buffering and improving playback.

## Design:

## User Experience (UX) Design

# Navigation Structure:

Uses a Bottom navigation bar for easy access to key sections (e.g., Home, Categories, Search, Profile).
Bottom navigation is used on mobile devices for easier thumb access.
![bottom navigation image](images\bottonnav.jpg)


## User Flows:

Onboarding: New users are likely guided through a simple onboarding process, including account creation and subscription options.
Content Discovery: Users can browse content through categories, search, and personalized recommendations based on viewing history.
Playback: Users can easily start playback with a single click/tap, with controls for adjusting video quality, subtitles, and audio tracks.

## Personalization:

The platform likely offers personalized recommendations based on user preferences, watch history, and trending content in the region.

## Visual Hierarchy

"-- Movie Thumbnails:"

Large, high-quality movie thumbnails are likely the focal point of the design, with titles and key information (e.g., release year, genre) displayed prominently.

Content Sections:

Content is likely organized into sections (e.g., "Trending", "New Releases") with clear headings and horizontal scrolling for easy browsing.
![content section](images\homescreen.jpg)

## Interaction Design

Gestures and Touch Interactions:

On mobile, users can likely swipe to navigate between content categories or scroll through movie lists.
Tap interactions are used for selecting movies, playing content, and interacting with buttons.

Microinteractions:

Subtle animations (e.g., hover effects, button presses, loading spinners) likely enhance the user experience by providing feedback on user actions.

## Tools and Technologies

Design Tools:

The design may have been created using tools like Figma.

Prototyping:

Interactive prototypes may have been created to test user flows and interactions before development.

## Design Challenges and Solutions

Challenge: Ensuring a smooth and responsive experience across different devices and screen sizes.

Solution: Implementing a responsive grid system and using media queries to adapt the layout for mobile, tablet, and desktop users.

Challenge: Balancing aesthetics with performance, especially for users with slower internet connections.

Solution: Using lazy loading for images and videos, and optimizing assets to reduce load times.

## Testing:

1. Testing Overview
   Testing is a critical part of the development process for app.mymovies.africa to ensure that the application is stable, performs well, and provides a seamless user experience. The testing process was carried out using Expo Go, which allowed the team to test the app on both Android and iOS devices in real-time.

## Why Expo Go?

Real-Time Testing: Expo Go allows developers to instantly preview changes on real devices without needing to rebuild the app.
Cross-Platform Testing: The app can be tested on both Android and iOS devices using a single codebase.
Ease of Use: Expo Go simplifies the testing process by eliminating the need for complex setup and configuration, making it easier to focus on testing the app's functionality.

2. Types of Testing Performed
   # a. Manual Testing
   Manual testing was the primary method used during the development process to ensure that the app's core features functioned as expected. The team used Expo Go to manually test the app on both Android and iOS devices.

Device Testing: The app was tested on a variety of devices, including:

Android: Different screen sizes.
iOS: iPhones and iPads with different screen sizes.

# Key Features Tested:

- User Authentication: Sign-up, login, and password recovery flows were tested to ensure users could create accounts and access the app.
- Video Playback: The video player was tested for smooth playback, buffering, and quality adjustments.
- Search and Filtering: The search functionality and content filtering options were tested to ensure users could easily find movies and series.
- Subscription and Payment: The subscription process, including payment gateway integration, was tested to ensure users could subscribe and manage their plans.
- Offline Viewing: If applicable, the offline viewing feature was tested to ensure users could download and watch content without an internet connection.
- Push Notifications: Notifications were tested to ensure users received updates about new content, subscription reminders, and other alerts.

   # b. Functional Testing
Functional testing was performed to ensure that each feature of the app worked as intended. The team used Expo Go to test the following functionalities:

- Navigation: Ensured that users could navigate between different sections of the app (e.g., Home, Categories, Profile) without issues.
- Content Loading: Verified that content (e.g., movies, series) loaded correctly and that users could view details, trailers, and related content.
- Playback Controls: Tested the video player controls (e.g., play, pause, forward, rewind, subtitles) to ensure they worked as expected.
- User Profiles: Tested the creation and management of user profiles, including watchlists and viewing history.

   #  c. Cross-Platform Testing
Since app.mymovies.africa is a cross-platform app, it was essential to ensure that the app worked seamlessly on both Android and iOS devices. Expo Go was used to test the app on multiple devices to ensure consistent behavior across platforms.

- Android Testing: The app was tested on various Android devices with different screen sizes and OS versions to ensure compatibility.
- iOS Testing: The app was tested on iPhones to ensure that the UI and functionality were consistent with the Android version.

    # d. Performance Testing
While Expo Go is primarily used for functional and manual testing, basic performance testing was also conducted to ensure the app performed well under different conditions.

- Load Times: The team tested the app's load times, especially for content-heavy pages like the home screen and movie details pages.
- Video Streaming: The video streaming performance was tested to ensure smooth playback, minimal buffering, and adaptive streaming based on network conditions.
- Memory Usage: The app's memory usage was monitored to ensure it did not consume excessive resources, especially on lower-end devices.

    # e. User Experience (UX) Testing
The team conducted UX testing to ensure that the app provided a smooth and intuitive experience for users. This involved testing the app's design, navigation, and overall usability.

- Ease of Navigation: The team tested how easily users could navigate through the app, find content, and interact with features like search, filters, and watchlists.
- Visual Consistency: The app's design was tested for consistency across different devices and screen sizes, ensuring that UI elements were properly aligned and displayed.
- Accessibility: Basic accessibility testing was conducted to ensure that the app was usable by people with disabilities, including testing for screen reader compatibility and text scaling.

## 3. Testing Tools and Framework
   While Expo Go was the primary tool used for manual and functional testing, other tools and frameworks were also used to ensure the app's quality.
   a. Expo Go
   Purpose: Used for real-time testing on both Android and iOS devices.
   Features: Allowed the team to instantly preview changes, test cross-platform functionality, and ensure the app worked on a variety of devices.



### Guide to Using the App

1. Login/Signup: Create an account or log in with details such as your fullname, phone number, email.
   ![Login/Signup Screen](path/to/login_screenshot.jpg)

2. Browsing Movies: Browse for movies using the search bar or our user-friendly UI to access great content.
   ![Movie Browsing Screen](path/to/browsing_screenshot.jpg)

3. Streaming a Movie: Select a movie of your liking, choose whether to Rent it for 7 days or Own it for life. After that Top-Up your account with your preferred method, pay for the movie and start streaming.
   ![Movie Streaming Screen](path/to/streaming_screenshot.jpg)

4. Request Screening: Users can request for screening and fill out a form.
   ![Screening Request Form](path/to/screening_request_screenshot.jpg)

5. See upcoming Events.
   ![Upcoming Events Screen](path/to/events_screenshot.jpg)

```

```
