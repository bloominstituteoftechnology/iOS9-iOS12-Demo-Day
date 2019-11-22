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

* Github Code: https://github.com/mitchellgbudge/Lambda-Progress
* Github Proposal: https://github.com/mitchellgbudge/ios-build-sprint-project-proposal
* Trello/Github Project Kanban: https://trello.com/b/81Qix9b8/lambda-progress-tracker
* Test Flight Signup (Recommended): https://testflight.apple.com/join/wrVaCkSO
* YouTube demo video (Recommended): `<insert video url here>`

## Hero Image

<img width="400" height="700" src="https://github.com/mitchellgbudge/Lambda-Progress/blob/master/HeroImage.jpeg" />

## Questions (Answer indented below)

1. What was your favorite feature to implement? Why?

    My favorite feature was recreating a UIControl that created star labels and allowed users to assess their confidence and rating on guided and afternoon projects on the classic Lambda scale of 1-3. It was tricky to take the code I had already sort of written for this project and adjust it to what I needed. This whole process made me realize how important it is to write modular code, beginning with the mindset that I would want to be able to use any chunk of code in another project later. 

2. What was your #1 obstacle or bug that you fixed? How did you fix it?

    One difficult aspect was that each individual lesson could have anywhere from 2 to 8 objectives. I needed a way for the user to check off these aspects and have that factor into an overall mastery score. I implemented a custom delegate method to adjust the score for however many times a button in a cell was tapped, and then calculated that out of the total number of objectives. 
  
3. Share a chunk of code (or file) you're proud of and explain why.

    ```private func calculateMastery() -> Double {
        guard let module = module else { return 0 }
        let oMastery = module.objectiveMastery / Double(module.objectives!.count)
        arithmetic = oMastery + module.confidence + module.rating
        
        switch arithmetic {
        case 4..<5:
            module.mastery = 90
        case 3.5..<4:
            module.mastery = 80
        case 3..<3.5:
            module.mastery = 70
        case 2.5..<3:
            module.mastery = 60
        case 2..<2.5:
            module.mastery = 50
        default:
            module.mastery = 100
        }
        return module.mastery
    }
    
    @IBAction func saveButtonPressed(_ sender: Any) {
        guard let module = module else { return }
        moduleController?.updateModule(module: module, confidence: module.confidence, rating: module.rating, mastery: calculateMastery())
        self.navigationController?.popToRootViewController(animated: true)
    }```
  
4. What is your elevator pitch? (30 second description your Grandma or a 5-year old would understand)

    Lambda students need a way to track their progress in a fluid and intensive course. The Lambda Progress app allows students to check off critical aspects and assignments throughout their day to ensure that they are meeting the standards established by the curriculum. Students can check off progress in lectures, afternoon project, career assignments, and conceptual mastery. 
  
5. What is your #1 feature?

    Progress evaluation via a calculating method that takes in scores of students guided project confidence, afternoon project MVP self-rating, and overall objective mastery. After the user has scored their work and understanding, the app displays a percentage level of mastery in the master view.
  
6. What are you future goals?

    - Add functionality for CS track
    - Make project modular in order to enable UX, Web, and DS students to have the same access and information
    - Integrate a date-keeping/calendar system for students to track their progress through the entire course
    - Configure a login criteria and give every user unique access
    - Establish a notification process to ensure that students are given timely reminders to work through past modules and career assignments

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
