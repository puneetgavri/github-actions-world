
# GITHUB ACTIONS – OVERVIEW

---

**What Are GitHub Actions?**

A **GitHub Action** is a reusable automation component used inside a workflow. Instead of writing everything in shell scripts, you can plug in prebuilt automation to perform common CI/CD tasks.

Actions can help you:

* Check out source code
* Set up programming languages (Node.js, Python, Java, etc.)
* Install dependencies
* Run tests
* Build containers
* Deploy applications
* Upload artifacts
* Perform security scans

They promote reuse, standardization, and faster pipeline development.

---

**How to Find Actions**

The main place to discover actions is the **GitHub Marketplace**.

You can search by:

* Programming language
* Cloud provider (AWS, Azure, GCP)
* CI/CD category
* Security tools
* Verified publishers

When selecting an action, evaluate:

* ⭐ Community adoption (stars and usage)
* ✔️ Verified publisher status
* 📅 Recent release activity
* 📖 Documentation clarity
* 🛠 Maintenance and issue responsiveness

GitHub also maintains official actions under repositories such as **actions/*** and **github/***. These are widely trusted and commonly used.

---

**How to Use an Action**

Actions are referenced using the `uses` keyword inside a workflow step.

Basic example:

uses: actions/checkout@v4

Example with configuration:

uses: actions/setup-node@v4
with:
node-version: 20

General format:

uses: owner/repository@version

Inputs (if required) are passed using the `with` section.

---

**Ways to Specify the Action Version**

When referencing an action, you must specify a version after `@`. There are three common approaches:

**1. Major Version (Convenient)**
Example: actions/checkout@v4

* Tracks the latest compatible release within that major version
* Easy to maintain
* Automatically receives minor and patch updates

---

**2. Full Version Tag (More Precise)**
Example: actions/checkout@v4.1.1

* Locks the workflow to a specific release
* More predictable and stable
* Recommended for controlled production environments

---

**3. Commit SHA (Most Secure)**
Example: actions/checkout@3df4ab11b4c5f9a8e7d6c2b0b1234567890abcd

* Pins the action to an exact commit
* Cannot change unless manually updated
* Provides maximum supply-chain security
* Recommended for high-security or regulated systems

---

**Security Best Practices**

**1. Always Pin Versions**
Avoid using branch references like `@main`. These can change without notice.

**2. Review Third-Party Actions**
Treat them like external dependencies. Inspect their source code and maintenance history.

**3. Apply Least Privilege**
Restrict `GITHUB_TOKEN` permissions to only what your workflow requires.

**4. Be Careful with Forked Pull Requests**
Secrets are not available to forks by default. Changing this behavior can introduce risk.

**5. Never Log Sensitive Data**
Even though GitHub masks secrets, do not print or transform them intentionally.

---

**Popular Actions**

**Core CI/CD Actions**

* actions/checkout – Clones the repository
* actions/setup-node – Installs Node.js
* actions/setup-python – Installs Python
* actions/cache – Caches dependencies
* actions/upload-artifact – Uploads build outputs

**Cloud & Deployment**

* aws-actions/configure-aws-credentials – AWS authentication
* azure/login – Azure authentication
* google-github-actions/auth – Google Cloud authentication

**Security & Quality**

* github/codeql-action – Code scanning
* dependabot – Dependency updates

---

**Final Takeaway**

GitHub Actions are powerful, reusable automation building blocks that simplify CI/CD workflows. However, because they execute code inside your pipeline, they should be treated as production dependencies.

Always review them carefully, pin versions appropriately, and follow strong security practices.
