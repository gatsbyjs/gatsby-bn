---
title: আপনার ডেভেলপমেন্ট ইনভায়রনমেন্ট সেটআপ
typora-copy-images-to: ./
disableTableOfContents: true
---

Gatsby দিয়ে প্রথম সাইটটি বানানো শুরু করার আগে আপনার কিছু কোর ওয়েব টেকনোলজির সাথে পরিচিত হতে হবে এবং প্রয়োজনীয় সকল সফটওয়্যার টুলস গুলো ইন্সটল করেছেন কিনা তা নিশ্চিত করতে হবে।

## কমান্ড লাইনের সাথে পরিচিত হউন

কমান্ড লাইন হল টেক্সট-বেইজড একটি ইন্টারফেস যা দিয়ে কম্পিউটারে কমান্ড রান করা যায়। এটার আরেক নাম হচ্ছে টার্মিনাল। এই টিউটোরিয়ালে আমরা এই দুটো নাম ই অদলবদল করে ব্যবহার করব। এটা ম্যাক এর ফাইন্ডার অথবা উইন্ডোজ এর এক্সপ্লোরার ব্যবহারের মত নয়। ফাইন্ডার এবং এক্সপ্লোরার গ্রাফিকাল ইউজার ইন্টারফেস বা GUI এর উদাহরণ। অপরদিকে কমান্ড লাইন হল টেক্সট এর মাধ্যমে কম্পিউটারের সাথে যোগাযোগ এর একটি ক্ষমতাশালী উপায়।

একটু সময় নিয়ে কমান্ড লাইন ইন্টারফেসটি (CLI) খুঁজে নিন এবং চালু করুন। কোন অপারেটিং সিস্টেম ব্যবহার করছেন তার উপর নির্ভর করে দেখুন [**Mac এর জন্য নির্দেশাবলী**](http://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/), [**Windows এর জন্য নির্দেশাবলী**](https://www.lifewire.com/how-to-open-command-prompt-2618089) অথবা [**Linux এর জন্য নির্দেশাবলী**](https://www.howtogeek.com/140679/beginner-geek-how-to-start-using-the-linux-terminal/)

_**বিঃদ্রঃ:** আপনি যদি কমান্ড লাইন ব্যবহারে নতুন হয়ে থাকেন, কমান্ড রান করানোর অর্থ হচ্ছে কমান্ড প্রম্পট এ কিছু প্রদত্ত  ইন্সট্রাকশন  লিখে তা  "এন্টার" দেয়া। কমান্ড গুলো হাইলাইটেড বক্সে দেখানো হবে, যেমন `node --version`, কিন্তু সকল হাইলাইটেড বক্স ই কমান্ড নয় ! কোন কিছু যদি কমান্ড হয়ে থাকে তাহলে সেটা আপনাকে চালানো অথবা এক্সিকিউট করার কথা বলা হবে।_

## আপনার অপারেটিং সিস্টেম এ Node.js ইন্সটল করুন

Node.js হছে একটি  এনভায়রনমেন্ট যা জাভাস্ক্রিপ্ট কোড ওয়েব ব্রাউজার এর বাইরে চালাতে পারে। Gatsby Node.js দিয়ে তৈরি করা। Gatsby দিয়ে কোন কিছু করার আগে আপনাকে Node.js এর একটি সাম্প্রতিক ভার্সন ইন্সটল করতে হবে। npm Node.js এর সাথেই আসে, সুতরাং আপনার যদি npm না থাকে তাহলে সম্ভবত আপনার Node.js ও ইন্সটল করা নেই।

### Mac এর জন্য নির্দেশাবলী

Mac এ Gatsby এবং Node.js ইন্সটল করার জন্য [Homebrew](https://brew.sh/) ব্যবহার করা সুবিধাজনক। এটার ব্যবহার আপনাকে পরের অনেক ঝামেলা থেকে মুক্তি দেবে!

#### যেভাবে আপনার কম্পিউটারে Homebew ইন্সটল এবং ভেরিফাই করবেনঃ

1. আপনার টার্মিনালটি চালু করুন।
2. নিচের কমান্ড টি টার্মিনালে এন্টার করে দেখুন Homebrew ইন্সটল করা আছে কিনা। ইন্সটল করা থাকলে আপনি "Homebrew" এবং একটি ভার্সন নাম্বার দেখতে পাবেন। 

    ```shell
    brew -v
    ```

3. যদি এমন না দেখতে পান, তাহলে [Homebrew ইন্সটল করার নির্দেশাবলী](https://docs.brew.sh/Installation) অনুসরণ করে তা ডাউনলোড এবং ইন্সটল করুন।
4. Homebrew ইন্সটল করার পর তা আসলেই হয়েছে কিনা যাচাই করতে দুই নাম্বার ধাপের পুনরাবৃত্তি করুন।

#### Xcode কমান্ড লাইন টুলস ইন্সটল করুনঃ

1. আপনার টার্মিনালটি চালু করুন।
2. নিচের কমান্ড টি চালানোর মাধ্যমে Xcode কমান্ড লাইন টুলস ইন্সটল করুন:

    ```shell
    xcode-select --install
    ```

> 💡 If that fails, download it [directly from Apple's site](https://developer.apple.com/download/more/), after signing-in with an Apple developer account.

3. After being prompted to start the installation, you'll be prompted again to accept a software license for the tools to download.

#### Install Node

1. Open your Terminal
2. Install node with Homebrew:

```shell
brew install node
```

> 💡 If you don't want to install it through Homebrew, download the latest Node.js version from [the official Node.js website](https://nodejs.org/en/), double click on the downloaded file and go through the installation process.

### Windows Instructions

- Download and install the latest Node.js version from [the official Node.js website](https://nodejs.org/en/)

### Linux Instructions

Install nvm (Node Version Manager) and needed dependencies. nvm is used to manage Node.js and all its associated versions.

> 💡 When installing a package, if it asks for confirmation, type `y` and press enter.

Select your distro:

- [Ubuntu, Debian, and other apt based distros](#ubuntu-debian-and-other-apt-based-distros)
- [Arch, Manjaro and other pacman based distros](#arch-manjaro-and-other-pacman-based-distros)
- [Fedora, RedHat, and other dnf based distros](#fedora-redhat-and-other-dnf-based-distros)

> 💡 If the Linux distribution you are using is not listed here, please find instructions on the web.

#### Ubuntu, Debian, and other `apt` based distros:

1. Make sure your Linux distribution is ready to go run an update and an upgrade:

```shell
sudo apt update
sudo apt -y upgrade
```

2. Install curl which allows you to transfer data and download additional dependencies:

```shell
sudo apt-get install curl
```

3. After it finishes installing, download the latest nvm version:

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```

4. Confirm this has worked. The output should be a version number.

```shell
nvm --version
```

5. Continue with the section: [Set default Node.js version](#set-default-nodejs-version)

#### Arch, Manjaro and other `pacman` based distros:

1. Make sure your distribution is ready to go:

```shell
sudo pacman -Sy
```

2. These distros come installed with curl, so you can use that to download nvm:

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```

3. Before using nvm, you need to install additional dependencies by running:

```shell
sudo pacman -S grep awk tar
```

4. Confirm this has worked. The output should be a version number.

```shell
nvm --version
```

5. Continue with the section: [Set default Node.js version](#set-default-nodejs-version)

#### Fedora, RedHat, and other `dnf` based distros:

1. These distros come installed with curl, so you can use that to download nvm:

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```

2. Confirm this has worked. The output should be a version number.

```shell
nvm --version
```

3. Continue with the section: [Set default Node.js version](#set-default-nodejs-version)

#### Set default Node.js version

When nvm is installed, it does not default to a particular node version. You’ll need to install the version you want and give nvm instructions to use it. This example uses the version 10 release, but more recent version numbers can be used instead.

```shell
nvm install 10
nvm use 10
```

Confirm that this worked:

```shell
npm --version
node --version
```

The output should look similar to the screenshot below, showing version numbers in response to the commands.

![Check node and npm versions in terminal](01-node-npm-versions.png)

Once you have followed the installation steps and you have checked everything is installed properly, you can continue to the next step.

## Install Git

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. When you install a Gatsby "starter" site, Gatsby uses Git behind the scenes to download and install the required files for your starter. You will need to have Git installed to set up your first Gatsby site.

The steps to download and install Git depend on your operating system. Follow the guide for your system:

- [Install Git on macOS](https://www.atlassian.com/git/tutorials/install-git#mac-os-x)
- [Install Git on Windows](https://www.atlassian.com/git/tutorials/install-git#windows)
- [Install Git on Linux](https://www.atlassian.com/git/tutorials/install-git#linux)

## Using the Gatsby CLI

The Gatsby CLI tool lets you quickly create new Gatsby-powered sites and run commands for developing Gatsby sites. It is a published npm package.

The Gatsby CLI is available via npm and should be installed globally by running:

```shell
npm install -g gatsby-cli
```

_**Note**: when you install Gatsby and run it for the first time, you'll see a short message notifying you about anonymous usage data that is being collected for Gatsby commands, you can read more about how that data is pulled out and used in the [telemetry doc](/docs/telemetry)._

See the available commands:

```shell
gatsby --help
```

![Check gatsby commands in terminal](05-gatsby-help.png)

> 💡 If you are unable to successfully run the Gatsby CLI due to a permissions issue, you may want to check out the [npm docs on fixing permissions](https://docs.npmjs.com/getting-started/fixing-npm-permissions), or [this guide](https://github.com/sindresorhus/guides/blob/master/npm-global-without-sudo.md).

## Create a Gatsby site

Now you are ready to use the Gatsby CLI tool to create your first Gatsby site. Using the tool, you can download “starters” (partially built sites with some default configuration) to help you get moving faster on creating a certain type of site. The “Hello World” starter you’ll be using here is a starter with the bare essentials needed for a Gatsby site.

1.  Open up your terminal.
2.  Create a new site from a starter:

```shell
gatsby new hello-world https://github.com/gatsbyjs/gatsby-starter-hello-world
```

> 💡 What just happened?
>
> - `new` is a gatsby command to create a new Gatsby project.
> - Here, `hello-world` is an arbitrary title — you could pick anything. The CLI tool will place the code for your new site in a new folder called “hello-world”.
> - Lastly, the GitHub URL specified points to a code repository that holds the starter code you want to use.

> 💡 Depending on your download speed, the amount of time this takes will vary. For brevity's sake, the gif below was paused during part of the install

3.  Change into the working directory:

```shell
cd hello-world
```

> 💡 This says _'I want to change directories (`cd`) to the “hello-world” subfolder'_. Whenever you want to run any commands for your site, you need to be in the context for that site (aka, your terminal needs to be pointed at the directory where your site code lives).

4.  Start the development mode:

```shell
gatsby develop
```

> 💡 This command starts a development server. You will be able to see and interact with your new site in a development environment — local (on your computer, not published to the internet).

<video controls="controls" autoplay="true" loop="true">
  <source type="video/mp4" src="./03-create-site.mp4" />
  <p>Sorry! Your browser doesn't support this video.</p>
</video>

### View your site locally

Open up a new tab in your browser and navigate to `http://localhost:8000/`

![Check homepage](04-home-page.png)

Congrats! This is the beginning of your very first Gatsby site! 🎉

You’ll be able to visit the site locally at `http://localhost:8000/` for as long as your development server is running. That’s the process you started by running the `gatsby develop` command. To stop running that process (or to “stop running the development server”), go back to your terminal window, hold down the “control” key, and then hit “c” (ctrl-c). To start it again, run `gatsby develop` again!

_**Note:** If you are using VM setup like `vagrant` and/or would like to listen on your local IP address, run `gatsby develop --host=0.0.0.0`. Now, the development server listens on both `http://localhost` and your local IP._

## Set up a code editor

A code editor is a program designed specifically for editing computer code. There are many great ones out there.

### Download VS Code

Gatsby documentation sometimes includes screenshots that were taken in VS Code, so if you don't have a preferred code editor yet, using VS Code will make sure that your screen looks just like the screenshots in the tutorial and docs. If you choose to use VS Code, visit the [VS Code site](https://code.visualstudio.com/#alt-downloads) and download the version appropriate for your platform.

### Install the Prettier plugin

We also recommend using [Prettier](https://github.com/prettier/prettier), a tool that helps format your code to avoid errors.

You can use Prettier directly in your editor using the [Prettier VS Code plugin](https://github.com/prettier/prettier-vscode):

1.  Open the extensions view on VS Code (View => Extensions).
2.  Search for "Prettier - Code formatter".
3.  Click "Install". (After installation, you'll be prompted to restart VS Code to enable the extension. Newer versions of VS Code will automatically enable the extension after download.)

> 💡 If you're not using VS Code, check out the Prettier docs for [install instructions](https://prettier.io/docs/en/install.html) or [other editor integrations](https://prettier.io/docs/en/editors.html).

## ➡️ What’s Next?

To summarize, in this section you:

- Learned about the command line and how to use it
- Installed and learned about Node.js and the npm CLI tool, the version control system Git, and the Gatsby CLI tool
- Generated a new Gatsby site using the Gatsby CLI tool
- Ran the Gatsby development server and visited your site locally
- Downloaded a code editor
- Installed a code formatter called Prettier

Now, move on to [**getting to know Gatsby building blocks**](/tutorial/part-one/).

## References

### Overview of core technologies

It’s not necessary to be an expert with these already — if you’re not, don’t worry! You’ll pick up a lot through the course of this tutorial series. These are some of the main web technologies you’ll use when building a Gatsby site:

- **HTML**: A markup language that every web browser is able to understand. It stands for HyperText Markup Language. HTML gives your web content a universal informational structure, defining things like headings, paragraphs, and more.
- **CSS**: A presentational language used to style the appearance of your web content (fonts, colors, layout, etc). It stands for Cascading Style Sheets.
- **JavaScript**: A programming language that helps us make the web dynamic and interactive.
- **React**: A code library (built with JavaScript) for building user interfaces. It’s the framework that Gatsby uses to build pages and structure content.
- **GraphQL**: A query language that allows you to pull data into your website. It’s the interface that Gatsby uses for managing site data.

### What is a website?

For a comprehensive introduction to what a website is -- including an intro to HTML and CSS -- check out “[**Building your first web page**](https://learn.shayhowe.com/html-css/building-your-first-web-page/)”. It’s a great place to start learning about the web. For a more hands-on introduction to [**HTML**](https://www.codecademy.com/learn/learn-html), [**CSS**](https://www.codecademy.com/learn/learn-css), and [**JavaScript**](https://www.codecademy.com/learn/introduction-to-javascript), check out the tutorials from Codecademy. [**React**](https://reactjs.org/tutorial/tutorial.html) and [**GraphQL**](https://graphql.org/graphql-js/) also have their own introductory tutorials.

### Learn more about the command line

For a great introduction to using the command line, check out [**Codecademy’s Command Line tutorial**](https://www.codecademy.com/courses/learn-the-command-line/lessons/navigation/exercises/your-first-command) for Mac and Linux users, and [**this tutorial**](https://www.computerhope.com/issues/chusedos.htm) for Windows users. Even if you are a Windows user, the first page of the Codecademy tutorial is a valuable read. It explains what the command line is, not just how to interface with it.

### Learn more about npm

npm is a JavaScript package manager. A package is a module of code that you can choose to include in your projects. If you just downloaded and installed Node.js, npm was installed with it!

npm has three distinct components: the npm website, the npm registry, and the npm command line interface (CLI).

- On the npm website, you can browse what JavaScript packages are available in the npm registry.
- The npm registry is a large database of information about JavaScript packages available on npm.
- Once you’ve identified a package you want, you can use the npm CLI to install it in your project or globally (like other CLI tools). The npm CLI is what talks to the registry — you generally only interact with the npm website or the npm CLI.

> 💡 Check out npm’s introduction, “[**What is npm?**](https://docs.npmjs.com/getting-started/what-is-npm)”.

### Learn more about Git

You will not need to know Git to complete this tutorial, but it is a very useful tool. If you are interested in learning more about version control, Git, and GitHub, check out GitHub's [Git Handbook](https://guides.github.com/introduction/git-handbook/).
