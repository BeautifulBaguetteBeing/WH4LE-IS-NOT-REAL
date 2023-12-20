# Investing the Integrity of the WH4LE Exploit.
TL;DR -  WH4LE is just a troll exploit to trick tech illterate people to powerwash their device repeatedly.
___
Here is the proof that WH4LE is a fake exploit, diving into the WH4LE and "ChromeOS Debug Menu's" Source Code:
## 1. The first step button doesn't do anything!
Here is the code that runs when you click on the first button to "start" the WH4LE "exploit"
```js
function start() {
    let startBtn = document.getElementById("startBtn");
    startBtn.innerText = "Beginning the WH4LE exploit...";
    startBtn.disabled = "true";
startBtn.outerHTML = startBtn.outerHTML + '<img id="startBtnSpinner" style="border:unset;width:20px;height:20px;padding:0;margin:0;transform:translateY(5px);margin-left:2px;" src="loading.gif">'
    let randomTime = Math.random() * 5000 + 5000;
    setTimeout(() => {
        alert("The WH4LE exploit has successfully begun. Please proceed to Step 2.");
        startBtn.innerText = "Please proceed to Step 2.";
        document.getElementById("afterStep1").style.display = "block";
  document.getElementById("startBtnSpinner").remove();
    }, randomTime);
}
```
As you can see, literally all it does is pretends it's doing something by taking a completely random amount of time and says that the exploit has started. Like... What?

## 2. Neither does the downloadable file with the extension input!
The code for this is as follows:
```js
function extClick() {
  let randomTime = Math.random() * 2000 + 3000;
  let extBtn = document.getElementById("extBtn");
  extBtn.innerText = "Injecting..."; extBtn.disabled = "true";
  if (document.getElementById("ext-id").value.length === 32) {
    setTimeout(() => {
      alert("Your extension has successfully injected the script. Please proceed to Step 4.");
      extBtn.innerText = "Please proceed to Step 4.";
      document.getElementById("hiddenAtFirst").style.display = "block";
    }, randomTime);
  } else {
    setTimeout(() => {
      alert("You don't have this extension installed, or it isn't an admin extension.");
      extBtn.innerText = "Try Again";
      extBtn.removeAttribute("disabled");
    }, randomTime / 2);
  }
}
```
As you can see, all it does is check the length of the extension token that is supplied and doesn't actually do anything with it. You can verify this by going to that input box and typing 32 "a's".
## 3. The name "Matthew Smith" is hard-coded.
This isn't a real password input field... yea...
```html
 <p>Welcome, Matthew Smith.</p>
```
I don't think I need to elaborate.

## 4. The Function that Handles the Actual Exploits
It's LITERALLY CALLED `troll()` and all it does is throw exactly one error and then just shoots out an alert saying that it did something when it didn't. Here is the entire function.
```js
    let hasHadError = false;
    function troll(num) {
        if(hasHadError) {
            switch(num) {
                case "updates":
                alert("Updates successfully frozen.")
                break;
                case "policies":
                alert("Go to chrome://policy, there should now be an Edit button. If not, restart your Chromebook.");
                break;
                case "unenroll":
                alert("Powerwash your Chromebook. check_enrollment has been set to 0. All user data will be saved.");
                break;
                case "cros81":
                alert("Powerwash your Chromebook. It'll reboot into ChromeOS v81. All user data will be saved.");
                break;
                case "win11":
                alert("Powerwash your Chromebook. It'll reboot into Windows 11. All user data will be saved.");
                break;
                case "mac":
                alert("Powerwash your Chromebook. It'll reboot into MacOS. All user data will be saved.");
                break;
                case "shimmer":
                alert("Powerwash your Chromebook. It'll reboot into SH1MMER. All user data will be saved.");
                break;
                case "debian":
                alert("Powerwash your Chromebook. It'll reboot into Debian. All user data will be saved.");
                break;
                case "flagsEnable":
                alert("Restart your Chromebook. The selected flag will be applied.");
                break;
                case "flagsDisable":
                alert("Restart your Chromebook. The selected flag will be disabled.");
                break;
                case "devmode":
                alert("Powerwash your Chromebook. block_devmode has been set to 0. All user data will be saved.");
                break;
                case "wp":
                alert("Error disabling write protection. Write protection has been enabled indefinitely.");
                break;
                case "brick":
                alert("Powerwash your Chromebook within the next 5 minutes. It'll be soft-bricked. All user data will not be saved.");
                break;
                case "crostini":
                case "crash":
                document.getElementById("debugError").style.display = "block";
                document.getElementById("menu").style.display = "none";
                break;
                case "install":
                alert("The specified extension has been installed. It may not show up, but it should within the hour.");
                break;
                case "adminInstall":
                alert("The specified extension has been installed as an admin extension. It may not show up, but it should within the hour.");
                break;
                case "uninstall":
                alert("The specified extension has been uninstalled. It may still show up, but it should disappear within the hour.");
                break;
                case "disable":
                alert("The specified extension has been disabled. It may still show as enabled, but it should show as disabled within the hour.");
                break;
                case "enable":
                alert("The specified extension has been enabled. It may still show as disabled, but it should show as enabled within the hour.");
                break;
                case "steam":
                alert("If you upgrade to Windows 11, Steam will be pre-installed.");
                break;
            }
```
___
## Closing:
If you don't believe me on my explanations and excerpts, the full decoded source code is in `WH4LE Decoded Source.html`. If you think that I completely made that up, the decoder that you can paste into the console of [The Official WH4LE Site](https://whale.mom) is in `WH4LE Decoder.js`. It will spit out the entirety of the decoded source code and you can copy and compare.

If you are still suspicious, you have some weird cognitive dissonance that you need to reflect on. Or, you're just arguing so you can keep trolling kids and get them to powerwash their device repeatedly. Either way, not my problem.
