# Working with Legislator Data

## Summary
This challenge is a fairly comprehensive reflection of our understanding of and abilities in applying object-oriented principles, schema design, and Active Record.  The challenge is to build a command line application that allows us to interact with data on U.S. legislators.  We'll be designing a database to hold data pulled from the [Sunlight Foundation][Sunlight Foundation].

We'll be given a list of required functionality for our application, but it's up to us to figure out how to build out that functionality.  What tables should our database have?  What models do we need?  What are the relationships between our classes?  What about views and controllers?  How will we get input from users?  We'll need to make and implement all of these decision ourselves.

### Required Functionality

For a given state ...
- obtain a list of all the state's legislators.
- obtain a list of just the state's representatives.
- obtain a list of just the state's senators

For a given political party ...
- obtain a list of legislators affiliated with the party.
- obtain a list of representatives affiliated with the party.
- obtain a list of senators affiliated with the party.

For a given legislator ...
- obtain a list of attributes:
  - birthday
  - fax
  - gender
  - name
  - party affiliation
  - phone
  - twitter id 
  - webform for e-mail
  - website url
- determine whether the legislator is currently in office.


## Releases

### Pre-release: Running Your Application
Take a minute to get acquainted with the provided code base.  When we run our application, we'll execute the `runner.rb` file.  This file requires another file, `config/environment.rb`, that more-or-less requires everything else we'll need.

Before moving on, let's bundle and create our database.


### Release 0: Models and Migrations
We'll begin this challenge by reflecting on the requirements described in the *Summary*, determining the models we'll need, and determining the design of the database that backs up the models.

After making a decision about what we need, we'll need to implement our decision.  Create the models, write and run the migrations, etc.

What makes our models valid or not?  How will we know whether or not our models behave as expected?


### Release 1: Seed the Database
In order to use our application, we'll need to get the legislator data into the database.  The legislator data can be found in the file `db/data/legislators.csv`.  Based on the requirements of our application, there's data in the CSV file that we don't need and don't want to store.  In addition, the data is not necessarily in the format that we want or it might not conform to our validations.  We might want or need to *scrub* the data before we save it in our database.

A `SunlightLegislatorsImporter` module is provided in the file `lib/sunlight_legislators_importer.rb`.  This module will be responsible for populating our database based on the data in the provided CSV file—we need to define its `.import` method though.

A `db/seeds.rb` file has been provided that calls this `.import` method.  Once we've defined the method, we can run the `db:seed` rake task to seed our database with the legislator data.  Before we try to seed our database, can we know whether or not our importer is working as we expect?


## Conclusion
Sum up the challenge.


[Sunlight Foundation]: https://sunlightfoundation.com/