# Troubleshooting & Debugging Guide

## 🛠️ 1. Turn Debugging On and Read Error Messages

- **Enable debugging**: Turn on debugging in your local `web.config` file (e.g., set `<compilation debug="true">`) before starting—catches more details.
- **Read the errors**: Check error messages in the browser console or server logs. If they confuse you, Google them or ask an LLM first before taking it to your pod/senior.

## 🐞 2. Replicate the Bug

- **Replicate**: Ensure you can replicate the bug consistently before you start other debugging steps.
- **Simplify the setup**: Reduce to the minimal code needed to recreate the bug, then test.
- **Note conditions**: Record specifics (e.g., screen size, browser type) where the bug appears—hints at the source.

## 🕵️ 3. Isolate the Problem

- **Make it easy**: Narrow down to the specific file, include, script, or `if` statement—then dig deeper to the control, property, or variable.
- **Reduce to basics**: Strip back to a minimal case that still triggers the bug.
- **Prove you’ve isolated**: Remove the suspect code to stop the bug, then re-add it to replicate—validate, don’t guess.

## 👀 4. Make Things Visible

- **Log client-side data out**: Add `console.log(variable)` in JS to print values and track what’s breaking in real-time.
- **Render server-side data to the page**: Dump data (e.g., `<pre id="debug"><%= SomeLiteral.Text %></pre>`) to confirm values match expectations—often reveals the issue.
- **Check the console**: Read error messages—they pinpoint lines and issues (e.g., "null is not a function"). Google or LLM them *before* asking for help.
- **Compare changes**: If the bug varies across pages or environments (local, dev, UAT, live), compare file versions. If need-be, pull down deployed files and diff against your local copies.
- **Add a debug border**: Toss `border: 1px solid red` on elements to reveal their size and position.
- **Use Dev Tools to help you see more:** Lean on Dev Tools—inspect elements, set breakpoints, check the Network tab.
- **Inspect styles**: Hover over CSS rules in Dev Tools to see what’s applied.
- **Watch the network**: Use the Network tab to confirm files load.
- **Look at the sources tab:** see what scripts etc are being loaded, and what their content is. Use [local overrides](https://developer.chrome.com/docs/devtools/overrides) to make changes that persist after refresh.

## 🔧 5. Change One Thing, Then Look Again

- **Test small tweaks**: Replicate the bug, tweak one line, then refresh—see the impact.
- **Toggle CSS**: Uncheck styles in Dev Tools to isolate their effect—no blind edits.
- **Reload fresh**: Ctrl+Shift+R clears cache for a clean slate—ensure you’re seeing reality.

## ⚖️ 6. Compare What Works

- **Test against a working version**: Load a bug-free version (different environment or commit) and spot differences.

## 🧰 7. Other Tools

- **Jam browser extension:** Consider using The [Jam browser extension](https://jam.dev/) to help with your debugging.

## 🔍 8. Research by Yourself Before Asking for Help

- **Search the clue**: Google the error or behavior after replicating—answers are out there.
- **Prompt an LLM**: Feed the error code to an LLM and ask for a breakdown if it’s unclear.
- **Describe the problem**: Google or prompt based on a clear description of the issue.