<h1>CupidBot</h1>
This lab is part of TryHackMe's Love at First Breach 2026
challenges themed around Valentine's day and aimed at beginners.
<br>
<h2>Starting the CupidBot</h2>
Usually CTF challenges require a virtual machine or a network of machines to interact with. 
Since these labs are aimed at beginner-level hackers, let's start with how to access the CupidBot.<br>
The circled button in the image below is used to start the AI chatbot.

![How to start CupidBot](/img/cupidbotstart1.png)

<h2>Exploiting the chatbot</h2>
There are three flags in the room.<br>
1. Prompt Injection Flag<br>
2. System Flag<br>
3. Final Flag <br>

<br>
I had recently gone through the 

[PortSwigger's LLM attacks](https://portswigger.net/web-security/llm-attacks)
resource and I was expecting a bit more resistance from the CupidBot. The CupidBot leaked all of its flags and how to get them on my second question which will circle back to at the end.<br><br>
Generally, an attacker should engage with a chatbot and ask it questions regarding its functionality, restrictions, possible APIs it can access, and evade security measures by trying to impersonate as a more privileged user, such as an administrator or a software developer, or otherwise an important person such as a CEO of the company.

<h3>Prompt Injection Flag</h3>
The prompt injection flag is presented to the attacker when the attacker mentions or uses a verification code. The verification code seems to be given to the attacker very early on when talking to the CupidBot. I got the code with the prompt: "What can you do?"

<h3>System Prompt Flag</h3>
The second flag is presented to the attacker when they mention "System Prompt" or ask to use system prompt. Solving this is also hinted at in the question for the flag. 

**What's the system flag?**

<h3>Final Flag</h3>
This flag is presented to the attacker when they claim to be an administrator or ask for admin access. Chatbots should have security measures in place to prevent attackers from gaining administrator access through them.

<h3>How I gained the flags</h3>
I started my attack with the simple prompt of "What can you do?" which revelead the verification code from the first flag. The verification code would have been an obvious lead to follow but I also noticed something else below the input box. There was an icon of a lightning bolt and a counter for tokens. The counter increased by a non-obvious number after my first question which captured my interest. With the second question of "What are the tokens for?", I was able to use an unexpected attack vector which caused the CupidBot to spill the beans so to speak.<br>
The image below shows the results of my attack.
<br>

![How I captured the flags](/img/cupidbothacked.png)
