<h1>$${\color{red}Intruder} $$</h1>

Intruder is Burp Suite's built-in fuzzing tool that allows for automated request modification and repetitive testing with variations in input values. By using a captured request (often from the Proxy module), Intruder can send multiple requests with slightly altered values based on user-defined configurations. It serves various purposes, such as brute-forcing login forms by substituting username and password fields with values from a wordlist or performing fuzzing attacks using wordlists to test subdirectories, endpoints, or virtual hosts. Intruder's functionality is comparable to command-line tools like Wfuzz or ffuf.

However, it's important to note that while Intruder can be used with Burp Community Edition, it is rate-limited, significantly reducing its speed compared to Burp Professional. This limitation often leads security practitioners to rely on other tools for fuzzing and brute-forcing. Nonetheless, Intruder remains a valuable tool and is worth learning how to use it effectively.

Let's explore the Intruder interface:


<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/0e299d0c-740f-4038-97e5-4af06a08f502" >
</p> 



The initial view of Intruder presents a simple interface where we can select our target. This field will already be populated if a request has been sent from the Proxy (using ```Ctrl + I``` or right-clicking and selecting "Send to Intruder").

There are four sub-tabs within Intruder:

  - **Positions**: This tab allows us to select an attack type (which we will cover in a future task) and configure where we want to insert our payloads in the request template.
  - **Payloads**: Here we can select values to insert into the positions defined in the Positions tab. We have various payload options, such as loading items from a wordlist. The way these payloads are inserted into the template depends on the attack type chosen in the Positions tab. The Payloads tab also enables us to modify Intruder's behavior regarding payloads, such as defining pre-processing rules for each payload (e.g., adding a prefix or suffix, performing match and replace, or skipping payloads based on a defined regex).
  - **Resource Pool**: This tab is not particularly useful in the Burp Community Edition. It allows for resource allocation among various automated tasks in Burp Professional. Without access to these automated tasks, this tab is of limited importance.
  - **Settings**: This tab allows us to configure attack behavior. It primarily deals with how Burp handles results and the attack itself. For instance, we can flag requests containing specific text or define Burp's response to redirect (3xx) responses.

**Note**: The term "fuzzing" refers to the process of testing functionality or existence by applying a set of data to a parameter. For example, fuzzing for endpoints in a web application involves taking each word in a wordlist and appending it to a request URL (e.g., http://MACHINE_IP/WORD_GOES_HERE) to observe the server's response.

************

<h1>$${\color{yellow}2.} \space {\color{yellow}Positions }$$</h1>


When using Burp Suite Intruder to perform an attack, the first step is to examine the positions within the request where we want to insert our payloads. These positions inform Intruder about the locations where our payloads will be introduced (as we will explore in upcoming tasks).

Let's navigate to the Positions tab:



<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/1e8d7fe1-0ab0-4d92-a8f3-b406fe05c33b" >
</p> 

Notice that Burp Suite automatically attempts to identify the most probable positions where payloads can be inserted. These positions are highlighted in green and enclosed by section marks (```§```).

On the right-hand side of the interface, we find the following buttons: ```Add §```, ```Clear §```, and ```Auto §```:

 - The ```Add §``` button allows us to define new positions manually by highlighting them within the request editor and then clicking the button.
 - The ```Clear §``` button removes all defined positions, providing a blank canvas where we can define our own positions.
 - The ```Auto §``` button automatically attempts to identify the most likely positions based on the request. This feature is helpful if we previously cleared the default positions and want them back.

The following GIF demonstrates the process of adding, clearing, and automatically reselecting positions:


<p align="center">
<img src="https://github.com/4bo4yman/T00LS/assets/156849852/4b4c490c-2213-423c-b9e5-41212a93f519" >
</p> 















