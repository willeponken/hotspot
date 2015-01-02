Hotspot (Work in Progress) [![Build Status](https://travis-ci.org/willeponken/hotspot.svg)](https://travis-ci.org/willeponken/hotspot)
=======

Captive portal for CJDNS

## TODO
- [x] Don't use a upload form for the cjdroute.conf (security problems)
- [ ] Work out how this should be done?

## Vision
The idea is to have a CJDNS-only network, but before that, people want to be able to access the Internet.
This ~~is a~~ will be a general purpose captive portal, but as I'm in quite a hurry for my school project (inter alia this) there is some hardcoded stuff.

## Contribute
I appreciate contributions, but also scolding for mistakes, etc.

## Deploy & setup
### Easy way
`npm install && npm start`

### Custom way
Download all dependenices with `npm install`

Now you can edit the view and stylesheets for a custom appearance.

* Views `views/`
* Stylesheets `public/src/stylesheets/`

You'll then need to rebuild the stylesheets with `npm install` or `bin/make`.

To start the hotspot, run `npm start` or `bin/hotspot`

## Test
Run tests with
`npm test`

## How
Here I'll brainstorm how this should be done.

### Basic CJDNS -> Hypeboria connection
| CLIENT                                                      | SERVER                                |
|-------------------------------------------------------------|---------------------------------------|
| Connect via WiFi through AP which gateway is the server.    |                                       |
| Tries to connect to a webpage.                              |                                       |
|                                                             | Redirecting to captive portal.        |
| Registering at the captive portal.*                         |                                       |
| Downloads CJDNS from captive portal, and then runs it.      |                                       |

* Could be removed and only show the user a download link for CJDNS and instructions.

### IP Tunnel connection to Internet
| CLIENT                                                      | SERVER                                                                     |
|-------------------------------------------------------------|----------------------------------------------------------------------------|
| Tries to access non-local IPv4 and IPv6.                    |                                                                            |
|                                                             | Redirecting to captive portal.                                             |
| Clicks on IP Tunnel registration.                           |                                                                            |
|                                                             | Creates credentials for user and add him/her to CJDNS.                     |
|                                                             | Present credentials to user that he/she should add to their cjdroute.conf. |
| Adds credentials.                                           |                                                                            |
| Restarts CJDNS.                                             |                                                                            |
| Tada! Able to access Internet.                              |                                                                            |
