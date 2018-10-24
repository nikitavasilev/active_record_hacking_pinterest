# Database with Rails - Active Record - Hacking Pinterest Project

This work was done as a project for [The Hacking Project Bootcamp](https://www.thehackingproject.org/).
The goal was to learn the basics of the Database with Rails and build an SQL database of a Pinterest like app with the main functionalities of a Pinterest database, like the pins, users, comments, etc.

## Requirements

You need at least ruby 2.5.1 (maybe under but not tested) and bundler installed on your computer.

1. First of all `git clone the repo`
2. Run `$ cd active_record_hacking_pinterest`
3. Run `$ bundle install`
4. Run `$ rake db:reset` which gonna clean all the cells of our database, and create brand new tables along with our `seeds.rb` file
5. To play with the database run `$ rails console`
6. To check the content of each table, run `sqlite3 db/development.sqlite3` and then run:
	* `.mode column` for better readability
	* `.headers on` to show headers cells in our tables
	* `.tables` to see the list of all tables
	* `SELECT * FROM replace_it_with_the_name_of_a_table;` this command actually shows you the table that you select (don't forget the semicolon at the end!)
	* `.width` if you want to change the width of the columns for better readability. For example, if you wand to set the width of the first column to 20px and the 2nd column to 50px, run `.width 20 50`

### This is the database schema of our app:

```ruby
ActiveRecord::Schema.define(version: 2018_10_24_173756) do

  create_table "comments", force: :cascade do |t|
    t.text "content"
    t.integer "user_id"
    t.integer "pin_id"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.index ["pin_id"], name: "index_comments_on_pin_id"
    t.index ["user_id"], name: "index_comments_on_user_id"
  end

  create_table "pins", force: :cascade do |t|
    t.string "url"
    t.string "title"
    t.integer "user_id"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.index ["user_id"], name: "index_pins_on_user_id"
  end

  create_table "users", force: :cascade do |t|
    t.string "name"
    t.string "pseudo"
    t.string "email"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

end
``` 

## Contributions

This project was build with the help of:
* [Nikita Vasilev](https://github.com/nikitavasilev)
* [Arthur Mansuy](https://github.com/tutus06)
* [Nathaniel Debache](https://github.com/Natdenice)
* [Thomas Charvet](https://github.com/TomacTh)
* [Ysaline Macé](https://github.com/Ysalien)

## Contact

Problems or questions? File an issue at [GitHub](https://github.com/nikitavasilev/active_record_hacking_pinterest/issues).