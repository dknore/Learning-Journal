# Heroku

Heroku lets you deploy, run and manage applications written in Ruby, Node.js, Java, Python, Clojure, Scala, Go and PHP.
### <u>Deploy</u>
Applications consist of your source code, a description of any dependencies, and a Procfile.
<u>**Procfiles**</u> list process types - named commands that you may want executed.
Deploying applications involves sending the application to Heroku using either Git, GitHub, Dropbox, or via an API.
<u>**Buildpacks**</u> lie behind the slug compilation process. Buildpacks take your application, its dependencies, and the language runtime, and produce slugs.
A <u>**slug**</u> is a bundle of your source, fetched dependencies, the language runtime, and compiled/generated output of the build system - ready for execution.
<u>**Config vars**</u> contain customizable configuration data that can be changed independently of your source code. The configuration is exposed to a running application via environment variables.
<u>**Add-ons**</u> are third party, specialized, value-added cloud services that can be easily attached to an application, extending its functionality.
A <u>**release**</u> is a combination of a slug (your application), config vars and add-ons. Heroku maintains an append-only ledger of releases you make.

### <u>Runtime</u>
<u>**Dynos**</u> are isolated, virtualized Unix containers, that provide the environment required to run an application.
Your application’s <u>**dyno formation**</u> is the total number of currently-executing dynos, divided between the various process types you have scaled.
The <u>**dyno manager**</u> is responsible for managing dynos across all applications running on Heroku.
Applications that use the free dyno type will <u>**sleep**</u> after 30 minutes of inactivity. Scaling to multiple web dynos, or a different dyno type, will avoid this.
<u>**One-off Dynos**</u> are temporary dynos that run with their input/output attached to your local terminal. They’re loaded with your latest release.
Each dyno gets its own <u>**ephemeral filesystem**</u> - with a fresh copy of the most recent release. It can be used as temporary scratchpad, but changes to the filesystem are not reflected to other dynos.
<u>**Logplex**</u> automatically collates log entries from all the running dynos of your app, as well as other components such as the routers, providing a single source of activity.
<u>**Scaling**</u> an application involves varying the number of dynos of each process type.