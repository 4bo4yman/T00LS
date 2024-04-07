<h1>$${\color{red}Burp} \space {\color{red}Suite}$$</h1>

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/0cfd035a-8f34-484b-8738-fa737cb9135e" >
</p> 



   - Tasks: The Tasks menu allows you to define background tasks that Burp Suite will perform while you use the application. In Burp Suite Community, the default “Live Passive Crawl” task, which automatically logs the pages visited, is sufficient for our purposes in this module. Burp Suite Professional offers additional features like on-demand scans.

   - Event log: The Event log provides information about the actions performed by Burp Suite, such as starting the proxy, as well as details about connections made through Burp.

   - Issue Activity: This section is specific to Burp Suite Professional. It displays the vulnerabilities identified by the automated scanner, ranked by severity and filterable based on the certainty of the vulnerability.

   - Advisory: The Advisory section provides more detailed information about the identified vulnerabilities, including references and suggested remediations. This information can be exported into a report. In Burp Suite Community, this section may not show any vulnerabilities.

Throughout the various tabs and windows of Burp Suite, you will notice question mark icons (question mark icon).

Clicking on these icons opens a new window with helpful information specific to that section. These help icons are invaluable when you need assistance or clarification on a particular feature, so make sure to utilise them effectively.

Help menu when the question mark logo is clicked

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/a34855d3-e73d-4840-9b25-ea83ce528625" height=550 width=800>
</p> 

By exploring the different tabs and functionalities of Burp Suite, you will gradually become familiar with its capabilities.

****************

<h1>$${\color{yellow}2.} \space {\color{yellow}Navigation }$$</h1>

In Burp Suite, the default navigation is primarily done through the top menu bars, which allow you to switch between modules and access various sub-tabs within each module. The sub-tabs appear in a second menu bar directly below the main menu bar.

Here's how the navigation works:

  - Module Selection: The top row of the menu bar displays the available modules in Burp Suite. You can click on each module to switch between them. For example, the Burp Proxy module is selected in the image below.


<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/76cc404e-c5b9-4919-81f1-7094b7f8c26c" >
</p> 

  - Sub-Tabs: If a selected module has multiple sub-tabs, they can be accessed through the second menu bar that appears directly below the main menu bar. These sub-tabs often contain module-specific settings and options. For example, in the image above, the Proxy Intercept sub-tab is selected within the Burp Proxy module.

  - Detaching Tabs: If you prefer to view multiple tabs separately, you can detach them into separate windows. To do this, go to the Window option in the application menu above the Module Selection bar. From there, choose the "Detach" option, and the selected tab will open in a separate window. The detached tabs can be reattached using the same method.

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/058c8a3e-f9bf-4254-bd09-cac3f1a54127 " >
</p> 

Burp Suite also provides keyboard shortcuts for quick navigation to key tabs. By default, the following shortcuts are available:


![image](https://github.com/4bo4yman/T00LS/assets/156849852/dfd7866e-9183-4016-a571-3837660bf1da)

***************

<h1>$${\color{yellow}3.} \space {\color{yellow}Options }$$</h1>


Before diving into the Burp Proxy, let's explore the available options for configuring Burp Suite. There are two types of settings: Global settings (also known as User settings) and Project settings.

  - Global Settings: These settings affect the entire Burp Suite installation and are applied every time you start the application. They provide a baseline configuration for your Burp Suite environment.
  - Project Settings: These settings are specific to the current project and apply only during the session. However, please note that Burp Suite Community Edition does not support saving projects, so any project-specific options will be lost when you close Burp.

    To access the settings, click on the Settings button in the top navigation bar. This will open a separate settings window.

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/b56b5842-28ec-4a2e-a52a-6dc30973fb4c " >
</p> 


In the Settings window, you will find a menu on the left-hand side. This menu allows you to switch between different types of settings, including:

  1. Search: Enables searching for specific settings using keywords.
  2. Type filter: Filters the settings for User and Project options.
     - User settings: Shows settings that affect the entire Burp Suite installation.
     - Project settings: Displays settings specific to the current project.
  3. Categories: Allows selecting settings by category.


<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/f40b2fe5-9fa9-46f0-abca-81ed86eeadc9 " >
</p>

It's worth noting that many tools within Burp Suite provide shortcuts to specific categories of settings. For example, the Proxy module includes a Proxy settings button that opens the settings window directly to the relevant proxy section.


<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/c413943f-e90c-4861-b9a5-0f54280130d1 " >
</p>

The search feature on the settings page is a valuable addition, allowing you to quickly search for settings using keywords.

Take some time to familiarise yourself with the range of configurable options in Burp Suite. Once you are comfortable, you can proceed with the exercises related to configuring Burp Suite settings.

**************
<h1>$${\color{yellow}4.} \space {\color{yellow}FoxyProxy }$$</h1>

To use the Burp Suite Proxy, we need to configure our local web browser to redirect traffic through Burp Suite. In this task, we will focus on configuring the proxy using the FoxyProxy extension in Firefox.

Please note that the instructions provided are specific to Firefox. If you are using a different browser, you may need to find alternative methods.

Here are the steps to configure the Burp Suite Proxy with FoxyProxy:

  1. **Install FoxyProxy**: Download and install the [FoxyProxy Basic extension](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/).

  2. **Access FoxyProxy Options**: Once installed, a button will appear at the top right of the Firefox browser. Click on the FoxyProxy button to access the FoxyProxy options pop-up.

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/910f29cb-769e-4890-b7bf-23df138d62e7" >
</p>

  3. **Create Burp Proxy Configuration**: In the FoxyProxy options pop-up, click the **Options** button. This will open a new browser tab with the FoxyProxy configurations. Click the Add button to create a new proxy configuration.

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/3bdd8c38-a085-401f-8388-a4fe93e95a38" >
</p>

  4. **Add Proxy Details**: On the "Add Proxy" page, fill in the following values:

  - Title: ```Burp``` (or any preferred name)
  - Proxy IP: ```127.0.0.1```
  - Port: ```8080```

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/34232bb4-00a4-4957-98c0-d64ad2a7b002" >
</p>


  5. **Save Configuration**: Click **Save** to save the Burp Proxy configuration.

  6. **Activate Proxy Configuration**: Click on the FoxyProxy icon at the top-right of the Firefox browser and select the ```Burp``` configuration. This will redirect your browser traffic through ```127.0.0.1:8080```. Note that Burp Suite must be running for your browser to make requests when this configuration is activated.

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/f453c1ce-7845-4faf-a00b-4fc57cfa378c" >
</p>

  7. **Enable Proxy Intercept in Burp Suite**: Switch to Burp Suite and ensure that Intercept is turned on in the **Proxy** tab.

<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/2702a9bf-b080-4292-ab19-4e9f01167cf4" >
</p>



















