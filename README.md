# Keep Me Up
Ping websites to prevend them from spinning down

## Installation

  * Add `Upfile` with a list of websites (full URL e.g. `http://www.thefeedbackbutton.com/`) on separate lines
  * Upload to heroku.
  * schedule worker: `heroku addons:add scheduler:standard` and add task to it `rake up:all`

## Debugging

  * run `heroku logs -t` to see if the pings are not failing.

## Deadman's Snitch

  Set `KMA_DMS_KEY` to your [Deadman's Snitch](https://deadmanssnitch.com) hash and get email alerts on failed pings with:

  `heroku config:add KMA_DMS_KEY=55592ba555`

  You can get your hash id from the URL provided by DMS: `https://nosnch.in/55592ba555`

  Optionally, you can set a custom message: `heroku config:add KMA_MESSAGE="Hello from keep-me-up"`


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/yurikoval/keep-me-up/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

