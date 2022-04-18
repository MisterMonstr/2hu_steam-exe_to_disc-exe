# 2hu_steam-exe_to_disc-exe
After buying the Touhou Project games on Steam and trying to run the popular vpatch mod with them to decrease latency, I was unable to launch the games. It seems that the .exe files Steam provides are different than the .exe files used in their original disc releases. I'm assuming mods such as vpatch rely on the exact hex order of the original .exe's, and fail to function if the game's .exe is at all different than what the mod expects.

I made a few .bdf files for use with bspatch (https://github.com/mendsley/bsdiff) to convert the .exe's provided by Steam into the .exe's provided by the original disc releases. These should be the latest version of each respective game's .exe(ex: Touhou 12 should convert to a Ver. 1.00b Disc .exe), but I may have left a few games unpatched by accident. If you run into any problems, file an issue to let me know. In the meantime, you can download the official updater for that game via ZUN's site(https://www16.big.or.jp/~zun/html/game.html). https://www.thpatch.net has links to these patches as well, if you're having a hard time navigating.

## "Okay, okay. How do I use these?"
1. Download your games on Steam. 
2. Download bspatch. ROMHacking.net has a precompiled Windows version here: https://www.romhacking.net/utilities/929/.
    - Linux users can simply download bsdiff from their distribution's package manager.
    - If you can't find precompiled binaries for your operating system, you can always build bspatch from source.
3. Download the .bdf files from this repository and put them in the bspatch folder. 
    - Alternatively, if installed from source or using Linux, just put each .bdf file in their respective game's folder.
4. Rename your thXX.exe file in each game's directory to thXX.exe.steam. (ex: Undefined Fantastic Object would have its .exe renamed from th12.exe to th12.exe.steam)
    - If you're using Windows or have built bspatch from source without installing it, copy that thXX.exe.steam into the bspatch folder.
5. Open the command line in the folder that your .bdf and thXX.exe.steam file are. 
    - On Windows, hold shift, right click any whitespace in that folder and click "Open Powershell here". Make sure this folder also has the bspatch executable.
6. Tell bspatch to patch thXX.exe.steam and save it as thXX.exe, using thXX.bdf.
    - `"[\path\to\bspatch.exe"] ["\path\to\thXX.steam.exe"] ["\path\to\game\thXX.exe"] ["\path\to\thXX.bdf"]`
    - example (assuming bspatch.exe, thXX.exe.steam and thXX.bdf are all in the same folder): 
        - `bspatch.exe th12.exe.steam th12.exe th12.bdf`
    - example 2 (we're in the bspatch folder, and the thXX.exe.steam and thXX.bdf files are in the game's folder): 
        - `bspatch.exe "C:\Program Files (x86)\Steam\steamapps\common\th12\th12.exe.steam" "C:\Program Files (x86)\Steam\steamapps\common\th12\th12.exe" "C:\Program Files (x86)\Steam\steamapps\common\th12\th12.bdf"`
    - example 3 (bspatch.exe is in another folder): 
        - `"C:\Users\You\Downloads\bspatch\bspatch.exe" "C:\Program Files (x86)\Steam\steamapps\common\th12\th12.exe.steam" "C:\Program Files (x86)\Steam\steamapps\common\th12\th12.exe" "C:\Program Files (x86)\Steam\steamapps\common\th12\th12.bdf"`
    - example 4 (Linux):
        - `bspatch "~/.local/share/Steam/steamapps/common/th12/th12.exe.steam" "/home/you/.local/share/Steam/steamapps/common/th12/th12.exe" "/home/you/.local/share/Steam/steamapps/common/th12/th12.bdf"`
7. Move the newly created thXX.exe to its game folder if it's not already there.
8. Play! If you want to know how to run the thcrap translation patch and vsync patch from within Steam, check out my guide [here](https://steamcommunity.com/sharedfiles/filedetails/?id=2196860604). 

By the way, beware that if you ever hit 'verify integrity of game files', your converted .exe will be lost. You could make a backup of it beforehend and call it thXX.disc.exe, as a precaution.

*
*
*

The purpose of this repository is to make it easier for people to play these games they bought on Steam with the least amount of input delay as possible. I want to help current and potential Steam buyers use vpatch and other steam-incompatible mods without being tempted to resort to piracy. In light of recent events, I aim to provide this service using the least amount of official material as possible, hence why I'm using .bdf diff files and not just uploading the .exe's outright.
