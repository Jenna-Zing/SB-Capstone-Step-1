# SB-Capstone-Step-1

Springboard SE Bootcamp - Capstone - Step 1

## My 3 project ideas:

1. **MindfulMe** - mental health app that helps users track their daily mental wellness by logging habits and emotional patterns such as water intake, sleep, stress level, and mood. The app analyzes trends and offers suggestions to improve well-being. It also offers daily quotes, calming videos, and journaling to promote self-care.
2. **My Routine Pal** - a productivity app where users can create and manage cyclical checklists—routines like morning skincare, grocery shopping, or cleaning. Lists are structured with headers, substeps, and embedded resources (e.g. PDF, word doc, or YT links, etc.). Users can share, collaborate, and even clone others’ routines into their own workspace.
3. **Walk With Me** - an app that encourages users to walk 30 minutes daily by combining walking route tracking, reminders, and social sharing. Users can view completed walks on a map, discover new paths, or plan walks with friends.

## Breaking down my app ideas and data

1. **MindfulMe** - User Functionalities
   - Register / Login
   - Daily Log (quiz):
     - water intake (cups)
     - sleep (hours)
     - stress level (1 - 5, half points allowed)
     - mood (denoted by pill-shaped button with icon and text label)
     - notes / journal entries
   - Dashboard
     - view history (calendar/week/month)
     - trend graphs (e.g. mood over time, water vs. stress)
   - Personalized Suggestions:
     - "You're often stressed on Monday mornings"
     - "You sleep better when you drink 6+ cups of water"
   - Optional push/email reminders
2. **My Routine Pal** - User Functionalities
   - Register / Login
   - Create structured lists:
     - Header -> Substeps (nested items)
     - Optional Notes/Resources per item (e.g. PDF, word doc, Youtube Link)
   - Assign frequency (daily, weekly, monthly) - so it auto-refreshes, OR... maybe let users manually handle this via a "START OVER" / "REPEAT ME" button at bottom to start checklist over
   - Optional due dates/reminders
   - Categorize lists: Skincare, Fitness, Errands, etc.
   - Share list:
     - view-only (read access) or collaborative mode (write access)
     - clone shared lists into personal space
   - "Routine Mode" (step-by-step progress tracking) - not sure if we should have an overview mode to see how far someone has gotten into a list - denoted by percentage or number of steps completed. - E.g. "Cleaning - 3/7 completed"
3. **Walk With Me** - User Functionalities
   - Register / Login
   - "Start Walk" - begin GPS tracking
   - "End Walk" - save route + duration
   - View Walking History (map view + stats - e.g. miles, duration, walking speed, not sure if there's a way to get incline and difficulty)
   - Set Walking Schdule - (e.g. every day at 6pm)
   - Join a friend's walking route
   - Suggested Walking routes (based on area or popularity?)

## Where will you find your data?

1. **MindfulMe** - a mental health app that helps users track their daily mental wellness (through a quiz).

   - **CONTEXT**: I want this app to be meaningful and insightful to users to help them learn more about how they think and what habits they have and how they're impacting them. I want this app to accomplish this by analyzing trends and offering suggestions to improve well-being.
   - Internal Endpoints:

     - Register / Login
     - User Daily Mental Health Quiz
       - Journaling (to promote self-care) - not sure if this should be included in the Daily Mental Health Quiz, but I'm leaning towards separate and labeling it as a "Journal / Get off your chest / Vent" area. I want it such that a user can submit their quiz + a journal and it's organized by DATE.
     - Dashboard - Data Trends and Analytics
       - **QUESTION/DISCUSSION WITH MENTOR**:
         I was thinking this could be an internal analytic from my backend:
         - Fetch a user’s last 7–30 days of entries
         - Group by: Day of week, Stress or sleep score, Mood frequency
         - Analyze averages, patterns, or fluctuations
         - Return summaries or trends like: "You sleep more on weekends.", "Your mood tends to drop on days you get < 6 hours of sleep.", "Stress is usually higher on Mondays and Wednesdays."

   - External API's / Endpoints (to offer small meaningful user exp/interactions to improve their day): daily quotes, calming videos (e.g. encourage user to take a meditation break), and journaling to promote self-care (this would be through internal - see above).
     - Daily Motivational Quote
       - e.g. [API Ninjas - Quotes API](https://api-ninjas.com/api/quotes) - can use category\*
       - e.g. [ZenQuotes - inspirational quotes](https://zenquotes.io/) - inspirational quotes, but doesn't quite match the mental health theme, but can be motivational
       - e.g. [RapidAPI - Mood Based Quote API](https://rapidapi.com/sanyamjain007/api/mood-based-quote-api) - not sure about the setup for this, but I like the mood to query. Perhaps this can link up with the mood\* that the user logs in their daily quiz.
     - Meditation or music embeds

2. **My Routine Pal** - a productivity app where users can create and manage cyclical checklists—routines like morning skincare, grocery shopping, or cleaning.

   - **INSPIRATION**: I have a ton of notes on my phone for checklists, etc. and I do share/collaborate them, but I'm not a fan of their UI and if you need to nest more information when in lists (bullet or numbered). I want this app to help users organize and share/collaborate their routines/lists. I want this design to be flexible for things like multi-store grocery lists, or skincare routines, or even event-planning lists - e.g. Jenna is in charge of appetizers, Sam is in charge of drinks, etc. and you can actively see people working on their sections and their breakdown. Ideally, I want the option for users to put comments like a Google Doc too.
   - Internal Endpoints:

     - Register / Login
     - GET all user-created lists
     - GET/create/update individual user-created list (full list structure)
     - share list with read or edit access
     - clone shared list into user's space
     - set reminders with external API like Cronofy

   - External API's / Endpoints:
     - [Cronofy Calendar API](https://www.cronofy.com/developer/calendar-api) - integrate reminders into calendars - e.g. Google or Outlook
       - **TO DISCUSS WITH MENTOR** - how would this one work? If the API fails, can I fall back on an internal API to generate an ".ics" file (which seems to be universal) - e.g. [ical-generator](https://www.npmjs.com/package/ical-generator) in Node.js -> (1) offer download button, (2) user opens it and adds to their calendar
     - [Giphy API](https://developers.giphy.com/docs/api/#quick-start-guide) - to add fun GIFs to routines - increases engagement and personalization

3. **Walk With Me** - an app that encourages users to walk 30 minutes daily by combining walking route tracking, reminders, and social sharing.

   - **INSPIRATION**: I struggle with building good habits like getting fresh air and exercise, but I know starting to incorporate regular habits like walking outside have helped me in the past. This app is my way of encouraging myself and users to walk at least 30 minutes a day, as it helps with heart health and overall wellness.
   - **THOUGHTS ON INTERACTIVITY**: I want users to be ble to have routine tracking to know what paths they walk and could share it with family/friends to join them - the main idea is that it'll show the route (allowing users to preview, etc.).
   - Internal Endpoints:

     - Register New User
     - Authenticate user
     - POST walks/start - start a new walk (initialize tracking)
     - POST walks/end - save a completed route
     - GET walks/history - show all previous/saved routes
     - POST walks/reminders - set habitual walk reminders
     - GET walks/suggestions - get suggested local walks
     - POST walks/share - invite a friend to a walking session

   - External API's / Endpoints:
     - [Google Maps API](https://developers.google.com/maps/documentation/routes) - route tracking?
       - [Google Maps JavaScript API](https://developers.google.com/maps/documentation/javascript) - _Description_: Build dynamic, interactive, deeply customized maps, location, and geospatial experiences for your web apps.  
         -> For my app, to display a map in my frontend.
       - [Google Directions API](https://developers.google.com/maps/documentation/directions) - to calculate and draw walking routes??
       - [Google Places API](https://developers.google.com/maps/documentation/places/web-service/overview) - to suggest landmarks or popular places?
     - [Weatherstack API](https://weatherstack.com/?utm_source=Github&utm_medium=Referral&utm_campaign=Public-apis-repo-Best-sellers) - weather - real-time weather/history/forecast
