# Ghost (v4) Deployment on Railway

This example deploys self-hosted version of [Ghost](https://ghost.org/). Internally it uses a MySQL database to store the data.

## ✨ Features

- Ghost
- MySQL

## 💁‍♀️ How to use

- Fork the project
- Go to railway dashboard and setup a new project
- Create a mysql database deployment in the new project
- Add new service based on your gh repository
- 🚨 Add the required environment variables. Attached is a .env.example (template with all the required values)
- Copy the mysql env variables to your ghost service (mysql username, password etc)

## 💁‍♀️ Required variables for the project to deploy

1. BLOG_URL
2. NODE_ENV
3. MYSQLDATABASE
4. MYSQLHOST
5. MYSQLPASSWORD
6. MYSQLPORT
7. MYSQLUSER
8. PORT

## 💁‍♀️ Extra variables for a production grade deployment

1. CLOUDINARY_URL
2. MAILGUN_SMTP_LOGIN
3. MAILGUN_SMTP_PASSWORD

- If you do not add the `CLOUDINARY_URL` environment variable, your images/files will not be persisted between deploys.
- Add the `MAILGUN_SMTP_LOGIN` and `MAILGUN_SMTP_PASSWORD` variables if you want to invite users to your admin panel or send emails to your subscribers when you publish a new post.

## 📝 Notes

- Railway's filesystem is ephemeral which is why any changes to the filesystem are not persisted between deploys. This is why, this example uses Cloudinary for storage.
- The above limitation also affects the way themes work with Ghost, we use the `bin/themes.sh` script to copy over the themes every time you deploy. That way, the theme is always present.
  - To add a theme, first add the package as a dependency to the `package.json` file and then add it to the list of themes in the `bin/themes.sh` file.
  - Do NOT add a theme directly using the Ghost UI, it will look like it worked but will break whenever you deploy your app again.

## 📝 Final Step

Incase you encounter the `yarn could not be found` error, upon deployment, change the start command of the ghost service to use npm

```bash
npm run start
```
