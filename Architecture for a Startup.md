- **URL:** https://medium.com/p/86651962bc99
- **Author:** Mitesh
- **Tags:** #articles
- **Date:** [[2021-05-13]]
---

Static web app: We had a static website that was deployed on S3 and served using the static web hosting feature provided by S3. I added a CloudFront CDN in front of S3 to serve users faster, as CDN will cache content. All domains were routed through Route53 %% highlight_id: 113319203 %%


Monitoring: We used the NewRelic free tier for monitoring the system along with a self-hosted sentry server to catch all server issues. Sentry was very helpful for catching backend bugs that came when the application is live. Sentry was deployed in separate admin VPC as that is the same for all environments %% highlight_id: 113319197 %%


Deployment: We used Jenkins for deployment. I tried using other tools but felt at home with Jenkins. Overall philosophy was to build once, deploy everywhere. We had two jobs for each deployment, one which builds a branch and the other which deploys that build. This way we can have the same build deployed on any environment. This was deployed in admin VPC which was used for common use cases. %% highlight_id: 113319195 %%


Metabase is an open-source business analytics server. This was deployed in the app subnet and exposed using ALB with Cognito (google auth) to keep access secure for internal users only. %% highlight_id: 113319202 %%


Terraform is used for infrastructure as code and Ansible is used as configuration management. %% highlight_id: 113319204 %%

