credit: https://forum.obsidian.md/t/copy-settings-from-existing-vault-option/11082/6

Here’s how to make it work, in case you’re not familiar with hidden folders (instructions for macOS / Linux):

1.  Launch Obsidian app on desktop
2.  Open a random note. Use command palette (⌘ + p) and execute the command “Show in system explorer” command:

[![Screen Shot 2021-10-18 at 2.32.51 PM](https://forum.obsidian.md/uploads/default/optimized/3X/9/9/99ada136e44a4dda2fccd1aa3bef8b64c3c4a9a7_2_690x175.png)

Screen Shot 2021-10-18 at 2.32.51 PM884×225 10.4 KB

](https://forum.obsidian.md/uploads/default/original/3X/9/9/99ada136e44a4dda2fccd1aa3bef8b64c3c4a9a7.png "Screen Shot 2021-10-18 at 2.32.51 PM")

3.  You should now be seeing the note in Finder or equivalent system explorer.
    
4.  From here, navigate up the folders until you get to your vault’s folder.
    
5.  Launch Terminal (this is a built-in program that ships with macOS and Linux computers).
    
6.  You’re going to type a command now to navigate to your obsidian vault folder. Type `cd` (with space), and then drag-and-drop the obsidian folder from Finder into Terminal. It should result in something like this: `cd /Users/nickang/Library/Mobile\ Documents/iCloud~md~obsidian/Documents/nickang-obsidian`
    
7.  Hit enter. Now you’re viewing your vault folder in Terminal.
    
8.  Finally, issue the last command to open the hidden .obsidian folder by typing and hitting enter: `open ./.obsidian`. You should now see the contents of the hidden folder.
    
9.  Now it’s a matter of copy-pasting this into the .obsidian folder in the vault folder in your new computer.
    

Hope this helps!