Update \[6-2-26]:

* added zoo code (formerly roo) rule template. Locate .roo folder inside the template folder and copy-paste it to your current project directory. You can also use this in roo code.
* on your very first prompt or in the new chat session, prompt this "-setup". To initialize memory files and record the context of your current project then after that you can start working.
* Other specialized prompts in roo/zoo code: 

&#x09;-context //updates or stores only the project\_memory.md file where from there it stores the current context of your current project.

&#x09;-error //updates or stores error\_memory.md file where it logs active and resolved errors.

&#x09;-codebase //updates or stores codebase\_map.md file where it contains the logic and workflow of your project. This is important so 	you won't lose track of ai changes and progress.

&#x09;-setup //dynamically updates all three at once above. Recommended in first use or fresh start of chat session in ai agent.

\_\_\_\_\_



How to?



cd Downloads



git clone https://github.com/worriee/clinerulestemplate.git

