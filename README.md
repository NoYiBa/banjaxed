# Banjaxed

Banjaxed is an incident management tool.


# Configuration

GitHub OAuth is used to authenticate users. You'll need to [register an application](https://github.com/settings/applications/new) and make the details available as environment variables, as well as the organisation to use to restrict access.

| Name                 | Purpose                                                    |
| -------------------- | ---------------------------------------------------------- |
| GITHUB_CLIENT_ID     | GitHub OAuth client ID to use for authentication.          |
| GITHUB_CLIENT_SECRET | GitHub OAuth client secret to use for authentication.      |
| GITHUB_ORG           | Only members of this GitHub organisation will have access. |


# Deployment

Banjaxed is a simple Rails app and should be relatively straightforward to deploy.

It is configured to use Postgres by default, but should work with any Active Record database adapter.


## On Heroku

Here's how you could deploy Banjaxed on Heroku from the command line:

```
git clone git@github.com:intercom/banjaxed.git
cd banjaxed
heroku apps:create
heroku addons:add heroku-postgresql:hobby-basic
heroku config:set GITHUB_CLIENT_ID=x GITHUB_CLIENT_SECRET=y GITHUB_ORG=z
git push heroku
heroku run rake db:schema:load
heroku apps:open
```

Obviously, you'll want to use actual valid GitHub application details.

The GitHub application's callback URL will need to be updated to match the Heroku app.
