# Setting up a dev container for Rust

* Primary author: [Alexander Shang](https://github.com/alexander-shang)
* Reviewer: [Dhyey Shah](https://github.com/dhyeyvshah)

## Part 1: Prerequisites
1. A GitHub Account
2. Git installed
3. Visual Studio Code
4. Docker installed
5. Command-line basics

## Part 2: Creating the Dev Container
First, you'll want to start with a new blank directory. In your terminal you'll run three commands:

```
mkdir <directory-name>
cd <directory-name>
git init
```

Then create a README.me file:
```
echo "# Rust Tutorial" > README.md
git add README.md
git commit -m "Initial commit with README.md" 
```

## Part 3: Create a Remote Repository on GitHub
Log in to your GitHub account and navigate to the Create a New Repository page.

Fill in the details as follows:

* Repository Name: <directory-name>
* Description: "Rust Tutorial" (this is optional)
* Visibility: Public

Do not initialize the repository with a README, .gitignore, or license.

Click Create Repository.

To link your local repository to GitHub you can run the following:
```
git remote add origin https://github.com/<your-username>/<directory-name>.git
git branch -M main
git push -u origin main
```

## Part 4: Setting up the Development Environment
Next, you'll want to open up VSCode and open the directory you just created. You can do this via: File > Open Folder. Make sure you have the Dev Containers extension downloaded (you can find extensions on the left toolbar). Then，create a ```.devcontainer``` directory in the root of your project with the following file inside of this "hidden" configuration directory:
```.devcontainer/devcontainer.json```

In this file, you'll want to include the following code:
```
{
  "name": "COMP423 Rust Tutorial",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
        "extensions": ["rust-lang.rust-analyzer"]
    }
  }
}
```
!!! Note
    ```name```: A descriptive name for your dev container.
    
    ```image```: The Docker image to use, in this case, the latest version of a Rust environment. Microsoft maintains a collection of base images for many programming language environments, but you can also create your own!
    
    ```customizations```: Adds useful configurations to VS Code, like installing the Rust extension.


After this, you should reopen the project in the container. You can do this by pressing Ctrl+Shift+P on Windows or Cmd+Shift+P on Mac and entering "Dev Containers: Reopen in Container."

You can confirm the rust version in the container by runnning the command:
```rustc --version```.
If the output is something other than a version number, double check that the above instructions are followed correctly.

## Part 5: Creating your Rust Project
1. Inside the Rust project, we're going to use Rust's package manager, Cargo:
```
cargo new --vcs none hello_comp423
cd hello_comp423
```
!!! Note
    ```--vcs-none``` ensures that a new git repository is not automatically created on your behalf

2. Open the 'main.rs' file inside of the src directory and replace the contents with:
```
fn main(){
    println("Hello COMP423!");
}
```

## Part 6: Compiling and Running your Project
Build your project by running the command:
```
cargo build
```
!!! Note
    This is similar to the ```gcc``` command in C/C++, but it does more than just compile your program. The ```cargo build``` command also automates the management of dependencies, configuration, and build settings.  

To run the program, run the following:
```
cargo run
```
Your output should be:
```
Hello COMP423!
```
If the following output doesn't match, make sure that you followed all the instructions.

!!! Note
    ```cargo run``` combines all the steps that are executed with the 'build' command, but also executes the program!