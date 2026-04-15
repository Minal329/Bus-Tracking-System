UniTrack – GPS-Based University Campus Bus Tracking System
Product Specification Document

1. Overview
UniTrack is a mobile application that uses real-time GPS technology to track university campus buses. The app allows students to view live bus locations on a map, get arrival notifications, and check route details. Drivers broadcast their GPS location automatically while on duty. Admins manage buses, routes, stops, and drivers through a dedicated dashboard.

Target Platforms: Android and iOS

2. Key Features
- Real-time GPS bus tracking on Google Maps
- Live ETA (Estimated Time of Arrival) for each bus stop
- Push notifications when bus is near a stop
- Role-based access for Students, Drivers, and Admins
- Route and stop management
- Driver GPS auto-broadcasting
- Scan and notification history
- Smart onboarding wizard

3. App Flow
Splash Screen with Branding
        ↓
Onboarding Wizard (permissions + intro)
        ↓
Login / Register Screen
        ↓
Role Check (Student / Driver / Admin)
                ↓
  ┌─────────────┬──────────────┬
  ▼             ▼              ▼
Student       Driver         Admin
Dashboard     Dashboard      Dashboard

4. Main Navigation
- Home
- Map (Live Tracking)
- Notifications
- Routes
- Profile

5. Screens Overview
5.1 Home Screen
- Welcome Section: Personalized greeting (e.g., "Welcome back, Ali!")
- Search Bar: Search for routes or stops
- Active Bus Cards: Shows currently active buses with status
- Quick Access Tiles: Live Map, My Route, Notifications, Schedule
- Main Actions:
  - Track Bus: View live bus location on map
  - My Route: View subscribed route details and stops
  - Notifications: Recent arrival alerts and announcements

5.2 Map Screen
- Google Map centered on user's current location
- Live bus marker that updates every 5 seconds automatically
- Route polyline drawn on map (bus path)
- Stop markers with stop names and landmarks
- Bottom info card showing:
  - Bus Number (e.g., UMT-01)
  - Current Speed
  - Next Stop Name
  - ETA in minutes
- Tap on bus marker → shows driver name and bus details
- Tap on stop marker → shows stop name and landmark

5.3 Route Detail Screen
- Route name and total distance
- Estimated total travel time
- Morning and evening departure times
- Complete stop list in order with:
  - Stop name
  - Landmark
  - Estimated time from start
- Active bus position on mini-map

5.4 Notifications Screen
- List of all push notifications received
- Notification types:
  - Arrival Alert: "UMT-01 is arriving at Shahabpura Road in 5 minutes"
  - Delay Alert: "UMT-01 is delayed by 15 minutes today"
  - Cancellation: "Morning bus UMT-01 is cancelled today"
- Mark as read / delete notification
- Notification timestamp displayed

5.5 Driver Screen
- Start Duty / End Duty button
- Currently assigned route display
- Live GPS status indicator (Active / Inactive)
- Current speed display
- Next stop name and distance
- Duty timer (how long driver has been on route)
- Auto GPS broadcasting starts on "Start Duty" — no manual input needed

5.6 Admin Dashboard
- Overview stats:
  - Total active buses
  - Total registered students
  - Total routes
  - Buses currently on duty
- Quick action buttons:
  - Manage Buses
  - Manage Routes
  - Manage Drivers
- Live map view of all active buses simultaneously

5.7 Manage Buses Module
- Bus List: All registered buses with status (Active / Inactive)
- Add Bus: Enter bus number, plate number, model, capacity, assign driver and route
- Edit Bus: Update any bus details
- Deactivate Bus: Toggle active/inactive status
- Assign Driver: Dropdown to assign a registered driver to a bus

5.8 Manage Routes Module
- Route List: All created routes with stop count and distance
- Add Route: Enter route name, start point, end point, morning/evening times
- Add Stops: Add stops to a route with name, GPS coordinates, landmark, and order
- Edit Route: Update route details or reorder stops
- Deactivate Route: Toggle active/inactive

5.9 Profile Screen
Main Features & Options:
- Edit Profile: Update name, phone, email, profile picture
- My Route: View and change subscribed bus route
- Notification Settings: Toggle arrival, delay, and cancellation alerts
- App Language: Change app language
- Theme: Toggle Light / Dark mode
- FAQ: Frequently asked questions
- Feedback: Submit feedback to development team
- Rate Us: Link to Play Store / App Store rating
- Privacy Policy: View privacy policy
- Terms of Use: View terms and conditions
- Logout: Sign out of the app
- Delete Account: Permanently delete user account

5.10 Edit Profile
- Profile Picture: Upload from gallery or capture from camera
- Full Name
- Email Address
- Phone Number
- University Roll Number
- Subscribed Route: Select from available routes
- Notification Preferences:
  - Arrival Alerts: Toggle on/off
  - Delay Alerts: Toggle on/off
  - Cancellation Alerts: Toggle on/off

5.11 Onboarding Wizard
- App introduction and branding
- Location permission request (required for map)
- Notification permission request (for arrival alerts)
- Feature highlights:
  - Live bus tracking
  - Arrival notifications
  - Route information
- Get Started button → Login / Register screen

5.12 FAQ Section
Purpose: Help users with common questions
Sample Questions:
- How do I track my bus in real time?
- How do I subscribe to a route?
- Why is my bus location not updating?
- How do arrival notifications work?
- What should I do if the bus is late?
- How do I change my subscribed route?
- Can I track multiple buses at once?
- How accurate is the ETA shown?

6. Real-Time Workflow
Driver taps "Start Duty"
        ↓
App accesses device GPS automatically
        ↓
Every 5 seconds:
  GPS coordinates captured silently in background
        ↓
  Location sent to Firebase (liveLocations collection)
        ↓
  Cloud Function triggers automatically
        ↓
  ETA calculated to next stop
        ↓
  If ETA ≤ 5 minutes:
    Push notification sent to subscribed students
        ↓
    Student app receives Firestore update in real-time
        ↓
    Bus marker moves on student's map automatically

7. Tech Stack
|        Layer      |               Technology               |
|-------------------|----------------------------------------|
| Frontend          | Flutter (Dart)                         |
| Backend           | Firebase (Firestore + Cloud Functions) |
| Authentication    | Firebase Authentication                |
| Database          | Cloud Firestore (NoSQL)                |
| Maps              | Google Maps SDK                        |
| Real-Time Updates | Firestore Realtime Listeners           |
| Notifications     | Firebase Cloud Messaging (FCM)         |
| Storage           | Firebase Storage (profile pictures)    |
| GPS on Device     | Geolocator Flutter Package             |
| State Management  | Provider Package                       |

8. Data Handling
- All user data stored securely on Firebase servers
- GPS location stored only while driver is on duty
- FCM tokens refreshed automatically on app launch
- Privacy-first approach — location not stored after duty ends
- Admin-only access to sensitive bus and driver data

9. Target Users
- University students and faculty who use campus bus service
- Bus drivers assigned to university routes
- University admin staff managing transport department

9. Deployment
- Android: Google Play Store
- iOS: Apple App Store

10. Conclusion
UniTrack delivers a modern real-time GPS tracking experience for university campus transport. Its simple interface, automatic driver broadcasting, and instant student notifications make daily commuting more efficient and stress-free. The scalable Firebase architecture ensures the system can grow with the university's needs.

*Document Version: 1.0*
*Phase: 1 — Implementation*
*Project: UniTrack *
*Institution: UMT Sialkot Campus*
