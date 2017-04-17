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

## Postman
If you're not already familiar with Postman (https://www.getpostman.com), 
I encourage you to do so. It's a great tool for testing and using with API 
endpoints. There is a Chrome app as well as a standalone app.

## JIRA REST API
Unfortunately, it's not as easy to import Components into a project in JIRA.
You can import stories and epics with associations to components, but they
need to be already existing. We'll get around this by leveraging JIRA's REST 
API and the Postman app to import our list of Components. This list is the
JSON file `components_description.json` with Titles and Descriptions. Edit
this file to your liking.

## Set up a Collection in Postman
Once you have downloaded and set up Postman, set up your first Collection.
For this Collection, you'll need the URL of the JIRA instance you'll be 
importing the Components into. First, in the Authorization tab, use Basic 
Auth along with your username and password for the JIRA instance, to create 
a base-64 encoded Header for all requests. You'll need this in the next step.

To shortcut this, you can import the Collection preset, and update this
appropriately. Use the `Add Components.postman_collection.json` file, but 
update:
* JIRA instance URL - `http://YOURJIRAINSTANCE.atlassian.net`
* JIRA project shortcode - `[PROJECTCODE]`

Next, add your username and password to access the JIRA project. Postman
will convert this to a base64 encoded string. In the Authorization tab, 
use Basic Auth along with your username and password for the JIRA instance, 
to create a base-64 encoded Header for all requests. The Header will be 
added automatically.

Once imported, check the Collection header's settings:

![Collection Headers](/README_images/collection-headers.png)

In body, use the following settings to allow us to leverage the data file.
![Collection Body](/README_images/collection-body.png)

To connect these variables - the title and description - we need to 
assign the variables:
![Collection PreRequest](/README_images/collection-prerequest.png)

Once your collection is set up, next go to the Collection Runner, to 
connect it with the data set of Components.
![Collection Runner Setup](/README_images/setup-collection-runner.png)


## More info
For more information about using Postman to run multiple datasets: 
https://www.getpostman.com/docs/multiple_instances

