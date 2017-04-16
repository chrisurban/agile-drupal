# agile-drupal
Useful files for setting up Drupal projects in JIRA

# Assumptions
This collection of files assumes use of Atlassian JIRA for project management.

# Background
If you've setup a new project in JIRA before, then you know it'd be nice to 
have a lot of things setup or pre-entered to make things easier when 
entering in new user stories. Two key things I use in projects - and would
use more frequently if they were in the project to begin with - are epics
and components. The files and this README provide a method to load these
quickly and easily into your projects.

Some benefits by using a standard starting point include: consistency among
your projects, and easier initial organization of user stories per project.

# Epics
If Epics are preloaded into your new JIRA project, then you immediately have
a means of organizing tickets and stories as you add them. Rather than 
repeating entry of the same list of epics over and over, I've collected 
some of the most often used ones here. Feel free to add your own to make 
your own custom Epics list.

## Import Epics list
Download the `BulkCreate-Sample_Epics` and `Sample_Epics_list` files. Using
JIRA's Issues > Import issues from CSV feature, upload the 
`Sample_Epics_list` as the data source (required) and the
`BulkCreate-Sample_Epics` as the settings file (not required, but easier)
If uploaded correctly and your JIRA instance is compatible, you should see:
![Import Epics to JIRA](/README_images/import-epics-setup.png)

You will still need to specify into which project these Epics should 
be imported.

Once the import is completed, when you return to your project Backlog view:
![Epics in Baclog](/README_images/jira-epics.png)
# Components
One of the most under-used and under-appreciated tools in JIRA, Components
allow users to organize and tag Stories and tickets. For Drupal projects, 
a natural extension is to use Content Types, and Regions to catalog work
and identify connections among tickets, during testing or QA, for example.
