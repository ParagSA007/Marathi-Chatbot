# Feasibility study of running a Marathi chatbot on a local machine:

## Machine details:

### Hardware: Intel Core i3-2120 CPU @ 3.30 GHz

### System: Ubuntu-24.04 via wsl2 on Windows 10 Home, 64-bit OS, x64-based processor.

### Using open-webui, qwen3:1.7b (works with Indic languages), Edge-TTS for speech response, browser based STT for voice to text feature.

### Python3.11 is recommended because it was used heavily in the testing but pyton3.12 is now supported (some issues are possible but my setup worked fine with 3.12.3).\
Python 3.13 is not supported yet.

### The limited capabilities of my current machine required minimized use of additional resources.\ 
The setup would work better if running on Windows directly but I wanted results for a linux setup (even with the wsl overhead).\
    Since the computing resources are limited, all components were run natively in linux thus allowing some saving in the form of Docker environment resource usage.\
    A brief review of the installation process follows:

### 1.	open-webui:

#### Installing open-webui  natively on linux, without Docker, can be accomplished using Python’s package manager (pip) or inside a virtual environment uv.

#### a)	Setup a Python virtual environment:
python3  –m  venv  my-env

#### b)	In bash, activate the environment:
source  my-env/bin/activate  		
##### The prompt will be preceded by (my-env).\
(Use deactivate to exit the workspace)

#### c)	Install open-webui using pip (always update)
pip  install  - -upgrade pip\
pip install open-webui

#### For running open-webui, just activate the environment as before:

##### a)	Activate the environment
source  my-env/bin/activate

##### b)	Run the server
open-webui  serve

##### Ollama is a great open-source agent for running Large Language Models (LLM).\ The latest version is available at the official website ollama.com. 

### 2. Ollama:\
Ollama is a great open-source agent for running Large Language Models (LLM).\
    The latest version is available at the official website ollama.com. 

##### a)	Install using:\
curl  –fsSL https://ollama.com/install.sh  |  sh

##### b)	In bash, activate the environment:\
source  my-env/bin/activate\  		
The prompt will be preceded by (my-env).

##### c)	To start the server, use:\
ollama  serve

##### d)	Available models grouped by family are listed at :\
https://ollama.com/library

#### For running open-webui, just activate the environment as before:

##### e)	For loading a specific model:\
ollama  pull  name_of_model\
(e.g.: llama3.1, qwen2.5, gemma3, mistral, deepseek-r1).

##### f)	To run the model:\
ollama  run  name_of_model

### 3.	Edge-TTS:\
#### For conversion of the model response from text-to-speech (TTS) I used Edge-TTS.\
    This is a free tool and library that uses the natural-sounding neural voice engine used by Microsoft Edge Browser’s “Read Aloud” feature.\
    Edge-TTS can be obtained from https://tts.travisvn.com.

##### To install the Open-AI-compatible TTS API, clone the git repository:\

##### a)	Clone the repository at:\
git clone  https://github.com/travisvn/openai-edge-tts.git\
cd ./openai-edge-tts

##### b)	In bash, setup the virtual environment:\
python3 –m venv my-edge-env

##### c)	Install the .bash dependencies:\
pip install –r requirements.txt

##### d)	Activate the environment, to run Edge-TTS:\
source ../my-edge-env/bin/activate

##### e)	Run the server:\
python  ~/openai-edge-tts/app/server.py

##### Set the TTS Engine in the browser by:\
                 Admin Panel -> Settings -> Audio (under Experience) ->\

##### a)	TTS Engine: OpenAI\
b)	API Base URL:http://localhost:5050/v1 (/v1 essential)\
c)	API Key: your_api_key_here (or some string)\
d)	TTS_Model: tts-1\
e)	TTS Voice: us-en-(your_choice)\
*** For non-english languages, select appropriate voice\
     List obtained from: edge-tts --list (in terminal)\
     For Marathi I used mr-IN-AarohiNeural.\
May have to set environment variables:\
     AUDIO_TTS_ENGINE=”openai”\
     AUDIO_TTS_ENGINE_OPENAI_BASE_URL=”http://localhost:5050/v1\


#### 4.	Speech-to-text (STT):\
For the sake of minimizing the computational overhead, I used the built-in STT capability in open-webui.\
    The browser based STT can be accessed by setting:\ 

##### a)	Admin Panel -> Settings -> Audio (under Experience) to WebAPI.

##### b)	Admin Panel -> Settings -> Audio (under Preferences) -> Turn on Autosend After Voice Translation (Optional)

##### May have to set environment variables:\
     WHISPER_MULTILINGUAL=True\
     WHISPER_LANGUAGE=”mr” (for Marathi)\

These variables can be set in .bashrc with EXPORT

# Preliminary Results

## The qwen3:1.7b model is not adequate for use as the engine for a Marathi Chatbot.\
The "intent" of the response may possibly be surmised after careful scrutiny and multiple reads.\ 
The grammar is rudimentary and the model is prone to repitition and confusion with pronouns.\
Indic languages are notorious for these issues as most of the LLM's are trained on western language constructs.\
Further study with other larger models or models specialized for this task is indicated.\
Results will be updated as soon as they are available.\
## Greatly appreciate your interest and please stay tuned for news and updates from this space.\
--Parag


```python

```
