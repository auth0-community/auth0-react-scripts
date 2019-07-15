# React Scripts
[![All Contributors](https://img.shields.io/badge/all_contributors-1-orange.svg?style=flat-square)](#contributors)
<img src="https://img.shields.io/badge/community-driven-brightgreen.svg"/> <br>

Use [create-react-app](https://github.com/facebookincubator/create-react-app) to bootstrap a new React project with authentication.

This repo is not a fork of `create-react-app`. It's just a fork of `react-scripts` with modifications to the project template.

This repo is supported and maintained by Community Developers, not Auth0. For more information about different support levels check https://auth0.com/docs/support/matrix .

## Getting started

### Installation

```
create-react-app my-app --scripts-version auth0-react-scripts
```

- Create a `.env` file at the root of the project with your Auth0 configurations. You can find your Auth0 clientId and domain at your dashboard: https://manage.auth0.com/#/clients

- Add `http://localhost:3000/login` to your [Auth0 callback URLs](https://manage.auth0.com/#/clients).

## Usage

Here you can find a link to example: [sample app](https://auth0-react-app.now.sh)

### Auth Helpers

**login(lockOptions)**

Show [Auth0 lock](https://auth0.com/lock). Accepts any options that [`lock.show()`](https://github.com/auth0/lock#showoptions) accepts.

**logout()**

Clears authentication token from the browser and redirects to `/login`.

**requireAuth**

An [onEnter handler](https://github.com/ReactTraining/react-router/blob/master/docs/API.md#onenternextstate-replace-callback) for `react-router`. Add this handler to any `Route` that requires an authenticated user. The handler will ensure the user is authenticated before displaying the route. If the user is not authenticated, the handler will redirect them to `/login` and return them back to their previous route once they authenticate.

```js
<Route path="/profile/edit" component={EditProfile} onEnter={requireAuth} />
```

**connectProfile(Component)**

Connects a react component to an authenticated user's profile. It does not modify the component class passed to it. Instead, it returns a new, connected component class, for you to use. Your wrapped component will receive two additional props:

* **profile**
	An [Auth0 Profile](https://auth0.com/docs/user-profile) object for an authenticated user.

* **onUpdateProfile(attributes)**
	Call to update profile. Returns a `Promise` that may resolve into an error if the update fails.

	*Tip: The profile props can be quickly added to your component's `propTypes` with `connectProfile.PropTypes`*

```js
static propTypes = {
  ...connectProfile.PropTypes
}
```

**fetchAsUser(input, init)**

A wrapper around [`window.fetch`](https://developer.mozilla.org/en-US/docs/Web/API/GlobalFetch), that will automatically set the `Authorization` header when a user is authenticated.

## Contribute

Feel like contributing to this repo? We're glad to hear that! Before you start contributing please visit our [Contributing Guideline](https://github.com/auth0-community/getting-started/blob/master/CONTRIBUTION.md) and [Contributing file](https://github.com/auth0-community/auth0-react-scripts/blob/master/CONTRIBUTING.md) of this repo.

Here you can also find the [PR template](https://github.com/auth0-community/auth0-react-scripts/blob/master/PULL_REQUEST_TEMPLATE.md) to fill once creating a PR. It will automatically appear once you open a pull request.

## Issues Reporting

Spotted a bug or any other kind of issue? We're just humans and we're always waiting for constructive feedback! Check our section on how to [report issues](https://github.com/auth0-community/getting-started/blob/master/CONTRIBUTION.md#issues)!

Here you can also find the [Issue template](https://github.com/auth0-community/auth0-react-scripts/blob/master/ISSUE_TEMPLATE.md) to fill once opening a new issue. It will automatically appear once you create an issue.

## Repo Community

Feel like PRs and issues are not enough? Want to dive into further discussion about the tool? We created topics for each Auth0 Community repo so that you can join discussion on stack available on our repos. Here it is for this one: [React Scripts](https://community.auth0.com/t/auth0-community-oss-auth0-react-scripts/16000)

<a href="https://community.auth0.com/">
<img src="/assets/join_auth0_community_badge.png"/>
</a>

## License

This project is licensed under the MIT license. See the [LICENSE](https://github.com/auth0-community/auth0-react-scripts/blob/master/LICENSE) file for more info.

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like
  * Google
  * Facebook
  * Microsoft
  * Linkedin
  * GitHub
  * Twitter
  * Box
  * Salesforce
  * etc.

  **or** enterprise identity systems like:
  * Windows Azure AD
  * Google Apps
  * Active Directory
  * ADFS
  * Any SAML Identity Provider

* Add authentication through more traditional [username/password databases](https://docs.auth0.com/mysql-connection-tutorial)
* Add support for [linking different user accounts](https://docs.auth0.com/link-accounts) with the same user
* Support for generating signed [JSON Web Tokens](https://docs.auth0.com/jwt) to call your APIs and create user identity flow securely
* Analytics of how, when and where users are logging in
* Pull data from other sources and add it to user profile, through [JavaScript rules](https://docs.auth0.com/rules)

## Create a free Auth0 account

* Go to [Auth0 website](https://auth0.com/signup)
* Hit the **SIGN UP** button in the upper-right corner

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
<table>
  <tr>
    <td align="center"><a href="http://ryanchenkie.com"><img src="https://avatars1.githubusercontent.com/u/1847678?v=4" width="100px;" alt="Ryan Chenkie"/><br /><sub><b>Ryan Chenkie</b></sub></a><br /><a href="https://github.com/auth0-community/auth0-react-scripts/commits?author=chenkie" title="Code">💻</a></td>
  </tr>
</table>

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!