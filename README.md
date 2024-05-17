# Birthday Paradox
Inspired by a cyber security lecture I attended during university, this paradox lends itself perfectly to a little web application project.
See the [Birthday Problem](https://en.wikipedia.org/wiki/Birthday_problem) on wikipedia.

## Authentication/Security
To minimize on complexity, I am simply generating a UUID and storing this in local storage to keep the user "logged in".

Similarly, the "ownership" of a room is just managed using a local storage key/value pair called "owned" which just allows the user to delete the room when they are finished.

## Database
To store the birthdays for each room, a supabase table is used with the following columns:

| Name | Data Type | Purpose |
| -------- | -------- | -------- |
| id       | int8     | Default primary key |
| created_by | text    | UUID of user that submitted the birthday |
| room    | text    | A truncated UUID that acts as a room ID |
| birthday    | date (yyyy-mm-dd) | The submitted birthday  |

## CI/CD
This application is hosted using GitHub Pages and is available at the domain [daydox.my.to](https://daydox.my.to) which concatenates the last 3 letters out of the words "birthday" and "paradox".

Every time a commit is pushed to the main branch, the website is built using an action and deployed. As this is a static, single file website, there are no build steps.