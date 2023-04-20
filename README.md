# Agri-Cloud 


This is an open-source project built using Ruby on Rails, designed to collect agricultural data from multiple sources including farmers, government agencies, and research organizations. The API allows users to collect data on crop yields, weather patterns, soil quality, pest and disease control, and other relevant information. It's intended to be an easy-to-use interface that allows for data analysis, and the integration of external data sets, such as satellite imagery and market prices.

<!-- toc -->

- [Welcome contributors!](#welcome-contributors)
  - [About this project](#about-this-project)
- [Developing! ✨🛠✨](#developing-)
  - [How to Contribute](#how-to-contribute)
  - [Installation](#installation)
    - [General Setup Instructions](#general-setup-instructions)
    - [Platform Specific Installation Instructions](#platform-specific-installation-instructions)
      - [Ubuntu and WSL](#ubuntu-and-wsl)
  - [Running the App / Verifying Installation](#running-the-app--verifying-installation)
- [Other Documentation](#other-documentation)
    - [Common issues](#common-issues)
- [Communication and Collaboration](#communication-and-collaboration)
- [History](#history)

<!-- tocstop -->

## Welcome contributors!

We are very happy to have you! OpenTechies is committed to welcoming new contributors of all skill levels.

We highly recommend that you join us in slack by contacting us at open.00.tech@gmail.com

Issues on the issue board https://github.com/OpenTechies/Agri-Cloud-back-end/issues in the TODO column are fair game. An issue can be claimed by commenting on it.

Pull requests which are not for an issue but which improve the codebase are also welcome! Feel free to make GitHub issues for bugs and improvements. A maintainer will be keeping an eye on issues and PRs every day or three.

### About this project

The platform provides a way for farmers to connect and share information and best practices, enabling them to improve their crop yields and income. Government agencies and research organizations can use the data to track and understand the impact of their policies and programs.

This system provides value by:

- Creating a platform for farmers to connect and share information and best practices, enabling them to improve their crop yields and income
- Helping government agencies and research organizations to track and understand the impact of their policies and programs, and make necessary adjustments to improve the agricultural sector in the country
- Providing an open-source solution for agricultural data collection, analysis, and sharing, allowing for wider access to important information and insights.

<!-- Read about the [product sense](doc/productsense.md) that guides our approach to this work. -->

**How Agri cloud works:**

- As an open-source project, the platform allows for wider access to important information and insights, promoting collaboration and innovation in the agricultural sector.

# Developing! ✨🛠✨  
## How to Contribute  
  See our [contributing guide](./doc/CONTRIBUTING.md) 💖 ✨
## Installation
### General Setup Instructions
**Downloading the Project**
(*on a Mac or Linux machine*)
1. `git clone https://github.com/OpenTechies/Agri-Cloud-back-end.git` clone the repo to your local machine.  
2. You can ask a maintainer (barakadan421@gmail.com) for permission to make a branch on this repo.  
3. You can also [create a fork on GitHub](https://docs.github.com/en/get-started/quickstart/fork-a-repo) and make a pull request from the fork.  

**Ruby**
1. Install a ruby version manager: [rvm](https://rvm.io/) or [rbenv](https://github.com/rbenv/rbenv)
1. when you cd into the project directory, let your version manager install the ruby version in `.ruby-version`. Right now that's Ruby 3.1.2
1. `gem install bundler`

**node.js**
1. (Recommended) Install [nvm](https://github.com/nvm-sh/nvm#installing-and-updating), which is a **n**ode **v**ersion **m**anager.
1. Install a current LTS version of Node. lts/fermium works.
1. Install [yarn](https://classic.yarnpkg.com/en/docs/install). On Ubuntu, [make sure you install it from the official Yarn repo instead of cmdtest](https://classic.yarnpkg.com/en/docs/install/#debian-stable).

**PostgreSQL ("postgres")**
1. Make sure that postgres is installed.
  - If you're on Ubuntu/WSL, use `sudo apt-get install libpq-dev` so the gem can install. [Use the Postgres repo for Ubuntu or WSL to get the server and client tools](https://www.postgresql.org/download/linux/ubuntu/).
  - If you're on Fedora/Cent Os use `sudo dnf install libpq-devel`. [If you prefer choose package of libpq-devel via rpm](https://pkgs.org/download/libpq-devel)
  - If you're on Windows, use the official [installer](https://www.postgresql.org/download/windows/) and accept all defaults.  Alternatively, a [Chocolatey](https://chocolatey.org/packages/postgresql) package is available with `choco install postgresql`.

**Chrome Browser**

1. The Spec tests uses Chrome Browser and Chromedriver for some of the tests. A current version of chromedriver will be installed when `bundle install` is run. TO install Chrome, see [Chrome Install](https://support.google.com/chrome/answer/95346?hl=en&ref_topic=7439538).

Another option is to install the Chromium browser for your operating system so the browser-based Ruby feature/integration tests can run. Installing `chromium-browser` is enough, including for many WSL (Windows subsystem for Linux) distributions.

If you are using Ubuntu on WSL and receive the following message when trying to run the test suite...

> Command '/usr/bin/chromium-browser' requires the chromium snap to be installed. Please install it with:
> `snap install chromium`

...check out the instructions on [installing google-chrome and chromedriver for WSL Ubuntu](https://github.com/rubyforgood/casa/blob/main/doc/WSL_SETUP.md#google-chrome).

**Installing Packages**
1. `bundle install` install ruby dependencies.
1. `yarn` install javascript dependencies.

**Database Setup**
1. `bin/rails db:setup` create schema
    requires running local postgres, with a role created for whatever user you're running rails as
1. `bin/rails db:seed:replant` generates test data (can be rerun to regenerate test data)

**Compile Assets**  
1.  `yarn build` compile javascript  
&ensp;&ensp;`yarn build:dev` to auto recompile for when you edit js files  
3.  `yarn build:css` compile css  
&ensp;&ensp;`yarn build:css:dev` to auto recompile for when you edit sass files  

### Platform Specific Installation Instructions
 - [Linux](doc/LINUX_SETUP.md)
 - [Mac](doc/MAC_SETUP.md)
 - Windows(Help Wanted)
 - [Windows Subsystem for Linux(WSL)](https://github.com/rubyforgood/casa/blob/main/doc/WSL_SETUP.md)

#### Ubuntu and WSL

1. Rbenv

    If you are on Ubuntu in Windows Subsystem for Linux (WSL) and `rbenv install` indicates that the Ruby version is unavailable, you might be using Ubuntu's default install of `ruby-build`, which only comes with old installs of Ruby (ending before 2.6.) You should uninstall rvm and ruby-build's apt packages (`apt remove rvm ruby-build`) and install them with Git like this:

    - `git clone https://github.com/rbenv/rbenv.git ~/.rbenv`
    - `echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`
    - `echo 'eval "$(rbenv init -)"' >> ~/.bashrc`
    - `exec $SHELL`
    - `git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build`

    You'll probably hit a problem where ruby-version reads `ruby-2.7.2` but the install available to you is called `2.7.2`. If you do, install [rbenv-alias](https://github.com/tpope/rbenv-aliases) and create an alias between the two.

2. Chrome / Chromium

    If you are on Ubuntu in Windows Subsystem for Linux (WSL) you may need to install google-chrome and chromedriver if your version of Ubuntu requires the chromium snap to be installed.
    For instructions how to do this, check out our [WSL Setup docs](https://github.com/rubyforgood/casa/blob/main/doc/WSL_SETUP.md#google-chrome).

### Common issues

1. If your rails/rake commands hang forever instead of running, try: `rails app:update:bin`
1. There is currently no option for a user to sign up and create an account through the UI. This is intentional. If you want to log in, use a pre-seeded user account and its credentials.
1. If you are on windows and see the error "Requirements support for mingw is not implemented yet" then use https://rubyinstaller.org/ instead
1. Install imagemagick to see images locally. Instructions: https://imagemagick.org/script/download.php

## Running the App / Verifying Installation
1. `bin/rails server` or `bin/rails s` to start the local webserver

**Running Tests**
 - run the ruby test suite `bin/rails spec`
 - run the javascript test suite `yarn test`

If you have trouble running tests, check out CI scripts in [`.github/workflows/`](.github/workflows/) for sample commands.
Test coverage is run by simplecov on all builds and aggregated by CodeClimate
