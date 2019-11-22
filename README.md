# iOS9 and iOS12 Demo Day

## Requirements

1. Fork and clone the repository
2. **Add your presentation content**
    1. Slide deck (4 required slides)
    2. Links
    3. Answer all questions 
    4. YouTube demo video (1-2 min max)
3. Polish your Github Code repository
    1. Add screenshots and an overview to your GitHub Code Repository
    2. You should make that repository the "Public Portfolio" for your project
    3. Look at [John Sundell's Splash project](https://github.com/JohnSundell/Splash) for inspiration (code, images, GIFs)
4. Create a pull request (PR) and **tag your TL and Instructor**

## Links

* Github Code: `<insert Github repository link here>`
* Github Proposal: `<insert Proposal Pull Request here>`
* Trello/Github Project Kanban: `<insert trello board here>`
* Test Flight Signup (Recommended): `<insert beta signup link here>`
* YouTube demo video (Recommended): `<insert video url here>`

## Hero Image

`<Post one screenshot in an iPhone Simulator frame or an iPhone 11 Pro render using placeit.com>`

## Questions (Answer indented below)

1. What was your favorite feature to implement? Why?

    The onboarding. I think it brings a new level of professional feel to the app.

2. What was your #1 obstacle or bug that you fixed? How did you fix it?

    Notifications not firing. I realized that I not only had to pass in the hour for the notification, but also the minutes.
  
3. Share a chunk of code (or file) you're proud of and explain why.

```
    /// Function to set up timed notifications for every medication scheduled in the medications array
    /// - Parameter medicationController: The medication controller to be passed in
    func setupTimeNotifications(medicationController: MedicationController) {
        for medication in medicationController.medications {
            for (index, time) in medication.times.enumerated() {
                let content = UNMutableNotificationContent()
                content.title = NSString.localizedUserNotificationString(forKey: "Medication Alert", arguments: nil)
                content.body = NSString.localizedUserNotificationString(forKey: "It's time to take your \(self.dateFormatter.string(from: time)) \(medication.name)", arguments: nil)
                
                let request = UNNotificationRequest(identifier: medication.timesId[index], content: content, trigger: UNCalendarNotificationTrigger(dateMatching: Calendar.current.dateComponents([.hour, .minute], from: time), repeats: true))
                self.center.add(request) { error in
                    if let error = error {
                        print(error.localizedDescription)
                    }
                }
            }
        }
    }
 ```
    
   This code sets up notifications for all medications in the medications array. Therefore allowing the user to get a notification when it is time to take their medications.
  
4. What is your elevator pitch? (30 second description your Grandma or a 5-year old would understand)

    Take medications daily? Are you always forgetting to take your medications? Then daily does is for you! This app allows the user to store a list of their daily medications and then sends them a notification when it is time to take them. It also sends a daily medicaiton low reminder when the dosage drops below 10.
  
5. What is your #1 feature?

    Low dosage and scheduled medication notificaitons.
  
6. What are you future goals?

    Remove the plist persistence and conform it to CoreData and CloudKit

## Required Slides (Add your Keynote to your PR)

1. App Name / Team Slide
2. Elevator Pitch
3. Your #1 Feature (Customer facing — what can I do with your app?)
4. Future Goals

## Slide Requirements

1. 50 pt font minimum
2. Be concise — don't write sentences/paragraphs (put these in your slide notes for speaking)
3. 3-6 bullets maximum per slide
4. Do the squint test (can you read the text if you squint, if so, make the font bigger)
6. Images are always welcome
7. Do the Grandma Test (Would your Grandma understand you?)

### Optional Slides

1. Blooper: What's a funny bug or blooper? (screenshots/GIFs please)
2. Revenue Model: If the app was your sole source of income, how would you monetize it?

## Presentation Format

**7 minutes/team**

* 4 minute presentation (5 minute hard cap)
* 3 minutes of questions

We have ~12 teams presenting today — please practice your presentation with a timer (as a team), and make sure you fit within the time limit.

Plan on having one person present the slides and live demo. Please practice your presentation in front of a mirror or with your team 2-5 times. Have the app running and visible (Simulator or QuickTime) so you can quickly transition between slides and live demo.

* App Name / Team Slide (30 seconds)
* Elevator Pitch Slide (30 seconds)
* Your #1 Feature (30 seconds)
* Live Demo (2 minutes)
* Future Goals (30 seconds)
* Questions (3 minutes)
