# auth0-react-scripts

Use [create-react-app](https://github.com/facebookincubator/create-react-app) to bootstrap a new React project with authentication.

## Example

https://auth0-react-app.now.sh

## Disclaimer

This repo is not a fork of `create-react-app`. It's just a fork of `react-scripts` with modifications to the project template.

## Setup

```
create-react-app my-app --scripts-version auth0-react-scripts
```

- Create a `.env` file at the root of the project with your Auth0 configurations. You can find your Auth0 clientId and domain at your dashboard: https://manage.auth0.com/#/clients

- Add `http://localhost:3000/login` to your [Auth0 callback URLs](https://manage.auth0.com/#/clients).

## Auth Helpers

### `login(lockOptions)`

Show [Auth0 lock](https://auth0.com/lock). Accepts any options that [`lock.show()`](https://github.com/auth0/lock#showoptions) accepts.

### `logout()`

Clears authentication token from the browser and redirects to `/login`.

### `requireAuth`

An [onEnter handler](https://github.com/ReactTraining/react-router/blob/master/docs/API.md#onenternextstate-replace-callback) for `react-router`. Add this handler to any `Route` that requires an authenticated user. The handler will ensure the user is authenticated before displaying the route. If the user is not authenticated, the handler will redirect them to `/login` and return them back to their previous route once they authenticate.

```js
<Route path="/profile/edit" component={EditProfile} onEnter={requireAuth} />
```

### `connectProfile(Component)`

Connects a react component to an authenticated user's profile. It does not modify the component class passed to it. Instead, it returns a new, connected component class, for you to use. Your wrapped component will receive two additional props:

#### `profile`

An [Auth0 Profile](https://auth0.com/docs/user-profile) object for an authenticated user.

#### `onUpdateProfile(attributes)`

Call to update profile. Returns a `Promise` that may resolve into an error if the update fails.

*Tip: The profile props can be quickly added to your component's `propTypes` with `connectProfile.PropTypes`*

```js
static propTypes = {
  ...connectProfile.PropTypes
}
```

### `fetchAsUser(input, init)`

A wrapper around [`window.fetch`](https://developer.mozilla.org/en-US/docs/Web/API/GlobalFetch), that will automatically set the `Authorization` header when a user is authenticated.

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, among others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
* Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
* Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
* Support for generating signed [JSON Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
* Analytics on how, when and where users are logging in.
* Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a free Auth0 account

1. Go to [Auth0](https://auth0.com/signup) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to log in.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## Author

[Auth0](https://auth0.com)

## License

This project is licensed under the MIT license. See the [LICENSE](LICENSE.txt) file for more info.
