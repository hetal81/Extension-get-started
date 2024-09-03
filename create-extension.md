---
hide_table_of_contents: false
title: Get Started
custom_edit_url: null
sidebar_label: Get Started
---
This guide provides a step-by-step framework for creating a new extension. It includes all necessary dependencies, starter code, and a well-organized folder structure to streamline your development process. The provided starter code features a pre-implemented OAuth flow, simplifying authentication. Additionally, it offers an easy setup for webhook configuration, enabling seamless integration. Follow this guide to efficiently build and deploy your extension.

## What you'll learn?

You'll learn how to do the following tasks:
1. [Installation of FDK CLI](#install-fdk-cli)
2. [Generate starter code for your extension using FDK CLI](#generate-the-starter-code-for-extension)
3. [Extension Preview on development account](#preview-your-extension-on-a-development-account)

## Prerequisites

Before getting started, you'll need the following:
* You've created a [Partner account](https://partners.fynd.com) and a [Development account](docs/partners/testing-extension/development-acc.md#create-development-account).
* You’ve installed either of the following:
  * [Node.js (v16.x)](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) with npm
  * [Java (v17)](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) with maven
* You've installed [Git](https://git-scm.com/downloads).
* You've installed [Redis](https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/).[optional]

## 1. Installation of FDK-CLI

FDK-CLI is a command-line interface tool to simplify the development process of themes and extensions. It optimizes the development workflow by offering key commands for creating, testing, and launching projects efficiently. For more information, read [FDK-CLI](https://github.com/gofynd/fdk-cli).

- To install the latest version of FDK-CLI, run the following command in your terminal:
```bash
npm install -g @gofynd/fdk-cli
```

- To Check `fdk-cli` is successfully installed, run this command in your terminal:
```bash
fdk --version
```

- If successfully installed, it will return the version:

![cli_version](https://cdn.pixelbin.io/v2/himanshu01010/original/Extension-build/fdk_install_version_v2.png)

:::tip
To see list of available commands and their descriptions, use `fdk --help`.
:::

## 2. Generate the starter code for extension

Steps to generate your extension's starter code using FDK CLI:

1. Login to FDK-CLI using command below:

  ```bash
  fdk login
  ```

  Verify if you're logged in by running the following command:
  ```bash
  fdk user
  ```

2. To create new extension run the following command:

  ```bash
  fdk extension init
  ```
  :::info
  To know more about the init command, [click here](https://github.com/gofynd/fdk-cli/blob/master/README.md#extension-init).
  :::

:::note
**Heads up!**

When you run the `fdk extension init` command, you'll be prompted with two choices if you've already set up an extension:

1. Create a new extension
2. Use an existing extension

If you want to kickstart your extension from an existing one, choose second option. This will automatically skip steps 3 and 4, saving you some time.
:::

3. Enter **Extension** Name
4. Select Extension Type. You can select between [Private](../publishing/private-extension) and [Public](../publishing/public-extension).
5. Select your preferred technology stack from these options:
    - Node + Vue 3 + SQLite
    - Node + React.js + SQLite
    - Java + Vue 2 + SQLite
    - Java + React.js + SQLite

  ![extension init](https://cdn.pixelbin.io/v2/himanshu01010/original/Extension-build/extension_init_3.png)

  FDK-CLI will create the extension's folder into the current directory of the local system with starter code and register the extension in your [Fynd Partners](https://partners.fynd.com/) account. Navigate to Partner Panel > Extensions > Your Extension, to check and edit your extension's registration details

6. Change the directory to your extension's directory by running the following command:

  ```javascript
  cd "Example Extension"
  ```

:::info
Internally, FDK-CLI integrates the FDK Extension and Client libraries into the starter code. These libraries facilitate OAuth implementation, enable SDK method calls, and assist in configuring webhooks. For detailed guidance, refer to the documentation corresponding to your preferred technology stack.

#### FDK Extension Libraries

The FDK Extension library facilitates seamless configuration of authentication for accessing Fynd Platform APIs and webhooks subscriptions. OAuth implementation is essential for establishing the necessary foundational authentication for both functionalities. Explore the following libraries in your preferred language.

* [fdk-extension-javascript](https://github.com/gofynd/fdk-extension-javascript)
* [fdk-extension-java](https://github.com/gofynd/fdk-extension-java)

#### FDK Client Libraries

FDK Client Library is a peer dependency in FDK Extension Library and contains all the methods to call Fynd platform API's.

* [fdk-client-javascript](https://github.com/gofynd/fdk-client-javascript)
* [fdk-client-java](https://github.com/gofynd/fdk-client-java)
* [fdk-client-swift](https://github.com/gofynd/fdk-client-swift)
* [fdk-client-kotlin](https://github.com/gofynd/fdk-client-kotlin)
:::

## 3. Extension Preview on development account

1. Run following `fdk` command to get the extension preview URL.

```bash
fdk extension preview
```

:::info
The above command will launch both the frontend and backend servers of your extension, followed by establishing a secure public tunnel, making your extension accessible to external users. For more information about this command, check out [this link](https://github.com/gofynd/fdk-cli/tree/master?tab=readme-ov-file#extension-preview-url).
:::

:::note
To install or preview a Private extension on any company, ensure the company is added as a subscriber to your extension first.
:::

2. Copy Preview URL and paste it into the browser to Install/Launch Extension

![extension_launch](https://cdn.pixelbin.io/v2/himanshu01010/original/Extension-build/extension_launch.png)

Congratulations!! You have created your first extension. Now, start building your extension features by using APIs and SDKs.




## Advance guide

- If you want to use a different environment (cluster) for extension development, you can change the active environment by using the following command:

  ```bash
  fdk login --host your-partner-domain
  ```
- This command will change the active environment to the provided cluster host. For example, if your partner account exists at partners.fynd.com, you should use:

  ```bash
  fdk login --host partners.fynd.com
  ```
  This will set the active environment to the Fynd cluster.
  