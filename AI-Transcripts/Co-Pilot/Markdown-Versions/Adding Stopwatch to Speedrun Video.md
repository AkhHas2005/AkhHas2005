# Adding Stopwatch to Speedrun Video  

## Me
(Now Wednesday, Jun 11)  
I'm making a long speedrun video on YouTube where the sppedrun tookm around 2 hours. I want to have a stopwatch on screen counting up the time, however in my video will be loats of cuts and I syill want the stopwatch to progress with how much actual time it took. For example I show the stopwatch for the first 5 mins then I cut to around 8 mins and show the stoipwatch again at 8 mins. The thing is that I don't know when or where the cuts will be and I want to download a 2 hour video that counts up that I can then edit with my original recording. Can you point me to a 2 hour countup video I can download for free from somehwre or if that's not possible, how shpould I do it?  

## Co-Pilot
You can download a **2-hour count-up timer video** for free from [this YouTube video](https://www.youtube.com/watch?v=Ap_NS_fejgw). It’s a simple, no-sound timer that counts up continuously, which should work well for your speedrun editing.

If you prefer a more customized approach, you could create your own timer using **Adobe After Effects**. This [tutorial](https://www.youtube.com/watch?v=FhDK12uvOBM) walks you through setting up a count-up timer with keyframes, allowing you to control the timing precisely. That way, you can match the stopwatch to your actual speedrun duration without worrying about pre-made cuts.

Would you like help with integrating the timer into your video editing workflow?  

## Me
I'm on the video you linked, but I can't download the count-up, I can only view it on Youtube, how do I download it?  

## Co-Pilot
Downloading YouTube videos directly from the platform isn't officially supported unless you have **YouTube Premium**, which allows offline viewing within the app. However, there are alternative methods you can explore:

1. **YouTube Premium** – If you subscribe, you can download videos for offline viewing, but they remain within the YouTube app.
2. **Online Downloaders** – Websites like **4K Video Downloader** or **ClipGrab** allow you to save YouTube videos to your device  [tomshardware.com](https://www.tomshardware.com/how-to/download-youtube-videos)  [clipchamp.com](https://clipchamp.com/en/blog/download-youtube-videos/).
3. **Browser Extensions** – Some Firefox and Chrome extensions can help download videos, though availability may vary  [clipchamp.com](https://clipchamp.com/en/blog/download-youtube-videos/).
4. **Command-Line Tools** – If you're comfortable with tech, **youtube-dl** or **yt-dlp** are open-source tools that let you download videos  [tomshardware.com](https://www.tomshardware.com/how-to/download-youtube-videos).

Keep in mind that downloading videos without permission may violate YouTube’s terms of service. If you want a **custom stopwatch**, you could create one using **Adobe After Effects** or a simple Python script with OpenCV.

Would you like guidance on setting up a custom timer instead?  

## Me
I get this message when I try to download it [Uploade Image Expired], how can I make a script in Python that generates a video of a stopwatch counting up from a start time stamp that I enter to an end time stamp in hours, minutes and seconds and tehn lets me download/save the video as mp4 at a fiole path of my choice?  

## Co-Pilot
You can create a Python script using **MoviePy** and **OpenCV** to generate a stopwatch video that counts up from a specified start time to an end time. Here's a complete script to achieve this:

### Steps the script will follow:
1. Accept a **start timestamp** (hours, minutes, seconds).
2. Accept an **end timestamp** (hours, minutes, seconds).
3. Generate frames displaying the current elapsed time.
4. Save the final video as an MP4 file at the desired location.

### Python Script:
```python
import cv2
import numpy as np
from moviepy.editor import VideoClip

def generate_stopwatch_video(start_time, end_time, file_path):
    start_seconds = start_time[0] * 3600 + start_time[1] * 60 + start_time[2]
    end_seconds = end_time[0] * 3600 + end_time[1] * 60 + end_time[2]
    duration = end_seconds - start_seconds

    def make_frame(t):
        total_seconds = int(t) + start_seconds
        hours, remainder = divmod(total_seconds, 3600)
        minutes, seconds = divmod(remainder, 60)
        time_str = f"{hours:02}:{minutes:02}:{seconds:02}"

        frame = np.zeros((200, 400, 3), dtype=np.uint8)  # Black background
        cv2.putText(frame, time_str, (50, 100), cv2.FONT_HERSHEY_SIMPLEX, 2, (255, 255, 255), 3, cv2.LINE_AA)
        return frame

    video = VideoClip(make_frame, duration=duration)
    video.write_videofile(file_path, fps=24)

# Example usage:
start_time = (0, 0, 0)  # Start at 00:00:00
end_time = (2, 0, 0)    # End at 02:00:00
file_path = "stopwatch_video.mp4"

generate_stopwatch_video(start_time, end_time, file_path)
```

### Explanation:
- The script calculates the total elapsed **seconds** from the provided timestamps.
- It creates video frames dynamically using OpenCV.
- The stopwatch text is updated per frame and embedded on a blank video background.
- The **final video** is exported as an MP4 file with a **24 FPS** frame rate.

This method ensures that the stopwatch correctly follows your intended speedrun timing even with cuts. Would you like additional features, such as **custom colors or fonts** for the stopwatch display?  

## Me
what would be the pip install commands for MoviePy and OpenCV  

## Co-Pilot
You can install **MoviePy** and **OpenCV** using the following commands:

```sh
pip install moviepy
pip install opencv-python
```

If you also need OpenCV’s **full package** with extra functionalities, use:

```sh
pip install opencv-python-headless
```

This version is useful if you **don’t** need OpenCV’s GUI features (e.g., window display functions) and just want the core processing capabilities.

Let me know if you run into any installation issues! 🚀  

## Me
Traceback (most recent call last):  
```
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\video\VideoClip.py", line 342, in write_videofile
    codec = extensions_dict[ext]["codec"][0]
            ~~~~~~~~~~~~~~~^^^^^
KeyError: ''
```  
During handling of the above exception, another exception occurred:  
```
Traceback (most recent call last):
  File "c:\Users\fifau\Downloads\generate_time_video.py", line 35, in <module>
    generate_stopwatch_video(start_time, end_time, file_path)
  File "c:\Users\fifau\Downloads\generate_time_video.py", line 21, in generate_stopwatch_video
    video.write_videofile(file_path, fps=30)
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 53, in requires_duration
    return func(clip, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 153, in wrapper
    return func(clip, *new_args, **new_kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 24, in convert_masks_to_RGB
    return func(clip, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 102, in wrapper
    return func(*new_args, **new_kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\video\VideoClip.py", line 344, in write_videofile
    raise ValueError(
ValueError: MoviePy couldn't find the codec associated with the filename. Provide the 'codec' parameter in write_videofile.  
```

## Co-Pilot
It looks like **MoviePy** is unable to determine the correct codec for encoding your MP4 file. You can resolve this issue by explicitly specifying the codec when calling `write_videofile`.

Try this updated line in your script:

```python
video.write_videofile(file_path, fps=30, codec="libx264")
```

### Why this happens:
- `MoviePy` tries to determine the codec based on your file extension, but sometimes it fails.
- `"libx264"` is a commonly used codec for MP4 videos and should work.
- Some systems might require **FFmpeg** installed for proper video encoding.

If you still encounter issues, try installing or updating **FFmpeg** using:

```sh
pip install imageio[ffmpeg]
```

Let me know if this solves the problem or if the error persists!  

## Me
Enter the hour of the starting time (Press Enter if 0): 0  
Enter the minute of the starting time: 0  
Enter the second of the starting time: 0  
Enter the hour of the ending time (Press Enter if 0): 0  
Enter the minute of the ending time: 1  
Enter the second of the ending time: 36  
Enter the filepath for where to save it: C:\Users\fifau\Videos\Screen Recordings\Memes-Effects-Sounds  
MoviePy - Building video C:\Users\fifau\Videos\Screen Recordings\Memes-Effects-Sounds.  
MoviePy - Writing video C:\Users\fifau\Videos\Screen Recordings\Memes-Effects-Sounds  

```
frame_index:   0%|                                                    | 2/2880 [00:00<03:56, 12.15it/s, now=None]
Traceback (most recent call last):
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\video\io\ffmpeg_writer.py", line 169, in write_frame
    self.proc.stdin.write(img_array.tobytes())
BrokenPipeError: [Errno 32] Broken pipe

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "c:\Users\fifau\Downloads\generate_time_video.py", line 35, in <module>
    generate_stopwatch_video(start_time, end_time, file_path)
  File "c:\Users\fifau\Downloads\generate_time_video.py", line 21, in generate_stopwatch_video
    video.write_videofile(file_path, fps=30, codec="libx264")
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 53, in requires_duration
    return func(clip, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 153, in wrapper
    return func(clip, *new_args, **new_kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 24, in convert_masks_to_RGB
    return func(clip, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Roaming\Python\Python312\site-packages\decorator.py", line 232, in fun
    return caller(func, *(extras + args), **kw)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\decorators.py", line 102, in wrapper
    return func(*new_args, **new_kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\video\VideoClip.py", line 393, in write_videofile
    ffmpeg_write_video(
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\video\io\ffmpeg_writer.py", line 295, in ffmpeg_write_video
    writer.write_frame(frame)
  File "C:\Users\fifau\AppData\Local\Programs\Python\Python312\Lib\site-packages\moviepy\video\io\ffmpeg_writer.py", line 221, in write_frame
    raise IOError(error)
OSError: [Errno 32] Broken pipe

MoviePy error: FFMPEG encountered the following error while writing file C:\Users\fifau\Videos\Screen Recordings\Memes-Effects-Sounds:

 [AVFormatContext @ 00000225bbf10840] Unable to choose an output format for 'C:\Users\fifau\Videos\Screen Recordings\Memes-Effects-Sounds'; use a standard extension for the filename or specify the format manually.
[out#0 @ 00000225bbec3b00] Error initializing the muxer for C:\Users\fifau\Videos\Screen Recordings\Memes-Effects-Sounds: Invalid argument
Error opening output file C:\Users\fifau\Videos\Screen Recordings\Memes-Effects-Sounds.
Error opening output files: Invalid argument
```  

## Copilot
You're encountering a **MoviePy FFMPEG error** because the filename you provided **does not have a file extension**. 

### **Fix: Add `.mp4` to the filename**
Modify the file path like this:

```python
file_path = "C:\\Users\\fifau\\Videos\\Screen Recordings\\Memes-Effects-Sounds.mp4"
```

Then rerun your script with this proper **MP4 file extension**.

### **Why this happens?**
- MoviePy relies on the file extension (`.mp4`, `.avi`, `.mov`) to determine the **correct output format**.
- If no extension is provided, **FFMPEG fails to choose a format** and throws an error.

Once you've updated the filename, give it another shot and let me know how it goes! 🚀  

*End of this Conversation*
