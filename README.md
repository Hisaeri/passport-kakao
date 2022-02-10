# Passport-kakao

Kakao oauth2 passport login module.

## Install

```sh
npm install passport-kakao-oauth2
```

## How to use

- Register a web app on https://developers.kakao.com/
- Setup the strategy on your app

```javascript
const passport = require('passport')
const KakaoStrategy = require('passport-kakao').Strategy

passport.use(new KakaoStrategy({
    clientID : clientID,
    clientSecret: clientSecret,
    callbackURL : callbackURL
  },
  (accessToken, refreshToken, profile, done) => {
    User.findOrCreate(..., (err, user) => {
      if (err) { return done(err) }
      return done(null, user)
    })
  }
))
```

## Profile information

You can get the following properties from the user profile.

| key      | value  | Note                                      |
| -------- | ------ | ----------------------------------------- |
| provider | String | kakao                                     |
| id       | Number | User kakao ID                             |
| \_raw    | String | User JSON stringified profile information |
| \_json   | Object | User JSON profile information             |

## Sample

1. Set "appKey" of `./sample/sample.js` to you app key.
2. Run the app and go to `127.0.0.1:3000/login` in your browser.

```
cd ./sample
npm install
node app
```
