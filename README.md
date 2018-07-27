# Brown University CBC Dockerhub Autobuild Practices

**Warning: Any push to this repository, irrespective of its nature, will trigger an autobuild event; that includes updating this README file.**  That probably won't break anything if the dockerfile isn't edited, but it will cause redundant builds to appear in the build log.

## Docker Autobuild

The purpose of this repository is to host our conda-build dockerfile and automate its building into a usable image.  This repository is integrated with Dockerhub through a process called 'autobuild', wherein pushed changes to conda-build/Dockerfile will be automatically built and hosted on Dockerhub as an image bearing that name.  Any change that is pushed will cause the dockerfile to be submitted to Dockerhub's autobuild queue, beginning a build process that takes approximately 30 minutes depending service congestion.

### Accessing the CBC Dockerhub

To gain access to our Dockerhub organization, please contact Ashok to be added.

Once you've been added, navigate to your Dockerhub landing page (hub.docker.com), then locate your username within a wide white rectangle in the upper left corner.  Click it, and then select 'compbiocore' from the resulting dropdown menu, as depicted below:

![Select organization](https://raw.githubusercontent.com/compbiocore/dockerfiles/master/docs/dockerhub_organization.png)

There, you will see one or more docker images; the one associated with this github repository, `compbiocore/dockerfiles` will appear as follows:

![Docker image](https://raw.githubusercontent.com/compbiocore/dockerfiles/master/docs/dockerhub_image.png)


### Docker Autobuild Tag

Dockerhub autobuild tagging is a bit confusing.  Generally, a dockerfile's version number is noted in the dockerfile itself with the syntax `LABEL tag [version]`; autobuild images have tags that work differently, and must be explicitly defined on the Dockerhub site.

To access the tagging screen, click on the repository depicted in the screenshot above, then click on 'Build Settings'.  Once there, you will see a variety of options regarding the autobuild process.  The important one for our purposes is 'Docker Tag Name'; no other option should be changed without talking to Ashok or Andrew first.

![Autobuild tag](https://raw.githubusercontent.com/compbiocore/dockerfiles/master/docs/dockerhub_tag.png)

**It is imperative that this tag be manually incremented before pushing a new version of the dockerfile** (not including when pushing bug fixes etcetera).  Any push will be built using the specified tag, meaning old versions will be overwritten unless the tag is updated.  This update must be manual, as autobuild is unable to parse the `LABEL tag [version]` information from inside the dockerfile.

Be absolutely sure you've updated the tag as instructed before pushing, else an important image may be accidentally overwritten.