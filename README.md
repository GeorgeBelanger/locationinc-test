## 2/28/19 Thursday 9:00pm Home
  - Had a lot to do today before my trip to NYC so I am just making my outline and intial thoughts about the project.
    - Here is the original text: 

> This is a small sample exercise, but please approach it as if you were developing this as a real
> project. The goal is to demonstrate:
>
> - Your Ruby/Rails skills
> - Your front-end skills
> - Your web app building skills
> - Your data modeling skills
> - Your coding style and practices
>
> Any reasonably competent programmer can "solve" this exercise—nearly every submission we
> receive *works*. We're looking for more than just a working solution to the problem; we're
> trying to get a feel for your skills as a programmer and how it would be to work with you on a
> team.
>
> It is okay to use libraries beyond the standard ones built into Rails, but keep in mind the goals
> listed above.
>
> __Here's the scenario__
>
> You have been asked to create a web application that shows a sortable table of baseball player
> statistics. The table should show the following statistics for each hitter: AVG, HR, RBI, RUNS,
> SB, and OPS.
>
> The default sort should be by AVG, descending. Clicking on a column header should sort the
> data by the selected column, without reloading the page. Anticipating that many thousands of
> player records will be a part of this system, only the data relevant to the current display should
> be sent to the browser; do not send all rows at once.
>
> Clicking on the same column that is currently being used to sort the players should flip the
> direction of the sort. Only 25 players should be shown at a time (the top or bottom 25
> depending on if it's descending or ascending).
>
> This xml file contains statistics for all baseball players in the Major Leagues during the 1998
> season. Assume you'll eventually have access to similar files for every year from 1930-2005,
> but to provide a proof of concept, you only need to display sortable statistics from 1998.
>
> Please use GitHub to host the application, and host it on Heroku—the free app server and
> database tiers will be more than adequate. You may document some of your design decisions in
> the Readme if there is anything specific that you wish to highlight.
>
> Please let me know if you have any questions!

  - I want to have a styled table with baseball cards for the #1 best and #1 worst player for each stat
  - Here's my breakdown of what is asked and how it is solved, including details and ? uncertainties:
      - A table of baseball players with stats
        - This is going to require a rails application for serving the app 
        - A tr & td HTML table for displaying the stats
        - CSS for styling the table
        - Baseball cards for the #1 best and #1 worst player for each stat
          <img src=images/%current-top-player%.jpg class="image col-4">
        - Flexbox to align table and baseball card horizontally on desktop and vertically on mobile
        - Postgres Database 
          - A command something like `rails create player AVG, HR, RBI, RUNS, SB, and OPS.` to create the migration file for player
          - `rake db:create` to create our schema
          - `rake db:migrate` to create our .db file
          - create a seed file with the xml
          - `rake db:seed` to seed our .db with data
        - Postgres interface using active record
          - some combination with %yield% & @players.first(25) sorted by AVG DESC
      - Click on column header to sort by column
        - This I'm not entirely sure about and would probably have to research it. 
        - This article looks good but I'm not sure if it works without reloading the page. https://richonrails.com/articles/sortable-table-columns
      - Change data shown without reloading page
        - Not sure if I should use AJAX or go into react. With React I get the ability to change the location based on the query which would allow users to press back to go one step back. 
        - Not sure how the ? operator works in the route where you can have localhost:3000?AVG-RUNS-SB and every new sort increments the route and query
        - Would also like a reset button
      - Only show Top/bottom 25 players relevant to that column
        @players.first(25)
      - Needs simple way to incorporate new data
        - Set up a file that takes XML data and turns it into a seed file
      - Styling:
        - Would like to have a transition for the baseball cards when the query changes
        - Would like an initial fade in for the card and table