MIT (Most Important Task)
=========================

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](http://opensource.org/licenses/MIT)
![Version](https://img.shields.io/badge/version-1.3-green.svg)

Overview
--------

Most Important Tasks addon for todo.txt-cli.

MIT adds functionality to Gina Trapani's [todo.txt-cli](https://github.com/ginatrapani/todo.txt-cli).  MITs are intended to be critical tasks that need to be accomplished on a particular day.  You can read more about MITs here:

* [zenhabits](http://zenhabits.net/purpose-your-day-most-important-task/)
* [lifehacker](http://lifehacker.com/software/top/geek-to-live--control-your-workday-187074.php)

Installation
------------

1. Install and configure [todo.txt-cli](https://github.com/ginatrapani/todo.txt-cli).
2. Ensure TODO_ACTIONS_DIR is defined in todo.cfg or in your profile.
3. Place mit in your actions directory.
4. Ensure mit is executable.

Usage
-----

The mit addon can be used to both view and add MITs.

__To add mits:__

    todo.sh mit [DATE|DAY] [task]

    $ todo.sh mit tue buy dog food @chores
    113 {2013.06.04} buy dog food @chores
    TODO: 113 added.
    $

A date or day is required along with the task.  Dates must be in the format of YYYY.MM.DD.  Days can be days of the week (Monday, Tuesday, etc.), or abbreviated days of the week (Mon, Tue, etc.).  "Today" or "Tomorrow" are also accepted.

__To view mits:__

    todo.sh mit [not @context|@context]

    $ todo.sh mit @chores
    Tuesday, June 04:
      buy dog food @chores (113)

    $

Specifying a context to filter by is optional but can be helpful if you define MITs for multiple contexts.  MITs will be grouped by day with any old incomplete MITs listed under "Past Due:".

__To move mits:__

    todo.sh mit mv [ID] [DATE|DAY]

    $ todo.sh mit mv 113 tomorrow
    TODO: MIT 'buy dog food @chores' moved to tomorrow.
    $

As with adding mits dates must be in the format of YYYY.MM.DD, day names are accepted, or you can specify "Today" or "Tomorrow".  Thanks to [rcraggs](https://github.com/rcraggs) you can now convert non-mit tasks to mits with the move command as well, the usage is the same.

__To convert mits to normal tasks:__

    todo.sh mit rm [ID]

    $ todo.sh mit rm 113
    Removed MIT from task 113
    $

  Another bit of functionality provided by [rcraggs](https://github.com/rcraggs) that allows you to convert a mit to a normal task.

Format
------

MITs are stored directly in the todo.txt file with the following format:

    {YYYY.MM.DD} task info @context         # standard mit with set context
    {YYYY.MM.DD} (A) task info @context     # prioritized mit with set context
    {YYYY.MM.DD} (A) 2013-05-29 task info   # mit with priority and date added (-t option)


MITs are displayed as follows:

    Past Due:                               # all past due items displayed here
      mow the lawn @home (13)               # task numbers displayed on the end

    Today:
      change oil in car (23)
      prepare tps report @work (15)

    Wednesday:
      buy groceries @shopping (28)

    Monday, December 17:                    # anything a week out or more gets a date
      call mother (30)
