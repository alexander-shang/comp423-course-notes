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

If you want to push this repository to your GitHub you can run the following:
```
git remote add origin https://github.com/<your-username>/comp423-rust-tutorial.git
git branch -M main
git push -u origin main
```

## Part 3: Setting up the Development Environment
Next, you'll want to open up VSCode and open the directory you just created. You can do this via: File > Open Folder. Make sure you have the Dev Containers extension downloaded (you can find extensions on the left toolbar). Then，create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:
```.devcontainer/devcontainer.json```

In this file, you'll want to include the following code:
```
{
  "name": "COMP423 Course Notes",
  "image": "mcr.microsoft.com/devcontainers/python:latest",
  "customizations": {
    "vscode": {
        "extensions": ["rust-lang.rust-analyzer"]
    }
  },
  "postCreateCommand": "pip install -r requirements.txt"
}
```

After this, you should reopen the project in the container. You can do this by pressing Ctrl+Shift+P on Windows or Cmd+Shift+P on Mac and entering "Dev Containers: Reopen in Container."

You can confirm the rust version in the container by runnning the command:
```rustc --version```.
If the output is something other than a version number, double check that the above instructions are followed correctly.

## Part 4: Creating your Rust Project
1. Inside the Rust project, we're going to use Rust's package manager, Cargo:
```
cargo new hello_world
cd hello_world
```

2. Open the 'main.rs' file inside of the src directory and replace the contents with:
```
fn main(){
    println("Hello World!");
}
```

## Part 5: Compiling and Running your Project
1. Build your project by running the command:
```
cargo build
```
This is similar to the ```gcc``` command in C/C++, but it does more than just compile your program. The ```cargo build``` command also automates the management of dependencies, configuration, and build settings.  

2. To run the program, run the following:
```
cargo run
```
Your out put should be:
```
Hello World!
```
If the following output doesn't match, make sure that you followed all the instructions.

```cargo run``` combines all the steps that are executed with the 'build' command, but also executes the program!