## UpWork Task - Authenticate Tinder API using FB Access token

Create an authentication mechanism that can obtain facebook access token to be used for authentication with Tinder based app - http://tindhancer.com/

Preference is given to the following solution
![image](image.png)

### User Story

- Given I am on a “Home Page” of TindHancer.com
- And I am the existing Tinder's User
- When I click on “Login With Facebook”
- Then I expect to see a pop up - [confirmation window](https://www.facebook.com/v2.6/dialog/oauth?redirect_uri=fb464891386855067%3A%2F%2Fauthorize%2F&scope=user_birthday%2Cuser_photos%2Cuser_education_history%2Cemail%2Cuser_relationship_details%2Cuser_friends%2Cuser_work_history%2Cuser_likes&response_type=token%2Csigned_request&client_id=464891386855067&ret=login&fallback_redirect_uri=221e1158-f2e9-1452-1a05-8983f99f7d6e&ext=1556057433&hash=Aea6jWwMP_tDMQ9y) - `You previously logged in to Tinder with Facebook.Would you like to continue?`
- When I hit OK there will be a POST request to [confirm](https://www.facebook.com/v2.9/dialog/oauth/confirm/)
- The body of the the response of POST request will contain Token 
- Parse the BODY for 'access_token' in the response

Once token is retrieved, store it in the local storage.

To test the correct access Token place it as into the POST body:

```
curl --location --request POST 'https://api.gotinder.com/v2/auth/login/facebook' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'platform: web' \
--header 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/77.0.3865.90 Safari/537.36' \
--header 'Content-Type: application/json' \
--data-raw '{"token": "%FACEBOOK_ACCESS_TOKEN%"}'
```

to get simular response:

```
{
    "meta": {
        "status": 200
    },
    "data": {
        "_id": "9e68ceffb2fbde0100dfe1k2",
        "api_token": "7705c759-ac26-4bd3-942d-d6cbahheaf6c",
        "refresh_token": "eyJhbGciOpnIUzI1NiJ9.ODEzMjM5ODI5MTYwNDAw.sOZ1HTWNiZxzoG-GnNVYo5PK27Flj8Afslz2T669kHU",
        "is_new_user": false
    }
}
```

### Helpful Links & Resorses

[Getting access token](https://gist.github.com/taseppa/66fc7239c66ef285ecb28b400b556938)

[Tinder web based app](https://tinder.com/)

---

To complete this task please use this repo which is bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.
