# scalafmt-config
Scalafmt configuration file used across several projects

## How To Use

1. In your main project that needs scalafmt config file, add a new submodule
```bash
  git submodule add https://github.com/jozic/scalafmt-config.git
  ```
  Please note it uses `https` and not `git` protocol to allow Travis CI (or other tools) to access submodule repo without additional configurations)
  
2. In your main project setup scalafmt to use config file from submodule
  - SBT
    - add sbt-scalafmt plugin (if not yet)
    ```scala
      addSbtPlugin("com.geirsson" % "sbt-scalafmt" % "1.6.0-RC4")
     ```
    - set `scalafmtConfig` key to point to the config file from submodule
     ```scala
     scalafmtConfig := Some(root.base / "scalafmt-config/.scalafmt.conf")
     ```
  - Maven
    - setup maven plugin accordinly (if not yet) - https://github.com/SimonJPegg/mvn_scalafmt
    - set `configLocation` to point to the config file from submodule
    ```xml
      <configLocation>${project.basedir}/scalafmt-config/.scalafmt.conf</configLocation>
    ```
3. When cloning a fresh copy of main project (or just updating another fork) don't forget to get submodule
```bash
  git clone --recursive my-project-that-uses-scalafmt-config-as-submodule-git-url
  ```
  or
  ```bash
  git clone my-project-that-uses-scalafmt-config-as-submodule-git-url
  git pull --recurse-submodules
  ```
4. If you push updates to `.scalafmt.conf`, don't forget to update main project to point to the latest commit of submodule  
  
