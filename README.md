Ping websites to prevend them from spinning down

## Installation

  * Add `Upfile` with a list of websites (full URL e.g. `http://www.thefeedbackbutton.com/`) on separate lines
  * Upload to heroku.
  * schedule worker: `heroku addons:add scheduler:standard` and add task to it `rake up:all`
