# Handling Deleted YouTube Footage Dilemma  

## Me
I have a dilemma. For the past few weeks, I've been uploading a Fifa Career Mode series to YouTube on my gaming channel. However the current episode, I was nearly finished editing the episode, however I was then having a clean out of my laptop storage a d didn't realise I deleted a lot of the footage that I edited for the video. Now I don't have that footage at all anywhere, I could record the full gameplay again but that'll take a long time and set me back another month probably, what should I do? Could you please respond as if you were a YouTube expert and have knowledge of Fifa Career Mode  

## Co-Pilot
That’s a tough spot, Hasan, but don’t panic—we’ve got options. As someone well-versed in YouTube strategy and FIFA Career Mode content, here’s what I’d suggest to salvage your episode without setting you back a month.

### 1. **See if Recovery is Possible**  
Before you assume the footage is completely gone, check your laptop’s **Recycle Bin** or try using recovery software like **Recuva** (for Windows) or **Disk Drill** (for Mac). If you deleted the files recently, there’s a chance they might still be recoverable.

### 2. **Use What You Still Have**  
Even if the edited footage is gone, do you still have parts of the raw gameplay saved? If so, you could:
   - **Re-edit with what remains** and make it a slightly different episode.
   - **Do a “Match Recap” format** instead of full gameplay—use commentary to explain key moments and add highlight clips.
   - **Get creative with storytelling**—use FIFA menus, squad updates, and still images to narrate what happened.

### 3. **Turn the Mistake into Content**  
Many YouTubers turn their setbacks into engaging videos. You could make an episode titled **"I Accidentally Deleted My FIFA Career Mode Episode... Here's What Happened"** and summarize the lost gameplay in a creative way. This could actually be **great engagement content** because viewers love authenticity and behind-the-scenes insights.

### 4. **Fast-Forward Instead of Replaying**  
If you’re open to re-recording, **simulate the results** using FIFA’s match sim or manually play the key moments. Rather than redoing everything from scratch, you could **explain the original episode**, show a few re-created highlights, and quickly move into the next episode.

### 5. **Poll Your Audience**  
If you have an engaged audience, consider making a community post or short video asking viewers **how they’d like you to handle this**. Would they rather see a summary and move on? Or a full replay? This makes them part of the journey.

### **Final Thought**  
The worst thing to do is let this setback discourage you. Many successful YouTubers have faced similar issues and used them to their advantage. If you approach this creatively, you might even make an **unexpectedly viral** episode out of it.

What do you think—does any of this sound doable?  
Let’s make this a **legendary comeback** instead of a disaster. 🔥  

## Me
What recovery software can I use, I permanently deleted about 4 or 5 decently long video clips from my windows laptop? Also re-editing isn't an option since I only have the first 10 or 15 minutes of the episode and not the rest. Also it was the end of the season so technically I need to show everything, I won the FA Cup and UCL in the Career Mode.  

## Co-Pilot
That’s a huge moment in your FIFA Career Mode—you definitely don’t want to lose that footage! Since you’ve permanently deleted the files, your best bet is using **data recovery software** to try and restore them before they get overwritten.

### **Best Recovery Software for Windows**
Here are some top-rated options that might help:
- **EaseUS Data Recovery Wizard** – Known for its deep scan capabilities and ability to recover lost files efficiently  [techradar.com](https://www.techradar.com/best/best-data-recovery-software).
- **Recuva** – A free tool that’s great for recovering deleted videos, especially if they were recently removed  [handyrecovery.com](https://www.handyrecovery.com/best-video-recovery-software/).
- **Disk Drill** – Offers powerful recovery features and works well for retrieving lost media files  [handyrecovery.com](https://www.handyrecovery.com/best-video-recovery-software/).
- **Stellar Data Recovery** – A premium option that supports video recovery and works on formatted drives  [handyrecovery.com](https://www.handyrecovery.com/best-video-recovery-software/).
- **MiniTool Power Data Recovery** – Another solid choice with a free version that allows limited recovery  [recoverit.wondershare.com](https://recoverit.wondershare.com/video-recovery/video-recovery-software-windows.html).

### **What to Do Next**
1. **Stop using the drive** – The more you use your laptop, the higher the chance that new data will overwrite the deleted files.
2. **Download one of the recovery tools** – Try **Recuva** first if you want a free option, or **EaseUS** for a more advanced recovery.
3. **Run a deep scan** – These tools will scan your storage for recoverable files. If the videos show up, restore them ASAP.

Since this was the **FA Cup and UCL final**, if recovery doesn’t work, you might need to **recreate the episode creatively**—maybe a **highlight reel** or a **storytelling recap** with commentary. But let’s hope recovery works first!

Let me know if you need help with the recovery process. Fingers crossed you get those clips back! 🔥🎮  

### References
[The best data recovery software; tried and tested by our experts | TechRadar](https://www.techradar.com/best/best-data-recovery-software?utm_source=copilot.com)  
[10 Best Video Recovery Software in 2026 (Free, Freemium & Paid)](https://www.handyrecovery.com/best-video-recovery-software/?utm_source=copilot.com)  
[Top 10 Free Video Recovery Software & App for Windows PC (2026)](https://recoverit.wondershare.com/video-recovery/video-recovery-software-windows.html?utm_source=copilot.com)  

## Me
(Now Wednesday, Jun 4)  
I managed to recover all the videos with Recuva! Thabnks a lot for your help!  

## Co-Pilot
That’s amazing news, Hasan! 🎉 I’m so glad Recuva worked for you. Now you can go ahead with your FIFA Career Mode finale without losing all that hard work.  

If you ever run into issues like this again, it might be a good idea to **back up your project files** either on an external drive or cloud storage—just to be safe.  

Can’t wait to see how your FA Cup and UCL triumph plays out in the episode! If you ever need ideas for improving engagement or making the episode extra special, I’m always here to brainstorm with you.  
Keep up the great content! 🔥⚽🎮  

## Me
How do I fix this error when using Pyinstaller to run a Python script as an exe, my game has a main.py file, however it also has a couple of text files that are used to generate the level and 3 image files that use for sprites:  
```
Traceback (most recent call last):
  File "main.py", line 210, in <module>
FileNotFoundError: [Errno 2] No such file or directory: 'C:\\Users\\fifau\\AppData\\Local\\Temp\\_MEI145602\\Vertical_walls.txt'
```  

## Co-Pilot
It looks like PyInstaller is having trouble finding your **Vertical_walls.txt** file when running the executable. This happens because when PyInstaller packages your script into an `.exe`, it doesn’t automatically include external files like text files or images unless explicitly told to do so.  

### **How to Fix It**
Since your game depends on those files, you need to **tell PyInstaller to include them** in the bundle. Here’s what you can do:

#### **1. Use `--add-data` in Your PyInstaller Command**  
Try running PyInstaller with the following flag to ensure the text and image files get included:  

```bash
pyinstaller --onefile --add-data "Vertical_walls.txt;." --add-data "another_file.txt;." --add-data "sprite1.png;." main.py
```

- Replace `Vertical_walls.txt`, `another_file.txt`, and `sprite1.png` with **all the files** your game needs.
- The `.;` tells PyInstaller to place the files in the same directory as the executable.  

#### **2. Modify Your Code to Load Files Correctly**  
Once bundled, your files are stored in a **temporary directory** (`_MEIxxxxx`). Modify your code to load them dynamically when running as an `.exe`:  

```python
import os
import sys

# Function to get the absolute path of bundled files
def resource_path(relative_path):
    if getattr(sys, 'frozen', False):
        # Running as an executable
        base_path = sys._MEIPASS
    else:
        # Running as a script
        base_path = os.path.abspath(".")

    return os.path.join(base_path, relative_path)

# Use resource_path() when loading files
file_path = resource_path("Vertical_walls.txt")
with open(file_path, "r") as f:
    data = f.read()
```

#### **3. Double-Check File Placement**  
Make sure your files are in the right **working directory**:
- If you’re running the `.exe`, ensure the external files are actually **packaged inside** the dist folder.
- If needed, **place them manually** alongside the `.exe` before running.

#### **4. Try `--collect-data` Instead (for Certain Packages)**  
If you're using third-party packages that depend on external files, you might need:  
```bash
pyinstaller --onefile --collect-data package_name main.py
```

### **Final Steps**
1. **Rebuild with PyInstaller** using `--add-data`.
2. **Test the `.exe`** and make sure it loads all necessary files correctly.
3. **If issues persist**, check the output folder (`dist`) and confirm your files exist there.

Let me know how it goes or if you need any tweaks to your PyInstaller setup! 🎮🔥  

## Me
(Now Thursday, Jun 5)  
Going back to the topic of the deleted videos, 2 of tehm that I recover appear to be broken and can't be processed by the editor. I can use the other clips as reference videos, but what softwrae/website would you recommend for me to fjix the videos forv free? Bare ijn mind one of tehm is quite large at 750MB  

## Co-Pilot
That’s frustrating, but don’t worry—there are some solid free tools that can help repair your broken video files. Since one of them is quite large (750MB), you’ll need a tool that can handle big files efficiently.

### **Recommended Free Video Repair Tools**
1. **[Clever Online Video Repair](https://repair.cleverfiles.com/)** – A free online tool that can fix corrupted MP4 and MOV files. You’ll need to upload a working reference video with the same settings for best results.
2. **[VLC Media Player](https://thegeekpage.com/12-free-video-repair-softwares-to-fix-any-video/)** – Surprisingly, VLC has a built-in repair feature for damaged AVI files. Go to **Tools > Preferences > Inputs/Codecs**, then set **Damaged or incomplete AVI file** to **Always Fix**.
3. **[MiniTool Video Repair](https://www.minitool.com/video-repair/free-video-repair-tool.html)** – A free Windows tool that supports MP4, MOV, and other formats. It allows batch repair and has an advanced repair mode for severely damaged files.
4. **[DivFix++](https://thegeekpage.com/12-free-video-repair-softwares-to-fix-any-video/)** – If your videos are in AVI format, this tool can help reconstruct missing data and make them playable again.

### **What to Do Next**
- Try **Clever Online Video Repair** first if your videos are MP4 or MOV.
- If that doesn’t work, use **MiniTool Video Repair** for a more advanced fix.
- If your videos are AVI, **VLC or DivFix++** might do the trick.

Let me know how it goes—hopefully, we can get those clips working again! 🔥🎮  

## Me
I triede to repair it on an online tool, however it shows that the repaired video is one that's overwritten the actual video I wanted to use. Recuva also said that the video had been overwritten by a different on ethat I recorded afterwards  

## Copilot
That’s really frustrating, Hasan—I get why this is such a headache. If Recuva is saying the video was overwritten, unfortunately, that means the original file is likely **corrupted beyond repair** or completely replaced by new data.  

### **What Can You Do Now?**  
Since the original footage is unrecoverable, here are some options to move forward:  

#### **1. Use Reference Clips Creatively**  
You mentioned having other clips as reference—maybe you could:
- **Recreate the key moments visually** using FIFA highlights, screenshots, or edited-in commentary.
- **Narrate the match** in an engaging way with voiceover or subtitles.
- **Make a cinematic recap** with reactions, player stats, and title celebrations.

#### **2. Re-record the Finals Efficiently**  
I know **replaying everything** sounds frustrating, but since it was the FA Cup and UCL finals, you could:
- **Simulate the matches** using FIFA’s built-in match simulation.
- **Replay just the crucial moments** (goals, trophies, celebrations).
- **Fast-forward gameplay** to get through it quicker.

#### **3. Turn It into a Special Episode**  
Instead of trying to do a normal episode, you could **make it a comeback story**:
- **Title it:** _"I Lost My FIFA Career Mode Finale... So I Recreated It!"_
- **Explain the setback** briefly at the start.
- **Show what happened using creative editing** (memes, highlights, commentary).
- **Engage viewers** by asking them how they’d handle the situation.

### **Final Thought**  
It sucks to lose footage, but if you **embrace the challenge**, you might actually create an episode that stands out. Some YouTubers turn setbacks into **viral moments** by making them fun and engaging.  

Let me know what direction you want to take—I’m happy to help brainstorm more ideas to salvage this! 🔥⚽🎮  

## Me
The footage that has been lost includes my FA cup triumph and an all-importnat UCL semi-final, should I just re-record these parts and edit them again?  

## Copilot
Since those moments are **huge milestones** in your Career Mode journey, it’s definitely worth re-recording them to keep your series authentic and complete. Here’s how I’d approach it to **save time** and make it **engaging**:

### **1. Re-Record the Games Efficiently**  
- **Use FIFA’s match simulation** to get through portions quickly while keeping the results similar.
- **Focus on the biggest moments**—goals, crucial saves, the final whistle, trophy celebrations.
- **Adjust sliders if needed** to ensure a competitive match and keep it exciting.

### **2. Make the Re-recording a “Special” Episode**  
Instead of just replaying, you could:
- **Title it:** _"Recreating My FA Cup & UCL Semi-Final After Losing the Footage!"_
- **Show behind-the-scenes clips** of the recovery process.
- **Explain what happened in a fun way**—could add a dramatic intro or memes about the lost footage.

### **3. Keep It Authentic With Commentary**  
- If you remember how the original matches played out, **react in a similar way** to key moments.
- **Turn setbacks into entertainment**—maybe even joke about how FIFA “forced” you to replay your biggest matches.

### **4. Engage Your Audience**  
- **Ask viewers if they’ve ever lost gaming footage**—it’s a relatable problem.
- **Let them know how you recreated the games** and whether the results changed.
- **If you win differently**, make it a fun discussion point: “Was fate trying to rewrite history?”

### **Final Thought**  
You’ve put so much work into this Career Mode series—**don’t let lost footage ruin the climax**. If you re-record smartly and embrace the storytelling aspect, **you might turn this setback into one of your best episodes**.

How do you feel about this plan? You’ve got this! 🎮⚽🔥  

*End of this Conversation*
