# Cashflow 2.0

Django project to manage receipts and reimbursements at Datasektionen.

## Developing locally

Cashflow uses Python 3.6.2

- Install PostgreSQL

- `pipenv install`

- `pipenv run ./manage.py migrate`

- `pipenv run ./manage.py runserver`

The server will restart on file changes.

## Environment variables

The following environment variables are required to run the project:


| Variable             | Description                          | Default                        |
| -------------------- | ------------------------------------ | ------------------------------ |
| DATABASE_URL         | PostgreSQL server url                | ---                            |
| DEBUG                | Django debug mode. Set to True when developing locally. Never set to True in production.                     | False                          |
| SECRET_KEY           | Django encryption key                | ---                            |
| LOGIN_KEY            | Login API key for KTH authentication | ---                            |
| S3_BUCKET_NAME       | Amazon AWS s3 bucket name            | ---                            |
| S3_ACCESS_KEY_ID     | Amazon AWS IAM access key id         | ---                            |
| S3_SECRET_ACCESS_KEY | Amazon AWS IAM secret access key     | ---                            |
| S3_USE_SIGV4         | If Frankfurt, set to False           | True                           |
| S3_HOST              | Url to s3 server                     | s3.eu-central-1.amazonaws.com  |
| SPAM_API_KEY         | API key for the spam mail system     | ---                            |
| SPAM_URL             | URL to spam service                  | https://spam.datasektionen.se  |
| PLS_URL              | URL to pls service                   | https://pls.datasektionen.se   |
| LOGIN_URL            | URL to login service                 | https://login.datasektionen.se |
| SEND_EMAILS          | If False, does not send emails       | True                           |

They can be put in an .env-file in root. They will be loaded automatically by `pipenv`.

Check out [.env.example](.env.example) for an example.

## Protip
The default max upload size in nginx is 1 MB. To allow larger file uploads, set the max size of file uploads to for example 100 MB.

```bash
echo "client_max_body_size 100M;" > /home/dokku/cashflow/nginx.conf.d/max_size.conf
```
