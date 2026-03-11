What is this?
=============

Speak is a voice synthesis activity for the Sugar desktop.

Speak shows a face that will talk what is typed, within reason.

How to use?
===========

Speak is part of the Sugar desktop and is often included.  Please refer to;

* [How to Get Sugar on sugarlabs.org](https://sugarlabs.org/),
* [How to use Sugar](https://help.sugarlabs.org/),
* [Download Speak using Browse](https://v4.activities.sugarlabs.org/), search for `Speak`, then download, and;
* [How to use Speak](https://help.sugarlabs.org/en/speak.html).

How to upgrade?
===============

On Sugar desktop systems;
* use [My Settings](https://help.sugarlabs.org/en/my_settings.html), [Software Update](https://help.sugarlabs.org/en/my_settings.html#software-update), or;
* use Browse to open [v4.activities.sugarlabs.org](https://v4.activities.sugarlabs.org/), search for `Speak`, then download.

How to integrate?
=================

Speak depends on Python, [Sugar Toolkit for GTK+ 3](https://github.com/sugarlabs/sugar-toolkit-gtk3), GStreamer 1, GTK+ 3, and gst-plugins-espeak.

Speak is started by [Sugar](https://github.com/sugarlabs/sugar).

Speak is [packaged by Fedora](https://src.fedoraproject.org/rpms/sugar-speak).  On Fedora systems;

```
dnf install sugar-speak
```

Speak is not packaged by Debian and Ubuntu distributions.  On Debian
and Ubuntu systems dependencies include `gstreamer1.0-espeak`,
`gir1.2-gstreamer-1.0`, and `gir1.2-gst-plugins-base-1.0`.

Branch master
=============

The `master` branch targets an environment with latest stable release
of [Sugar](https://github.com/sugarlabs/sugar), with dependencies on
latest stable release of Fedora and Debian distributions.

Branch not-gstreamer1
=====================

The `not-gstreamer1` branch is a backport of features and bug fixes
from the `master` branch for ongoing maintenance of the activity on
Fedora 18 systems which don't have well-functioning GStreamer 1
packages.


Speak-AI Architecture
=====================

Speak-AI is built on three main components that work
together to deliver an AI-powered voice experience
inside the Sugar learning environment.

1. Speech Engine (kokoro/)
---------------------------
Handles neural text-to-speech generation using the
Kokoro TTS model. Text input is converted to phonemes,
processed through the neural network, and output as
a human-like audio waveform.

Key files:
- kokoro/pipeline.py  : controls the speech pipeline
- kokoro/model.py     : neural network architecture
- kokoro/modules.py   : supporting network components

2. Conversation AI (GenAI/, aiml/, bot/)
-----------------------------------------
Manages AI-powered responses using both a Small
Language Model (SLM) and a Large Language Model (LLM).
Handles the conversation logic before passing text
to the speech engine.

3. Sugar Activity UI (activity/)
----------------------------------
Provides the GTK-based interface integrated into the
Sugar learning environment. Handles voice selection,
character animation, and user interaction.

Voice Pipeline
==============

The flow from user input to audio output:

  User Text
      |
      v
  GenAI / AIML Response
      |
      v
  kokoro/pipeline.py
      |
      v
  KModel (neural network)
      |
      v
  Audio Output (speaker)

Development Setup
=================

1. Fork and clone the repository

   git clone https://github.com/YOUR_USERNAME/speak-ai.git
   cd speak-ai

2. Create a virtual environment

   python -m venv venv

3. Activate it

   Windows : venv\Scripts\activate
   Linux   : source venv/bin/activate

4. Install dependencies

   pip install -r requirements.txt

5. Connect to original repository

   git remote add upstream https://github.com/sugarlabs/speak-ai.git

Available Voices
================

The Kokoro TTS engine supports multiple voice styles
defined in speech.py. These include American English,
British English, and other regional variants.

Voice identifiers are mapped in kokoro/pipeline.py
through the LANG_CODES and ALIASES dictionaries.
```

---

### Step 4 — Click "Commit changes" button
Top right green button. Click it.

---

### Step 5 — Fill commit details exactly like this

**Commit title:**
```
docs: add architecture overview and setup guide to README
```

**Commit description:**
```
The README lacked an architecture overview making it 
difficult for new contributors to understand how the 
components connect.

This PR adds:
- Architecture section explaining the three main components
- Voice pipeline flow showing data from input to output
- Development setup guide for new contributors
- Available voices section explaining LANG_CODES and ALIASES

No functional changes. Documentation only.
```

---

### Step 6 — Select the branch option

You will see two options at the bottom:
```
○ Commit directly to the main branch
● Create a new branch for this commit
```

Select:
```
● Create a new branch for this commit
```

Name the branch:
```
docs-readme-architecture
```

---

### Step 7 — Click "Propose changes"

GitHub will take you to the PR page automatically.

---

### Step 8 — On the PR page fill these details

**PR Title:**
```
docs: add architecture overview and setup guide to README
```

**PR Description:**
```
While setting up and exploring the speak-ai codebase I 
noticed the README lacked an architecture overview, which 
makes it harder for new contributors to understand how the 
components connect.

This PR adds:
- Architecture section explaining the three main components
  (Speech Engine, Conversation AI, Sugar Activity UI)
- Voice pipeline flow diagram showing the full path from
  user text to audio output
- Development setup guide for new contributors
- Available voices section explaining how LANG_CODES and 
  ALIASES work in pipeline.py

No functional changes. Documentation only.
