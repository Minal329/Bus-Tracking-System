Bus Tracking System - Detailed Documentation
**GPS-Based University Campus Bus Tracking System**
University of Management and Technology (UMT), Sialkot Campus
Society Project — Software Engineering


##Table of Contents:
1.  Project Overview
2.  System Architecture
3.  Tech Stack
4.  Database Design
5.  Backend Architecture
6.   Frontend Architecture
7.  Authentication Flow
8.  Real-Time Tracking Flow
9.  Notification System
10. API & Services
11. Project Folder Structure
12. Phase 1 Deliverables
13. Future Phases

##1. Project Overview:
Bus Tracking System is a modern and smart project that makes transport system easier for university students, faculty and drivers. 
Its main purpose is to avoid waiting time and delays, and to inform users whether the bus is coming or not.The software will be both android 
and web-based providing live GPS location, bus alerts to its users so that they don’t need to contact anyone and get information directly through application.

###1.1 Problem Statement:
University transport management is a serious issue nowadays. Students and faculty are usually unaware of where the bus is, if it’s gone or coming or not. 
For these reasons, they might miss the bus, wait for a long time, call drivers again and again or depemd om whatsapp groups with internet  connection. 
This system is inefficient and unreliable.

###1.2 Proposed Solution
UniTrack is a mobile application that provides:
- Live GPS tracking of university buses on a map
- Real-time ETA (Estimated Time of Arrival) for each bus stop
- Push notifications when bus is near the stop
- Route and schedule management for admins
- Driver-side app for automatic GPS broadcasting

###1.3 Target Users
| User Type | Description |
|-----------|-------------|
| Student   | Views live bus location, gets arrival alerts |
| Driver    | Broadcasts live GPS location while on duty |
| Admin     | Manages buses, routes, stops, and drivers |

###1.4 Key Features (Phase 1)
- User registration and login (role-based)
- Live bus location on Google Map
- Route and stop display on map
- Driver GPS broadcasting
- Push notifications for bus arrival
- Admin dashboard for management

##2. System Architecture
┌────────────────────────────────────────────────────────────────────┐
│                            FLUTTER APP                             │
│                                                                    │
│     Student Screen             Driver Screen      Admin Screen     │
└────────────┬────────────────────────┬─────────────────┬────────────┘
             │                        │                 │
             ▼                        ▼                 ▼
┌───────────────────────────────────────────────────────────────────┐
│               FIREBASE BACKEND                                    │
│                                                                   │
│  Firebase Authentication  │  Cloud Firestore  │  Cloud Function   │
│  (Login/Roles)            │  (Database)       │  (Logic)          │
│                                                                   │
│  Firebase FCM             │  Firebase Storage │  Google Maps      │
│  (Notifications)          │  (Profile Pics)   │  (Map API)        │
└───────────────────────────────────────────────────────────────────┘

###How It Works (Simple)
1. Driver opens app → GPS location sends to Firebase every 5 seconds
2. Firebase stores that location in `liveLocations` collection
3. Student app listens to that collection in real-time
4. Map updates automatically with new bus position
5. When bus is near a stop → Cloud Function triggers → FCM notification sent to students


##3. Tech Stack
###3.1 Frontend
|    Technology   | Version | Purpose |
|-----------------|---------|---------|
| Flutter         | 3.x     | Cross-platform mobile app (Android + iOS) |
| Dart            | 3.x     | Programming language for Flutter |
| Google Maps SDK | Latest  | Map display, markers, polylines |
| Provider        | 6.x     | State management |
| Geolocator      | 10.x    | GPS location access on device |

###3.2 Backend
|             Technology         | Purpose |
|--------------------------------|---------|
| Firebase Authentication        | User login, registration, role management |
| Cloud Firestore                | NoSQL real-time database |
| Firebase Cloud Functions       | Server-side logic, ETA calculation, notifications |
| Firebase Cloud Messaging (FCM) | Push notifications to students |
| Firebase Storage               | Profile picture uploads |

###3.3 APIs
|                API         | Purpose |
|----------------------------|---------|
| Google Maps API            | Map rendering |
| Google Directions API      | Route polyline drawing |
| Google Distance Matrix API | ETA calculation |






