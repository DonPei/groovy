# Philanthropy Campaign Sync

The project has been designed for **AEM as a Cloud Service** for Philanthropy campaign website.
Please check the [wiki](http://aoprlaemutil1.mdanderson.edu/philanthropy/campaign/wikis/home) for task/issue workflow.

## Git Feature Workflow Commands

1. Clone the project:

   ```
   git clone git@aoprlaemutil1.mdanderson.edu/philanthropy/campaign.git
   ```

   You should be prompted for username and password

2. Change directory to your working folder:

   ```
   cd ${working_folder}
   ```

3. Check out the `develop` branch:

   ```
   git checkout develop
   ```

4. Check status of branch (should be up-to-date with `'origin/develop'` with nothing to comit, working directory clean):

   ```
   git status
   ```

5. Create your feature branch

   Use the below naming convention for your feature branch, and ensure that yor branch is based off the `develop` branch:

   ```
   git checkout -b [feat]-[JIRA-ID]-[storyname]-[short-description] develop
   ```

6. Develop the story or fix.

7. Check your changes:

   ```
   git status
   ```

   The above command should show all that is modified, use the add command to add it to your local git repo:

   ```
   git add .
   ```

8. Commit changes frequently and incrementally, so as to maintain a clear log of what was changed. Always commit your changes with a clear and concise message:

   ```
   git commit -m "Example message that explains what changes were made."
   ```

9. Push your local branch to the remote branch:

   ```
   git push origin [your-feature-branch]
   ```

10. When your feature or story is complete, with all functionality in place, and not before, merge your feature branch into the `develop` branch. Starting from your feature branch:

    ```
    git pull origin develop
    ```

    This will pull and merge the remote `develop` branch into your feature branch to make your branch is up-to-date with all changes in code that have been made during your feature development. Next you will switch to the `develop` branch:

    ```
    git checkout develop
    ```

    Now you can merge your feature branch into the `develop` branch:

    ```
    git merge [your-feature-branch]
    ```

    Finally, you can push this to the central repository:

    ```
    git push origin develop
    ```

## Modules

The main parts of the project are:

- **core**: Java bundle containing all core functionality like OSGi services, listeners or schedulers, as well as component-related Java code such as servlets or request filters.
- **ui.apps**: contains the /apps (and /etc) parts of the project, ie JS & CSS clientlibs, components, templates, runmode specific configs
- **ui.content**: contains mutable content (not /apps) that is integral to the running of the site. This include template types, templates, policies, users and base-line organization page and asset structures.
- **ui.acl**: contains the acl specific configs yaml files
- **dispatcher.cloud**: contains dispatcher configurations for AEM as a Cloud Service
- **repository-structure**: Empty package that defines the structure of the Adobe Experience Manager repository the Code packages in this project deploy into.
- **all**: An empty module that embeds the above sub-modules and any vendor dependencies into a single deployable package.

## How to build

To build all the modules run in the project root directory the following command with Maven 3:

```
mvn clean install
```

If you have a running AEM instance you can build and package the whole project using the `all` module with:

```
mvn clean install -PautoInstallSinglePackage
```

Depending on your maven configuration, you may find it helpful to force the resolution of the Adobe public repo with

```
mvn clean install -PautoInstallSinglePackage -Padobe-public
```

Or to deploy it to a publish instance, run

```
mvn clean install -PautoInstallSinglePackagePublish
```

Or alternatively

```
mvn clean install -PautoInstallSinglePackage -Daem.port=4503
```

Or to deploy only `ui.apps` to the author, run

```
cd ui.apps
mvn clean install-PautoInstallPackage
```

Or to deploy only the bundle to the author, run

```
cd core
mvn clean install -PautoInstallBundle
```

## Testing

There are three levels of testing contained in the project:

unit test in core: this show-cases classic unit testing of the code contained in the bundle. To test, execute:

```
mvn clean test
```

### TO DO

- Junit test cases
- More custom component examples

## Reference Content

This contains pages created using core components(v2.10.0) and basic styling to demonstrate how to use CSS and AEM style system to setup a basic site using core components.

Sample pages are at [https://github.com/arunpatidar02/aemaacs-aemlab/tree/master/ui.content/src/main/content/jcr_root/content/aemlab/oneweb/reference-content](https://github.com/arunpatidar02/aemaacs-aemlab/tree/master/ui.content/src/main/content/jcr_root/content/aemlab/oneweb/reference-content)

**Example**

[https://github.com/arunpatidar02/aemaacs-aemlab/tree/master/ui.content/src/main/content/jcr_root/content/aemlab/oneweb/reference-content/embed](https://github.com/arunpatidar02/aemaacs-aemlab/tree/master/ui.content/src/main/content/jcr_root/content/aemlab/oneweb/reference-content/embed)

![embed core component reference content](https://github.com/arunpatidar02/aemaacs-aemlab/blob/master/embed.png)
