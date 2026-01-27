# Software Construction Assignment: Spotify Analysis

## Assignment 1

**Course:** Software Construction  
**Chosen Application:** Spotify

---

## Part A: Understanding the App

### 1. App Overview

#### Problem the App Solves
Spotify addresses the challenge of accessing, discovering, and managing digital music content. Originally, users had to search different websites and applications, which were sometimes unreliable, so as to purchase, download, and store music files. Spotify removes this burden by providing instant access to millions of songs and podcasts within a single application through online streaming.

From a software construction perspective, Spotify draws complex systems such as content storage, copyright enforcement, algorithms for user recommendations, and network streaming into a single user-friendly application.

#### Primary Users
Spotify serves multiple categories of users:
- General listeners who stream music casually
- Premium subscribers who require offline and ad-free access
- Artists and content creators who upload and analyze content
- Podcast listeners

However, supporting diverse user groups increases system complexity and requires careful architectural design.

## 2. Core Features of Spotify (5–7)

The following are seven key features of Spotify that clearly expose its underlying software architecture:

1. User Authentication such as login and registration, and User Profiles  
2. Music Streaming (Play, Pause, Seek)  
3. Music Search and Discovery  
4. Managing Playlists (Create, Edit, Share)  
5. Recommendations and Personalised Feeds  
6. Offline Downloads  
7. Social and Sharing Features  

---

## Part B: Design Behind the App (Feature-by-Feature Analysis)

Each feature is analysed based on:
- Software components involved  
- Internet connectivity requirements  
- System behaviour under slow or unavailable network conditions  

---

### 1. User Authentication and User Profiles

#### Software Components Involved

**User Interface**
- Login screen  
- Sign-up forms  
- Profile page  

**Business Logic**
- Authentication rules  
- Subscription checks (Free vs Premium)  

**Network / API**
- Authentication APIs (login, token refresh)  

**Data Storage**
- User accounts  
- User preferences  
- Subscription status  

#### Internet Connectivity
- Required  

#### Behavior When Network Is Slow or Unavailable
- Login may fail or take longer than expected  
- User may be logged out  
- Cached profile information may be shown with limited functionality  

---

### 2. Music Streaming (Core Playback)

#### Software Components Involved

**User Interface**
- Player controls (play, pause, skip)  
- Progress bar
- Music album cover art 

**Business Logic**
- Playback rules for both premium and free tier users
- Advertisement insertion for free users  

**Network / API**
- Streaming servers  
- Content Delivery Network (CDN)  

**Data Storage**
- Audio files stored in the cloud  
- Local cache for buffered audio  

#### Internet Connectivity
- Required (except when using offline mode)  

#### Behaviour When Network Is Slow or Unavailable
- Buffering delays  
- Reduced audio quality  
- Playback pauses or stops  

---

### 3. Music Search and Discovery

#### Software Components Involved

**User Interface**
- Search bar  
- Search results list  

**Business Logic**
- Ranking algorithms  
- Filtering and relevance logic  

**Network / API**
- Search APIs  
- Metadata retrieval services  

**Data Storage**
- Song metadata  
- Artist information  
- Indexed data for fast search  

#### Internet Connectivity
- Required  

#### Behaviour When Network Is Slow or Unavailable
- Search results load slowly  
- No results returned  
- Previously cached results may appear  

---

### 4. Managing Playlists (Create, Edit, Share)

#### Software Components Involved

**User Interface**
- Playlist editor  
- Add and remove song interface  

**Business Logic**
- Playlist ownership rules 
- Ordering and permission management (public or private) 

**Network / API**
- Playlist CRUD (Create, Read, Update, Delete) APIs  

**Data Storage**
- Playlist metadata  
- Song references  

#### Internet Connectivity
- Required for editing and synchronisation  

#### Behaviour When Network Is Slow or Unavailable
- Playlist changes may not be saved immediately  
- Local changes may sync later  
- Read-only access to cached playlists  

---

### 5. Recommendations and Personalised Feeds

#### Software Components Involved

**User Interface**
- Home feed  
- Personalised sections such as "Discover Weekly"  

**Business Logic**
- Machine learning models  
- User behaviour analysis  

**Network / API**
- Recommendation and personalisation services  

**Data Storage**
- Listening history  
- User behaviour data  

#### Internet Connectivity
- Required  

#### Behaviour When Network Is Slow or Unavailable
- Feed does not refresh  
- Older recommendations are displayed  
- Personalisation accuracy decreases  

---

### 6. Offline Downloads

#### Software Components Involved

**User Interface**
- Download buttons  
- Offline status indicators  

**Business Logic**
- Digital Rights Management (DRM) enforcement  
- Download limits and verification  

**Network / API**
- Download and license verification services  

**Data Storage**
- Encrypted audio files stored locally on the device  

#### Internet Connectivity
- Not required for playback  
- Required for downloading and periodic verification  

#### Behaviour When Network Is Slow or Unavailable
- Downloads pause or fail  
- Offline playback remains available  
- Periodic online verification is required  

---

### 7. Social and Sharing Features

#### Software Components Involved

**User Interface**
- Share buttons  
- Friend activity feed
- Chat spaces with friends 

**Business Logic**
- Privacy and visibility rules  
- Activity tracking  

**Network / API**
- Social interaction APIs  
- Third-party integration APIs  

**Data Storage**
- User activity logs  
- Shared content references  

#### Internet Connectivity
- Required  

#### Behaviour When Network Is Slow or Unavailable
- Sharing actions fails  
- Friend activity does not update  
- Cached activity data may be shown  

---

## Part C: Change and Maintainability

### Chosen Change Scenario: Optimise the App for Low-End Smartphones

#### Goal of the Change
The goal is to make Spotify run smoothly on low-end smartphones. These devices usually have limited RAM and storage, slower processors, older operating systems, and unreliable internet connections. Optimising the app would reduce crashes, improve responsiveness, lower data usage, and extend battery life while still keeping the core features usable.

#### Parts of the App That Would Need Changes
- **User Interface (UI):** The user interface would need to be simplified to reduce memory and CPU usage. Heavy animations, complex transitions, and high-resolution images would be reduced or disabled. Layouts would be made lighter so the app loads faster and consumes less RAM. The use of Dark mode could also be used to reduce the amount of power consumed when the app is open.
- **Business Logic:** Background tasks such as recommendation updates and analytics would be optimised or run less frequently. Non-essential features would be frozen and only load when needed. This prevents the app from doing too much work in the background on weak devices.
- **Network and Data Usage:** The app would default to lower audio bitrates to save data and reduce buffering. It could also allow for streaming of songs in the lowest usable quality possible to reduce the amount of data needed when streaming. This helps the app work better on slow or unstable networks.
- **Data Storage:** Offline downloads would be limited based on available storage. Cached data would be cleaned automatically to prevent the app from consuming too much space. Metadata such as playlists and recommendations would be stored in a more compact format. The downloaded songs would also be stored in their lowest usable quality, thus demanding less storage to download songs for offline use.

#### Existing Features That Could Be Affected or Broken
Some features might change as a result of optimisation. High-quality audio streaming may not be available by default. Visual effects and animations might be reduced, creating a poor user experience in the app. Personalised recommendations could update less frequently. If not carefully designed, these changes could also affect users on higher-end devices, thus maybe requiring an option for the user to download a version of the app that suits them.

#### Why This Change Is Difficult to Implement
Optimising for low-end smartphones is challenging because the app must support many different hardware configurations. Developers must ensure performance improvements do not break existing features or reduce functionality too much. Maintaining different performance modes increases code complexity and testing effort. Extensive testing across many device types and operating system versions is required because it would be optimization for systems would be different depending on if the system is low end or high end.

---

## Challenges in Spotify's Software Construction

1. **Scalability:** Supporting millions of concurrent users worldwide.
2. **Performance:** Ensuring low-latency streaming across varying network conditions.
3. **Security and Privacy:** Protecting user data and listening habits requires a high level of encryption and continuous updates which results in developers having to actively and continuously work on the same app.
4. **Testing Complexity:** Supporting multiple devices and operating systems results in developers having to create varying testing measures for the different OS and devices making the testing process longer.
5. **Maintainability:** Adding features without breaking existing functionality requires developers to extensively test before pushing each update which results in creating new testing measures each time an update is created.

---

## Part E: Group Reflection

### 1. What Surprised Us Most
We were surprised by the number of interconnected systems required just to play a single song, including networking, buffering, security, and analytics systems. One of the most surprising aspects of Spotify’s system design was the extent to which it relies on a highly distributed, microservices-based architecture built on a client–server model. Rather than operating as a single centralised system, Spotify decomposes its functionality into numerous independent services, each responsible for a specific domain such as playback, search, recommendations, or user management. This architecture is heavily supported by cloud infrastructure and Content Delivery Networks (CDNs), which enable low-latency audio streaming and global scalability. The use of CDNs to deliver media content close to users, combined with cloud-based services that scale independently, highlights how modern software systems prioritize performance, reliability, and resilience. This design choice demonstrated how large-scale applications manage complexity and user demand far beyond what a traditional monolithic architecture could support.

### 2. Why Working Code Is Not Enough
At this scale, software must be maintainable, scalable, and secure. Code that only works today may fail as user demands and system requirements evolve.

 **Notes:** Found out that Spotify had a Lite version for lower-end phones, which was discontinued due to the continuing drop in price of flagship phones, allowing almost everyone to have a strong enough phone to run standard Spotify.

### Group Contributions
- **Aturinda Beinembabazi**: I analyzed the selected mobile application, Spotify, by identifying the problem it solves and its primary target users. I also identified and summarized the core features of the app to provide a high-level understanding of its functionality from a software engineering perspective. Knowing who uses this application and why helped us to identify which features to focus on for optimization.
- **Charis Opol**: I analysed the underlying software components(UI, Business logic, Network/API, Data storage) of each feature. I also defined whether the feature's dependency on internet access, and what would happen if the internet were unstable or unavailable.
- **Mbabazi Joseph Owen**: I created the repositiry that we are using for this assignemnt .I evaluated the change scenario of optimizing the app for low-end smartphones by identifying which parts of the system would require modification, which existing features could be affected, and why implementing this change would be challenging in a large-scale software system.
- **Kasule Ezra Evans**: I identified and explained key software construction challenges involved in maintaining and improving Spotify, including performance, scalability, reliability under poor network conditions, security and  testing.
- **Adrian Rugaba Asiimwe**: I focused on the technical organization and maintainability of the project by structuring the documentation in a clear, modular way that mirrors real software development practices. I also supported the team’s use of GitHub by helping create and manage the repository, manage commits, reviewing changes for consistency, and ensuring the documentation accurately reflected versioned updates and collaborative contributions and worked on ensuring the application's long-term maintainability.

---


