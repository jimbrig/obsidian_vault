%%
ID: 6408956
Updated: 2021-05-13
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[Readwise/Articles/Architecture for a Startup]]
Author: [[Mitesh]]
Category: #articles
Number of Highlights: ==5==
Last Highlighted: *2020-11-25*
Readwise URL: https://readwise.io/bookreview/6408956
Source URL: https://medium.com/p/86651962bc99


# Highlights 
Deployment: We used Jenkins for deployment. I tried using other tools but felt at home with Jenkins. Overall philosophy was to build once, deploy everywhere. We had two jobs for each deployment, one which builds a branch and the other which deploys that build. This way we can have the same build deployed on any environment. This was deployed in admin VPC which was used for common use cases.  ^113319195

---

Monitoring: We used the NewRelic free tier for monitoring the system along with a self-hosted sentry server to catch all server issues. Sentry was very helpful for catching backend bugs that came when the application is live. Sentry was deployed in separate admin VPC as that is the same for all environments  ^113319197

---

Metabase is an open-source business analytics server. This was deployed in the app subnet and exposed using ALB with Cognito (google auth) to keep access secure for internal users only.  ^113319202

---

Static web app: We had a static website that was deployed on S3 and served using the static web hosting feature provided by S3. I added a CloudFront CDN in front of S3 to serve users faster, as CDN will cache content. All domains were routed through Route53  ^113319203

---

Terraform is used for infrastructure as code and Ansible is used as configuration management.  ^113319204

