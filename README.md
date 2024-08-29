# Godot Copilot Selfhost (Based on https://github.com/minosvasilias/godot-copilot)

![Godot Copilot Selfhost logo](public_assets/logo500.png)

AI-assisted development for the Godot engine.

Compatible with `4.x`.
### What does this do?

Godot Copilot uses OpenAI APIs and the API of LM Studio to run models locally (other models/providers may be supported in the future) to retrieve AI-generated code completions.

After installing the plugin, simply press the selected keyboard shortcut to generate code in the code editor at the current caret position, directly within the engine!

### Check out my profile and the tutorial page for more information!

- [Profile](https://tnl.one/s/drakonkat)
- [Tutorial](https://tnl.one/s/gdcopilot)


### How do i install this?

Follow these steps:
- Search for "Copilot selfhost" in the Godot asset library directly within the engine. Download the addon and enable in the project settings. (To be added)
- You may also clone this repository and copy the `copilot-advanced` addon into the `res://addons` directory of your project

Afterwards, enable the addon in the project settings, and enter your OpenAI API key in the `Copilot selfhost` tab located on the right-hand dock.

Use the selected keyboard shortcut within the code editor to request completions.

If you have difficulties, please follow the [tutorial](https://tnl.one/s/gdcopilot) linked above or open an [issue](https://github.com/drakonkat/godot-copilot-selfhost/issues).

### How much will this cost me?

- Nothing if you [install](https://lmstudio.ai/) `LM studio` and configure a server to run the models yourself, otherwise, you will need to pay OpenAI for the completions.
  - FREE

Godot Copilot selfhost currently supports this paid models:

- `text-davinci-003` (Completion interface)
  - $0.02 / 1K tokens
- `gpt-3.5-turbo` (Chat interface)
  - $0.002 / 1K tokens
- `gpt-4` (Chat interface)
  - $0.03 / 1K tokens

Therefore, turbo is cheapest.

For each request, Copilot will attempt to send your entire current script to the model, up to a maximum length, after which the code will be trimmed.

Being a good engineer that doesn't work in 5k-line spaghetti-scripts pays. Literally!

> Comprehensive example data on cost per month/day/hour for each model is appreciated! Please open an issue if you are willing to contribute!

### How well does this work?

**GDScript is underrepresented in OpenAI's training data!**

Do not expect performance matching that of popular languages such as Python or Javascript. This will not replace you... yet!

It is however perfectly capable of writing useful functions, generating pre-populated objects, and completing all the tedious code you don't want to write yourself.

One significant complication affecting performance is the changes introduced in Godot 4.0. The training data of all supported models largely cuts off in September 2021. This means some of the new syntax was included, some not, and the models know a combination of GDScript 1 and 2.

Godot Copilot automatically injects zero-shot explanations of some of the most important GDScript changes in the prompts! This helps model performance quite significantly, but doesn't resolve all issues. Expect some varying performance when it comes to concepts such as `Callable` or hallucinated Python methods.

### Why no autocomplete?

A couple reasons:

- Godot's autocomplete system for `CodeEdit` nodes is not particularly well suited for AI-completions, as it does not preview completions directly within the text, but instead in a small popup that is not able to preview longer/multi-line predictions.
- The prefix-system it uses does not always handle runtime-additions of completions smoothly. Whether or not completions work is highly context dependent.
- Triggering LLM-requests on each autocompletion signal is expensive. As in, really expensive. Unlike Github Copilot, this can not be a one-size-fits-all payment model. You pay for what you use.

Testing has shown targeted completions on shortcut presses to be much more reliable and efficient.

Autocomplete may be an optional setting in the future if above issues can be sufficiently addressed.

### Does this share sensitive data?

If you use LM Studio, no data is shared with any third party, everything is processed locally.

If you use Open AI subscription you will find here the detail -> Since March 1st 2023, OpenAI states it will [no longer use data sent via their APIs in future training runs](https://openai.com/policies/api-data-usage-policies).

### Why should i use this over Github Copilot?

Do use Github Copilot when suitable!

This does offer code completions directly within the Godot editor, which is the main usecase.

When using OpenAIs APIs, Godot Copilot may also be more expensive than GitHub Copilot, depending on your model choice and usage.

### Can this do anything other than code completion?

I have run experiments with further automation capabilities, such as populating and modifying the active scene. Such features may be added in the future.

Other interesting usecases may be using embeddings to more accurately model cross-script functionality for your codebase, or using generative models for texture, sprite or 3D asset creation.

Please feel free to open issues requesting features or changes.

### Which models are suggested?

Actually there is no suggested model, llama 3 is a good one, but if someone has a better suggestion, please open an issue.


### Exist a guide to install LM Studio?

 Actually not, is in project to create a guide to install LM Studio, but if you want to help, please open an issue.
