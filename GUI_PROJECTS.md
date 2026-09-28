# Using GitHub Codespaces for a GUI Project

You may use GitHub Codespaces and GitHub Copilot to develop your GUI project. This gives you a consistent development environment without requiring you to configure a complete C++ toolchain on every computer you use.

There is one important limitation: GitHub Codespaces runs on Linux. You can develop and compile your GUI application there, but you generally will not be able to see and interact with the GUI window directly from Codespaces.

The recommended workflow is:

> Develop in Codespaces, push to GitHub, then build and test the GUI locally.

## 1. Use a cross-platform GUI library

Your project should use a GUI or graphics library that supports both Linux and Windows. Examples include:

- [SFML](https://www.sfml-dev.org/)
- [SDL](https://www.libsdl.org/)
- [Qt](https://www.qt.io/)
- [Dear ImGui](https://github.com/ocornut/imgui)

This allows the same C++ source code to be compiled in Codespaces and on a Windows PC.

## 2. Use CMake

Using [CMake](https://cmake.org/) is strongly recommended.

CMake is not a C++ compiler. It configures your project so that it can use the appropriate compiler on each operating system.

```text
Codespaces / Linux: CMake -> GCC  -> Your program
Windows:            CMake -> MSVC -> Your program
```

This lets you keep the same source code and `CMakeLists.txt` in your GitHub repository while building the project on different operating systems.

Your project might look like this:

```text
MyProject/
├── CMakeLists.txt
├── main.cpp
├── src/
└── include/
```

Depending on the GUI library you choose, CMake can also download and configure the library automatically with features such as [`FetchContent`](https://cmake.org/cmake/help/latest/module/FetchContent.html).

## 3. Develop and build in Codespaces

Open your repository in GitHub Codespaces. From the terminal, configure the project:

```bash
cmake -S . -B build
```

Then compile it:

```bash
cmake --build build
```

This is useful for finding compiler errors and verifying that the project builds successfully. You can continue to write and debug your code in Codespaces using GitHub Copilot or another coding agent.

Remember that successfully compiling the program does not mean that you have fully tested the GUI. You still need to run and interact with it.

## 4. Push your work to GitHub

Commit and push your changes:

```bash
git add .
git commit -m "Update GUI project"
git push
```

Your source code is now available from the local computer where you want to test the GUI.

## 5. Test the GUI locally

Clone the repository onto the local computer if you have not already done so:

```bash
git clone YOUR_REPOSITORY_URL
```

If you already cloned it, update it instead:

```bash
git pull
```

Then build the project locally using CMake. In a properly configured Windows development environment:

```powershell
cmake -S . -B build
cmake --build build
```

Run the executable produced by the Windows build and test the GUI.

### Important: Linux and Windows executables are different

Do not copy the executable produced in Codespaces to a Windows PC and expect it to run. Codespaces builds a Linux executable.

If you are testing on Windows, pull the source code from GitHub and compile it again on Windows. This produces a Windows executable.

```text
                 GitHub repository
                        |
                  C++ source code
                    /       \
                   /         \
          Codespaces         Windows PC
             Linux
               |                 |
             CMake             CMake
               |                 |
              GCC               MSVC
               |                 |
        Linux program      Windows program
                                  |
                               Run GUI
```

## 6. Ask your coding agent for help

You do not need to memorize all of these commands.

GitHub Copilot or another coding agent can help you configure and build the project. For example, you can tell your agent:

> I am developing this C++ GUI project in GitHub Codespaces, which runs Linux, but I also need to build and run it on a Windows PC. Please configure the project using CMake so that it builds on both platforms. Help me set up the GUI library and tell me the commands I should use to build it in Codespaces and Windows.

You can also ask your agent to diagnose CMake errors, configure your GUI library, or explain how to build and run the project on the computer you are currently using.

The goal is not to struggle with build-system configuration. Use the available tools and your coding agent to get the development environment working so that you can focus on building your application.
