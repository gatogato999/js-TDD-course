# Module 0: Foundations & Setup

## 0.0 Introduction to Test-Driven Development (TDD)

Welcome to the Test-Driven Development (TDD) course! This course is designed to take you from a beginner to a job-ready full-stack developer, focusing on JavaScript/Node.js, PostgreSQL, and SQLite, all through the lens of TDD. You've made an excellent choice in wanting to learn TDD, as it's a powerful methodology that can significantly improve the quality, maintainability, and design of your software.

### What is Test-Driven Development (TDD)?

Test-Driven Development (TDD) is a software development process that relies on the repetition of a very short development cycle: first, the developer writes an automated test case that defines a desired new function or an improvement to existing functionality, then produces the minimum amount of code necessary to pass that test, and finally refactors the new code to acceptable standards. This cycle is often referred to as "Red-Green-Refactor."

Let's break down the core components of this definition:

1.  **Automated Test Case:** Unlike manual testing, where a human manually checks if software works, TDD emphasizes writing tests that can be run automatically by a computer. These tests are code themselves, designed to verify specific behaviors of your application.

2.  **Defines Desired Functionality:** In TDD, tests are written *before* the actual code that implements the feature. This might seem counterintuitive at first, but it forces you to think about the requirements and the expected behavior of your code from the perspective of a user or another part of the system. The test becomes a clear, executable specification of what the code should do.

3.  **Minimum Code to Pass:** The goal in the initial coding phase is *not* to write perfect, optimized code. It's simply to write just enough code to make the failing test pass. This keeps you focused on the immediate requirement and prevents over-engineering.

4.  **Refactor:** Once the test passes, you have working code. Now, and only now, do you improve its design, readability, and efficiency without changing its external behavior. The passing tests give you the confidence that your refactoring efforts haven't broken anything.

### The Red-Green-Refactor Cycle

The heart of TDD is its iterative, three-step cycle:

*   **Red (Write a failing test):**
    *   Write a new test that describes a small piece of functionality you want to add. This test should fail because the functionality doesn't exist yet. This failure confirms that the test is actually testing something and that your understanding of the requirement is correct.
    *   *Why Red?* The test output will typically be red, indicating failure.

*   **Green (Make the test pass):**
    *   Write the simplest possible code to make the failing test pass. Do not worry about perfect design or elegance at this stage. The only goal is to get the test to pass.
    *   *Why Green?* The test output will typically be green, indicating success.

*   **Refactor (Improve the code):**
    *   Once the test is green, you have working code. Now, you can improve the code's structure, remove duplication, enhance readability, and optimize performance, all while continuously running your tests to ensure you haven't introduced any regressions (bugs).
    *   *Why Refactor?* This step ensures your codebase remains clean, maintainable, and adaptable as it grows.

This cycle is repeated many times throughout the development of a feature, often several times an hour. Each cycle adds a small, verifiable piece of functionality to the system.

### Why Practice TDD?

TDD offers numerous benefits that contribute to higher quality software and a more efficient development process:

1.  **Improved Code Quality and Design:**
    *   **Executable Specification:** Tests act as living documentation, clearly showing how the code is intended to be used and what its expected behavior is. This makes it easier for new developers to understand the codebase and for existing developers to remember how parts of the system work.
    *   **Better Design:** Writing tests first forces you to think about the API and structure of your code from the perspective of its consumers. This often leads to more modular, loosely coupled, and easier-to-use code. Code that is hard to test is often poorly designed.
    *   **Fewer Bugs:** By writing tests before code, you catch defects early in the development cycle, when they are cheapest and easiest to fix. The comprehensive test suite acts as a safety net, preventing regressions when changes are made.

2.  **Increased Developer Confidence:**
    *   **Safety Net for Refactoring:** With a robust suite of automated tests, you can confidently refactor your code, knowing that if you break existing functionality, a test will immediately tell you. This encourages continuous improvement of the codebase.
    *   **Clear Progress:** The Red-Green-Refactor cycle provides immediate feedback on your progress. Seeing tests go from red to green is a tangible sign of accomplishment and helps maintain momentum.

3.  **Faster Development in the Long Run:**
    *   While TDD might seem slower initially due to the overhead of writing tests, it often leads to faster development in the long run. Less time is spent debugging, and the cost of fixing bugs later in the development cycle (or in production) is significantly reduced.
    *   **Reduced Technical Debt:** The constant refactoring encouraged by TDD helps keep the codebase clean and reduces the accumulation of technical debt, which can slow down future development.

4.  **Better Collaboration:**
    *   Tests provide a common language for developers to discuss requirements and behavior. They serve as a shared understanding of what the system does.

### TDD vs. Traditional Testing

It's important to distinguish TDD from simply writing tests. In traditional development, tests are often written *after* the code is complete, or sometimes not at all. This can lead to:

*   **Tests that only confirm existing bugs:** If you write tests after the fact, you might inadvertently write tests that pass even when the code has subtle flaws, because your understanding of the code's behavior is already influenced by its implementation.
*   **Incomplete test coverage:** It's harder to think of all edge cases and failure scenarios once the code is already written.
*   **Difficulty in testing:** Code not designed with testability in mind can be very difficult to test, leading to complex setups and brittle tests.

TDD flips this paradigm, making testing an integral part of the design and development process, not an afterthought.

### What You Will Learn in This Course

Throughout this course, you will not only learn the theory behind TDD but, more importantly, you will apply it hands-on by building practical projects. We will cover:

*   Setting up a professional development environment on Windows 10 using WSL, Node.js, and VS Code.
*   Mastering **Jest** for unit and integration testing in Node.js.
*   Building robust RESTful APIs with **Express.js** using a TDD approach.
*   Integrating and testing with **PostgreSQL** for relational data management.
*   Exploring **SQLite** for simpler, embedded database needs.
*   Introduction to **Cypress** for end-to-end testing of full-stack applications.
*   Advanced TDD concepts, refactoring, and best practices.

By the end of this course, you will have a solid understanding of TDD principles and practical experience applying them to build high-quality, maintainable full-stack applications. You will be equipped with the skills and confidence to apply TDD in your own projects and in a professional development environment.

Let's get started with setting up your development environment!



## 0.1 Setting Up Your Development Environment

Before we dive into writing tests and code, we need to set up a robust and efficient development environment. As you're working on Windows 10 and have experience with WSL, we'll leverage the Windows Subsystem for Linux (WSL) to provide a Linux-like environment for our Node.js and database development. This approach offers several advantages, including better compatibility with many development tools and a more consistent experience with production environments, which are often Linux-based.

This section will guide you through installing and configuring:

1.  **Windows Subsystem for Linux (WSL):** A compatibility layer for running Linux binary executables natively on Windows.
2.  **Ubuntu (or Debian) Distribution:** A popular Linux distribution to run within WSL.
3.  **Node.js and npm:** The JavaScript runtime and its package manager.
4.  **Visual Studio Code (VS Code):** Our primary code editor, with excellent WSL integration.
5.  **Git:** The industry-standard version control system.

Let's get started!

### 0.1.1 Installing Windows Subsystem for Linux (WSL)

WSL allows you to run a GNU/Linux environment directly on Windows, without the overhead of a traditional virtual machine. For Windows 10, you'll typically install WSL 1 first, and then upgrade to WSL 2 for better performance and full system call compatibility.

**Step 1: Enable WSL Optional Features**

Open PowerShell as Administrator (search for "PowerShell" in the Start Menu, right-click, and select "Run as Administrator"). Execute the following command:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

This command enables the Windows Subsystem for Linux feature. You might be prompted to restart your computer. If so, please restart before proceeding.

**Step 2: Enable Virtual Machine Platform (for WSL 2)**

WSL 2 uses a lightweight utility virtual machine for better performance. To enable it, run the following command in PowerShell as Administrator:

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Again, if prompted, restart your computer.

**Step 3: Download and Install the Linux Kernel Update Package**

WSL 2 requires an update to the Linux kernel. Download the latest package from the official Microsoft documentation:

*   [WSL 2 Linux kernel update package for x64 machines](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) [1]

Download and run this installer. Follow the prompts to install the kernel update.

**Step 4: Set WSL 2 as your default version**

Open PowerShell or Command Prompt and run:

```powershell
wsl --set-default-version 2
```

You should see a message confirming that WSL 2 is now the default. If you encounter an error like "WSL 2 requires an update to its kernel component," ensure you've completed Step 3.

**Step 5: Install a Linux Distribution (Ubuntu Recommended)**

Open the Microsoft Store (search for "Microsoft Store" in the Start Menu). Search for "Ubuntu" and select the latest LTS (Long Term Support) version (e.g., "Ubuntu 22.04 LTS"). Click "Get" or "Install."

Once installed, launch the Ubuntu application from your Start Menu. The first time you launch it, it will take a few minutes to set up. You will then be prompted to create a username and password for your new Linux distribution. Remember these credentials, as you'll use them frequently.

Congratulations! You now have a functional Linux environment running within Windows via WSL.

### 0.1.2 Installing Node.js and npm

Node.js is the JavaScript runtime we'll use for our backend development, and npm (Node Package Manager) is used to install and manage Node.js packages and libraries.

We will use `nvm` (Node Version Manager) to install Node.js. `nvm` allows you to easily switch between different Node.js versions, which is very useful for managing multiple projects.

**Step 1: Open your WSL (Ubuntu) Terminal**

Launch the Ubuntu application from your Start Menu.

**Step 2: Install `curl` (if not already installed)**

`curl` is a command-line tool for transferring data with URLs. We'll use it to download the `nvm` installation script.

```bash
sudo apt update
sudo apt install curl -y
```

`sudo apt update` updates the package lists, and `sudo apt install curl -y` installs `curl` (the `-y` flag automatically answers yes to prompts).

**Step 3: Install `nvm`**

Run the following command to download and run the `nvm` installation script:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

*Note: The version number (v0.39.1) might be outdated. You can check the latest version on the [nvm GitHub repository](https://github.com/nvm-sh/nvm#install-update-script) [2]. Replace `v0.39.1` with the latest stable version if different.*

After the installation script runs, you need to close and reopen your WSL terminal for `nvm` to be properly loaded into your shell. Alternatively, you can run `source ~/.bashrc` or `source ~/.zshrc` (depending on your shell) to load it immediately.

**Step 4: Verify `nvm` Installation**

In your WSL terminal, type:

```bash
nvm --version
```

You should see the `nvm` version number printed. If you get a "command not found" error, ensure you've closed and reopened your terminal or sourced your shell configuration file.

**Step 5: Install Node.js**

Now, use `nvm` to install the latest Long Term Support (LTS) version of Node.js. LTS versions are recommended for most users as they are stable and well-supported.

```bash
nvm install --lts
```

This command will install the latest LTS version of Node.js and its bundled npm. `nvm` will also automatically set this version as the default.

**Step 6: Verify Node.js and npm Installation**

To confirm Node.js and npm are installed correctly, run:

```bash
node -v
npm -v
```

You should see the version numbers for both Node.js and npm. This confirms your JavaScript runtime environment is ready!

### 0.1.3 Installing Visual Studio Code (VS Code) and WSL Extension

VS Code is a powerful, free, and open-source code editor developed by Microsoft. Its integration with WSL is seamless, allowing you to develop in your Linux environment while using the familiar VS Code interface on Windows.

**Step 1: Download and Install VS Code for Windows**

If you don't already have it, download and install VS Code from the official website:

*   [Visual Studio Code Download](https://code.visualstudio.com/download) [3]

Choose the "Windows" installer (User Installer is usually sufficient). Run the installer and follow the prompts. It's generally recommended to check the option "Add 'Open with Code' action to Windows Explorer file context menu" during installation, as it's very convenient.

**Step 2: Install the WSL Extension in VS Code**

Open VS Code. Go to the Extensions view by clicking on the Extensions icon in the Activity Bar on the side (or press `Ctrl+Shift+X`).

Search for "WSL" and find the extension named "WSL" by Microsoft. Click "Install."

This extension allows VS Code to run commands and open folders within your WSL environment.

**Step 3: Open Your WSL Project Folder in VS Code**

Now, let's open your WSL home directory in VS Code. There are two common ways:

**Method A (Recommended): From WSL Terminal**

1.  Open your WSL (Ubuntu) terminal.
2.  Navigate to your home directory (or any directory you want to open in VS Code). For example, to go to your home directory:
    ```bash
    cd ~
    ```
3.  Type `code .` and press Enter.

    ```bash
    code .
    ```

    This command will launch a new VS Code window connected to your WSL environment, with the current directory (`.`) opened. You'll notice a green indicator in the bottom-left corner of VS Code saying "WSL: Ubuntu" (or your distribution name), indicating you're connected to the remote WSL environment.

**Method B: From VS Code (if Method A doesn't work initially)**

1.  Open VS Code.
2.  Click on the green remote indicator in the bottom-left corner of the VS Code window.
3.  Select "New WSL Window" or "Connect to WSL" and choose your Ubuntu distribution.
4.  Once connected, go to `File > Open Folder...` and navigate to your desired folder within the WSL filesystem (e.g., `/home/your_username/`).

Now you have VS Code running on Windows, but editing files and executing commands directly within your WSL Linux environment. This is the ideal setup for our course.

### 0.1.4 Installing Git

Git is a distributed version control system that tracks changes in source code during software development. It's essential for collaboration and managing your project's history.

**Step 1: Open your WSL (Ubuntu) Terminal**

**Step 2: Install Git**

Git is usually pre-installed on many Linux distributions, but it's good to ensure you have the latest version.

```bash
sudo apt update
sudo apt install git -y
```

**Step 3: Configure Git**

After installation, you need to configure your Git username and email. These details will be associated with your commits.

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Replace `"Your Name"` and `"your.email@example.com"` with your actual name and email address.

**Step 4: Verify Git Installation**

To confirm Git is installed and configured, run:

```bash
git --version
```

You should see the Git version number.

### Your Development Environment is Ready!

With WSL, Node.js, npm, VS Code, and Git all set up, you have a powerful and professional development environment ready for Test-Driven Development. In the next section, we'll start diving into the core concepts of TDD and writing our first tests using Jest.

---

### References

[1] [WSL 2 Linux kernel update package for x64 machines](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
[2] [nvm GitHub repository](https://github.com/nvm-sh/nvm#install-update-script)
[3] [Visual Studio Code Download](https://code.visualstudio.com/download)


