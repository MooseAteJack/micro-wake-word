# micro-wake-word
Custom wake words for Respeaker Lite and Home Assistant

To use on the device, you need to write a Model JSON file. See https://esphome.io/components/micro_wake_word for the documentation and https://github.com/esphome/micro-wake-word-models/tree/main/models/v2 for examples.
Adjust the probability threshold based on the test results obtained after training is finished. You may also need to increase the Tensor arena model size if the model fails to load.

Setting probability_cutoff properly (this matters)

You do NOT want 0.97 unless your model is insanely clean.

Start with:

"probability_cutoff": 0.75


Then tune:

Behavior	Adjust
False wakes	Increase by +0.05
Missed detection	Decrease by -0.05
Works well	Leave it

Most custom models settle between:

0.70 – 0.85

🧠 Tensor arena size: how to tune

The example:

26080


…is for a tiny known model.

Your custom model likely needs more.
Safe starting point:

30000


If ESPHome logs:

Failed to allocate tensor arena

Increase:

35000
→ 40000
→ 50000