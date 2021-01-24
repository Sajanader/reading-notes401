## Deploying Your Next.js App
### Push to GitHub
Before we deploy, let’s push our Next.js app to GitHub if you haven’t done so already. This will make deployment easier.

>>On your personal GitHub account, create a new repository called nextjs-blog.
The repository can be public or private. You do not need to initialize it with a README or other files.
If you need help setting up your repo, take a look at this guide on GitHub.
Then:

>> If you haven’t initialized the git repository locally for your Next.js app, do so now.
Push the Next.js app to your GitHub repository.
To push to GitHub, you can run the following commands (replace <username> with your GitHub username):

```
git remote add origin https://github.com/<username>/nextjs-blog.git
git push -u origin main
```

>> Once your GitHub repository is ready, continue to the next page.

## Deploy to Vercel
The easiest way to deploy Next.js to production is to use the Vercel platform developed by the creators of Next.js.

Vercel is an all-in-one platform with Global CDN supporting static & JAMstack deployment and Serverless Functions. We believe Vercel is the optimal place to deploy Next.js apps. You can start using it for free — no credit card required.

### Create a Vercel Account

> First, go to https://vercel.com/signup to create a Vercel account. Choose Continue with GitHub and go through the sign up process.

> Import your nextjs-blog repository
Once you’re signed up, import your nextjs-blog repository on Vercel. You can do so from here: https://vercel.com/import/git.

> You’ll need to Install Vercel for GitHub. You can give it access to All Repositories.
Once you’ve installed Vercel, import nextjs-blog.
You can use default values for the following settings — no need to change anything. Vercel automatically detects that you have a Next.js app and chooses optimal build settings for you.

```
Project Name
Root Directory
Build Command
Output Directory
```
Development Command
When you deploy, your Next.js app will start building. It should finish in under a minute.


>> When it’s done, you’ll get deployment URLs. Click on one of the URLs and you should see the Next.js starter page live.

>> Congratulations! You just deployed your Next.js app to production. On the next page, we’ll go into the details of Vercel and the recommended workflow.


## Next.js and Vercel
Vercel is made by the creators of Next.js and has first-class support for Next.js. When you deploy your Next.js app to Vercel, the following happens by default:

>> Pages that use Static Generation and assets (JS, CSS, images, fonts, etc) will automatically be served from the Vercel Edge Network, which is blazingly fast.
Pages that use Server-Side Rendering and API routes will automatically become isolated Serverless Functions. This allows page rendering and API requests to scale infinitely.
Vercel has many more features, such as:

>> Custom Domains: Once deployed on Vercel, you can assign a custom domain to your Next.js app. Take a look at our documentation here.

>> Environment Variables: You can also set environment variables on Vercel. Take a look at our documentation here. You can then use those environment variables in your Next.js app.

>> Automatic HTTPS: HTTPS is enabled by default (including custom domains) and doesn't require extra configuration. We auto-renew SSL certificates.

