# Using GitHub Codespaces + Copilot for C++

Everything runs in your web browser, so you do not need to install a C++ compiler or coding environment on the computer.

## Initial Setup

### 1. Sign Up for GitHub Copilot as a Student

GitHub provides Copilot to verified students through GitHub Education.

1. Sign in to your GitHub account.
2. Apply for or verify your student status through **GitHub Education**:
   https://github.com/education/students
3. Follow the instructions to verify your student status and activate your student benefits.
4. Make sure GitHub Copilot is available on your account before continuing.

Student verification may take some time, so complete this step before you plan to work on the project.

---

### 2. Create a GitHub Repository

1. Go to:
   https://github.com
2. Create a **new repository**.
3. Give the repository a name.
4. Create a new file named `main.cpp`.
5. Add a simple Hello World program:

```cpp
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello World!" << endl;
    return 0;
}
```

6. Click **Commit changes** to save `main.cpp` to the repository.

---

### 3. Create a Codespace

From your GitHub repository:

1. Click the green **`<> Code`** button.
2. Select the **Codespaces** tab.
3. Click **Create codespace on main**.
4. Wait for the Codespace to start.

A browser-based version of VS Code will open with your repository already loaded.

---

### 4. Compile and Run the Program

Open the terminal at the bottom of the Codespace.

Compile `main.cpp`:

```bash
g++ main.cpp -o main
```

If there are no compiler errors, run it:

```bash
./main
```

You should see:

```text
Hello World!
```

You now have a working C++ development environment running entirely in your browser.

---

### 5. Start GitHub Copilot

In the Codespace terminal, enter:

```bash
copilot
```

This starts an interactive Copilot session.

You can now give Copilot instructions about your project. For example:

```text
Review this C++ project and explain what it currently does.
```

You can ask Copilot to create or modify code, compile the project, run it, test it, fix problems, or make other changes.

**Read what Copilot is doing before approving its actions.**

To leave Copilot and return to the normal terminal, press:

```text
Ctrl+C
```

---

# Returning to Your Codespace Later

You do **not** need to create a new Codespace every time you work on the project.

1. Go to your repository on GitHub.
2. Click the green **`<> Code`** button.
3. Select **Codespaces**.
4. Find your existing Codespace in the list.
5. Click it to reopen it.

You can also access your Codespaces directly at:

https://github.com/codespaces

Once the Codespace opens, you can continue working where you left off.

To start Copilot again, open the terminal and enter:

```bash
copilot
```

---

# Typical Workflow

Each time you work on the project:

1. Open your existing Codespace.
2. Start Copilot with `copilot`.
3. Give Copilot instructions and review the changes it makes.
4. Compile and run your program.
5. Test your work.
6. Commit and push your changes to GitHub.
