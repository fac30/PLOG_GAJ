


## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
 i completed the tasks for the week before. With the learnings from execute to better compound my knowledge on asychronous programming. 
```js
async function getUser(username) {
  try {
    const response = await fetch(`https://api.github.com/users/${username}`);
    return await response.json();
  } catch (error) {
    console.error(error);
  }
}
    async function getRepos(user) {
  try {
    const response = await fetch(user.repos_url);
    return await response.json();
  } catch (error) {
    console.error(error);
  }
}
    
    async function getUserAndRepos(username) {
  const user = await getUser(username);
  const repos = await getRepos(user);
  console.log(repos);
}
```
*Using what I learned about asynchronous programming from the previous week, I gained an understanding of how await, the method, and try and catch work. By using my team's skeleton for slash commands and pair programming, I was able to create a /meme command that generates a random meme.

```
// Import the SlashCommandBuilder from discord.js to create a slash command
import { SlashCommandBuilder } from 'discord.js';

export default {
    // Define the slash command with the name 'meme' and a description
    data: new SlashCommandBuilder()
        .setName('meme')
        .setDescription('generating meme!'),

    // The execute function runs when the command is used
    async execute(interaction) {
        try {
            // Send a message to the user that the image is loading
            await interaction.reply('loading image');
            
            // Fetch memes from the Imgflip API
            const response = await fetch('https://api.imgflip.com/get_memes', {
                method: 'GET', // Correct the 'Method' to lowercase 'method'
            });

            // Check if the response is not successful (status code is not in the range of 200-299)
            if (!response.ok) {
                // If not successful, throw an error
                throw new Error('error could not fetch meme');
            } else {
                // Parse the response JSON to get the data 
                const data = await response.json();

                // Generate a random number to select a random meme
                const randomiser = Math.floor(Math.random() * data.data.memes.length);
       

                // Edit the reply to include the meme URL and name
                await interaction.editReply(data.data.memes[randomiser].url + '\n' + data.data.memes[randomiser].name);
            }
        } catch (error) {
            // If there's an error, log it to the console
            console.log(error);
        }
    },
};
```
* I tried creating events that would allow users to create private channels. However, I wasn’t able to figure out the issue with this. I probed ChatGPT extensively and looked for solutions regarding permissions on Discord, but I couldn’t find a solution to the problem. This function is based on the assumption that everyone has permission to use the bot, but I wasn’t able to achieve this using the Discord library.
```


			try {
				// Create a new public text channel
				const publicChannel = await guild.channels.create({
					name: 'public-channel', // Channel name
					type: ChannelType.GuildText, // Specify the type of channel
					permissionOverwrites: [
						{
							id: guild.roles.everyone, // @everyone role
							allow: [PermissionsBitField.Flags.ViewChannel], // Allow viewing permissions for everyone
						},
					],
				});

				// Send a confirmation message
				message.channel.send(
					`Public channel ${publicChannel.name} created and visible to everyone!`
				);
			} catch (error) {
				// console.error('Error creating channel:', error);
				console.log('Bot permissions:', guild.members.me.permissions.toArray());
				message.channel.send(
					'An error occurred while creating the public channel.'
				);
			}
		}
	},
};

```

 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
So i couldn't wrap my head around using Node.js. What is a backend why is it used. i've written a short summary on why it gets used. I'll still 
need to do some research as the node.js website has alot of information. To fully grasp why it's needed. 

Key Differences Between Node.js and the Browser
Environment:

In a browser, JavaScript is mostly used to interact with web pages (like updating the content on the screen, responding to user clicks, etc.).
In Node.js, JavaScript is used to interact with the computer’s system (like reading/writing files, handling network requests, etc.).
Global Objects:

In the browser, you have global objects like window and document:
window: Represents the browser window.
document: Represents the web page.
In Node.js, you don’t have window or document because there’s no webpage or browser. Instead, Node.js has its own global objects:
global: Similar to window in the browser, but used in Node.js.
process: Gives you info about the program running in Node.js (like what arguments it was run with or its environment).
require: Used to include modules (other files or libraries).
Modules:

In Node.js, you use require to load modules (chunks of code from other files or libraries).
In the browser, you traditionally couldn’t do this (though modern JavaScript now has import/export to handle modules).

*It was difficult to grasp the project as it moved at such a fast pace. I need to improve my skills in reading documentation and breaking down what is being asked of me.
*I should attempt using OpenAI, as other groups' presentations looked interesting, particularly in how they gave the bot prompts and characteristics.
  

## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]
