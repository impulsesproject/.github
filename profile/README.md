# The Impulses Project

Ever since I started my journey as a software developer, one of the biggest challenges I've had to face on an almost regular basis is setting up a dev environment as soon as possible. The faster I configure my environment, the quicker I can get to coding up the project - the part that really matters in the end.

Having spent the past decade or so working in a variety of fields - from machine learning and game development to quantum computing and web development - I've wrestled with countless technologies and their environment setups. Some are easy, some are brutal, but none are impossible. Indeed, the problem wasn't how hard the process ended up being. The problem was how many *times* I had to go through the same process each time I wanted to start a new project. How difficult the setup was just made it that much worse each time around. As they say, time is money, and I needed to save money.

Scaffolders and boilerplate generators were made to address this very issue of repetition, but it remains to be said that the setup of a dev environment is quite opinionated. What configs you choose, what packages you install, what naming conventions you prefer, are all unique to the developer. I had my own set of styles and conventions that I would make sure to enforce across many projects. For instance, almost all my `JS`/`TS` projects enforce the `Google JS Style Guide`. I settled on this style guide after trying and calling it quits on the very opinionated `Airbnb Style Guide`. 

Most modern day scaffolders like `Vite` or `Create-Next-App` allow for a wide variety of configuration settings, but they cannot account for all. Indeed, the very nature of scaffolding has the consequence of taking away some of the flexibility that comes with doing it yourself from scratch. Furthermore, the existence of reliable scaffolding software was very dependent on what tech I was working on. Web developers are exceptionally lazy and wrestle with numerous technologies per project, so it comes as no surprise that some of the best scaffolders I've used were in web development. However, the same cannot be said about machine learning and data science or the very nascent field of quantum computing. 

I was also frustrated with the amount of environment pollution that comes with working with technologies across many different fields. At one point in time, I had to install `anaconda` because of some ML stuff I was working on, but later I spent a couple of months working on web development and only needed to work with `node`. The aforementioned `anaconda` installation stayed idle on my system, just eating space. I didn't know whether I needed to uninstall it or not because I didn't know whether I would use it again anytime soon. 

When I discovered Docker and Docker Dev Environments, I immediately knew a powerful workflow was at the tip of my fingers. The ability for images to be self-contained templates that could spin up isolated containers meant that I could, in theory, solve all of my dev environment setup problems by creating a vast collection of starter images containing all the necessary configurations and installations prepackaged at build time, and spinning up dev containers from these images as and when I needed to start a project. No more did I have to spend days trying to recollect what I had done during the setup process numerous times before so as to not miss a step and sabotage everything. I just had to do it once - when I need to build the image from the Dockerfile.

Couple this with the power of Docker Dev Environments and VS Code's awesome Docker toolchain, I never had to install anything locally ever again. Docker was all I needed. I would generate images for each tech stack I worked with, and spin up dev containers containing my preferred VS Code extensions and settings that would be completely isolated from my computer. This way, each project would also have its own set of VS Code extensions and settings. No more having to configure and switch between VS Code profiles or even copy over settings from Github each time I create a project. Everything, would be be preprepared. Utopia.

In physics, an impulse is defined as the momentum transfer that is produced by a large force acting for a very short interval. 

$$
\Delta p = \int F dt
$$

The boot of a football player is in contact with the football for mere milliseconds, but the large force produced by the swing of the leg is enough to generate enough momentum to blast the ball across the entirety of the football field. The pace at which I can setup my dev environment is analogous to the force here. The faster the pace, the more momentum I have when it comes to coding the project and implementing my vision to almost its entirety. Impulse also has a colloquial meaning that we are all familiar with. Being an impulsive individual, I often start projects on a whim. Considering all of this, I thought it would be apt to name each docker image I create as an "Impulse". 

Presenting, **The Impulses Project**.

## How does it work?

To get started, you will need

- A working installation of `Docker` and `Docker Engine`
- A `VS Code` installation
- The official `Docker` extension from Microsoft for `VS Code`
- The official `Dev Containers - VS Code Extension` for `VS Code`

Each repository in this organization contains the following

- **Dockerfile** - This is the file that is used to build the tagged boilerplate image that is later on spun up by the dev container. Run `docker build -t [tagname] .` to build these images yourself
- **.devcontainer/devcontainer.json** - Contains configurations on how the `Dev Containers - VS Code Extension` should spin up a working dev container. This is quite irrelevant and used only by this particular `VS Code` extension.
- **.devcontainer/docker-compose.yml** - Arguably the most important file in this workflow. This docker compose config file in the `YAML` format contains information on what image must be used, what volumes must be mounted, and what environment must be setup when spinning up the dev container. If you want to use a different image or an image that you built, replace the `image:` field in the description with the appropriate `dockerhub` URI locator for your image.
- **.vscode/settings.json** - Contains workspace settings that VS Code will apply to the workspace **inside** your dev container once it is created and running.
- **.vscode/extensions.json** - Contains a list of recommended extensions that I personally like to use when working with the associated tech stack. `VS Code` will prompt you to install all of these in one go when the dev container is first created.

After installing the `Dev Containers - VS Code Extension`, open the directory containing the aforementioned files in `VS Code`. Then, open the `VS Code` command bar via `Ctrl + Shift + P` or `Cmd + Shift + P` and select `Dev Containers: Open Folder in Container` to create and run a dev container. 

## Feedback

I welcome any and all feedback, so feel free to let me know what you think of this project. If you think there are certain extensions, settings, or base images that work better than the ones I have determined for these toolchains, I would very much like to hear about them so don't hesistate to reach out 💙
