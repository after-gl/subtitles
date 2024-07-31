# Guide: Generating and Editing Subtitles

## Prerequisites

### 1. Generating Subtitles with Whisper

If your video does not have initial subtitles in the desired language, you can use the **faster-whisper-xxl** tool to analyze the video and extract subtitles in SRT format. Follow these steps:

1. **Download Whisper:**
   - Visit the [Whisper Standalone GitHub Releases page](https://github.com/Purfview/whisper-standalone-win/releases) to download the software.

2. **Read Documentation:**
   - For detailed usage instructions, refer to the [Whisper Readme file](https://github.com/Purfview/whisper-standalone-win?tab=readme-ov-file).

### 2. Editing and Translating Subtitles with Subtitle Edit

To edit, review, and translate subtitles, the open-source program **Subtitle Edit** is recommended. Here are the steps to get started:

1. **Download Subtitle Edit:**
   - Get the latest version from the [Subtitle Edit GitHub Releases page](https://github.com/SubtitleEdit/subtitleedit/releases).

2. **Read Documentation:**
   - For more details on using Subtitle Edit, you can refer to the [documentation available here](https://github.com/Purfview/whisper-standalone-win?tab=readme-ov-file).

3. **Integrate DeepL for Translation:**
   - You can enhance Subtitle Edit's translation capabilities by registering an API key with **DeepL**, a powerful translation service.

   **Steps to register and add DeepL API key:**
   - Visit [DeepL's official website](https://www.deepl.com) to create an account and obtain your API key.
   - In Subtitle Edit, navigate to `Options > Settings > Translation` and enter your DeepL API key. This will enable automatic translation features within the software.

## How to Generate Subtitles

### Step 1: Text Recognition Using Whisper

If initial subtitles are not available, use Whisper to perform text recognition and generate an SRT file:

1. **Run the following command:**
   ```
   whisper-faster.exe "D:\videofile.mkv" --language English --model medium --output_dir source
   ```

   - **`"D:\videofile.mkv"`**: Replace with the path to your video file.
   - **`--language English`**: Specify the language for text recognition.
   - **`--model medium`**: Choose the model size (small, medium, large, etc.).
   - **`--output_dir source`**: Specify the directory where the generated SRT file will be saved.

This command will recognize the English text in the video and output it as an SRT file in the specified directory.

### Step 2: Editing Subtitles with Subtitle Edit

1. **Open Subtitle Edit:**
   - Launch the Subtitle Edit program on your computer.

2. **Load the SRT File:**
   - Go to `File > Open` and select the SRT file generated in the previous step.

3. **Editing Subtitles:**
   - You can now review, edit, and translate the subtitles. Subtitle Edit offers a variety of tools for fine-tuning timing, splitting, merging, and translating subtitles.

4. **Saving the Edited Subtitles:**
   - After making the necessary edits, save your work by going to `File > Save As` and choosing the desired format and location.

## Burning-In Subtitles to Render Video

Burning-in subtitles means embedding the subtitles directly into the video, making them a permanent part of the visual track. This process is useful when you want to ensure that subtitles are always visible, regardless of the player's subtitle support.

### Steps to Burn-In Subtitles:

1. **Prepare the Video and Subtitle Files:**
   - Ensure that you have the final edited SRT file and the video file.

2. **Using a Video Editing Tool:**
   - To burn-in subtitles, you can use video editing software such as **HandBrake**, **FFmpeg**, **Adobe Premiere Pro**, or similar tools. For example, using FFmpeg, the command might look like:

   ```
   ffmpeg -i "D:\videofile.mkv" -vf subtitles="D:\subtitles.srt" "D:\outputfile.mp4"
   ```

   - **`-i "D:\videofile.mkv"`**: Input video file.
   - **`-vf subtitles="D:\subtitles.srt"`**: Apply the subtitle filter with the specified SRT file.
   - **`"D:\outputfile.mp4"`**: Output video file with burned-in subtitles.

3. **Rendering the Video:**
   - Once the subtitles are embedded, render the video file. The output file will have the subtitles permanently overlaid.
