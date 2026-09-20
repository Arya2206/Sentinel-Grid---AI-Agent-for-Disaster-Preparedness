# 🚨 SentinelGrid — Emergency Guidance & Response

> **Stay calm. Get informed. Take action.**

**SentinelGrid** is a responsive emergency-assistance web application designed to help people quickly understand what to do during common emergencies and access essential safety tools from a single interface.

The project combines **step-by-step emergency guidance**, **live browser location**, **nearby shelter discovery**, **emergency calling**, **safe-status messaging**, and a **personal safety checklist** into one simple, mobile-friendly experience.

---

## 🌐 Live Demo

🔗 **https://sentinelgrid.hatchable.site**

---

## 👨‍💻 Developed By

**Arya Khandekar**

---

## 🎯 Project Overview

During an emergency, people may have limited time and may not know what action to take first.

SentinelGrid is designed around a simple idea:

> **Give users clear information and useful actions without overwhelming them.**

The application provides an interactive emergency dashboard where users can:

* Select the type of emergency they are facing
* Follow step-by-step safety instructions
* Capture their current GPS location when needed
* Quickly access emergency services
* Find nearby mapped shelters
* Send a safe-status SMS
* Share their current location through Maps
* Track a personal emergency checklist
* Monitor their progress through the immediate safety plan

---

# 🛡️ Key Features

## 🚨 1. Emergency Guidance

SentinelGrid currently provides guidance for four emergency scenarios:

* 🌊 **Flash Flood**
* 🔥 **Wildfire**
* 🌀 **Cyclone**
* 🌎 **Earthquake**

Each scenario contains a sequence of actionable safety instructions.

Users can move through the guidance using:

**Back → I've done this → Next step**

A progress indicator shows where the user currently is in the emergency plan.

---

## 📍 2. Live Location Support

SentinelGrid uses the browser's **Geolocation API** when a location-dependent feature is activated.

The application requests location only when necessary, such as when the user chooses:

* Emergency Services
* Nearby Shelter
* Safe Status with Location
* Open Current Location on Maps

The application captures:

* Latitude
* Longitude
* Location accuracy

The interface also displays the captured coordinates so the user can understand what information has been obtained.

> 🔐 Location is not requested automatically when the page loads. It is requested when the user uses a location-dependent safety feature.

---

## ☎️ 3. Emergency Services

The **Emergency Services** feature is designed to help users quickly access the emergency calling interface.

The process is:

1. 📍 Request the user's current location.
2. Display the captured coordinates.
3. Open the device's phone dialer using `112`.

SentinelGrid does **not** silently place a phone call.

The final call action remains under the user's control through the device's operating system and phone service.

---

## 🏠 4. Nearby Shelter Finder

The **Find Nearby Shelter** feature uses the user's current GPS position to search for mapped shelters.

The frontend sends the coordinates to:

```text
/api/shelters
```

The backend then queries **OpenStreetMap / Overpass** for mapped locations such as:

* Shelters
* Homeless shelters
* Refugee shelters
* Other mapped shelter facilities

Results are:

* Sorted by distance
* Deduplicated
* Limited to nearby results
* Displayed with available names and addresses

This allows the application to provide location-aware shelter information without maintaining a separate hard-coded shelter database.

---

## 💚 5. "I'm Safe" Status Message

The **I'm Safe** feature allows a user to prepare a safety-status SMS.

The user can:

1. Enter a mobile number.
2. Choose whether to include their current location.
3. Generate a pre-filled SMS.
4. Open the device's messaging application.

Example message:

```text
I'm safe. This is a safety check-in from SentinelGrid.
My location: https://www.google.com/maps?q=LATITUDE,LONGITUDE
```

The final message is still controlled and sent by the user's device.

---

## 🗺️ 6. Live Safety Map

SentinelGrid provides a **Live Safety Map** section that displays the user's captured location.

The application provides:

* Current coordinates
* Location status
* An **Open in Maps** action

The Maps link allows the user to view their current position using a mapping service.

---

# ✅ 7. Personal Emergency Checklist

The **Personal Checklist** provides a quick final safety check before leaving.

Current checklist items include:

* 📱 Phone is charged
* 💊 Medicines are with me
* 🪪 ID & essentials packed
* 👨‍👩‍👧 Everyone is accounted for

The checklist includes:

* Progress counter
* Animated progress bar
* Interactive checkboxes
* Completion state
* Visual feedback when all items are completed

When all four items are checked, SentinelGrid displays:

> **✓ You're ready. Essentials checked.**

---

# 🤖 8. Live Assist

The **Live Assist** panel explains what SentinelGrid is doing through three stages:

### Observe

Identifies the selected emergency scenario and relevant situation.

### Decide

Provides the next recommended safety action within the selected guidance flow.

### Assist

Connects the user with available safety tools such as location, shelters, emergency services, and safe-status communication.

The purpose is to make the application's actions easier to understand rather than making the interface feel like a black box.

---

# 🎨 User Interface

SentinelGrid uses a dark, emergency-focused interface designed around:

* Clear information hierarchy
* High-contrast typography
* Compact safety cards
* Large actionable buttons
* Responsive layouts
* Clear status indicators
* Mobile-friendly controls

The interface is designed to keep important actions visible without creating unnecessary visual clutter.

---

# 📱 Responsive Design

SentinelGrid is designed to work across:

* 📱 Mobile phones
* 📲 Tablets
* 💻 Laptops
* 🖥️ Desktop screens

The layout adapts to smaller screens so that emergency actions remain accessible on mobile devices.

---

# 🧩 Technology Stack

### Frontend

* **HTML5**
* **CSS3**
* **Vanilla JavaScript**
* **Browser Geolocation API**
* **Responsive Web Design**

### Backend

* **JavaScript serverless API**
* `/api/shelters` endpoint
* **OpenStreetMap / Overpass API**

### Deployment

* **Hatchable**
* Live deployment with a public web interface

---

# 📂 Project Structure

```text
SentinelGrid/
│
├── public/
│   ├── index.html
│   ├── styles.css
│   ├── checklist.css
│   └── app.js
│
├── api/
│   └── shelters.js
│
└── README.md
```

### `public/index.html`

Contains the main SentinelGrid interface, including:

* Emergency selector
* Guidance interface
* Quick Help
* Safety Map
* Personal Checklist
* Live Assist
* Safe-status modal

### `public/styles.css`

Contains the primary application styling, including:

* Layout
* Cards
* Buttons
* Typography
* Responsive behavior
* Emergency interface
* Modal components

### `public/checklist.css`

Contains the dedicated styling for the Personal Checklist, including:

* Progress indicator
* Checklist cards
* Completion states
* Interactive effects

### `public/app.js`

Contains the application's core functionality, including:

* Emergency scenarios
* Guidance navigation
* Location handling
* Emergency calling
* Shelter lookup
* Safe-status messaging
* Map links
* Checklist updates
* UI interactions

### `api/shelters.js`

Provides the backend shelter-search endpoint.

It:

1. Receives latitude and longitude.
2. Validates the coordinates.
3. Queries OpenStreetMap / Overpass.
4. Calculates approximate distances.
5. Sorts nearby shelters.
6. Removes duplicate locations.
7. Returns structured JSON data.

---

# 🔄 How SentinelGrid Works

The overall user flow is:

```text
             ┌─────────────────────┐
             │   Open SentinelGrid │
             └──────────┬──────────┘
                        │
                        ▼
             ┌─────────────────────┐
             │ Select Emergency    │
             │ Flood / Fire / etc. │
             └──────────┬──────────┘
                        │
                        ▼
             ┌─────────────────────┐
             │ Step-by-Step Safety │
             │      Guidance       │
             └──────────┬──────────┘
                        │
              ┌─────────┼─────────┐
              ▼         ▼         ▼
          ☎ Emergency  🏠 Shelter  💚 I'm Safe
              │         │         │
              └─────────┼─────────┘
                        ▼
                 📍 Live Location
                        │
                        ▼
             ┌─────────────────────┐
             │   Safety Actions    │
             └─────────────────────┘
```

---

# 🔐 Privacy & Location Design

SentinelGrid follows a **user-initiated location model**.

The application does not request the user's location simply because the website was opened.

Location is requested when the user activates a feature that needs it.

Examples:

```text
Emergency Services → Location → Dialer
Nearby Shelter     → Location → Shelter Search
I'm Safe           → Location → Optional SMS location
Safety Map         → Location → Map coordinates
```

The browser also controls whether location access is granted.

---

# 🌍 OpenStreetMap Integration

Shelter information is obtained from **OpenStreetMap data through the Overpass API**.

The application does not claim that every physical shelter will appear in the results.

Availability depends on:

* OpenStreetMap mapping coverage
* Local data quality
* Internet connectivity
* Overpass availability
* Whether a facility has been correctly mapped

For real emergencies, users should also follow official local emergency and shelter information.

---

# ⚠️ Important Safety Notice

SentinelGrid is an **emergency-assistance and demonstration web application**.

It should not replace:

* Official emergency services
* Government disaster-management instructions
* Local authorities
* Professional emergency responders
* Official shelter information

For an actual emergency, use official emergency services and follow instructions from local authorities.

The application also depends on browser permissions, internet connectivity, device capabilities, and external mapping services.

---

# 🚀 Running the Project

The project can be deployed through a platform that supports:

* Static frontend files
* JavaScript
* Serverless/API routes

The frontend is contained in the `public/` directory.

The shelter API is located at:

```text
/api/shelters
```

When deployed correctly, the frontend can call the shelter endpoint using:

```text
/api/shelters?lat=LATITUDE&lon=LONGITUDE&radius=5000
```

---

# 🧪 Testing the Application

For testing, verify the following flows:

### Emergency Guidance

* [ ] Select Flash Flood
* [ ] Select Wildfire
* [ ] Select Cyclone
* [ ] Select Earthquake
* [ ] Move between guidance steps
* [ ] Complete the safety plan

### Location

* [ ] Allow browser location access
* [ ] Verify coordinates appear
* [ ] Verify location accuracy is displayed
* [ ] Open the location in Maps

### Emergency Services

* [ ] Select Emergency Services
* [ ] Verify location is requested
* [ ] Verify the phone dialer opens with `112`

### Shelter Finder

* [ ] Select Find Nearby Shelter
* [ ] Allow location access
* [ ] Verify nearby results appear
* [ ] Verify distances are displayed

### Safe Status

* [ ] Open I'm Safe
* [ ] Enter a mobile number
* [ ] Test with location enabled
* [ ] Test without location
* [ ] Verify the SMS composer opens

### Checklist

* [ ] Check individual items
* [ ] Verify progress updates
* [ ] Verify `0/4` → `4/4`
* [ ] Verify completion state

---

# 📌 Project Information

| Detail        | Information                         |
| ------------- | ----------------------------------- |
| **Project**   | SentinelGrid UserFirst              |
| **Version**   | 3                                   |
| **Status**    | Live                                |
| **Platform**  | Hatchable                           |
| **Live Demo** | https://sentinelgrid.hatchable.site |
| **Developer** | Arya Khandekar                      |

---

# 💡 Project Goal

SentinelGrid was built around a simple principle:

> **In an emergency, useful information should be easy to find and easy to act on.**

Instead of presenting users with a large amount of disconnected information, SentinelGrid brings essential emergency guidance and quick-response tools together in one interface.

---

# 🔮 Future Improvements

Possible future enhancements include:

* 📡 Offline emergency guidance
* 🏥 Integration with verified local emergency facilities
* 🚑 More official emergency-service integrations
* 🌐 Multi-language support
* 🔔 Emergency alerts and notifications
* 👥 Trusted-contact management
* 🗺️ Verified shelter databases
* 📊 Emergency-event analytics
* 📲 Progressive Web App support
* 🔒 Additional privacy and security controls

---

# 🙌 Acknowledgements

SentinelGrid uses publicly available mapping data through **OpenStreetMap / Overpass** for the nearby shelter feature.

The project also relies on browser capabilities such as:

* Geolocation
* Telephone URI handling
* SMS URI handling
* External map links

---

## ⭐ Final Note

SentinelGrid is more than a static emergency-information page. It is designed as an interactive safety companion that connects **guidance + location + communication + nearby resources** in one streamlined experience.

**Stay calm. Check your surroundings. Follow official instructions. Use the tools when you need them.**

---

### 👨‍💻 Developed by **Arya Khandekar**

**SentinelGrid — Emergency Guidance & Response** 🚨
