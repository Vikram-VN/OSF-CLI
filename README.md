# Oracle-Commerce-Cloud (CX) CLI Document


## Table of Contents
  1) [Options](#1-options)    
  
  2) [Configure](#2-configure)

  3) [Create-App](#3-create-app)

  4) [Configure-App](#4-configure-app)

  5) [Build](#5-build)

  6) [Deploy](#6-deploy)

  7) [Redeploy](#7-redeploy)

  8) [Deploy-Log](#8-deploy-log)

  9) [Deploy-Status](#9-deploy-status)

 10) [Output](#10-output)

 11) [Delete](#11-delete)

 12) [Download](#12-download)
     
 13) [List-Apps](#13-list-apps)

 14) [Set-Logging-Options](#14-set-logging-options)

 15) [Upgrade](#15-upgrade)

 16) [Download-Assets](#16-download-assets)

 17) [Upload-Search-Config](#17-upload-search-config)

 18) [Upload-Custom-TypeHead-KeyWords](#18-upload-custom-typehead-keywords)

 19) [Server](#19-serve)

 20) [Create-Template](#20-create-template)

 21) [Create-Widget](#21-create-widgete)

 22) [Create-Fetcher](#22-create-fetcher)

 23) [Create-Action](#23-creation-action)
     
 24) [Create-Selector](#24-create-selector)

 25) [Create-Endpoint](#25-create-endpoint)

 26) [List-Endpoints](#26-list-endpoints)

 27) [Create-Subscriber](#27-create-subscriber)

 28) [Validate-Assets](#28-validate-assets)

 29) [Version](#29-version)

 30) [Coming-Soon](#30-coming-soon)







## 1) OCC Options

### Usage: yarn occ [options] [command]

### Options:
  ```PowerShell
  -V, --version                                         output the version number
  -h, --help                                            display help for command
  ```

### Commands:
  ```PowerShell
  configure [options]                                   Updates workspace configuration.
  configure-app [appName] [options]                     Updates application configuration.
  build [appName] [options]                             Build an occ application.
  deploy [appName] [options]                            Deploy an occ application bundle
  redeploy [options] [clusterId]                        Instructs admin to resend either the preview or live deployment to the given cluster.
  deploy-log [appName] [options]                        Query the deployment logs for an application.
  deploy-status [appName] [options]                     Queries the deployment status for an application.
  output [appName] [options]                            Generates the deployment files for the given app.
  delete [appName] [options]                            Deletes an occ application from OCC Admin.
  download [appName] [options]                          Download the current deployment for an application
  list-apps [options]                                   List the available applications and clusters on the server.
  set-logging-options [options] [clusterId]             Sets various logging options for the given cluster.
  upgrade [options] [version]                           Upgrade the versions of OSF packages depended on throughout the workspace.
  download-assets [appName] [options]                   Downloads the assets from design studio and writes them to the workspace
  upload-search-config [appName] [options]              Upload the search configuration
  upload-custom-typeahead-keywords [appName] [options]  Reads the custom keyword records from the 'config/search/data/keywords.js' in the app, and appends them to the existing elements in the '/gsdata/v1/cloud/data/keywords' record collection.
  serve [appName] [options]                             Start presentation server [localhost]
  create-template [appName] [options]                   Creates a workspace template archive containing the given app.        
  create-widget [appName] [options]                     Create a widget plugin for a specific application.
  create-fetcher [appName] [options]                    Create a fetcher for a specific application.
  create-action [appName] [options]                     Create an action for a specific application.
  create-selector [appName] [options]                   Create a selector for a specific application. Please refer to the example in the sample application, or the OSF documentation.       
  create-endpoint [appName] [options]                   Create endpoint(s) for a URL or from a Swagger API document.
  list-endpoints [options]                              List all available endpoints from a Swagger API document.
  create-subscriber [appName] [options]                 Create a subscriber for named application.
  create-app [options] [appPackageName]                 Create a new app in an existing workspace from an accelerator template.
  validate-assets [appName]                             Validate all assets, including components, containers, pages and slots for the application.
  version [options]                                     List the version of various OSF elements on the workspace, and the Oracle Commerce Cloud version.
  help [command]                                        display help for command
  ```


## 2) Configure

### Usage: yarn occ configure [options]

**Updates workspace configuration.**

### Options:
  ```PowerShell
  -V, --version               output the version number
  -v, --verbose               Provides verbose logging where available
  --no-verbose                Disables verbose logging
  -L, --live                  Operate in the live context.
  --no-live                   Operate in the preview context. This is the default behavior.
  -n, --appName <name>        The application name to use as the default.
  -m, --dsAssetMode <mode>    Sets the rendering mode for design studio assets ("local" | "remote").
  --userName <name>           Sets the user name for any actions done from this workspace. Defaults to the OS username.
  --appContext <context>      The appContext to use as the default.
  -k, --appKey [key]          With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>       Application server URL
  -a, --appServerAdmin <url>  Application admin server URL
  -e, --serverEnv <env>       Cloud Commerce server environment to use
  --httpHost <host>           Presentation server hostname (http)
  --httpPort <port>           Presentation server port (http)
  --httpsHost <host>          Presentation server hostname (https)
  --httpsPort <port>          Presentation server port (https)
  --sslKey <path>             The path to the ssl key file used for https.
  --sslCert <path>            The path to the ssl cert file used for https.
  -l, --list                  Displays the current configuration settings
  --backup                    Back up assets related to the app before doing a 'reset' deployment. True by default.
  --no-backup                 Do not download existing preview assets and create a backup before 'reset' deploys
  -h, --help                  display help for command
  ```

### Examples:
  ```Shell
  yarn occ configure --appName blank-store --appServerAdmin http://someserver.oracle.com:9080 --appKey
  yarn occ configure --httpPort 5050 --httpsPort 5051
  yarn occ configure --list
  ```

## 3) Create-App

### Usage: yarn occ create-app [options] [appPackageName]

**Create a new app in an existing workspace from an accelerator template.**

### Options:
  ```PowerShell
  --template <templateName>   Accelerator template name. (default: "core-commerce-reference-store")
  --fromClassic               Convert the assests from SF classic to OSF
  -k, --appKey [key]          With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>       Application server URL
  -a, --appServerAdmin <url>  Application admin server URL     
  -e, --serverEnv <env>       Cloud Commerce server environment to use
  -h, --help                  display help for command
  ```

### Examples:
  ```Shell
  yarn occ create-app @acme/my-app
  yarn occ create-app --template blank-store
  yarn occ create-app @acme/my-app --template blank-store
  yarn occ create-app @acme/my-app --fromClassic
  ```


## 4) Configure-App

### Usage: yarn occ configure-app [appName] [options]

**Updates application configuration.**

### Options:
  ```PowerShell
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -l, --list                   Displays the current configuration settings
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ configure-app --localDevAppName marcus-app
  yarn occ configure-app --list
  ```


## 5) Build

### Usage: yarn occ build [appName] [options]

**Build an occ application.**

### Options:
  ```PowerShell
  -V, --version     output the version number
  -v, --verbose     Provides verbose logging where available
  --no-verbose      Disables verbose logging
  --legacy          Generate legacy client code when building
                    in development mode.
  -p, --production  Build an occ application in production
                    mode.
  -w, --watch       Watch for changes when building in
                    development mode.
  -h, --help        display help for command
  ```


### Examples:
  ```Shell
  yarn occ build
  yarn occ build marcus-app --production--watch
  ```



## 6) Deploy

### Usage: yarn occ deploy [appName] [options]

**Deploy an occ application bundle**

### Options:
  ```PowerShell
  -V, --version                  output the version number
  -v, --verbose                  Provides verbose logging where available
  --no-verbose                   Disables verbose logging
  -k, --appKey [key]             With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>          Application server URL
  -a, --appServerAdmin <url>     Application admin server URL  
  -e, --serverEnv <env>          Cloud Commerce server environment to use
  --deployType <type>            The type of deployment to do (e.g. 'full')
  --ignore <glob>                Path-like (e.g. '*.log') matching files to exclude from the deployment/accelerator zip (default: [])
  --include <glob>               Path-like (e.g. '*.md') matching files to include in the deployment/accelerator zip (default: [])
  --localDevAppName <appName>    Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName           Ignore the local development application name configured for the application.
  --no-validation                Do not validate assets when running yarn deploy.
  --replaceApp <appName>         When specified the application being deployed will replace this application in the hosted sandbox
  --zipFile [zip file location]  Deploy a specific zip file. The app name used to deploy is extracted from the zip.
  -t, --tag <value>              Associate a custom value with the deployment. This value will be included as part of the deployments metadata (default: [])
  -p, --publish                  With this option, any changes from the deploy/delete will be published.
  --publishAll [confirm]         With this option, all changes in the publishing queue will be published. You will be prompted to confirm this option. Optionally, the prompt can be bypassed by specifying 'Y'
  --no-build                     Skip the production build before deploying
  -r, --reset [confirm]          Resets the state of the application to that of the workspace. Note that any pending change to assets in Design Studio will be lost.
  -l, --list                     Query all deployments for an application.
  --debugMode                    Turn on development/debug mode on the given cluster. When used with redeploy, this implies '--force' to pick up the logging change. THIS WILL SLOW PERFORMANCE FOR MORE LOGGING.
  --no-debugMode                 Turn off development/debug mode on the given cluster. When used with redeploy, this implies '--force' to pick up the logging change.
  --backup                       Back up assets related to the app before doing a 'reset' deployment. True by default.        
  --no-backup                    Do not download existing preview assets and create a backup before 'reset' deploys
  -h, --help                     display help for command
  ```

### Examples:
  ```Shell
  yarn occ deploy blank-store --no-build
  yarn occ deploy blank-store --tag commit1234 --tag version 1.0.0
  yarn occ deploy --zipFile ./somefile.zip
  ```


## 7) Redeploy

### Usage: yarn occ redeploy [options] [clusterId]

**Instructs admin to resend either the preview or live deployment to the given cluster.**

### Options:
  ```PowerShell
  -L, --live                  Operate in the live context.
  --no-live                   Operate in the preview context. This is the default behavior.
  -V, --version               output the version number
  -v, --verbose               Provides verbose logging where available
  --no-verbose                Disables verbose logging
  -k, --appKey [key]          With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>       Application server URL
  -a, --appServerAdmin <url>  Application admin server URL     
  -e, --serverEnv <env>       Cloud Commerce server environment to use
  --force                     Whether to force environments that already report the deployment as ACTIVE to also accept the redeployment
  --debugMode                 Turn on development/debug mode on the given cluster. When used with redeploy, this implies '--force' to pick up the logging change. THIS WILL SLOW PERFORMANCE FOR MORE LOGGING.
  --no-debugMode              Turn off development/debug mode on the given cluster. When used with redeploy, this implies '--force' to pick up the logging change.
  -h, --help                  display help for command
  ```


### Examples:
  ```Shell
  yarn occ redeploy --appServerAdmin http://someserver.oracle.com --appKey
  yarn occ redeploy storefront --live
  ```


## 8) Deploy-Log
 
### Usage: yarn occ deploy-log [appName] [options]

**Query the deployment logs for an application.**

### Options:
  ```PowerShell
  -V, --version                output the version number       
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging        
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  -L, --live                   Operate in the live context.    
  --no-live                    Operate in the preview context. This is the default behavior.
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  --system                     Get the system log instead of the application log. Default is the application log.
  -c, --cluster [clusterId]    Return a cluster specific result. Provide a clusterId to change which cluster is targeted.     
  -d, --deployment <deployId>  Query information for a specific deployment
  --since <date>               Query the deployment log beginning at a specific date. Format is MM-DD-YYYY HH:MM:SS
  --until <date>               Query the deployment log ending at a specific date. Format is MM-DD-YYYY HH:MM:SS
  --queryText <text>           Query the messages in the deployment log for specific text.
  --label <value>              Query the log for entries matching the given label value.
  --zipFile <filename>         Return the deployment log in the specified zip file.
  --limit <number>             Limit the results to a specific number of lines.
  --includeArchives [number]   Query the deployment log including the given number of archived logs.
  -j, --json                   Output the results as raw JSON instead of formatted text.
  --loggingLevel <level>       Query the deployment log for messages at only the given level. Valid levels are error, warn, info, verbose or debug.
  --order <value>              Specify the order the log results are returned, either ascending or descending. Valid values are asc or desc.
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ deploy-log marcus-app
  yarn occ deploy-log marcus-app --limit 10
  ```
  

## 9) Deploy-Status

### Usage: yarn occ deploy-status [appName] [options]

**Queries the deployment status for an application.**

### Options:
  ```PowerShell
  -c, --cluster [clusterId]    Return a cluster specific result. Provide a clusterId to change which cluster is targeted.
  -d, --deployment <deployId>  Query information for a specific deployment
  -j, --json                   Output the results as raw JSON instead of formatted text.
  --last                       Check the status of an applications last deployment from this workspace
  -V, --version                output the version number       
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging        
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -h, --help                   display help for command
  ```


### Examples:
  ```Shell
  yarn occ deploy-status marcus-app
  yarn occ deploy-status marcus-app --json  --last
  ```


## 10) Output

### Usage: yarn occ output [appName] [options]

**Generates the deployment files for the given app.**

### Options:
  ```PowerShell
  -V, --version                output the version number
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging
  --deployType <type>          The type of deployment to do (e.g. 'full')
  --ignore <glob>              Path-like (e.g. '*.log') matching files to exclude from the deployment/accelerator zip (default: [])
  --include <glob>             Path-like (e.g. '*.md') matching files to include in the deployment/accelerator zip (default: [])
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ output marcus-app
  yarn occ output marcus-app --deployType full  --ignore *.log
  ```


## 11) Delete
 
### Usage: yarn occ delete [appName] [options]

**Deletes an occ application from OCC Admin Server.**

### Options:
  ```PowerShell
  -V, --version                output the version number
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  -p, --publish                With this option, any changes from the deploy/delete will be published.
  --publishAll [confirm]       With this option, all changes in the publishing queue will be published. You will be prompted to confirm this option. Optionally, the prompt can be bypassed by specifying 'Y'
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -h, --help                   display help for command
  ```   

### Examples:
  ```Shell
  yarn occ delete marcus-app
  yarn occ delete marcus-app --publishAll
  ```


## 12) Download

### Usage: yarn occ download [appName] [options]

**Download the current deployment for an application**

### Options:
  ```PowerShell
  -V, --version                output the version number       
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging        
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  -L, --live                   Operate in the live context.    
  --no-live                    Operate in the preview context. This is the default behavior.
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -d, --deployment <deployId>  Query information for a specific deployment
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ download marcus-app
  yarn occ download marcus-app --live true
  ```


# 13) List-Apps

### Usage: yarn occ list-apps [options]

**List the available applications and clusters on the server.**

### Options:
  ```PowerShell
  -j, --json                  Output the results as raw JSON instead of formatted text.
  -V, --version               output the version number
  -v, --verbose               Provides verbose logging where available
  --no-verbose                Disables verbose logging
  -k, --appKey [key]          With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>       Application server URL
  -a, --appServerAdmin <url>  Application admin server URL     
  -e, --serverEnv <env>       Cloud Commerce server environment to use
  -h, --help                  display help for command
  ```

### Examples:
  ```Shell
  yarn occ list-apps
  yarn occ list-apps --serverEnv development
  ```


## 14) Set-Logging-Options

### Usage: yarn occ set-logging-options [options] [clusterId]

**Sets various logging options for the given cluster.**

### Options:
  ```PowerShell
  -V, --version               output the version number        
  -v, --verbose               Provides verbose logging where available
  --no-verbose                Disables verbose logging
  -k, --appKey [key]          With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>       Application server URL
  -a, --appServerAdmin <url>  Application admin server URL     
  -e, --serverEnv <env>       Cloud Commerce server environment to use
  -L, --live                  Operate in the live context.     
  --no-live                   Operate in the preview context. This is the default behavior.
  --appLogLevel <level>       Sets the application log level for the given cluster.
  --systemLogLevel <level>    Sets the system log level for the given cluster.
  -h, --help                  display help for command
  ```

### Examples:
  ```Shell
  yarn occ set-logging-options
  yarn occ set-logging-options --appLogLevel 2
  ```


## 15) Upgrade

### Usage: yarn occ upgrade [options] [version]

**Upgrade the versions of OSF packages depended on throughout the workspace.**

### Options:
  ```PowerShell
  --dryRun                    Do not make any actual changes, just list what changes would be made.
  --latest                    Upgrade to the latest version, regardless of BREAKING CHANGES from the current OSF version      
  --acceptDowngrade           If the current OSF version is too new for the OCC server, downgrade to the latest OSF version that matches the OCC server
  --force                     Instead of exiting when unable to contact the registry/OCC Servers, found version incompatibilities, or encountered other errors, attempt to continue. MUST be used with a specific version of OSF (e.g. 'occ upgrade 2.0.0 --force')
  -k, --appKey [key]          With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>       Application server URL
  -a, --appServerAdmin <url>  Application admin server URL     
  -e, --serverEnv <env>       Cloud Commerce server environment to use
  --no-verifyOcc              Don't check the OCC Server version when determining what version of OSF to upgrade to (not recommended)
  -V, --version               output the version number        
  -v, --verbose               Provides verbose logging where available
  --no-verbose                Disables verbose logging
  -h, --help                  display help for command
  ```

### Examples:
  ```Shell
  yarn occ upgrade
  yarn occ upgrade --dryRun
  yarn occ upgrade --acceptDowngrade 4.0.0
  yarn occ upgrade --latest
  ```


## 16) Download-Assets

### Usage: yarn occ download-assets [appName] [options]

**Downloads the assets from design studio and writes them to the workspace**

### Options:
  ```PowerShell
  -V, --version                output the version number       
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging        
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  -L, --live                   Operate in the live context.    
  --no-live                    Operate in the preview context. This is the default behavior.
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  --confirm                    Bypasses the confirmation for overwriting the files in the local workspace.
  -r, --reset                  Resets the state of the workspace assets to that of the Design Studio. Note that any pending changes to assets in the workspace will be lost.
  --no-import                  Don't unpack the files into the workspace, simply save the assets to a zip file. They can then be imported/restored later using --fromFile.
  --dest <path>                Saves the downloaded zip file to a location other than the default.
  --fromFile <path>            Load the assets from a zip file on disk instead of from an OCC Admin server.
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ download-assets my-app
  yarn occ download-assets my-app --reset
  yarn occ download-assets my-app --fromFile ./assets.zip
  ```


## 17) Upload-Search-Config

### Usage: yarn occ upload-search-config [appName] [options]

**Upload the search configuration**

### Options:
  ```PowerShell
  -V, --version                output the version number       
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging        
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ upload-search-config marcus-app
  yarn occ upload-search-config marcus-app --no-localDevAppName
  ```


## 18) Upload-Custom-TypeHead-KeyWords

### Usage: yarn occ upload-custom-typeahead-keywords [appName] [options]

**Reads the custom keyword records from the 'config/search/data/keywords.js' in the app, and appends them to the existing elements in the '/gsdata/v1/cloud/data/keywords' record collection.** 

### Options:
  ```PowerShell
  -V, --version                output the version number       
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging        
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ upload-custom-typeahead-keywords marcus-app
  yarn occ upload-custom-typeahead-keywords marcus-app --help
  ```



## 19) Serve

### Usage: yarn occ serve [appName] [options]

**Start presentation server [localhost]**

### Options:
  ```PowerShell
  -V, --version                output the version number       
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging        
  -k, --appKey [key]           With this option you will be prompted for an application key (OAuth access token)
  -s, --appServer <url>        Application server URL
  -a, --appServerAdmin <url>   Application admin server URL    
  -e, --serverEnv <env>        Cloud Commerce server environment to use
  --httpHost <host>            Presentation server hostname (http)
  --httpPort <port>            Presentation server port (http) 
  --httpsHost <host>           Presentation server hostname (https)
  --httpsPort <port>           Presentation server port (https)
  --sslKey <path>              The path to the ssl key file used for https.
  --sslCert <path>             The path to the ssl cert file used for https.
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  -L, --live                   Operate in the live context.    
  --no-live                    Operate in the preview context. This is the default behavior.
  --listConfig                 List configuration used for the operation.
  --appContext <context>       Select an app config from config/app-config.
  -m, --dsAssetMode <mode>     Sets the rendering mode for design studio assets ("local" | "remote").
  --skipProxy                  Do not setup a proxy between the app and OCC server.
  -h, --help                   display help for command
  ``` 

### Examples:
  ```Shell
  yarn occ serve marcus-app
  yarn occ serve marcus-app --appServer http://a-vm.us.oracle.com:8080
  ```


## 20) Create-Template

### Usage: yarn occ create-template [appName] [options]

**Creates a workspace template archive containing the given app.**

### Options:
  ```PowerShell
  -V, --version                output the version number
  -v, --verbose                Provides verbose logging where available
  --no-verbose                 Disables verbose logging
  --deployType <type>          The type of deployment to do (e.g. 'full')
  --ignore <glob>              Path-like (e.g. '*.log') matching files to exclude from the deployment/accelerator zip (default: [])
  --include <glob>             Path-like (e.g. '*.md') matching files to include in the deployment/accelerator zip (default: [])
  --localDevAppName <appName>  Specify a local development application name to use in the context of this workspace when doing application specific operations such as occ deploy, occ start, etc. This is useful when multiple developers are working on the same application, sharing an OCC instance, and want to isolate their OCC asset changes. Each local dev app name will appear as a separate application in Design Studio. Note that when an application is deployed using a local app name, it will not be installed in the preview or live sandboxes. Developers must launch a local server using dsAssetMode=remote to serve assets from Design Studio.
  --no-localDevAppName         Ignore the local development application name configured for the application.
  --dest <path>                The destination location for the output.
  -h, --help                   display help for command
  ```

### Examples:
  ```Shell
  yarn occ create-template marcus-app --dest archives-directory
  yarn occ create-template marcus-app --ignore *.log --deployType full --dest archives-directory
  ```



## 21) Create-Widget

### Usage: yarn occ create-widget [appName] [options]

**Create a widget plugin for a specific application.**

### Options:
  ```PowerShell
  -n, --name <widget-name>    Name of the widget plugin to create.
  --template <template-name>  Name of the template to create the widget from (available templates: Blank, CurrencySelector). (default: "Blank")
  --list-templates            Show list of available widget templates available.
  -h, --help                  display help for command
  ```

### Examples:
  ```Shell
  yarn occ create-widget --name MyWidget
  yarn occ create-widget blank-store --name MyWidget
  yarn occ create-widget blank-store --name MyWidget --template CurrencySelector
  ```



## 22) Create-Fetcher

### Usage: yarn occ create-fetcher [appName] [options]

**Create a fetcher for a specific application.**

### Options:
  ```PowerShell
  -n, --name <fetcher-name>        Name of the fetcher plugin to create.
  --forComponent <component-name>  Create the fetcher for a specific component, default is to create a global fetcher.        
  --endpoint <endpoint>            An Endpoint for fetcher to invoke.
  --selector <selector>            A Selector to be used by the fetcher to check if data exists in the state.
  -h, --help                       display help for command
  ```

### Examples:
  ```Shell
  yarn occ create-fetcher --name MyWidget
  yarn occ create-fetcher --name myFetcher --endpoint anEndpoint --selector aSelector
  yarn occ create-fetcher --name myFetcher --endpoint anEndpoint --selector aSelector --forComponent HelloWorld
  ```



## 23) Creation-Action

### Usage: yarn occ create-action [appName] [options]

**Create an action for a specific application.**

### Options:
  ```PowerShell
  -n, --name <action-name>  Name of the action to create. Defaults to the endpoint name if not specified.
  --endpoint [endpoint]     Endpoint for action to invoke.     
  --reducer                 Create a reducer that updates the application state.
  -h, --help                display help for command
  ```

### Examples:
  ```Shell
  yarn occ create-action --name myAction
  yarn occ create-action --name myAction --endpoint
  yarn occ create-action --endpoint anEndpoint
  yarn occ create-action --name myAction --endpoint anEndpoint
  yarn occ create-action --name myAction --reducer
  ```



## 24) Create-Selector

### Usage: yarn occ create-selector [appName] [options]

**Create a selector for a specific application. Please refer to the example in the sample application, or the OSF documentation.**

### Options:
  ```PowerShell
  -n, --name <selector-name>      Name of the selector to create.
  --repository <repository-name>  Name of the repository to select.
  --table <table-name>            Name of the table to select from repository.
  --entity <entity-name>          Name of the entity to select from table.
  --entityId <entityId>           A selector to return an entity by ID.
  -h, --help                      display help for command
  ```

### Examples:
  ```Shell
  yarn occ create-selector --name mySelector --repository myRepository
  yarn occ create-selector --name mySelector --repository myRepository --table myTable
  yarn occ create-selector --name mySelector --repository myRepository --table myTable --entityId myEntityId
  yarn occ create-selector --name mySelector --repository myRepository --table myTable --entity myEntity
  yarn occ create-selector --repository myRepository
  yarn occ create-selector --repository myRepository --table myTable
  yarn occ create-selector --repository myRepository --table myTable --entityId myEntityId
  yarn occ create-selector --repository myRepository --table myTable --entity myEntity
  ```



## 25) Create-EndPoint

### Usage: yarn occ create-endpoint [appName] [options]

**Create endpoint(s) for a URL or from a Swagger API document.**

### Options:
  ```PowerShell
  -n, --directoryName  <name>      The directory name under which to create endpoints, relative to the default path /src/plugins/endpoints.
  --swagger <url | file>           The URL or Path of a Swagger API document from which to create endpoint(s).
  --url <url>                      The URL/Origin for which to create endpoint(s).
  --verb <method>                  Method for Non Swagger API document such as Get, Put, Post.
  --endpoints <list-of-endpoints>  Comma-separated list of endpointIds to create from the Swagger API document.
  -h, --help                       display help for command
  ```  

### Examples:
  ```Shell
  yarn occ create-endpoint --directoryName aDirectoryName --swagger http://example.com/catalogApi
  yarn occ create-endpoint --directoryName aDirectoryName --swagger http://example.com/catalogApi --endpoints endpointId1,endpointId2
  yarn occ create-endpoint --directoryName aDirectoryName --url http://example.com/catalogApi --verb [method]
  yarn occ create-endpoint --swagger http://example.com/catalogApi
  yarn occ create-endpoint --url http://example.com/catalogApi --verb [method]
  ```



## 26) List-EndPoints

### Usage: yarn occ list-endpoints [options]

**List all available endpoints from a Swagger API document.**   

### Options:
  ```PowerShell
  --swagger <url | file>  The URL or Path of a Swagger API document to list all endpoints from.
  -h, --help              display help for command
  ```

### Examples:
  ```Shell
  yarn occ list-endpoints --swagger http://example.com/catalogApi
  yarn occ list-endpoints --swagger http://example.com/organizationApi
  ```



## 27) Create-Subscriber

### Usage: yarn occ create-subscriber [appName] [options]

**Create a subscriber for named application.**

### Options:
  ```PowerShell
  -n, --name <subscriber-name>  Name of the subscriber plugin to create.
  -h, --help                    display help for command
  ```

### Examples:
  ```Shell
  yarn occ create-subscriber --name mySubscriber
  ```


## 28) Validate-Assets

### Usage: yarn occ validate-assets [appName] [options]

**Validate all assets, including components, containers, pages and slots for the application.**

### Options:
  ```PowerShell
  -h, --help  display help for command
  ```

### Examples:
  ```Shell
  yarn occ validate-assets
  yarn occ validate-assets marcus-app
  ```



## 29) Version

### Usage: yarn occ version [options]

**List the version of various OSF elements on the workspace, and the Oracle Commerce Cloud version.**

### Options:
  ```PowerShell
  -a, --appServerAdmin <url>  Application admin server URL.    
  -e, --serverEnv <env>       Cloud Commerce server environment to use (from '.occ/config.js')
  -h, --help                  display help for command
  ```

### Examples:
  ```Shell
  yarn occ version
  yarn occ version --serverEnv development
  ```

## 30) Coming soon...
