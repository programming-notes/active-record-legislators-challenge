# Activerecord Congress Database 1 Modeling Congresspeople 
 
##Learning Competencies 

* Identify and implement classes based on real world requirements
* Use the model-view-controller pattern to organize code and decouple concerns
* Model relationships in a relational database (one-to-one, one-to-many, many-to-many)
* Use Active Record Migrations to create a database
* Use Active Record Queries to query a database
* Use Active Record to create Associations between database tables

##Summary 

We're going to work with some [Sunlight Labs](http://sunlightlabs.com/) data again. This time, however, we're going to model things using ActiveRecord instead of plain old SQL.

The data can be found in the `db/data/legislators.csv` file, but can also be viewed [here](https://raw.github.com/dbc-challenges/ar-sunlight-legislators/master/db/data/legislators.csv).

##Releases

###Release 0 : Create your models and migrations

Looking at the data, figure out what is the best way to model it. Consider the following requirements:

1. Given a state, I can obtain a list of representatives in the House for that state.
2. Given a state, I can obtain the two senators for that state.
3. Given a political party, I can obtain a list of senators with that party affiliation.
4. Given a political party, I can obtain a list of representatives in the House with that party affiliation.
5. Given a senator or representative, I can obtain any of the following attributes: name, phone, fax, website, webform(for email), party affiliation, gender, birthdate, and twitter_id.
6. Given a senator or representative, I can determine whether s/he is currently actively in office.

Before you begin, think carefully about how to best use ActiveRecord to model things. How many tables do you need? How many models? Does each model have its own table? What kind of validations (if any) should there be on the models?

Remember, models belong in the `app/models` folder and should be named as singular (i.e., `senator.rb` and `class Senator`). Migrations belong in the `db/migrate` folder and should be named `<YYYYMMDDHHMMSS>_<migration_name>.rb`. Table names are always plural (i.e., `senators`).

Can you test your data?  Are your validations working?  Try some edge cases.


###Release 1 : Scrub and import the data

Now that you've finished modeling the data using ActiveRecord models, you need to import the data. We've stubbed out the outline of a class that should be able to handle the import. It can be found in the `lib/sunlight_legislators_importer.rb` file. The hooks for the work you need to do can be found between the block that looks like this:

```ruby
# TODO: begin
raise NotImplementedError, "TODO: figure out what to do with this row and do it!"
# TODO: end
```

Don't bother importing any fields that won't be used and be sure that you properly "scrub" the data so that it will pass any validations you have on your model(s). For example, do you *really* want to store dashes (i.e., `-`) in the phone numbers?

How will you run your importer?  Is this a "one-off" task?  Refer to previous challenges like AR Student Schema if you get lost on this.

###Release 2 : Write some ActiveRecord queries

Write some ruby that uses [ActiveRecord queries](http://guides.rubyonrails.org/active_record_querying.html) to handle the requirements as specified below. It's probably best to store your code in a simple ruby script, perhaps in `app/main.rb`. Since these are really just one-off pieces of code you're writing, don't worry too much about structure.

1. Given any state, first print out the senators for that state (sorted by last name), then print out the representatives (also sorted by last name). Include the party affiliation next to the name. The output might look something like this:

    ```
    Senators:
      Barbara Boxer (D)
      Diane Feinstein (D)
    Representatives:
      Xavier Becerra (D)
      Howard L. Berman (D)
      Brian P. Bilbray (R)
      (... etc., etc., ...)
      Diane E. Watson (D)
    ```

2. Given a gender, print out what number and percentage of the senators are of that gender as well as what number and percentage of the representatives, being sure to include only those congresspeople who are actively in office, e.g.:

    ```
    Male Senators: 83 (83%)
    Male Representatives: 362 (83%)
    ```

3. Print out the list of states along with how many active senators and representatives are in each, in descending order (i.e., print out states with the most congresspeople first).

    ````
    CA: 2 Senators, 53 Representative(s)
    TX: 2 Senators, 32 Representative(s)
    NY: 2 Senators, 29 Representative(s)
    (... etc., etc., ...)
    WY: 2 Senators, 1 Representative(s)
    ````

4. For Senators and Representatives, count the total number of each (regardless of whether or not they are actively in office).

    ```
    Senators: 137
    Representatives: 603
    ```

5. Now use ActiveRecord to delete from your database any congresspeople who are not actively in office, then re-run your count to make sure that those rows were deleted.

    ```
    Senators: 100
    Representatives: 435
    ``` 

<!-- ##Optimize Your Learning  -->

##Resources

* [ActiveRecord queries](http://guides.rubyonrails.org/active_record_querying.html)