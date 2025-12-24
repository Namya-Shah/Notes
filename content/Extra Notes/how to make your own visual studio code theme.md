Programming Language?: No

learn how to create your own vscode theme with @agenomicsphd ✨ first, you need to have git and node.js installed to run this

hey guys! liv here, just wanted to pop in and say that if you found this useful, please consider engaging with this video! it really helps with the algo + allows me to create keeping content for you! 

### 📝 SKIP TO 05:09 for the tutorial!

[https://www.youtube.com/watch?v=OiYDvwUbem8](https://www.youtube.com/watch?v=OiYDvwUbem8)

### Step 1. Install yo code

open a terminal and run the following code in order to install the package ‘yo code’.

```basic

npm install -g yo generator-code
yo code
```

### Step 2. Set up and name your theme

Use your arrow keys in order to select ‘New color theme’ from the drop down menu that appears.
![[Screenshot_2023-09-02_at_11.25.27.png]]
💡Hint: tick these off as you go to make sure you don’t miss anything..

- [ ] Select ‘New colour theme’
- [ ] Select ‘No, start fresh’
- [ ] Choose a name for your extension
- [ ] Choose an identifier (i just keep this the same as my name)
- [ ] Enter a description (for example ‘cozy light mode theme made by @agenomicsphd!’)
- [ ] Choose a theme name shown to user
- [ ] Select a base theme
- [ ] Select if you want a git repository (yo

You should then see something that looks like this!

![[Screenshot_2023-09-02_at_11.34.47.png]]
### Step 3. Navigate to your theme!

```basic
cd [your theme name]
# now see the contents using
ls
# you should have a CHANGELOG, README, themes directory, package.json and vsc.extension-quickstart.md
```

### Step 4. Open this dir in vscode

💡Hint: The file structure should look something like this!

![[Screenshot_2023-09-02_at_11.40.44.png]]
### Step 5. Picking our colours!

Now, this is where we can customise our colors! Now to go through each individual colour, it would be quite overwhelming and take a long time. So let’s navigate to a handy website that we can use to help us made my ‘Coder Coder’ on youtube!

This is what i use, you essentially just put in hex codes for the colours you want to use! then click on ‘GIMME MY THEME’! and it spits out a json block you can then copy and paste into your ‘packages.json’ file.

[https://coder-coder.com/vs-code-theme-color-generator/](https://coder-coder.com/vs-code-theme-color-generator/)

💡Hint: use ‘Coolors’ to help you come up with aesthetic colour palettes! [coolors.co](https://www.notion.so/how-to-make-your-own-visual-studio-code-theme-527b210524d145b1bfc06ae5b45eb2c9?pvs=21)

![[Screenshot_2023-09-02_at_11.48.22.png]]
### Step 6. But how do we know if we like the look?

So we have our json file, but what if we dont even like how it looks? how do we even know what it looks like? Well this is where we can use the ‘vs code theme debugger’!

To use the debugger, navigate to the top bar, click on ‘Run’ and then ‘Start debugging’. This should automatically open a new window which shows you how your theme looks! Then you can play about with it to make it perfect! ✨

💡Hint: when using the debugging tool, you can open code files in order to see how it looks in the languages you use! for example, I opened some R code so i can see exactly how it looks in R.

![[Screenshot_2023-09-02_at_12.07.39.png]]
💡Hint: use the ‘Tokens and Scopes’ inspector to help with perfecting your theme! Click ‘ctrl, shift, P’ and then type in ‘Developer: Inspect editor tokens and scopes’.

![[Screenshot_2023-09-02_at_12.28.24.png]]
Use it to hover over colours you’d like to change, the textmate.scopes will help you know what to look for in your json file to change the colours you want to!

### Step 7. Yay! Well done, you’ve completed your theme? Now, lets get it on to the marketplace so you can show off to your colleagues with it.

- [ ] First, head to [https://azure.microsoft.com/en-gb/products/devops](https://azure.microsoft.com/en-gb/products/devops) and sign up/ log in.
- [ ] Obtain a personal access token by navigating to settings in the top right, and clicking on personal access token for authentication.
- [ ] Click new token and then give it a name. Click on the ‘organisations’ drop down menu and make sure its set to ‘all accessible organisations’.
- [ ] Then, click on expiration and make sure its set to custom defined.
- [ ] Scroll to the bottom and click on ‘show all scopes’ and find marketplace, and make sure ‘manage’ is selected. Then click on create! Copy it and save it here ‘……..’ or somewhere else you wont lose it.
- [ ] Last step, lets create a publisher. head to [marketplace.visualstudio.com/manage](http://marketplace.visualstudio.com/manage) and enter your publisher name and id. then hit create!

📝Note: it should look like this 

![[Screenshot_2023-09-02_at_12.41.13.png]]
- [ ] Go back to vscode and open up your package.json file, here we need to add info about our theme.
- [ ] Add this into the file, replace it with your own publisher, repo and keywords!

*📝 MAKE SURE IT ALSO SUPPORTS YOUR CURRENT VISUAL STUDIO CODE VERSION in the ‘engines’ section*

```basic
"publisher" : "livcodes",
  "repository": {
    "type" : "git",
    "url" : "https://github.com/agenomicsphd/agenomicsphd-light"
  },
  "keywords": [
    "light theme",
    "pink theme",
    "agenomicsphd",
    "pink and blue theme"
  ]

```

- [ ] Lastly, write your README!

### Step 7. Package your theme!

In vscode, open a terminal and run

```basic
npm install -g vsce
vcse login 'publisher id'

```

then it will prompt you to enter your personal access token we saved earlier! copy and paste that in now.

now, run

```basic
vsce package
vcse publish
```

## YAY! head back to [marketplace.visualstudio.com/manage](http://marketplace.visualstudio.com/manage) to see your extension.

📝Note: it might take a few minutes to verify..

# YOU’VE DONE IT! NOW INSTALL YOUR THEME FROM THE MARKETPLACE + USE IT AS YOU WISH!
![[Screenshot_2023-09-02_at_13.29.23.png]]
📝 NOTE: you may want to make changes to your theme overtime, to do that, edit as we did above and commit changes to your git hub repository. Then run the following commands to commit your changes to the marketplace succesfully.

```basic
vcse login 'publisher id'
vcse publish minor
```

📝 NOTE: read the vcse documentation for how to correctly publish your changes

## Thanks for following along! Hope you found this useful. Don’t forget to support the youtube video below and share your themes in the comments when you’ve done them in this format:

‘Light mode theme with pink + blue accents, named ‘agenomicsphd-light’’.

### now, enjoy the rest of my vlog! or check out my other vlogs ⬇️

[https://www.youtube.com/watch?v=pJZnAazOE3k&t=300s](https://www.youtube.com/watch?v=pJZnAazOE3k&t=300s)

[https://www.youtube.com/watch?v=vKIdqxUOYvQ&t=286s](https://www.youtube.com/watch?v=vKIdqxUOYvQ&t=286s)