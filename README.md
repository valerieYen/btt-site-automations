# Google Sites Profile Card Display
This guide will help you set up a dynamic profile card display on your Google Site. The display shows participant cards with photos, names, team numbers, and other information pulled from a Google Sheet.

## Prerequisites
- A Google Site where you want to display the cards
- A Google Sheet containing participant information
- Basic familiarity with Google Sites and Google Sheets

## Setup Instructions

### 1. Prepare Your Google Sheet
1a. Update the existing "Career Launch Google Site Info" Google sheet, keeping column names and sheet names consistent OR
1b. Create a new Google Sheet with 2 sheet pages named "Participants" and "Projects"
2. Add the following columns in the Participants tab:
   - `hsUrl` (for profile photo URL) [Type: public .jpeg or .png image links; Use [imgur.com](https://imgur.com/)]
   - `firstName` [Type: text/string]
   - `lastName`  [Type: text/string]
   - `major` [Type: text/string]
   - `year` [Type: text/string]
   - `liUrl` (for LinkedIn profile URL) [Type: LinkedIn URL or placeholder link]
   - `group` (optional)  [Type: text/string]
   - `pronouns` (optional)  [Type: text/string]
3. Fill in your participant information
4. Add the following columns in the Projects tab:
   - `team_num` [Type: text/string] 
   - `devport_link` [Type: text/string]
   - `members`  [Type: text/string]
   - `project_name` [Type: text/string]
   - `cover_img` [Type: public .jpeg or .png image links; Use [imgur.com (https://imgur.com/)]
5. Fill in your project information
6. Make the sheet public:
   - Click "Share" in the top right
   - Change access to "Anyone with the link"
   - Set permission to "Viewer"

### 2. Set Up Sheety
1. Go to [sheety.co](https://sheety.co)
2. Create a new account or sign in
4. Create a new project
5. Paste your Google Sheet URL
6. Copy the generated API URL
** Note, somewhere Sheety will ask you what permissions you want to give it. This file only needs "READ" **

### 3. Add the Code to Google Sites
1. In Google Sites editor, click the `+` button to add an element
2. Choose "Embed"
   - Alternatively, just select "Embed" under the Insert tab
4. Click the `<>` (Embed code) option
5. Copy the entire HTML code provided
6. Replace `["YOUR SHEETY URL HERE; remove brackets but keep the quotations"]` with your Sheety API URL
7. Project Page ONLY: Find `<!-- update Max Team Number. {ie. (1 -> max) and (max -> 1)}-->` and update the max number of teams accordingly.
8. Click "Next" and then "Insert"

### 4. Updating the Google Sheet
- If the original Google sheet needs to be updated after embedding the code:
  1. Go to [sheety.co](https://sheety.co)
  2. Access your existing projects
  3. Click the Refresh button
  4. Test the website page
- Note: Major changes can lead to bugs that will require you to update the embedded code as well [see section 5](### 5. Updating the Code for Google Sites)
    
### 5. Updating the Code for Google Sites
- Highly recommended to use VSCode or another IDE for any code updates
- Test code independently using the `run without debugging` feature to ensure there are no bugs.
- Save changes using git:
  1. `git add -A` to stage changes
  2. `git status` to confirm changes are staged
  3. `git commit -m "insert informative message here"` to save changes to the local repository
  4. `git push` to send changes to the remote repository
- In the Google Site:
  1. Create a new embedded block and add the updated code [see section 3](### 3. Add the Code to Google Sites)
  2. Delete the old embedded block
- Note: Google Sites' embedded feature reacts negatively to any updates. It's easier to make a new block.



## Troubleshooting
- If cards don't appear, check your browser console for errors
- Testing this code in localhost will load all information except for profile pictures, ensure everything works when you put the embed into the site
- Verify your Sheety URL is correct
- Ensure your Google Sheet is publicly accessible
- Check that column names in your sheet exactly match the ones used in the code
  - Verify this by using a "console.log()" on the json returned from Sheety to verify object attribute names



## Participant Page Features
- Responsive card layout
- Sort participants by:
  - Name
  - Team number
  - Year (ascending and descending)
- Automatic fallback image for missing profile photos



## Career Launch Project Page Features
- Responsive card layout
- Sort participants by:
  - Project Name
  - Team number
  - Team Member names
- Sort page by Team Number (ascending/descending)
- Sort page by Project Name
- Cross-device compatibility

## Notes
- Profile photos should be hosted online at Imgur (when you host the photo, you must copy the image's address, not the link to the post)
- LinkedIn URLs must start with "https://" to display properly
