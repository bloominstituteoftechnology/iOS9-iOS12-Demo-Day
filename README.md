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

* Github Code: `<https://github.com/Patrickm79/Duplicate-No-More>`
* Github Proposal: `<https://github.com/Patrickm79/ios-build-sprint-project-proposal>`
* Trello/Github Project Kanban: `<https://github.com/Patrickm79/Duplicate-No-More/projects/1>`
* Test Flight Signup (Recommended): `<insert beta signup link here>`
* YouTube demo video (Recommended): `<insert video url here>`

## Hero Image

![](https://i.imgur.com/EgnXLpl.png)

## Questions (Answer indented below)

1. What was your favorite feature to implement? Why?

    `<My favorite feature was implimenting the modal segues to select two images from a collection view and put them into a seperate view controller>`

2. What was your #1 obstacle or bug that you fixed? How did you fix it?

`<My app wouldn't select the cells in the duplicate detector view controller even though I had all the code right, turns out by initializing the view controller as a property it was trying to call my functions to get the info from the cell before the collection view was even displayed. Fixed it by using a delegate to handle transfering the photos data.>`
  
3. Share a chunk of code (or file) you're proud of and explain why.

    `<
        
        guard let photo1 = imageOnePhoto else { return }
        guard let photo2 = imageTwoPhoto else { return }
        
        let imageOneIndex = imageOneIndexPath
        let imageTwoIndex = imageTwoIndexPath
        
        let photoOneString = photoComparisonController.convertPhoto(photo1)
        let photoTwoString = photoComparisonController.convertPhoto(photo2)
        
        check1 = photoOneString
        check2 = photoTwoString
        
        guard let result = photoComparisonController.hammingDistance(photoOne: check1, photoTwo: check2) else { return }
        
        if imageOneIndex == imageTwoIndex {
            let alertController = UIAlertController(title: "CAUTION", message: "You have selcted the same initial image", preferredStyle: .alert)
            let alertAction = UIAlertAction(title: "Return to selection", style: .cancel) { (_) in
                self.navigationController?.popViewController(animated: true)
            }
            alertController.addAction(alertAction)
            
            self.present(alertController, animated: true, completion: nil)
        }
        
        if result == 0 && imageOneIndex != imageTwoIndex {
            guard let indexPath = imageTwoIndexPath else { return }
            photoController.photos.remove(at: indexPath.item)
            photoController.saveToPersistentStore()
            
            let alertController = UIAlertController(title: "Duplicate Detected", message: "", preferredStyle: .alert)
            let alertAction = UIAlertAction(title: "Delete Incoming!", style: .destructive) { (_) in
                self.navigationController?.popViewController(animated: true)
            }
            alertController.addAction(alertAction)
            self.present(alertController, animated: true, completion: nil)
        }
        
        if result != 0 {
            let alertController = UIAlertController(title: "No Duplicate Detected", message: "", preferredStyle: .alert)
            let alertAction = UIAlertAction(title: "Return", style: .cancel) { (_) in
                self.navigationController?.popViewController(animated: true)
            }
            alertController.addAction(alertAction)
            self.present(alertController, animated: true, completion: nil)
        }
    }>`
    
    This code essentially handles pulling all my resources together, from the photo data to my hammingDistance method and generates a response to the user based on what it finds out. It's where the whole app comes together.
  
4. What is your elevator pitch? (30 second description your Grandma or a 5-year old would understand)

`<This app can determine down to a bit to bit level if an image is a duplicate or not. Perfect for photographers or people concerned their images are being used elsewhere without their permission.>`
  
5. What is your #1 feature?

    `<Duplicate Detection>`
  
6. What are you future goals?

`<Perform multiple scans at the same time, backup images before they are deleted to revert if a User wants to do so. And make the process more efficient for scanning hundreds or more images simultaneously.>`

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
