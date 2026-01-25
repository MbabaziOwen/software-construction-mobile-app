# Software Construction Assignment: Spotify Analysis

## Assignment 1

**Course:** Software Construction  
**Chosen Application:** Spotify

---

## Part A: Understanding the App

### 1. App Overview

#### Problem the App Solves
Spotify addresses the challenge of accessing, discovering, and managing digital music content. Traditionally, users had to purchase, download, and store music files manually. Spotify removes this burden by providing instant access to millions of songs and podcasts through online streaming.

From a software construction perspective, Spotify abstracts complex systems such as content storage, copyright enforcement, recommendation algorithms, and network streaming into a single user-friendly application.

#### Primary Users
Spotify serves multiple categories of users:
- General listeners who stream music casually
- Premium subscribers who require offline and ad-free access
- Artists and content creators who upload and analyze content
- Podcast listeners

Supporting diverse user groups increases system complexity and requires careful architectural design.

### 2. Core Features
The core features of Spotify include:
1. User authentication (login and registration)
2. Music search
3. Music streaming
4. Playlist creation and management
5. Personalized recommendations
6. Offline downloads
7. Notifications

---

## Part C: Change and Maintainability

### Chosen Change Scenario: Optimize the App for Low-End Smartphones

#### Goal of the Change
The goal is to make Spotify run smoothly on low-end smartphones. These devices usually have limited RAM and storage, slower processors, older operating systems, and unreliable internet connections. Optimizing the app would reduce crashes, improve responsiveness, lower data usage, and extend battery life while still keeping the core features usable.

#### Parts of the App That Would Need Changes
- **User Interface (UI):** The user interface would need to be simplified to reduce memory and CPU usage. Heavy animations, complex transitions, and high-resolution images would be reduced or disabled. Layouts would be made lighter so the app loads faster and consumes less RAM. The use of Dark mode could also be used to reduce the amount of power consumed when the app is open.
- **Business Logic:** Background tasks such as recommendation updates and analytics would be optimized or run less frequently. Non-essential features would be frozen and only load when needed. This prevents the app from doing too much work in the background on weak devices.
- **Network and Data Usage:** The app would default to lower audio bitrates to save data and reduce buffering. It could also allow for streaming of songs in lowest usable quality possible to reduce the amount of data needed when streaming. This helps the app work better on slow or unstable networks.
- **Data Storage:** Offline downloads would be limited based on available storage. Cached data would be cleaned automatically to prevent the app from consuming too much space. Metadata such as playlists and recommendations would be stored in a more compact format. The downloaded songs would also be stored in their lowest usable quality thus demanding less storage to download songs for offline use.

#### Existing Features That Could Be Affected or Break
Some features might change as a result of optimization. High-quality audio streaming may not be available by default. Visual effects and animations might be reduced creating a poor user experience in the app. Personalized recommendations could update less frequently. If not carefully designed, these changes could also affect users on higher-end devices thus maybe requiring an option for the user to download a version of the app that suits them.

#### Why This Change Is Difficult to Implement
Optimizing for low-end smartphones is challenging because the app must support many different hardware configurations. Developers must ensure performance improvements do not break existing features or reduce functionality too much. Maintaining different performance modes increases code complexity and testing effort. Extensive testing across many device types and operating system versions is required because it would be optimization for systems would be different depending on if the system is low end or high end.

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
We were surprised by the number of interconnected systems required just to play a single song, including networking, buffering, security, and analytics systems.

### 2. Why Working Code Is Not Enough
At this scale, software must be maintainable, scalable, and secure. Code that only works today may fail as user demands and system requirements evolve.

### Group Contributions
- **Notes:** Found out that Spotify had a Lite version for lower-end phones which was discontinued due to the continuing drop in price of flagship phones allowing almost everyone to have a strong enough phone to run standard Spotify.

---

*This document was collaboratively prepared by the group for the Software Construction assignment.*
