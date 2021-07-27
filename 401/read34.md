##  Configuring Django Settings: Best Practices
Different environments. Usually, you have several environments: local, dev, ci, qa, staging, production, etc. Each environment can have its own specific settings (for example: DEBUG = True, more verbose logging, additional apps, some mocked data, etc). You need an approach that allows you to keep all these Django setting configurations.

Sensitive data.
Sharing settings between team members.
Django settings are a Python code.

### Setting Configuration: Different Approaches
1. settings_local.py
The basic idea of this method is to extend all environment-specific settings in the settings_local.py file, which is ignored by VCS. Here’s an example:

Pros:
Secrets not in VCS.
Cons:
settings_local.py is not in VCS, so you can lose some of your Django environment settings.
The Django settings file is a Python code, so settings_local.py can have some non-obvious logic.
You need to have settings_local.example (in VCS) to share the default configurations for developers.

### 12 Factors
actors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale in the Cloud. It was created by Heroku, a well-known Cloud hosting provider.

As the name suggests, the collection consists of twelve parts:

* Codebase
* Dependencies
* Config
* Backing  services
* Build, release,  run
* Processes
* Port binding
* Concurrency
* Disposability
* Dev/prod  parity
* Logs
* Admin processes
Each point describes a recommended way to implement a specific aspect of the project. Some of these points are covered by instruments like Django, Python, pip. Some are covered by design patterns or the infrastructure setup. In the context of this article, we are interested in one part: the Configuration.


#### Conclusion:
The Settings file is a small but very important part of any Django project. If you do it wrong, you’ll have a lot of issues during all phases of development. But if you do it right, it will be a good basis for your project that will allow it to grow and scale in the future.

Using the environment variables approach, you can easily switch from a monolith to microservice architecture, wrap your project in Docker containers, and deploy it in any VPS or Cloud hosting platform such as: Amazon, Google Cloud, or your own Kubernetes cluster.


##### Resources
* [Django Settings Best Practices](https://djangostars.com/blog/configuring-django-settings-best-practices/)
* [SSH Tutorial](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)
* [White Noise](http://whitenoise.evans.io/en/stable/)
* [IaaS](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)
* [PaaS](https://en.wikipedia.org/wiki/Platform_as_a_service)
* [CORS](https://en.m.wikipedia.org/wiki/Cross-origin_resource_sharing)